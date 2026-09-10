---
name: Research historical flights with AeroAPI
description: Pull past flights, tracks, routes and airport/operator boards from AeroAPI history, and manage the cost and entitlement limits that govern them.
api: openapi/flightaware-history-api-openapi.yml
operations: [get_history_flight, get_history_flight_track, get_history_flight_route, get_history_aircraft_last_flight, get_history_airports_flights_arrived, get_history_airports_flights_departed, get_history_operators_flights, get_account_usage]
generated: '2026-09-10'
method: generated
source: openapi/flightaware-history-api-openapi.yml, openapi/flightaware-account-api-openapi.yml (AeroAPI 4.30.0)
---

# Research historical flights with AeroAPI

## Auth

`x-apikey: <your key>` header. Base URL `https://aeroapi.flightaware.com/aeroapi`.

## Two limits govern every call here

1. **Your historical depth is an account entitlement, not an API parameter.** The same query
   succeeds on one account and returns 400 "Request may be for data before earliest date" on
   another. There is no operation that reports your depth — you discover it by hitting the wall.
2. **Historical queries are metered separately** and are capped at 500,000 result sets per month on
   the Standard and Premium tiers. The Personal tier has **no historical access at all**.

## Steps

1. **Find the flight.** `get_history_flight` — `GET /history/flights/{ident}`. Takes a flight
   number or registration and a time window. Returns past flights, each with its `fa_flight_id`.
   - Same rule as the live surface: everything downstream keys on `fa_flight_id`, never on the ident.

2. **Pull the track.** `get_history_flight_track` — `GET /history/flights/{id}/track`.
   **Pull the route.** `get_history_flight_route` — `GET /history/flights/{id}/route`.
   A 400 here usually means the id is not in `fa_flight_id` format; a 404 means the data does not
   exist for that flight.

3. **Last flight for an airframe.** `get_history_aircraft_last_flight` —
   `GET /history/aircraft/{registration}/last_flight`. The quickest way to answer "where did N12345
   go last?" without a window search.

4. **Historical boards.** `get_history_airports_flights_arrived`
   (`GET /history/airports/{id}/flights/arrivals`) and `get_history_airports_flights_departed`
   (`GET /history/airports/{id}/flights/departures`) — the history equivalents of the live airport
   board. `get_history_operators_flights` (`GET /history/operators/{id}/flights`) does the same for
   a carrier.
   - These carry hard window constraints in the contract: `start` and `end` are **required**, and
     the span is bounded (some operations to 24 hours). Read the 400 text — it names the exact rule
     for the operation you called.
   - `airline` and `type` cannot both be set.

5. **Watch your spend.** `get_account_usage` — `GET /account/usage`. Added in AeroAPI 4.30.0 and the
   only in-band consumption signal the API offers; there are no rate-limit response headers. Poll
   it during a backfill rather than after.

## Conventions you must honor

- **Pagination is where backfills go wrong.** `cursor` + `max_pages` in, `links.next` + `num_pages`
  out. Each page is a billable result set. Walk `links.next` in a controlled loop with your own
  counter; do not set a large `max_pages` and hope.
- **Rate limits are per tier**: 5 result sets/second (Standard), 100/second (Premium). No `429` is
  declared in the contract and no `Retry-After` is returned, so back off on your own schedule.
- **Errors**: `{title, reason, detail, status}`; `reason` is the stable discriminator. See
  `errors/flightaware-problem-types.yml`.
- **Read-only** — retries are safe, and billable.

## When history is not enough

For continuous historical replay rather than point queries, Firehose supports
`pitr <epoch>` and `range <start epoch> <end epoch>` replay over its streaming socket, priced as a
flat monthly rate rather than per result set. See `asyncapi/flightaware-events.yml`.
