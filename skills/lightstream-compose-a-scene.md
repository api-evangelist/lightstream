---
name: Compose and animate a scene with the API.stream Layout API
description: Build a layout, add and arrange layers, batch scene changes and switch between scenes on the API.stream Layout API for the Scene compositor workflow.
api: openapi/lightstream-layout-openapi-original.yml
operations:
  - LayoutService_CreateLayout
  - LayoutService_ListLayouts
  - LayoutService_GetLayout
  - LayoutService_UpdateLayout
  - LayoutService_DeleteLayout
  - LayerService_CreateLayer
  - LayerService_ListLayers
  - LayerService_GetLayer
  - LayerService_UpdateLayer
  - LayerService_DeleteLayer
  - LayerService_Batch
generated: '2026-07-19'
method: generated
source: https://www.api.stream/docs/api/layout/rest/
---

# Compose and animate a scene

Base URL: `https://live.api.stream/layout/v2`. Auth is the same
`Authorization: Bearer <access token>` minted on the Live API.

A **layout** is a composition document; **layers** are the elements inside it — image, video,
WebRTC track, or an arbitrary HTML/URL element. Layers nest through `children`, so a layout is a
tree, not a flat list.

## Steps

1. **Create the layout.** `LayoutService_CreateLayout` — `POST /layouts`. Set the canvas `width`
   and `height`, and any application `metadata` you want stored alongside it.
2. **Bind it to a project.** In the Live API, set the project's `composition.scene` to this layout
   so the Scene compositor renders it (`ProjectService_UpdateProject` with an `updateMask`
   covering `composition`).
3. **Add layers.** `LayerService_CreateLayer` — `POST /layouts/{layoutId}/layers`. Each layer
   carries `type`, `data`, `x`, `y`, `width`, `height`, `rotation`, `opacity`, `scale`, `hidden`
   and `children`.
4. **Change several layers atomically.** `LayerService_Batch` —
   `POST /layouts/{layoutId}/layers/batch`. Use this for scene switches so viewers never see a
   half-applied state; issuing individual create/update/delete calls will render intermediate
   frames.
5. **Animate.** Set the layer's animation properties and the request animation mode on update
   (`LayerService_UpdateLayer`). Transitions available at the layout level include cut, crossfade,
   fade-to-color, swipe and stinger.
6. **Read back.** `LayerService_ListLayers` (`GET /layouts/{layoutId}/layers`) and
   `LayoutService_ListLayouts` (`GET /layouts`) return full arrays — there is no pagination.
7. **Tear down.** `LayerService_DeleteLayer`, then `LayoutService_DeleteLayout`.

## Notes

- Updates are PATCH with `updateMask` (dotted paths). Omit it over REST and the gateway infers it.
- Errors are `rpcStatus` (`code`, `message`, `details[]`); a `404` on a layer path usually means the
  layout, not the layer, was not found.
- Every layout and layer mutation emits events on the Event API scoped to that `layoutId` — see
  the `lightstream-subscribe-to-events` skill to drive UI from those instead of polling.
