---
name: Build an airport operations board with AeroAPI
description: Assemble a live departures/arrivals board for an airport, with delay status and current weather, from AeroAPI.
api: openapi/flightaware-airports-api-openapi.yml
operations: [get_airports_canonical, get_airport, get_airport_flights, get_airport_flights_departed, get_airport_flights_arrived, get_airport_delays, get_airport_weather_observations]
generated: '2026-09-10'
method: generated
source: openapi/flightaware-airports-api-openapi.yml (AeroAPI 4.30.0)
---

# Build an airport operations board with AeroAPI

## Auth

`x-apikey: <your key>` header. Base URL `https://aeroapi.flightaware.com/aeroapi`.

## Resolve the airport code first

AeroAPI models **three** parallel code schemes as first-class members — `code_icao` (KIAH),
`code_iata` (IAH) and `code_lid` (the FAA Location Identifier). They are not interchangeable and
they are not collapsed into one field. If you are unsure which scheme you hold, call
`get_airports_canonical` — `GET /airports/{id}/canonical` — with `id_type` set to `icao`, `iata` or
`lid`. Anything else returns 400.

> Do not use the `alternate_ident` field you may see in older responses. It is marked
> `deprecated: true` in the contract; use `code_iata` or `code_lid`.

1. **Airport detail.** `get_airport` — `GET /airports/{id}` for name, location, timezone.

## Board contents

2. **Everything at once.** `get_airport_flights` — `GET /airports/{id}/flights` returns scheduled
   and actual arrivals and departures in one call. Start here; it is one result set rather than
   several.

3. **Split boards when you need them.** `get_airport_flights_departed` —
   `GET /airports/{id}/flights/departures` — and `get_airport_flights_arrived` —
   `GET /airports/{id}/flights/arrivals`.
   - `airline` and `type` query parameters **cannot both be set**; doing so returns 400.

4. **Delay status.** `get_airport_delays` — `GET /airports/{id}/delays`. For a network-wide view use
   `get_delays_for_all_airports` — `GET /airports/delays`.

5. **Weather.** `get_airport_weather_observations` —
   `GET /airports/{id}/weather/observations`. The response carries `raw_data`, the untouched METAR
   report string, alongside decoded members — so if you already speak METAR, use `raw_data` and
   ignore the decode. `get_airport_weather_forecast` returns the TAF equivalent, and 404s honestly
   when no forecast is currently available.

## Conventions you must honor

- **Cost control is the main design decision here.** A board refresh is a paginated collection call,
  and AeroAPI bills per result set. Prefer one `get_airport_flights` call over separate arrival and
  departure calls, keep `max_pages` low, and cache between refreshes. Personal-tier keys are capped
  at 10 result sets per minute, which a naive board will exhaust in seconds.
- **Pagination**: `cursor` + `max_pages` in, `links.next` + `num_pages` out.
- **Errors**: `{title, reason, detail, status}`. The dominant 400 is "Id must be a valid airport
  code and cannot be empty."
- **Read-only** — no idempotency or reversibility concerns.

## Linking a board row to a flight

Each row carries an `fa_flight_id`. Hand that to the flight-tracking flow
(`skills/flightaware-track-a-flight.md`) for position, track and route. Rows also carry
`inbound_fa_flight_id` — the previous leg of the same airframe — which is how you explain a
departure delay by pointing at a late inbound.
