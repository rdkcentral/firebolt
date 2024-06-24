---
title: MediaInfo

version: pr-feature-media-info
layout: default
sdk: manage
---

# MediaInfo Module

---

Version MediaInfo 1.2.0-feature-media-info.4

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [activeAudioFormats](#activeaudioformats)
  - [activeVideoFormats](#activevideoformats)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [activeAudioFormatsChanged](#activeaudioformatschanged)
  - [activeAudioFormatsChanged](#activeaudioformatschanged-1)
  - [activeVideoFormatsChanged](#activevideoformatschanged)
  - [activeVideoFormatsChanged](#activevideoformatschanged-1)
- [Types](#types)
  - [PipelineId](#pipelineid)
  - [VideoFormat](#videoformat)
  - [AudioFormat](#audioformat)

## Usage

To use the MediaInfo module, you can import it into your project from the Firebolt SDK:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'
```

## Overview

A module for query info about the media currently in the media pipeline (either playing or paused).

## Methods

### activeAudioFormats

Get a list of the active audio formats currently used across all media pipelines.

To get the value of `activeAudioFormats` call the method like this:

```typescript
function activeAudioFormats(): Promise<AudioFormat[]>
```

Promise resolution:

Capabilities:

| Role    | Capability                                      |
| ------- | ----------------------------------------------- |
| manages | xrn:firebolt:capability:media-info:audio-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let activeAudioFormats = await MediaInfo.activeAudioFormats()
console.log(activeAudioFormats)
```

Value of `activeAudioFormats`:

```javascript
;[
  {
    bitRate: 128,
    channels: '2',
    codec: 'aac',
    codecProfile: 'mp2lc',
    container: 'audio/mp4',
    pipelineId: 1,
    sampleRate: 48,
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.activeAudioFormats",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "bitRate": 128,
      "channels": "2",
      "codec": "aac",
      "codecProfile": "mp2lc",
      "container": "audio/mp4",
      "pipelineId": 1,
      "sampleRate": 48
    }
  ]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function activeAudioFormats(callback: (value) => AudioFormat[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let listenerId = await activeAudioFormats((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `activeAudioFormats`:

```javascript
;[
  {
    bitRate: 128,
    channels: '2',
    codec: 'aac',
    codecProfile: 'mp2lc',
    container: 'audio/mp4',
    pipelineId: 1,
    sampleRate: 48,
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onActiveAudioFormatsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "bitRate": 128,
      "channels": "2",
      "codec": "aac",
      "codecProfile": "mp2lc",
      "container": "audio/mp4",
      "pipelineId": 1,
      "sampleRate": 48
    }
  ]
}
```

</details>

---

### activeVideoFormats

Get a list of the active video formats currently used across all media pipelines.

To get the value of `activeVideoFormats` call the method like this:

```typescript
function activeVideoFormats(): Promise<VideoFormat[]>
```

Promise resolution:

Capabilities:

| Role    | Capability                                      |
| ------- | ----------------------------------------------- |
| manages | xrn:firebolt:capability:media-info:video-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let activeVideoFormats = await MediaInfo.activeVideoFormats()
console.log(activeVideoFormats)
```

Value of `activeVideoFormats`:

```javascript
;[
  {
    codec: 'hevc',
    codecLevel: '4.2',
    codecProfile: 'main',
    container: 'video/mp4',
    frameRate: 30,
    hdr: ['hdr10'],
    pipelineId: 1,
    resolution: [1920, 1080],
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.activeVideoFormats",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "codec": "hevc",
      "codecLevel": "4.2",
      "codecProfile": "main",
      "container": "video/mp4",
      "frameRate": 30,
      "hdr": ["hdr10"],
      "pipelineId": 1,
      "resolution": [1920, 1080]
    }
  ]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function activeVideoFormats(callback: (value) => VideoFormat[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let listenerId = await activeVideoFormats((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `activeVideoFormats`:

```javascript
;[
  {
    codec: 'hevc',
    codecLevel: '4.2',
    codecProfile: 'main',
    container: 'video/mp4',
    frameRate: 30,
    hdr: ['hdr10'],
    pipelineId: 1,
    resolution: [1920, 1080],
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onActiveVideoFormatsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "codec": "hevc",
      "codecLevel": "4.2",
      "codecProfile": "main",
      "container": "video/mp4",
      "frameRate": 30,
      "hdr": ["hdr10"],
      "pipelineId": 1,
      "resolution": [1920, 1080]
    }
  ]
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

## Events

### activeAudioFormatsChanged

```typescript
function listen('activeAudioFormatsChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role    | Capability                                      |
| ------- | ----------------------------------------------- |
| manages | xrn:firebolt:capability:media-info:audio-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let listenerId = await null((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `onActiveAudioFormatsChanged`:

```javascript
;[
  {
    bitRate: 128,
    channels: '2',
    codec: 'aac',
    codecProfile: 'mp2lc',
    container: 'audio/mp4',
    pipelineId: 1,
    sampleRate: 48,
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onActiveAudioFormatsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "bitRate": 128,
      "channels": "2",
      "codec": "aac",
      "codecProfile": "mp2lc",
      "container": "audio/mp4",
      "pipelineId": 1,
      "sampleRate": 48
    }
  ]
}
```

</details>

---

### activeAudioFormatsChanged

See: [activeAudioFormats](#activeaudioformats)

### activeVideoFormatsChanged

```typescript
function listen('activeVideoFormatsChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role    | Capability                                      |
| ------- | ----------------------------------------------- |
| manages | xrn:firebolt:capability:media-info:video-format |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaInfo } from '@firebolt-js/manage-sdk'

let listenerId = await null((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `onActiveVideoFormatsChanged`:

```javascript
;[
  {
    codec: 'hevc',
    codecLevel: '4.2',
    codecProfile: 'main',
    container: 'video/mp4',
    frameRate: 30,
    hdr: ['hdr10'],
    pipelineId: 1,
    resolution: [1920, 1080],
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaInfo.onActiveVideoFormatsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "codec": "hevc",
      "codecLevel": "4.2",
      "codecProfile": "main",
      "container": "video/mp4",
      "frameRate": 30,
      "hdr": ["hdr10"],
      "pipelineId": 1,
      "resolution": [1920, 1080]
    }
  ]
}
```

</details>

---

### activeVideoFormatsChanged

See: [activeVideoFormats](#activevideoformats)

## Types

### PipelineId

The media pipeline/session ID

```typescript

```

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
