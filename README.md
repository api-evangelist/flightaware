# FlightAware

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
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

**Areas:** Aviation · Flights · Flight Tracking · Mapping · Radar · Satellite · Traffic Control

## FlightAware on APIs.io

Everything profiled for FlightAware is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/flightaware/](https://apis.io/providers/flightaware/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [FlightAware AeroAPI](https://apis.io/apis/flightaware/aeroapi/) — AeroAPI is FlightAware's query-based REST API for accessing aviation data on demand. It exposes 60+ endpoints across flights, airports, operators, alerts,…
- [FlightAware Firehose](https://apis.io/apis/flightaware/firehose/) — Firehose is FlightAware's real-time streaming feed of global flight data, delivering ADS-B, radar, and ATC-derived position, status, and event messages over…
- [FlightAware Airports API](https://apis.io/apis/flightaware/flightaware-airports-api/) — The airports API from FlightAware — 17 operation(s) for airports.
- [FlightAware Alerts API](https://apis.io/apis/flightaware/flightaware-alerts-api/) — AeroAPI alerting can be used to configure and receive real-time alerts on key flight events. With customizable alerting offered by our alert endpoints,…
- [FlightAware Flights API](https://apis.io/apis/flightaware/flightaware-flights-api/) — The flights API from FlightAware — 11 operation(s) for flights.
- [FlightAware Foresight API](https://apis.io/apis/flightaware/flightaware-foresight-api/) — Foresight endpoints provide access to FlightAware's Foresight predictive models and predictions for key events. Our advanced machine learning (ML) models…
- [FlightAware History API](https://apis.io/apis/flightaware/flightaware-history-api/) — The history API from FlightAware — 5 operation(s) for history.
- [FlightAware Miscellaneous API](https://apis.io/apis/flightaware/flightaware-miscellaneous-api/) — The miscellaneous API from FlightAware — 6 operation(s) for miscellaneous.
- [FlightAware Operators API](https://apis.io/apis/flightaware/flightaware-operators-api/) — The operators API from FlightAware — 8 operation(s) for operators.
- [FlightAware Account API](https://apis.io/apis/flightaware/flightaware-account-api/) — The account surface of AeroAPI — GET /account/usage, added in AeroAPI 4.30.0. It reports the calling account's AeroAPI consumption over a requested period,…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Flightaware Events](https://apis.io/asyncapis/flightaware/flightaware-events/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [flightaware-aeroapi](https://apis.io/servers/flightaware/flightaware-aeroapi/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Flightaware Agentic Access](https://apis.io/agentic-access/flightaware/flightaware-agentic-access/)

#### Collections (8)

Postman and Open Collection request collections.

- [AeroAPI](https://apis.io/collections/flightaware/open-flightaware/)
- [Aero airports API](https://apis.io/collections/flightaware/open-flightaware-airports-api/)
- [Aero airports alerts API](https://apis.io/collections/flightaware/open-flightaware-alerts-api/)
- [Aero airports flights API](https://apis.io/collections/flightaware/open-flightaware-flights-api/)
- [Aero airports foresight API](https://apis.io/collections/flightaware/open-flightaware-foresight-api/)
- [Aero airports history API](https://apis.io/collections/flightaware/open-flightaware-history-api/)
- [Aero airports miscellaneous API](https://apis.io/collections/flightaware/open-flightaware-miscellaneous-api/)
- [Aero airports operators API](https://apis.io/collections/flightaware/open-flightaware-operators-api/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Flightaware Account Api Overlay](https://apis.io/overlays/flightaware/flightaware-account-api-overlay/)
- [Flightaware Airports Api Overlay](https://apis.io/overlays/flightaware/flightaware-airports-api-overlay/)
- [Flightaware Alerts Api Overlay](https://apis.io/overlays/flightaware/flightaware-alerts-api-overlay/)
- [Flightaware Flights Api Overlay](https://apis.io/overlays/flightaware/flightaware-flights-api-overlay/)
- [Flightaware Foresight Api Overlay](https://apis.io/overlays/flightaware/flightaware-foresight-api-overlay/)
- [Flightaware History Api Overlay](https://apis.io/overlays/flightaware/flightaware-history-api-overlay/)
- [Flightaware Miscellaneous Api Overlay](https://apis.io/overlays/flightaware/flightaware-miscellaneous-api-overlay/)
- [Flightaware Operators Api Overlay](https://apis.io/overlays/flightaware/flightaware-operators-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Flightaware Authentication](https://apis.io/security/flightaware/flightaware-authentication/)
- [Flightaware Domain Security](https://apis.io/security/flightaware/flightaware-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Flightaware Plans Pricing](https://apis.io/plans/flightaware/flightaware-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Flightaware Rate Limits](https://apis.io/rate-limits/flightaware/flightaware-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Flightaware Finops](https://apis.io/finops/flightaware/flightaware-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.flightaware.com/)
- [Documentation](https://www.flightaware.com/aeroapi/portal/documentation)
- [API reference](https://www.flightaware.com/aeroapi/portal/documentation)
- [Pricing](https://www.flightaware.com/commercial/aeroapi/)
- [Sign up](https://www.flightaware.com/account/join/)
- [Support](https://www.flightaware.com/about/contact/)
- [Blog](https://blog.flightaware.com/)
- [Terms of service](https://www.flightaware.com/about/termsofuse)
- [Privacy policy](https://www.flightaware.com/about/privacy)
- [Status](https://status.flightaware.com/)

## API Evangelist rating

**Kin Score 56.7** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 60.5 |
| Contract governance | 4.5 |
| Operational transparency | 76.3 |
| Developer ergonomics | 47.0 |
| Access clarity | 76.3 |

**Agent readiness 36.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | verified |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/flightaware/](https://apis.io/providers/flightaware/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for FlightAware: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/flightaware/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
