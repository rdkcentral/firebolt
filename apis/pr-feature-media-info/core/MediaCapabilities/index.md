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
  - [audioFormatSupported](#audioformatsupported)
  - [audioModes](#audiomodes)
  - [colorDepth](#colordepth)
  - [hdrProfiles](#hdrprofiles)
  - [videoCodecs](#videocodecs)
  - [videoFormatSupported](#videoformatsupported)
  - [videoModes](#videomodes)
- [Types](#types)
  - [AudioFormatOptions](#audioformatoptions)
  - [VideoFormatOptions](#videoformatoptions)

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

### audioCodecs

The audio codecs commonly supported by the device and all its connected audio peripherals.

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

### audioFormatSupported

Check whether content of a given audio format is supported by the device's current configuration and its AV output system. The result is based on the device's best possible audio output configuration. These values may change as different AV inputs or peripherals are activated or connected.

```typescript
function audioFormatSupported(
  codec: AudioCodec,
  options: AudioFormatOptions,
): Promise<boolean>
```

Parameters:

| Param     | Type                                         | Required | Description                                                                                                                                             |
| --------- | -------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `codec`   | [`AudioCodec`](../Media/schemas/#AudioCodec) | true     | Audio codec used to check whether its supported. <br/>values: `'aac' \| 'ac3' \| 'ac4' \| 'eac3' \| 'mpeg3' \| 'opus' \| 'pcm' \| 'truehd' \| 'vorbis'` |
| `options` | [`AudioFormatOptions`](#audioformatoptions)  | false    | Additional options to use for checking whether an audio format is supported by the device. All values must be true for the content to be playable.      |

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Check whether EAC3 codec with Atmos is supported

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let audioFormatSupported = await MediaCapabilities.audioFormatSupported(
  'eac3',
  { atmos: true },
)
console.log(audioFormatSupported)
```

Value of `audioFormatSupported`:

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
  "method": "MediaCapabilities.audioFormatSupported",
  "params": {
    "codec": "eac3",
    "options": {
      "atmos": true
    }
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

### audioModes

The audio output modes commonly supported by the device and its connected audio peripherals

```typescript
function audioModes(): Promise<AudioMode[]>
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

let audioModes = await MediaCapabilities.audioModes()
console.log(audioModes)
```

Value of `audioModes`:

```javascript
;['passthrough', 'stereo', 'surround']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.audioModes",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["passthrough", "stereo", "surround"]
}
```

</details>

---

### colorDepth

The maximum color depth commonly supported by the device and its connected video peripherals.

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

### hdrProfiles

The HDR profiles commonly supported by the device and its connected video peripherals.

```typescript
function hdrProfiles(): Promise<HDRProfile[]>
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

let hdrProfiles = await MediaCapabilities.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

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
  "method": "MediaCapabilities.hdrProfiles",
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

---

### videoCodecs

The video codecs commonly supported by the device and all of its connected video peripherals.

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

### videoFormatSupported

Check whether video content of the given format is supported by the device's current configuration and its AV output system. These values may change as different AV inputs or peripherals are activated or connected.

```typescript
function videoFormatSupported(
  codec: VideoCodec,
  options: VideoFormatOptions,
): Promise<boolean>
```

Parameters:

| Param     | Type                                         | Required | Description                                                                                                                                                           |
| --------- | -------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `codec`   | [`VideoCodec`](../Media/schemas/#VideoCodec) | true     | The video codec to check whether its supported by the device's current configuration. <br/>values: `'av1' \| 'avc' \| 'hevc' \| 'mpeg1' \| 'mpeg2' \| 'vp8' \| 'vp9'` |
| `options` | [`VideoFormatOptions`](#videoformatoptions)  | false    | Additional options to use for checking whether a video is supported by the device. All values must be true for the content to be playable.                            |

Promise resolution:

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:media-capabilities:info |

#### Examples

Specify the video format to check

JavaScript:

```javascript
import { MediaCapabilities } from '@firebolt-js/sdk'

let videoFormatSupported = await MediaCapabilities.videoFormatSupported(
  'hevc',
  { resolution: { width: 1920, height: 1080 } },
)
console.log(videoFormatSupported)
```

Value of `videoFormatSupported`:

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
  "method": "MediaCapabilities.videoFormatSupported",
  "params": {
    "codec": "hevc",
    "options": {
      "resolution": {
        "width": 1920,
        "height": 1080
      }
    }
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

### videoModes

The video output modes commonly supported by the device and its connected video peripherals.

```typescript
function videoModes(): Promise<VideoMode[]>
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

let videoModes = await MediaCapabilities.videoModes()
console.log(videoModes)
```

Value of `videoModes`:

```javascript
;['720p50', '720p60', '1080p50', '1080p60']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaCapabilities.videoModes",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["720p50", "720p60", "1080p50", "1080p60"]
}
```

</details>

---

## Types

### AudioFormatOptions

Options for checking audio playback support

```typescript
type AudioFormatOptions = {
  atmos?: boolean // Whether Dolby Atmos support is being requested
  codecLevel?: string // The level of the audio codec
  codecProfile?: AudioCodecProfile // Audio codec profile
  container?: AudioContainer // Audio container
  sampleRate?: number // The sample rate of the audio, in kHz
}
```

See also:

[AudioCodecProfile](../Media/schemas/#AudioCodecProfile)
[AudioContainer](../Media/schemas/#AudioContainer)

---

### VideoFormatOptions

Options for checking video playback support

```typescript
type VideoFormatOptions = {
  atmos?: boolean // Whether Dolby Atmos support is being requested
  codecLevel?: '4.1' | '4.2' | '5.0' | '5.1' | 'high' | 'main' // The level of the video codec
  codecProfile?: 'high' | 'main' | 'main10' | 'p0' | 'p2' // The profile of the video codec
  container?: VideoContainer // Video container format
  frameRate?: number // The frame rate of the video content
  hdr?: HDRProfile // HDR profile
  resolution?: Dimensions
}
```

See also:

[VideoContainer](../Media/schemas/#VideoContainer)
[HDRProfile](../Media/schemas/#HDRProfile)
[Dimensions](../Types/schemas/#Dimensions)

---
