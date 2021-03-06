
---
title: "debug_attachment.proto"
weight: 5
---

<!-- Code generated by solo-kit. DO NOT EDIT. -->


### Package: `squash.solo.io` 
#### Types:


- [DebugAttachment](#debugattachment) **Top-Level Resource**
- [State](#state)
- [Intent](#intent)
- [Plank](#plank)
- [PortSpec](#portspec)
  



##### Source File: [github.com/solo-io/squash/api/v1/debug_attachment.proto](https://github.com/solo-io/squash/blob/master/api/v1/debug_attachment.proto)





---
### DebugAttachment

 
Attachments store the information needed for squash to coordinate a debugging session

```yaml
"metadata": .core.solo.io.Metadata
"status": .core.solo.io.Status
"plankName": string
"debugger": string
"image": string
"processName": string
"node": string
"matchRequest": bool
"debugServerAddress": string
"pod": string
"container": string
"debugNamespace": string
"state": .squash.solo.io.DebugAttachment.State

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `metadata` | [.core.solo.io.Metadata](../../../../solo-kit/api/v1/metadata.proto.sk#metadata) |  |  |
| `status` | [.core.solo.io.Status](../../../../solo-kit/api/v1/status.proto.sk#status) |  |  |
| `plankName` | `string` |  |  |
| `debugger` | `string` |  |  |
| `image` | `string` |  |  |
| `processName` | `string` |  |  |
| `node` | `string` |  |  |
| `matchRequest` | `bool` |  |  |
| `debugServerAddress` | `string` |  |  |
| `pod` | `string` |  |  |
| `container` | `string` |  |  |
| `debugNamespace` | `string` |  |  |
| `state` | [.squash.solo.io.DebugAttachment.State](../debug_attachment.proto.sk#state) |  |  |




---
### State



| Name | Description |
| ----- | ----------- | 
| `RequestingAttachment` | Newly created DebugAttachments have state RequestingAttachment |
| `PendingAttachment` | When the event loop begins fullfilling an attachment request it sets DebugAttachments state to PendingAttachment |
| `Attached` | When squash client successfully attaches, it sets state to Attached |
| `RequestingDelete` | Indicates that user has requested an attachment be removed |
| `PendingDelete` | When the event loop begins fullfilling a delete request it sets this status and triggers a cleanup routine When the cleanup routine completes, it deletes the CRD |




---
### Intent

 
Describes the user's debug intentions

```yaml
"debugger": string
"pod": .core.solo.io.ResourceRef
"containerName": string
"processMatcher": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `debugger` | `string` | type of debugger to use |  |
| `pod` | [.core.solo.io.ResourceRef](../../../../solo-kit/api/v1/ref.proto.sk#resourceref) | pod to debug |  |
| `containerName` | `string` | name of container to debug |  |
| `processMatcher` | `string` | NOT YET IMPLEMENTED if a container has multiple processes and you do not want to debug the first process, this string is used to select a specific process |  |




---
### Plank

 
Describes the pod squash spawns for managing a particular debug session

```yaml
"pod": .core.solo.io.ResourceRef
"readyForConnect": bool

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `pod` | [.core.solo.io.ResourceRef](../../../../solo-kit/api/v1/ref.proto.sk#resourceref) | plank pod reference |  |
| `readyForConnect` | `bool` | indicates when plank has completed the debugger-specify preparation |  |




---
### PortSpec

 
Contains port information needed to connect or find a debugger

```yaml
"plank": string
"target": string

```

| Field | Type | Description | Default |
| ----- | ---- | ----------- |----------- | 
| `plank` | `string` | the relevant debug port on the plank pod |  |
| `target` | `string` | the relevant debug port on the target pod |  |





<!-- Start of HubSpot Embed Code -->
<script type="text/javascript" id="hs-script-loader" async defer src="//js.hs-scripts.com/5130874.js"></script>
<!-- End of HubSpot Embed Code -->
