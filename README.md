# Lightstream

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

Lightstream (Infiniscene, Inc.) is a Techstars-backed live video company best known for Lightstream Studio, a browser-based streaming studio used by creators to broadcast to Twitch, YouTube and other destinations without installing desktop encoding software. Lightstream also operates API.stream, its developer platform, which exposes the same cloud video pipeline to development partners as three API-first services: a Live API for managing collections, projects, sources, destinations and broadcasts; a Layout API for building and animating layered scene compositions; and an Event API for publishing and subscribing to real-time events across collaborators, guests and renderers. All three services are defined as gRPC Protobuf contracts and fronted by gRPC-Web and REST gateways, secured with a JWT access-token model and role-based permissions (HOST, COHOST, CONTRIBUTOR, GUEST, VIEWER), with first-party JavaScript/TypeScript SDKs and a Studio Kit for embedding a full studio experience.

**Areas:** Company · Video · Live Streaming · Broadcasting · WebRTC · RTMP · Media · Compositing · Real-Time · Event · gRPC · Creator Tools

## Lightstream on APIs.io

Everything profiled for Lightstream is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/lightstream/](https://apis.io/providers/lightstream/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [Lightstream BackendAuthenticationService API](https://apis.io/apis/lightstream/lightstream-backendauthenticationservice-api/) — The Backend Authentication Service provides token services for partner backend systems
- [Lightstream CollectionService API](https://apis.io/apis/lightstream/lightstream-collectionservice-api/) — The Collection Service operates on collections, which contain projects and collection live sources used in projects.
- [Lightstream DestinationService API](https://apis.io/apis/lightstream/lightstream-destinationservice-api/) — The Destination Service operates on Project Destinations. Destinations designate where a Broadcast associated with a Project is distributed downstream.
- [Lightstream LayerService API](https://apis.io/apis/lightstream/lightstream-layerservice-api/) — Layers
- [Lightstream LayoutService API](https://apis.io/apis/lightstream/lightstream-layoutservice-api/) — Layouts
- [Lightstream ProjectService API](https://apis.io/apis/lightstream/lightstream-projectservice-api/) — The Project Service operates on a Project.
- [Lightstream PublicAuthenticationService API](https://apis.io/apis/lightstream/lightstream-publicauthenticationservice-api/) — The Public Authentication Service provides token verification services
- [Lightstream SourceService API](https://apis.io/apis/lightstream/lightstream-sourceservice-api/) — The Source Service operates on Collection Live Sources and Project Sources.
- [Lightstream Authentication Service API](https://apis.io/apis/lightstream/lightstream-authentication-service-api/) — The Authentication Service provides token services for clients
- [Lightstream Event Service API](https://apis.io/apis/lightstream/lightstream-event-service-api/) — The event API provides a mechanism for you to subscribe and publish events between your backend services and the composition, as well as receive events from…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [API.stream Event API](https://apis.io/asyncapis/lightstream/lightstream-event-asyncapi/)

#### Event channels (2)

Individual events and webhooks the provider emits.

- [/publish](https://apis.io/channels/lightstream/publish/)
- [/stream](https://apis.io/channels/lightstream/stream/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [api.stream](https://apis.io/servers/lightstream/api-stream/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Lightstream Agentic Access](https://apis.io/agentic-access/lightstream/lightstream-agentic-access/)

#### Collections (10)

Postman and Open Collection request collections.

- [Event AuthenticationService API](https://apis.io/collections/lightstream/open-lightstream-authenticationservice-api/)
- [Event AuthenticationService BackendAuthenticationService API](https://apis.io/collections/lightstream/open-lightstream-backendauthenticationservice-api/)
- [Event AuthenticationService CollectionService API](https://apis.io/collections/lightstream/open-lightstream-collectionservice-api/)
- [Event AuthenticationService DestinationService API](https://apis.io/collections/lightstream/open-lightstream-destinationservice-api/)
- [Event AuthenticationService EventService API](https://apis.io/collections/lightstream/open-lightstream-eventservice-api/)
- [Event AuthenticationService LayerService API](https://apis.io/collections/lightstream/open-lightstream-layerservice-api/)
- [Event AuthenticationService LayoutService API](https://apis.io/collections/lightstream/open-lightstream-layoutservice-api/)
- [Event AuthenticationService ProjectService API](https://apis.io/collections/lightstream/open-lightstream-projectservice-api/)
- [Event AuthenticationService PublicAuthenticationService API](https://apis.io/collections/lightstream/open-lightstream-publicauthenticationservice-api/)
- [Event AuthenticationService SourceService API](https://apis.io/collections/lightstream/open-lightstream-sourceservice-api/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Lightstream Event Overlay](https://apis.io/overlays/lightstream/lightstream-event-overlay/)
- [Lightstream Layout Overlay](https://apis.io/overlays/lightstream/lightstream-layout-overlay/)
- [Lightstream Live Overlay](https://apis.io/overlays/lightstream/lightstream-live-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Lightstream Authentication](https://apis.io/security/lightstream/lightstream-authentication/)
- [Lightstream Domain Security](https://apis.io/security/lightstream/lightstream-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://golightstream.com/)
- [Documentation](https://www.api.stream/docs/)
- [Getting started](https://www.api.stream/docs/)
- [API reference](https://www.api.stream/docs/api/live/rest/)
- [Pricing](https://golightstream.com/studio/#plans)
- [Sign up](https://studio.golightstream.com/welcome)
- [Support](https://golightstream.com/support/)
- [Blog](https://golightstream.com/blog)
- [Terms of service](https://api.stream/terms-of-service/)
- [Privacy policy](https://api.stream/privacy-policy/)
- [GitHub](https://github.com/golightstream)
- [Status](https://status.api.stream/)

## API Evangelist rating

**Kin Score 46.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 59.5 |
| Contract governance | 4.5 |
| Operational transparency | 34.2 |
| Developer ergonomics | 68.5 |
| Access clarity | 21.1 |

**Agent readiness 25.0** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | yes |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/lightstream/](https://apis.io/providers/lightstream/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Lightstream: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/lightstream/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
