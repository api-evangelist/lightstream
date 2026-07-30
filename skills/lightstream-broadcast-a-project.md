---
name: Set up and run an API.stream broadcast
description: Create a collection and project, attach a live source and an RTMP destination, then start, monitor and stop a broadcast on the API.stream Live API.
api: openapi/lightstream-live-openapi-original.yml
operations:
  - BackendAuthenticationService_CreateAccessToken
  - CollectionService_CreateCollection
  - ProjectService_CreateProject
  - SourceService_CreateSource
  - SourceService_AddSourceToProject
  - DestinationService_CreateDestination
  - ProjectService_StartProjectBroadcast
  - ProjectService_GetProjectBroadcastStatus
  - ProjectService_GetProjectBroadcastSnapshot
  - ProjectService_StopProjectBroadcast
generated: '2026-07-19'
method: generated
source: https://www.api.stream/docs/api/live/rest/
---

# Set up and run a broadcast

Base URL: `https://live.api.stream/live/v2`. Every call below uses
`Authorization: Bearer <access token>`.

## Steps

1. **Get a token.** `BackendAuthenticationService_CreateAccessToken` — see the
   `lightstream-authenticate-partner-user` skill.
2. **Create a collection.** `CollectionService_CreateCollection` — `POST /collection`.
   A collection is the tenancy object that owns projects and collection-level sources.
   Keep the returned `collectionId`.
3. **Create a project.** `ProjectService_CreateProject` —
   `POST /collection/{collectionId}/project`. Set `rendering.video.width` / `height`
   (for example 1920x1080). Optionally pass `location` as `{latitude, longitude}` to hint at a
   region for lower latency; this is only a hint.
4. **Create a live source.** `SourceService_CreateSource` —
   `POST /collection/{collectionId}/source`. Choose the address type your ingest uses
   (RTMP push, SRT push, RTMP pull, or WebRTC).
5. **Attach the source to the project.** `SourceService_AddSourceToProject` —
   `PUT /collection/{collectionId}/project/{projectId}/source/{sourceId}`.
6. **Add a destination.** `DestinationService_CreateDestination` —
   `POST /collection/{collectionId}/project/{projectId}/destination`. Set the RTMP push URL and
   key, and `enabled: true`.
7. **Start.** `ProjectService_StartProjectBroadcast` —
   `PUT /collection/{collectionId}/project/{projectId}/broadcast/start`.
8. **Monitor.** Poll `ProjectService_GetProjectBroadcastStatus` —
   `GET .../broadcast/status` — for `phase`, `duration` and the actual `region`/`datacenter` the
   broadcast landed in. `ProjectService_GetProjectBroadcastSnapshot` returns a still frame.
   For push-based monitoring, subscribe on the Event API instead of polling.
9. **Stop.** `ProjectService_StopProjectBroadcast` — `PUT .../broadcast/stop`.

## Conventions that will bite you

- **Updates need a field mask.** `ProjectService_UpdateProject`,
  `DestinationService_UpdateDestination` and the other PATCH operations take `updateMask` — an
  array of dotted paths such as `address.rtmpPush.url`. Over REST you may omit it and the gateway
  infers it from the fields you send; over gRPC it is mandatory.
- **No idempotency key.** Retrying a create will create a second object. Guard retries yourself.
- **No pagination.** `CollectionService_GetCollections` and `SourceService_GetSources` return full
  arrays.
- **429 = busy.** Back off exponentially. `401` is an invalid token, `403` is a role that lacks the
  permission.
- **Development accounts cap broadcast duration** at a few minutes — expect a short broadcast to
  end on its own in testing.
