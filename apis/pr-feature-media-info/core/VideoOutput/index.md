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
  - [listen](#listen)
  - [once](#once)
  - [status](#status)
- [Events](#events)
  - [modeWillChange](#modewillchange)
  - [statusChanged](#statuschanged)
- [Types](#types)

## Usage

To use the VideoOutput module, you can import it into your project from the Firebolt SDK:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'
```

## Overview

A module for the device's video output system, including its output capabilities and configuration.

## Methods

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

### status

Various properties describing the current video output status of the device.

To get the value of `status` call the method like this:

```typescript
function status(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:video-output:status |

#### Examples

Default Example

JavaScript:

```javascript
import { VideoOutput } from '@firebolt-js/sdk'

let properties = await VideoOutput.status()
console.log(properties)
```

Value of `properties`:

```javascript
{
	"colorDepth": 10,
	"colorimetry": "BT2020YCC",
	"colorSpace": "YCbCr422",
	"frameRate": 60,
	"hdrFormat": "hdr10plus",
	"mode": "2160p60",
	"quantizationRange": "full",
	"resolution": {
		"width": 3840,
		"height": 2160
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
  "method": "VideoOutput.status",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "colorDepth": 10,
    "colorimetry": "BT2020YCC",
    "colorSpace": "YCbCr422",
    "frameRate": 60,
    "hdrFormat": "hdr10plus",
    "mode": "2160p60",
    "quantizationRange": "full",
    "resolution": {
      "width": 3840,
      "height": 2160
    }
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function status(callback: (value) => object): Promise<number>
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

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `properties`:

```javascript
{
	"colorDepth": 10,
	"colorimetry": "BT2020YCC",
	"colorSpace": "YCbCr422",
	"frameRate": 60,
	"hdrFormat": "hdr10plus",
	"mode": "2160p60",
	"quantizationRange": "full",
	"resolution": {
		"width": 3840,
		"height": 2160
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
  "method": "VideoOutput.onStatusChanged",
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
    "colorDepth": 10,
    "colorimetry": "BT2020YCC",
    "colorSpace": "YCbCr422",
    "frameRate": 60,
    "hdrFormat": "hdr10plus",
    "mode": "2160p60",
    "quantizationRange": "full",
    "resolution": {
      "width": 3840,
      "height": 2160
    }
  }
}
```

</details>

---

## Events

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
'2160p60'
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
  "result": "2160p60"
}
```

</details>

---

### statusChanged

See: [status](#status)

## Types
