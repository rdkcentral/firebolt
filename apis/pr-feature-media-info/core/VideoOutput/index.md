---
title: VideoOutput

version: pr-feature-media-info
layout: default
sdk: core
---

# VideoOutput Module

---

Version VideoOutput 1.2.0-feature-media-info.5

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [colorDepth](#colordepth)
  - [colorSpace](#colorspace)
  - [currentSettings](#currentsettings)
  - [hdrProfile](#hdrprofile)
  - [listen](#listen)
  - [mode](#mode)
  - [once](#once)
  - [quantizationRange](#quantizationrange)
  - [resolution](#resolution)
- [Events](#events)
  - [colorDepthChanged](#colordepthchanged)
  - [colorSpaceChanged](#colorspacechanged)
  - [currentSettingsChanged](#currentsettingschanged)
  - [hdrProfileChanged](#hdrprofilechanged)
  - [modeChanged](#modechanged)
  - [modeWillChange](#modewillchange)
  - [resolutionChanged](#resolutionchanged)
- [Types](#types)
  - [QuantizationRange](#quantizationrange-1)

## Usage

To use the VideoOutput module, you can import it into your project from the Firebolt SDK:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'
```

## Overview

A module for the device's video output system, including its output capabilities and configuration.

## Methods

### colorDepth

The color depth set for video output.

To get the value of `colorDepth` call the method like this:

```typescript
function colorDepth(): Promise<ColorDepth>
```

Promise resolution:

[ColorDepth](../Media/schemas/#ColorDepth)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:video-output:colordepth |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let colorDepth = await VideoOutput.colorDepth()
console.log(colorDepth)
```

Value of `colorDepth`:

```javascript
'10'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.colorDepth",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "10"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function colorDepth(callback: (value) => ColorDepth): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await colorDepth((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorDepth`:

```javascript
'10'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onColorDepthChanged",
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
  "result": "10"
}
```

</details>

---

### colorSpace

The color space and chroma set for video output.

To get the value of `colorSpace` call the method like this:

```typescript
function colorSpace(): Promise<ColorSpace>
```

Promise resolution:

[ColorSpace](../Media/schemas/#ColorSpace)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:video-output:colorspace |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let colorSpace = await VideoOutput.colorSpace()
console.log(colorSpace)
```

Value of `colorSpace`:

```javascript
'YCbCr422'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.colorSpace",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "YCbCr422"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function colorSpace(callback: (value) => ColorSpace): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await colorSpace((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorSpace`:

```javascript
'YCbCr422'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onColorSpaceChanged",
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
  "result": "YCbCr422"
}
```

</details>

---

### currentSettings

A convenience method that returns various properties currently set on the device related to video output.

To get the value of `currentSettings` call the method like this:

```typescript
function currentSettings(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:video-output:info |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let currentSettings = await VideoOutput.currentSettings()
console.log(currentSettings)
```

Value of `currentSettings`:

```javascript
{
	"colorDepth": "10",
	"colorSpace": "YCbCr422",
	"hdrProfile": "hdr10plus",
	"mode": "1080p60",
	"resolution": {
		"width": 1920,
		"height": 1080
	}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.currentSettings",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "colorDepth": "10",
    "colorSpace": "YCbCr422",
    "hdrProfile": "hdr10plus",
    "mode": "1080p60",
    "resolution": {
      "width": 1920,
      "height": 1080
    }
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function currentSettings(callback: (value) => object): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await currentSettings((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `currentSettings`:

```javascript
{
	"colorDepth": "10",
	"colorSpace": "YCbCr422",
	"hdrProfile": "hdr10plus",
	"mode": "1080p60",
	"resolution": {
		"width": 1920,
		"height": 1080
	}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onCurrentSettingsChanged",
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
  "result": {
    "colorDepth": "10",
    "colorSpace": "YCbCr422",
    "hdrProfile": "hdr10plus",
    "mode": "1080p60",
    "resolution": {
      "width": 1920,
      "height": 1080
    }
  }
}
```

</details>

---

### hdrProfile

The HDR profile set for video output.

To get the value of `hdrProfile` call the method like this:

```typescript
function hdrProfile(): Promise<HDRProfile>
```

Promise resolution:

[HDRProfile](../Media/schemas/#HDRProfile)

Capabilities:

| Role | Capability                                      |
| ---- | ----------------------------------------------- |
| uses | xrn:firebolt:capability:video-output:hdrprofile |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let hdrProfile = await VideoOutput.hdrProfile()
console.log(hdrProfile)
```

Value of `hdrProfile`:

```javascript
'hdr10plus'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.hdrProfile",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "hdr10plus"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdrProfile(callback: (value) => HDRProfile): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await hdrProfile((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdrProfile`:

```javascript
'hdr10plus'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onHdrProfileChanged",
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
  "result": "hdr10plus"
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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VideoOutput.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VideoOutput.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### mode

The current video output mode of the device.

To get the value of `mode` call the method like this:

```typescript
function mode(): Promise<VideoMode>
```

Promise resolution:

[VideoMode](../Media/schemas/#VideoMode)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:video-output:mode |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let mode = await VideoOutput.mode()
console.log(mode)
```

Value of `mode`:

```javascript
'1080p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.mode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "1080p60"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function mode(callback: (value) => VideoMode): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await mode((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `mode`:

```javascript
'1080p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onModeChanged",
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
  "result": "1080p60"
}
```

</details>

---

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VideoOutput.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VideoOutput.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### quantizationRange

The quantization range set for video output.

```typescript
function quantizationRange(): Promise<QuantizationRange>
```

Promise resolution:

[QuantizationRange](#quantizationrange-1)

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:video-output:quantization |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let quantizationRange = await VideoOutput.quantizationRange()
console.log(quantizationRange)
```

Value of `quantizationRange`:

```javascript
'limited'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.quantizationRange",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "limited"
}
```

</details>

---

### resolution

The width and height of the current video output, in pixels.

To get the value of `resolution` call the method like this:

```typescript
function resolution(): Promise<Dimensions>
```

Promise resolution:

[Dimensions](../Types/schemas/#Dimensions)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:video-output:mode |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let resolution = await VideoOutput.resolution()
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
  "method": "VideoOutput.resolution",
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function resolution(callback: (value) => Dimensions): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let listenerId = await resolution((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "VideoOutput.onResolutionChanged",
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
  "result": {
    "width": 1920,
    "height": 1080
  }
}
```

</details>

---

## Events

### colorDepthChanged

See: [colorDepth](#colordepth)

### colorSpaceChanged

See: [colorSpace](#colorspace)

### currentSettingsChanged

See: [currentSettings](#currentsettings)

### hdrProfileChanged

See: [hdrProfile](#hdrprofile)

### modeChanged

See: [mode](#mode)

### modeWillChange

```typescript
function listen('modeWillChange', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[VideoMode](../Media/schemas/#VideoMode)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:video-output:mode |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

VideoOutput.listen('modeWillChange', (mode) => {
  console.log(mode)
})
```

Value of `mode`:

```javascript
'1080p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VideoOutput.onModeWillChange",
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
  "result": "1080p60"
}
```

</details>

---

### resolutionChanged

See: [resolution](#resolution)

## Types

### QuantizationRange

The quantization range of video output

```typescript
QuantizationRange: {
    FULL: 'full',
    LIMITED: 'limited',
    UNKNOWN: 'unknown',
},

```

---
