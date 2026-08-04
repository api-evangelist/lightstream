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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Lightstream (Infiniscene, Inc.) is a Techstars-backed live video company best known for
**Lightstream Studio**, a browser-based streaming studio used by creators to broadcast to Twitch,
YouTube and other destinations without desktop encoding software.

Lightstream also operates **API.stream**, its developer platform, which exposes the same cloud
video pipeline to development partners as three API-first services:

| API | Base URL | Reference |
|---|---|---|
| Live API (2.1) | `https://live.api.stream/live/v2` | https://www.api.stream/docs/api/live/rest/ |
| Layout API (2.0) | `https://live.api.stream/layout/v2` | https://www.api.stream/docs/api/layout/rest/ |
| Event API (2.0) | `https://live.api.stream/event/v2` | https://www.api.stream/docs/api/event/rest/ |

All three are defined as gRPC Protobuf contracts and fronted by gRPC-Web and REST gateways,
secured with a JWT access-token model and role-based permissions (HOST, COHOST, CONTRIBUTOR,
GUEST, VIEWER). First-party SDKs ship on npm under `@api.stream`, including the Studio Kit for
embedding a full studio into a partner application.

- Website — https://golightstream.com/
- Developer portal — https://www.api.stream/
- Documentation — https://www.api.stream/docs/
- Status — https://status.api.stream/
- GitHub — https://github.com/golightstream

Backed by: techstars
