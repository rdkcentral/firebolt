---
title: VoiceGuidance

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# VoiceGuidance Module

---

Version VoiceGuidance 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [enabled](#enabled)
  - [listen](#listen)
  - [once](#once)
  - [speed](#speed)
- [Events](#events)
  - [enabledChanged](#enabledchanged)
  - [speedChanged](#speedchanged)

## Usage

To use the VoiceGuidance module, you can import it into your project from the Firebolt SDK:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing voice-guidance Settings.

## Methods

### enabled

Whether or not voice-guidance is enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Default example #1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let enabled = await VoiceGuidance.enabled()
console.log(enabled)
```

Value of `enabled`:

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
  "method": "VoiceGuidance.enabled",
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

Default example #2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let enabled = await VoiceGuidance.enabled()
console.log(enabled)
```

Value of `enabled`:

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
  "method": "VoiceGuidance.enabled",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>

---

To set the value of `enabled` call the method like this:

```typescript
function enabled(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.enabled(true)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.setEnabled",
  "params": {
    "value": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

Default example #2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.enabled(false)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.setEnabled",
  "params": {
    "value": false
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function enabled(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `enabled`:

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
  "method": "VoiceGuidance.onEnabledChanged",
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

Default example #2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `enabled`:

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
  "method": "VoiceGuidance.onEnabledChanged",
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
  "result": false
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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### speed

The speed at which voice guidance speech will be read back to the user.

To get the value of `speed` call the method like this:

```typescript
function speed(): Promise<VoiceSpeed>
```

Promise resolution:

[VoiceSpeed](../Accessibility/schemas/#VoiceSpeed)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Voice guidance speed to 1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let speed = await VoiceGuidance.speed()
console.log(speed)
```

Value of `speed`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.speed",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 1
}
```

</details>

Voice guidance speed to 2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let speed = await VoiceGuidance.speed()
console.log(speed)
```

Value of `speed`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.speed",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 2
}
```

</details>

---

To set the value of `speed` call the method like this:

```typescript
function speed(value: VoiceSpeed): Promise<void>
```

Parameters:

| Param      | Type                                                 | Required | Description       |
| ---------- | ---------------------------------------------------- | -------- | ----------------- |
| `value`    | [`VoiceSpeed`](../Accessibility/schemas/#VoiceSpeed) | true     | <br/>minumum: 0.5 |
| maximum: 2 |

Promise resolution:

```typescript
null
```

#### Examples

Voice guidance speed to 1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.speed(1)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.setSpeed",
  "params": {
    "value": 1
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

Voice guidance speed to 2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.speed(2)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.setSpeed",
  "params": {
    "value": 2
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function speed(callback: (value) => VoiceSpeed): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Voice guidance speed to 1

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await speed((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `speed`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.onSpeedChanged",
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
  "result": 1
}
```

</details>

Voice guidance speed to 2

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await speed((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `speed`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "VoiceGuidance.onSpeedChanged",
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
  "result": 2
}
```

</details>

---

## Events

### enabledChanged

See: [enabled](#enabled)

### speedChanged

See: [speed](#speed)
