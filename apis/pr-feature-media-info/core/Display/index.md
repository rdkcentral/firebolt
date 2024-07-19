---
title: Display

version: pr-feature-media-info
layout: default
sdk: core
---

# Display Module

---

Version Display 1.2.0-feature-media-info.5

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [colorDepth](#colordepth)
  - [colorimetry](#colorimetry)
  - [hdrProfiles](#hdrprofiles)
  - [nativeRefreshRate](#nativerefreshrate)
  - [nativeResolution](#nativeresolution)
  - [nativeResolutionName](#nativeresolutionname)
  - [size](#size)
  - [videoModes](#videomodes)
- [Types](#types)

## Usage

To use the Display module, you can import it into your project from the Firebolt SDK:

```javascript
import { Display } from '@firebolt-js/sdk'
```

## Overview

A module for querying various aspects of the currently connected display (connected or built-in).

## Methods

### colorDepth

The color depth supported by the display.

```typescript
function colorDepth(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorDepth = await Display.colorDepth()
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
  "method": "Display.colorDepth",
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

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorDepth = await Display.colorDepth()
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
  "method": "Display.colorDepth",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 0
}
```

</details>

---

### colorimetry

The colorimetry values supported by the display.

```typescript
function colorimetry(): Promise<Colorimetry[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorimetry = await Display.colorimetry()
console.log(colorimetry)
```

Value of `colorimetry`:

```javascript
;['BT2020RGB', 'BT2020YCC']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.colorimetry",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["BT2020RGB", "BT2020YCC"]
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorimetry = await Display.colorimetry()
console.log(colorimetry)
```

Value of `colorimetry`:

```javascript
;['BT2020RGB', 'BT2020YCC']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.colorimetry",
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

### hdrProfiles

The display's supported HDR profiles.

```typescript
function hdrProfiles(): Promise<HDRProfile[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let hdrProfiles = await Display.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['dolbyVision', 'hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.hdrProfiles",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["dolbyVision", "hdr10", "hdr10plus", "hlg"]
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let hdrProfiles = await Display.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['dolbyVision', 'hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.hdrProfiles",
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

### nativeRefreshRate

The native refresh rate of the display device.

```typescript
function nativeRefreshRate(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let refreshRate = await Display.nativeRefreshRate()
console.log(refreshRate)
```

Value of `refreshRate`:

```javascript
60
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeRefreshRate",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 60
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let refreshRate = await Display.nativeRefreshRate()
console.log(refreshRate)
```

Value of `refreshRate`:

```javascript
60
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeRefreshRate",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 0
}
```

</details>

---

### nativeResolution

The native resolution of the display device in pixels. Returns a zero value for width and height if no display is present.

```typescript
function nativeResolution(): Promise<Dimensions>
```

Promise resolution:

[Dimensions](../Types/schemas/#Dimensions)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolution = await Display.nativeResolution()
console.log(resolution)
```

Value of `resolution`:

```javascript
{
	"width": 1920,
	"height": 1080
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeResolution",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "width": 1920,
    "height": 1080
  }
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolution = await Display.nativeResolution()
console.log(resolution)
```

Value of `resolution`:

```javascript
{
	"width": 1920,
	"height": 1080
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeResolution",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "width": 0,
    "height": 0
  }
}
```

</details>

---

### nativeResolutionName

The user-friendly representation of the display's native resolution.

```typescript
function nativeResolutionName(): Promise<ResolutionName>
```

Promise resolution:

[ResolutionName](../Media/schemas/#ResolutionName)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolutionName = await Display.nativeResolutionName()
console.log(resolutionName)
```

Value of `resolutionName`:

```javascript
'uhd'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeResolutionName",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "uhd"
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolutionName = await Display.nativeResolutionName()
console.log(resolutionName)
```

Value of `resolutionName`:

```javascript
'uhd'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.nativeResolutionName",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "unknown"
}
```

</details>

---

### size

The physical width and height of the display panel (in centimeters).

```typescript
function size(): Promise<Dimensions>
```

Promise resolution:

[Dimensions](../Types/schemas/#Dimensions)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let size = await Display.size()
console.log(size)
```

Value of `size`:

```javascript
{
	"width": 157,
	"height": 91
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.size",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "width": 157,
    "height": 91
  }
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let size = await Display.size()
console.log(size)
```

Value of `size`:

```javascript
{
	"width": 157,
	"height": 91
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.size",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "width": 0,
    "height": 0
  }
}
```

</details>

---

### videoModes

The video modes supported by the display device.

```typescript
function videoModes(): Promise<VideoMode[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let videoModes = await Display.videoModes()
console.log(videoModes)
```

Value of `videoModes`:

```javascript
;[
  '720p50',
  '720p60',
  '1080i50',
  '1080i60',
  '1080p24',
  '1080p30',
  '1080p50',
  '1080p60',
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.videoModes",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    "720p50",
    "720p60",
    "1080i50",
    "1080i60",
    "1080p24",
    "1080p30",
    "1080p50",
    "1080p60"
  ]
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let videoModes = await Display.videoModes()
console.log(videoModes)
```

Value of `videoModes`:

```javascript
;[
  '720p50',
  '720p60',
  '1080i50',
  '1080i60',
  '1080p24',
  '1080p30',
  '1080p50',
  '1080p60',
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.videoModes",
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

## Types
