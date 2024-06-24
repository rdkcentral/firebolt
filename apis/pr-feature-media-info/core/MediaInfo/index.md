---
title: MediaInfo

version: pr-feature-media-info
layout: default
sdk: core
---

# MediaInfo Module

---

Version MediaInfo 1.2.0-feature-media-info.4

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audioFormat](#audioformat)
  - [listen](#listen)
  - [once](#once)
  - [videoFormat](#videoformat)
- [Events](#events)
  - [audioFormatChanged](#audioformatchanged)
  - [videoFormatChanged](#videoformatchanged)
- [Types](#types)
  - [PipelineId](#pipelineid)
  - [AudioFormat](#audioformat-1)
  - [VideoFormat](#videoformat-1)

## Usage

To use the MediaInfo module, you can import it into your project from the Firebolt SDK:

```javascript
import { MediaInfo } from '@firebolt-js/sdk'
```

## Overview

A module for query info about the media currently in the media pipeline (either playing or paused).

## Methods

### audioFormat

Get the audio format currently used by the specified media pipeline.

To get the value of `audioFormat` call the method like this:

```typescript
function audioFormat(pipelineId: PipelineId): Promise<AudioFormat>
```

Parameters:

| Param        | Type                        | Required | Description     |
| ------------ | --------------------------- | -------- | --------------- |
| `pipelineId` | [`PipelineId`](#pipelineid) | true     | <br/>minumum: 0 |
| maximum: 15  |

Promise resolution:

[AudioFormat](#audioformat-1)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-info:audio-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/sdk'

let audioFormat = await MediaInfo.audioFormat(1)
console.log(audioFormat)
```

Value of `audioFormat`:

```javascript
{
	"bitRate": 128,
	"channels": "2",
	"codec": "aac",
	"container": "audio/mp4",
	"pipelineId": 1,
	"sampleRate": 48
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.audioFormat",
  "params": {
    "pipelineId": 1
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "bitRate": 128,
    "channels": "2",
    "codec": "aac",
    "container": "audio/mp4",
    "pipelineId": 1,
    "sampleRate": 48
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audioFormat(
  pipelineId: PipelineId,
  callback: (value) => AudioFormat,
): Promise<number>
```

Parameters:

| Param        | Type                        | Required | Description     |
| ------------ | --------------------------- | -------- | --------------- |
| `pipelineId` | [`PipelineId`](#pipelineid) | true     | <br/>minumum: 0 |
| maximum: 15  |

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/sdk'

let listenerId = await audioFormat((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `audioFormat`:

```javascript
{
	"bitRate": 128,
	"channels": "2",
	"codec": "aac",
	"container": "audio/mp4",
	"pipelineId": 1,
	"sampleRate": 48
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onAudioFormatChanged",
  "params": {
    "pipelineId": 1,
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "bitRate": 128,
    "channels": "2",
    "codec": "aac",
    "container": "audio/mp4",
    "pipelineId": 1,
    "sampleRate": 48
  }
}
```

</details>

---

### listen

To listen to a specific event pass the event name as the first parameter:

```typescript
listen(event: string, callback: (data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaInfo.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaInfo.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
```

The `once` method will only pass the next instance of this event, and then dicard the listener you provided.

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaInfo.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaInfo.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### videoFormat

Get the video format currently used by the specified media pipeline.

To get the value of `videoFormat` call the method like this:

```typescript
function videoFormat(pipelineId: PipelineId): Promise<VideoFormat>
```

Parameters:

| Param        | Type                        | Required | Description     |
| ------------ | --------------------------- | -------- | --------------- |
| `pipelineId` | [`PipelineId`](#pipelineid) | true     | <br/>minumum: 0 |
| maximum: 15  |

Promise resolution:

[VideoFormat](#videoformat-1)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-info:video-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/sdk'

let videoFormat = await MediaInfo.videoFormat(1)
console.log(videoFormat)
```

Value of `videoFormat`:

```javascript
{
	"codec": "hevc",
	"codecLevel": "4.2",
	"codecProfile": "main",
	"container": "video/mp4",
	"frameRate": 30,
	"hdr": [
		"hdr10"
	],
	"pipelineId": 1,
	"resolution": [
		1920,
		1080
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.videoFormat",
  "params": {
    "pipelineId": 1
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "codec": "hevc",
    "codecLevel": "4.2",
    "codecProfile": "main",
    "container": "video/mp4",
    "frameRate": 30,
    "hdr": ["hdr10"],
    "pipelineId": 1,
    "resolution": [1920, 1080]
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoFormat(
  pipelineId: PipelineId,
  callback: (value) => VideoFormat,
): Promise<number>
```

Parameters:

| Param        | Type                        | Required | Description     |
| ------------ | --------------------------- | -------- | --------------- |
| `pipelineId` | [`PipelineId`](#pipelineid) | true     | <br/>minumum: 0 |
| maximum: 15  |

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/sdk'

let listenerId = await videoFormat((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoFormat`:

```javascript
{
	"codec": "hevc",
	"codecLevel": "4.2",
	"codecProfile": "main",
	"container": "video/mp4",
	"frameRate": 30,
	"hdr": [
		"hdr10"
	],
	"pipelineId": 1,
	"resolution": [
		1920,
		1080
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onVideoFormatChanged",
  "params": {
    "pipelineId": 1,
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "codec": "hevc",
    "codecLevel": "4.2",
    "codecProfile": "main",
    "container": "video/mp4",
    "frameRate": 30,
    "hdr": ["hdr10"],
    "pipelineId": 1,
    "resolution": [1920, 1080]
  }
}
```

</details>

---

## Events

### audioFormatChanged

See: [audioFormat](#audioformat)

### videoFormatChanged

See: [videoFormat](#videoformat)

## Types

### PipelineId

The media pipeline/session ID

```typescript

```

---

### AudioFormat

Details on the audio content format.

```typescript
type AudioFormat = {
  bitRate?: number // The audio bitrate in kbps.
  channels: string // The audio output channels.
  codec: AudioCodec // Audio codec
  codecLevel?: AudioCodecLevel // Audio codec level
  codecProfile?: AudioCodecProfile // Audio codec profile
  container?: AudioContainer // Audio container
  pipelineId: PipelineId // The media pipeline/session ID
  sampleRate: number // The audio sample rate in kHz.
}
```

See also:

[AudioCodec](../Media/schemas/#AudioCodec)
[AudioCodecLevel](../Media/schemas/#AudioCodecLevel)
[AudioCodecProfile](../Media/schemas/#AudioCodecProfile)
[AudioContainer](../Media/schemas/#AudioContainer)
[PipelineId](#pipelineid)

---

### VideoFormat

Details on the video content format.

```typescript
type VideoFormat = {
  codec: VideoCodec // video codec
  codecLevel?: '4.1' | '4.2' | '5.0' | '5.1' | 'high' | 'main'
  codecProfile?: 'high' | 'main' | 'main10' | 'p0' | 'p2'
  container?: VideoContainer // Video container format
  frameRate?: number
  hdr: HDRProfile[] // HDR profile
  pipelineId: PipelineId // The media pipeline/session ID
  resolution: Dimensions // The dimensions specified as width and height.
}
```

See also:

[VideoCodec](../Media/schemas/#VideoCodec)
[VideoContainer](../Media/schemas/#VideoContainer)
[HDRProfile](../Media/schemas/#HDRProfile)
[PipelineId](#pipelineid)
[Dimensions](../Media/schemas/#Dimensions)

---
