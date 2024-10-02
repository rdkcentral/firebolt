---
title: AudioOutput

version: pr-feature-media-info
layout: default
sdk: core
---

# AudioOutput Module

---

Version AudioOutput 1.2.0-feature-media-info.5

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [mode](#mode)
  - [once](#once)
  - [status](#status)
- [Events](#events)
  - [modeChanged](#modechanged)
  - [statusChanged](#statuschanged)
- [Types](#types)

## Usage

To use the AudioOutput module, you can import it into your project from the Firebolt SDK:

```javascript
import { AudioOutput } from '@firebolt-js/sdk'
```

## Overview

A module for the device's audio output system, including its output capabilities and configuration.

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioOutput.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioOutput.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### mode

The current audio output mode setting of the device.

To get the value of `mode` call the method like this:

```typescript
function mode(): Promise<AudioMode>
```

Promise resolution:

[AudioMode](../Media/schemas/#AudioMode)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:audio-output:mode |

#### Examples

Default Example

JavaScript:

```javascript
import { AudioOutput } from '@firebolt-js/sdk'

let mode = await AudioOutput.mode()
console.log(mode)
```

Value of `mode`:

```javascript
'auto'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AudioOutput.mode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "auto"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function mode(callback: (value) => AudioMode): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { AudioOutput } from '@firebolt-js/sdk'

let listenerId = await mode((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `mode`:

```javascript
'auto'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AudioOutput.onModeChanged",
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
  "result": "auto"
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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioOutput.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioOutput.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### status

Various properties describing the current audio output status of the device.

To get the value of `status` call the method like this:

```typescript
function status(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:audio-output:status |

#### Examples

Default Example

JavaScript:

```javascript
import { AudioOutput } from '@firebolt-js/sdk'

let status = await AudioOutput.status()
console.log(status)
```

Value of `status`:

```javascript
{
	"mode": "surround"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AudioOutput.status",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "mode": "surround"
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
import { AudioOutput } from '@firebolt-js/sdk'

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `status`:

```javascript
{
	"mode": "surround"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AudioOutput.onStatusChanged",
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
    "mode": "surround"
  }
}
```

</details>

---

## Events

### modeChanged

See: [mode](#mode)

### statusChanged

See: [status](#status)

## Types
