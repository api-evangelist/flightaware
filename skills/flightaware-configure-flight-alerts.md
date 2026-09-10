---
name: Configure AeroAPI flight alerts (push webhooks)
description: Set up an account-wide delivery endpoint and manage AeroAPI push alerts for departure, arrival, cancellation and diversion events.
api: openapi/flightaware-alerts-api-openapi.yml
operations: [set_alerts_endpoint, get_alerts_endpoint, create_alert, get_all_alerts, get_alert, update_alert, delete_alert, delete_alerts_endpoint]
generated: '2026-09-10'
method: generated
source: openapi/flightaware-alerts-api-openapi.yml (AeroAPI 4.30.0)
---

# Configure AeroAPI flight alerts

This is the **only mutating surface in AeroAPI**. Read the reversibility notes before you write
anything.

## Auth

`x-apikey: <your key>` header. Base URL `https://aeroapi.flightaware.com/aeroapi`.

## Order matters — the endpoint comes first

1. **Set the account-wide delivery URL** with `set_alerts_endpoint` —
   `PUT /alerts/endpoint`. This must happen **before** your first alert. If you skip it,
   `create_alert` returns 400 with a message reminding you of exactly this step.

   > **This setting is account-wide.** Every alert that does not carry its own `target_url` is
   > delivered here. Changing it silently reroutes the whole account's deliveries. Call
   > `get_alerts_endpoint` — `GET /alerts/endpoint` — and keep the previous value before you
   > overwrite it; there is no undo and no history.

2. **Create an alert.** `create_alert` — `POST /alerts`. Supply matching criteria (`ident`,
   `origin`, `destination`, `aircraft_type`, date range) and at least one event. Set `target_url`
   on the alert itself when you want per-application or per-environment routing without touching
   the account default.

## The event set

`filed`, `departure`, `out`, `off`, `on`, `in`, `arrival`, `cancelled`, `diverted`.

Two of them are **bundled** and produce more than one delivery:

- `departure` bundles the actual-off alert with the flight-plan-filed alert and up to five
  per-departure changes (delays over 30 minutes, gate changes, airport delays). FlightAware Global
  accounts also get *Power on* and *Ready to taxi*.
- `arrival` bundles the actual-on alert with up to five en-route changes (diversions excluded).
  Global accounts also get taxi-stop times.

Setting both a bundled type and its unbundled component (`departure` and `off`) yields a single
alert where they overlap, not two.

## Managing alerts

3. **List** with `get_all_alerts` — `GET /alerts` — to recover ids.
4. **Read one** with `get_alert` — `GET /alerts/{id}`.
5. **Change one** with `update_alert` — `PUT /alerts/{id}`. **Always update rather than creating a
   second alert.** The contract says so explicitly, and there is no idempotency key: a retried
   `POST /alerts` produces a duplicate configuration and duplicate deliveries.
6. **Delete** with `delete_alert` — `DELETE /alerts/{id}`.

## Reversibility — know this before you act

| Action | Reversible? | How |
|---|---|---|
| `create_alert` | Yes | `delete_alert` on the returned id |
| `update_alert` | **No** | The prior configuration is not retained. `get_alert` and keep the old body yourself if you need to roll back. |
| `delete_alert` | Recreatable, not restorable | A new `create_alert` yields a **new id**; anything keyed on the old id will not match. |
| `set_alerts_endpoint` | Only if you kept the old value | `get_alerts_endpoint` before writing |
| `delete_alerts_endpoint` | Yes | `set_alerts_endpoint` again — but while unset, alerts without their own `target_url` have nowhere to go |

**No window is published for any of these.** FlightAware states no retention, grace or undo period,
so treat every delete as immediate and permanent.

## Errors

`{title, reason, detail, status}`. The ones you will actually hit:

- 400 "Invalid parameters specified ... or alert configured would trigger more than [permitted]" —
  narrow the criteria.
- 400 "Bad address, missing hostname, or unsupported address protocol" — from
  `set_alerts_endpoint`; supply an HTTPS URL.
- 400 "Failed to get endpoint or no endpoint set" — you skipped step 1.
- 404 "No such alert exists" — the id does not belong to this key.

There is no dry-run mode, so the "would trigger more than" ceiling is only discoverable by
attempting the create.

## Testing delivery

FlightAware publishes a push-notification testing interface at
<https://www.flightaware.com/commercial/aeroapi/send.rvt> (signed-in browser tool) for exercising
delivery to your endpoint. The alert *payload* schema is not in the OpenAPI — the contract covers
configuring alerts, not the shape of what gets POSTed to you.
