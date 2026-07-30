---
name: Invite WebRTC guests to an API.stream broadcast
description: Mint guest access tokens, redeem guest codes and start or stop the WebRTC room for a project so collaborators and guests can join a live broadcast.
api: openapi/lightstream-live-openapi-original.yml
operations:
  - AuthenticationService_CreateGuestAccessToken
  - PublicAuthenticationService_GuestCodeRedirect
  - ProjectService_StartProjectWebRtc
  - ProjectService_StopProjectWebRtc
  - ProjectService_GetProject
  - ProjectService_UpdateProject
generated: '2026-07-19'
method: generated
source: https://www.api.stream/docs/api/auth/
---

# Invite WebRTC guests

Base URL: `https://live.api.stream/live/v2`. The host's calls use
`Authorization: Bearer <host access token>`.

## Steps

1. **Start the WebRTC room.** `ProjectService_StartProjectWebRtc` —
   `PUT /collection/{collectionId}/project/{projectId}/webrtc/start`. Only roles with the
   "Start WebRTC" permission (HOST, COHOST) may do this.
2. **Mint a guest token.** `AuthenticationService_CreateGuestAccessToken` —
   `POST /authentication/token/guest`, scoped to the collection and project, with the role the
   guest should hold: `GUEST` (read + join WebRTC), `VIEWER` (read + join), or `CONTRIBUTOR`
   (adds Live and Layout write).
3. **Deliver it.** The response is either a direct token or an exchange/guest-code form. A guest
   code is redeemed through `PublicAuthenticationService_GuestCodeRedirect` —
   `GET /r/{serviceId}/{code}` — which is the public, unauthenticated landing path for a shared
   invite link. Guest codes attached to a project are visible on `ProjectService_GetProject`
   as `guestCodes`.
4. **Join.** The guest client initializes the Studio Kit (or the JS SDK) with its token and joins
   the room.
5. **Stop.** `ProjectService_StopProjectWebRtc` — `PUT .../webrtc/stop` — tears the room down.

## Permission reminders

From the published role matrix: `GUEST` and `VIEWER` can read the Live and Layout APIs and join
WebRTC, but cannot write, invite further guests, manage the broadcast or start WebRTC.
`CONTRIBUTOR` adds Live and Layout write. Only `HOST` and `COHOST` can invite guests and manage
the broadcast. Grant the narrowest role that works.

## Notes

- Guest tokens are minted with a normal access token, not the API key — never expose the API key
  to do this.
- There is no idempotency key; minting a token twice yields two valid tokens.
- Refresh long-lived guest sessions with `AuthenticationService_RefreshAccessToken`.
