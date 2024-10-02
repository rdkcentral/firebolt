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
  - [colorimetry](#colorimetry)
  - [nativeResolution](#nativeresolution)
  - [size](#size)
  - [videoModes](#videomodes)
- [Types](#types)

## Usage

To use the Display module, you can import it into your project from the Firebolt SDK:

```javascript
import { Display } from '@firebolt-js/sdk'
```

## Overview

A module for querying various aspects of the currently connected (or built-in) display.

## Methods

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

---

### nativeResolution

The native resolution of the display device in pixels.

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

let nativeResolution = await Display.nativeResolution()
console.log(nativeResolution)
```

Value of `nativeResolution`:

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

---

## Types
