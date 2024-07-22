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
  - [audioModes](#audiomodes)
  - [colorDepth](#colordepth)
  - [hdrProfiles](#hdrprofiles)
  - [videoCodecs](#videocodecs)
  - [videoModes](#videomodes)
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
