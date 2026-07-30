---
name: Publish and subscribe to API.stream events
description: Use the API.stream Event API to stream broadcast, source, destination and layout events and to publish custom application events scoped to a collection, project or layout.
api: openapi/lightstream-event-openapi-original.yml
operations:
  - EventService_Stream
  - EventService_Publish
generated: '2026-07-19'
method: generated
source: https://www.api.stream/docs/api/event/rest/
---

# Publish and subscribe to events

Base URL: `https://live.api.stream/event/v2`. Auth is the same
`Authorization: Bearer <access token>` minted on the Live API.

The Event API is a long-lived stream, not a webhook callback. API.stream will not POST to your
server; you hold the connection open.

## Subscribe

`EventService_Stream` — `GET /stream`.

Query parameters:
- `subscribe.name` (required) — the event name. Wildcards (`my_service:*`) and alternation
  (`my_event|my_other_event`) are supported.
- `subscribe.target.collectionId`, `subscribe.target.projectId`, `subscribe.target.layoutId` —
  the scope. Targeting a `layoutId` implies its project and collection.
- `unsubscribe.name` and matching `unsubscribe.target.*` to drop a subscription.
- `correlationId` — an arbitrary string echoed back on responses and errors so you can tie a
  reply to the request that caused it.
- `ping` — initiates a ping/pong to keep the connection healthy.

Scope inheritance: an event published against a `layoutId` is received by subscribers targeting
that layout, its project, or its collection. An event published against a `collectionId` is
received by subscribers scoped to any project or layout beneath it.

Each `EventsStreamResponse` carries one of `event`, `pong`, `error`, `subscribed`, `unsubscribed`,
`published` or `reconnectBefore`.

## Handle reconnects

When the server sends `reconnectBefore`, re-open the connection before `beforeTimestamp`. If
`reauthenticate` is true, refresh the access token first
(`AuthenticationService_RefreshAccessToken` on the Live API). If you hold many connections,
reconnect at a random point inside the window so they do not stampede.

## Publish

`EventService_Publish` — `POST /publish` with:

```json
{
  "name": "my_app:user_chat",
  "payload": { "custom_event": true },
  "requestMetadata": { "example_data": true },
  "target": { "collectionId": "...", "projectId": "...", "layoutId": "..." }
}
```

`name` is 1–128 characters. `payload` is free-form and is never inspected by API.stream — put
*what* happened there. Put *why* it happened in `requestMetadata`.

## Errors

Stream errors arrive as `EventsStreamError` with a gRPC `code` and `message`, tied to your
`correlationId`. Unary publish errors use the `rpcStatus` envelope.

An AsyncAPI 3.0 description of this surface, generated from the provider's own spec, is at
`asyncapi/lightstream-event-asyncapi.yml`.
