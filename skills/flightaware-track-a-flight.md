---
name: Track a flight with AeroAPI
description: Resolve a flight number or tail number to a FlightAware fa_flight_id, then pull its current position, full track and filed route.
api: openapi/flightaware-flights-api-openapi.yml
operations: [get_flights_by_search, get_flight, get_flights_canonical, get_flight_position, get_flight_track, get_flight_route]
generated: '2026-09-10'
method: generated
source: openapi/flightaware-flights-api-openapi.yml (AeroAPI 4.30.0)
---

# Track a flight with AeroAPI

## Auth

Every request carries `x-apikey: <your key>` as a request header. There is no OAuth, no scopes and
no bearer token. Base URL: `https://aeroapi.flightaware.com/aeroapi`.

## The one rule that governs this whole flow

AeroAPI keys the flight surface on **`fa_flight_id`**, an opaque per-flight identifier — not on the
flight number. Calling `get_flight_position`, `get_flight_track` or `get_flight_route` with a bare
ident returns HTTP 400 `"Id may be missing or may not be fa_flight_id format."` So always resolve
first.

## Steps

1. **Resolve the identifier.** If you were given a flight number (`UAL1234`) or a tail number
   (`N12345`), call `get_flight` — `GET /flights/{ident}`. It returns the recent and scheduled
   flights matching that ident, each with its own `fa_flight_id`.
   - If the ident is ambiguous between a registration and a designator, set `ident_type` explicitly.
   - If you need FlightAware's canonical form of an ident, call `get_flights_canonical` —
     `GET /flights/{ident}/canonical`.
   - If you were given criteria rather than an ident (a route, a bounding box, an operator), use
     `get_flights_by_search` — `GET /flights/search`.

2. **Pick the right flight.** `get_flight` can return several legs. Choose by scheduled departure
   time and origin/destination, not by array position.

3. **Get the current position.** `get_flight_position` — `GET /flights/{id}/position`, passing the
   `fa_flight_id` as `{id}`.

4. **Get the full track.** `get_flight_track` — `GET /flights/{id}/track`. This is a position time
   series; each point carries its provenance (ADS-B, MLAT, radar, datalink, estimated).
   - A 404 here means *no track data exists*, not that the id is wrong. Treat it as an empty
     result and do not retry.
   - A 400 with "Aircraft may be blocked" means the owner has suppressed tracking for that airframe.

5. **Get the filed route.** `get_flight_route` — `GET /flights/{id}/route`. Same 404 semantics.

## Conventions you must honor

- **Pagination is cursor-based and BILLABLE.** Collection responses carry `links.next` and
  `num_pages`; `cursor` and `max_pages` are the request parameters. AeroAPI meters per *result set*,
  so raising `max_pages` multiplies the cost of a single call. Follow `links.next` deliberately
  rather than setting a large `max_pages`.
- **Errors** are `{title, reason, detail, status}` on `application/json; charset=UTF-8` — RFC
  7807-shaped but not RFC 9457. `reason` is the stable discriminator. See
  `errors/flightaware-problem-types.yml`.
- **No 401/429/5xx is declared in the contract**, but 401 `INVALID_API_KEY` is definitely returned.
  Handle it even though the spec does not mention it.
- **No rate-limit headers.** Your headroom is a tier attribute (10 result sets/minute on Personal,
  5/second on Standard, 100/second on Premium), not a response header. Poll `get_account_usage` —
  `GET /account/usage` — if you need to know your consumption.
- **This flow is entirely read-only**, so idempotency and reversibility do not apply. Retrying is
  always safe (and always billable).

## Want predictions too?

The Foresight mirrors of these operations add ML-predicted arrival and gate times:
`get_flight_with_foresight` (`GET /foresight/flights/{ident}`) and
`get_flight_position_with_foresight` (`GET /foresight/flights/{id}/position`). The non-Foresight
responses carry a `foresight_predictions_available` flag — check it before making the more
expensive call. Foresight requires the Premium tier.
