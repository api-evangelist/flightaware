# FlightAware (flightaware)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

FlightAware is a global flight tracking and data platform that provides real-time flight tracking, mapping, and predictive technology to both individual users and commercial aviation companies. The platform collects data from a variety of sources including air traffic control systems, radar, ADS-B, and satellite data, and exposes that data to developers and commercial customers through its AeroAPI query-based REST API and its Firehose streaming feed.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/flightaware/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/flightaware/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Aviation
- Flights
- Flight Tracking
- Mapping
- Radar
- Satellites
- Traffic Control

## Timestamps

- **Created:** 2025-02-24
- **Modified:** 2026-04-28

## APIs

### FlightAware AeroAPI

AeroAPI is FlightAware's query-based REST API for accessing aviation data on demand. It exposes 60+ endpoints across flights, airports, operators, alerts, history, and Foresight predictive analytics, and supports both real-time and historical flight tracking, status, positions, routes, and notifications.

- **Human URL:** [https://www.flightaware.com/aeroapi/portal/](https://www.flightaware.com/aeroapi/portal/)
- **Base URL:** `https://aeroapi.flightaware.com/aeroapi`

#### Tags

- Airports
- Alerts
- Aviation
- Flights
- Flight Tracking
- Foresight
- History
- Operators
- Predictive Analytics

#### Properties

- [Documentation](https://www.flightaware.com/aeroapi/portal/documentation)
- [Portal](https://www.flightaware.com/aeroapi/portal/)
- [Pricing](https://www.flightaware.com/commercial/aeroapi/)
- [Postman Collection](collections/flightaware.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flightaware.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### FlightAware Firehose

Firehose is FlightAware's real-time streaming feed of global flight data, delivering ADS-B, radar, and ATC-derived position, status, and event messages over a persistent TLS connection for enterprise-grade flight tracking, situational awareness, and operations analytics.

- **Human URL:** [https://www.flightaware.com/commercial/firehose/](https://www.flightaware.com/commercial/firehose/)

#### Tags

- ADS-B
- Aviation
- Flight Tracking
- Real-Time
- Streaming

#### Properties

- [Documentation](https://www.flightaware.com/commercial/firehose/documentation)
- [Product Page](https://www.flightaware.com/commercial/firehose/)
- [Postman Collection](collections/flightaware.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flightaware.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/flightaware)
- [Website](https://www.flightaware.com/)
- [Commercial Data](https://www.flightaware.com/commercial/data/)
- [Aero A P I Portal](https://www.flightaware.com/aeroapi/portal/)
- [Documentation](https://www.flightaware.com/aeroapi/portal/documentation)
- [Pricing](https://www.flightaware.com/commercial/aeroapi/)
- [Blog](https://blog.flightaware.com/)
- [Support](https://www.flightaware.com/about/contact/)
- [Privacy Policy](https://www.flightaware.com/about/privacy)
- [Terms of Service](https://www.flightaware.com/about/termsofuse)
- [Git Hub](https://github.com/flightaware)
- [Integrations](https://www.flightaware.com/apps)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
