---
name: Authenticate a partner user with API.stream
description: Mint an API.stream access token on behalf of an end user from a partner backend, then hand it to the client — the mandatory first step for every other API.stream flow.
api: openapi/lightstream-live-openapi-original.yml
operations:
  - BackendAuthenticationService_CreateAccessToken
  - AuthenticationService_RefreshAccessToken
  - PublicAuthenticationService_GetJsonWebKeySet
generated: '2026-07-19'
method: generated
source: https://www.api.stream/docs/api/auth/
---

# Authenticate a partner user

API.stream never authenticates end users. The partner authenticates its own user, then exchanges
an opaque user identifier for an API.stream access token.

Base URL: `https://live.api.stream/live/v2`

## Rules

- The secret API key (`X-API-Key`) is valid on **exactly one** operation:
  `BackendAuthenticationService_CreateAccessToken`. Never send it anywhere else.
- A **Production** API key must only be used server-side. A **Development** API key may be embedded
  in a client for testing, but the tokens it mints are limited in capability, duration and scope,
  and its broadcasts are limited to a few minutes.
- `serviceUserId` is an opaque string chosen by the partner. API.stream stores no personal data.
- Errors use the `rpcStatus` envelope (`code`, `message`, `details[]`). A `429` means the service is
  busy — retry with exponential backoff.

## Steps

1. Authenticate the user on your own system. API.stream is not involved.
2. From your backend, call `BackendAuthenticationService_CreateAccessToken`:
   `POST /authentication/token` with header `X-API-Key: <your api key>` and body
   `{ "serviceUserId": "<opaque user id>", "displayName": "<display name>" }`.
   Optionally set a `role` — one of `HOST`, `COHOST`, `CONTRIBUTOR`, `GUEST`, `VIEWER`.
3. Relay the returned `accessToken` to your client. The client sends it as
   `Authorization: Bearer <accessToken>` on every subsequent Live, Layout and Event call.
4. Before the token expires, call `AuthenticationService_RefreshAccessToken`
   (`PUT /authentication/token`) with the current bearer token.
5. If you need to verify a token signature yourself, fetch the key set with
   `PublicAuthenticationService_GetJsonWebKeySet` (`GET /authentication/jwks`).

## Role capabilities

`HOST` and `COHOST` get everything. `CONTRIBUTOR` gets Live/Layout read and write plus WebRTC join.
`GUEST` and `VIEWER` are read plus WebRTC join only — they cannot write, invite guests, manage a
broadcast or start WebRTC.
