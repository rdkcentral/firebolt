---
title: MediaCapabilities

version: pr-feature-media-info
layout: default
sdk: core
---

# MediaCapabilities Module

---

Version MediaCapabilities 1.2.0-feature-media-info.5

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [atmosSupported](#atmossupported)
  - [audioCodecs](#audiocodecs)
  - [colorDepth](#colordepth)
  - [hdrFormats](#hdrformats)
  - [listen](#listen)
  - [once](#once)
  - [preferredVideoMode](#preferredvideomode)
  - [videoCodecs](#videocodecs)
- [Events](#events)
  - [atmosSupportedChanged](#atmossupportedchanged)
  - [audioCodecsChanged](#audiocodecschanged)
  - [colorDepthChanged](#colordepthchanged)
  - [hdrFormatsChanged](#hdrformatschanged)
  - [preferredVideoModeChanged](#preferredvideomodechanged)
  - [videoCodecsChanged](#videocodecschanged)
- [Types](#types)

## Usage

To use the MediaCapabilities module, you can import it into your project from the Firebolt SDK:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'
```

## Overview

A module for querying the capabilities of the device all of its connected perirpherals (such as displays and soundbars).

## Methods

### atmosSupported

Whether or not Dolby Atmos immersive audio is commonly supported by the device and its connected audio peripherals.

To get the value of `atmosSupported` call the method like this:

```typescript
function atmosSupported(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let atmosSupported = await MediaCapabilities.atmosSupported()
console.log(atmosSupported)
```

Value of `atmosSupported`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.atmosSupported",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function atmosSupported(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await atmosSupported((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `atmosSupported`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onAtmosSupportedChanged",
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
  "result": true
}
```

</details>

---

### audioCodecs

The audio codecs supported by the audio decoding device. The response is based on the current audio output mode. For example, if the output mode is passthrough, the codecs of the audio sink (such as the soundbar or AV receiver) are returned.

To get the value of `audioCodecs` call the method like this:

```typescript
function audioCodecs(): Promise<AudioCodec[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let audioCodecs = await MediaCapabilities.audioCodecs()
console.log(audioCodecs)
```

Value of `audioCodecs`:

```javascript
;['aac', 'ac3', 'ac4', 'eac3', 'mpeg3', 'pcm']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.audioCodecs",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["aac", "ac3", "ac4", "eac3", "mpeg3", "pcm"]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audioCodecs(callback: (value) => AudioCodec[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await audioCodecs((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `audioCodecs`:

```javascript
;['aac', 'ac3', 'ac4', 'eac3', 'mpeg3', 'pcm']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onAudioCodecsChanged",
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
  "result": ["aac", "ac3", "ac4", "eac3", "mpeg3", "pcm"]
}
```

</details>

---

### colorDepth

The maximum color depth commonly supported by the device and its connected video peripherals.

To get the value of `colorDepth` call the method like this:

```typescript
function colorDepth(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let colorDepth = await MediaCapabilities.colorDepth()
console.log(colorDepth)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.colorDepth",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 10
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function colorDepth(callback: (value) => number): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await colorDepth((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onColorDepthChanged",
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
  "result": 10
}
```

</details>

---

### hdrFormats

The HDR formats commonly supported by the device and its connected video peripherals.

To get the value of `hdrFormats` call the method like this:

```typescript
function hdrFormats(): Promise<HDRFormat[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let hdrFormats = await MediaCapabilities.hdrFormats()
console.log(hdrFormats)
```

Value of `hdrFormats`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.hdrFormats",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["hdr10", "hdr10plus", "hlg"]
}
```

</details>

Device connected to an SDR (non-HDR) display

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let hdrFormats = await MediaCapabilities.hdrFormats()
console.log(hdrFormats)
```

Value of `hdrFormats`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.hdrFormats",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": []
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdrFormats(callback: (value) => HDRFormat[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await hdrFormats((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdrFormats`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onHdrFormatsChanged",
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
  "result": ["hdr10", "hdr10plus", "hlg"]
}
```

</details>

Device connected to an SDR (non-HDR) display

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await hdrFormats((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdrFormats`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onHdrFormatsChanged",
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
  "result": []
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

| Type     | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaCapabilities.clear(id)` |

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

| Type     | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaCapabilities.clear(id)` |

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

| Type     | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaCapabilities.clear(id)` |

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

| Type     | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `MediaCapabilities.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### preferredVideoMode

The best-possible video mode commonly supported by the device and its connected video peripherals.

To get the value of `preferredVideoMode` call the method like this:

```typescript
function preferredVideoMode(): Promise<VideoMode>
```

Promise resolution:

[VideoMode](../Media/schemas/#VideoMode)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let videoModes = await MediaCapabilities.preferredVideoMode()
console.log(videoModes)
```

Value of `videoModes`:

```javascript
'2160p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.preferredVideoMode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "2160p60"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function preferredVideoMode(callback: (value) => VideoMode): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await preferredVideoMode((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoModes`:

```javascript
'2160p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onPreferredVideoModeChanged",
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
  "result": "2160p60"
}
```

</details>

---

### videoCodecs

The video codecs supported by the device.

To get the value of `videoCodecs` call the method like this:

```typescript
function videoCodecs(): Promise<VideoCodec[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let videoCodecs = await MediaCapabilities.videoCodecs()
console.log(videoCodecs)
```

Value of `videoCodecs`:

```javascript
;['av1', 'avc', 'hevc', 'mpeg1', 'mpeg2', 'vp8', 'vp9']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.videoCodecs",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["av1", "avc", "hevc", "mpeg1", "mpeg2", "vp8", "vp9"]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoCodecs(callback: (value) => VideoCodec[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let listenerId = await videoCodecs((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoCodecs`:

```javascript
;['av1', 'avc', 'hevc', 'mpeg1', 'mpeg2', 'vp8', 'vp9']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.onVideoCodecsChanged",
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
  "result": ["av1", "avc", "hevc", "mpeg1", "mpeg2", "vp8", "vp9"]
}
```

</details>

---

## Events

### atmosSupportedChanged

See: [atmosSupported](#atmossupported)

### audioCodecsChanged

See: [audioCodecs](#audiocodecs)

### colorDepthChanged

See: [colorDepth](#colordepth)

### hdrFormatsChanged

See: [hdrFormats](#hdrformats)

### preferredVideoModeChanged

See: [preferredVideoMode](#preferredvideomode)

### videoCodecsChanged

See: [videoCodecs](#videocodecs)

## Types
