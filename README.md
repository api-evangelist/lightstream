# Lightstream

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
