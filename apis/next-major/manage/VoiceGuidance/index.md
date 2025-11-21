---
title: VoiceGuidance

version: next-major
layout: default
sdk: manage
---

# VoiceGuidance Module

---

Version VoiceGuidance 1.8.0-next-major.3

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [enabled](#enabled)
  - [listen](#listen)
  - [navigationHints](#navigationhints)
  - [once](#once)
  - [rate](#rate)
  - [speed](#speed)
- [Events](#events)
  - [onEnabledChanged](#onenabledchanged)
  - [onNavigationHintsChanged](#onnavigationhintschanged)
  - [onRateChanged](#onratechanged)
  - [onSpeedChanged](#onspeedchanged)
- [Private Events](#private-events)
- [Types](#types)

## Usage

To use the VoiceGuidance module, you can import it into your project from the Firebolt SDK:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing voice guidance settings.

## Methods

### enabled

Whether or not voice-guidance is enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Voice guidance enabled

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

Voice guidance disabled

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

#### Examples

Voice guidance enabled

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

Voice guidance disabled

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
function enabled(callback: (enabled) => boolean): Promise<number>
```

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Promise resolution:

```
number
```

#### Examples

Voice guidance enabled

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Voice guidance disabled

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
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

### navigationHints

The user's preference for whether additional navigation hints should be synthesized.

To get the value of `navigationHints` call the method like this:

```typescript
function navigationHints(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Navigation hints enabled

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let navigationHints = await VoiceGuidance.navigationHints()
console.log(navigationHints)
```

Value of `navigationHints`:

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
  "method": "VoiceGuidance.navigationHints",
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

Navigation hints disabled

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let navigationHints = await VoiceGuidance.navigationHints()
console.log(navigationHints)
```

Value of `navigationHints`:

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
  "method": "VoiceGuidance.navigationHints",
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

To set the value of `navigationHints` call the method like this:

```typescript
function navigationHints(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

#### Examples

Navigation hints enabled

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.navigationHints(true)
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
  "method": "VoiceGuidance.setNavigationHints",
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

Navigation hints disabled

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.navigationHints(false)
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
  "method": "VoiceGuidance.setNavigationHints",
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
function navigationHints(
  callback: (navigationHints) => boolean,
): Promise<number>
```

| Param             | Type      | Required | Description |
| ----------------- | --------- | -------- | ----------- |
| `navigationHints` | `boolean` | false    |             |

Promise resolution:

```
number
```

#### Examples

Navigation hints enabled

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await navigationHints((result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "VoiceGuidance.onNavigationHintsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Navigation hints disabled

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await navigationHints((result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "VoiceGuidance.onNavigationHintsChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
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

### rate

The rate at which voice guidance speech will be read back to the user.

To get the value of `rate` call the method like this:

```typescript
function rate(): Promise<SpeechRate>
```

Promise resolution:

[SpeechRate](../Accessibility/schemas/#SpeechRate)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Normal voice guidance speech rate

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let rate = await VoiceGuidance.rate()
console.log(rate)
```

Value of `rate`:

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
  "method": "VoiceGuidance.rate",
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

Doubled voice guidance speech rate

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let rate = await VoiceGuidance.rate()
console.log(rate)
```

Value of `rate`:

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
  "method": "VoiceGuidance.rate",
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

To set the value of `rate` call the method like this:

```typescript
function rate(value: SpeechRate): Promise<void>
```

Parameters:

| Param       | Type                                                               | Required | Description       |
| ----------- | ------------------------------------------------------------------ | -------- | ----------------- |
| `value`     | [`Accessibility.SpeechRate`](../Accessibility/schemas/#SpeechRate) | true     | <br/>minumum: 0.1 |
| maximum: 10 |

Promise resolution:

#### Examples

Normal voice guidance speech rate

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.rate(1)
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
  "method": "VoiceGuidance.setRate",
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

Doubled voice guidance speech rate

JavaScript:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let result = await VoiceGuidance.rate(2)
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
  "method": "VoiceGuidance.setRate",
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
function rate(callback: (rate) => SpeechRate): Promise<number>
```

| Param       | Type                                                               | Required | Description       |
| ----------- | ------------------------------------------------------------------ | -------- | ----------------- |
| `rate`      | [`Accessibility.SpeechRate`](../Accessibility/schemas/#SpeechRate) | false    | <br/>minumum: 0.1 |
| maximum: 10 |

Promise resolution:

```
number
```

#### Examples

Normal voice guidance speech rate

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await rate((result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "VoiceGuidance.onRateChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Doubled voice guidance speech rate

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await rate((result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "VoiceGuidance.onRateChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### speed

The speed at which voice guidance speech will be read back to the user.

To get the value of `speed` call the method like this:

```typescript
function speed(): Promise<SpeechRate>
```

Promise resolution:

[SpeechRate](../Accessibility/schemas/#SpeechRate)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Normal voice guidance speech rate

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

Doubled voice guidance speech rate

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
function speed(value: SpeechRate): Promise<void>
```

Parameters:

| Param       | Type                                                               | Required | Description       |
| ----------- | ------------------------------------------------------------------ | -------- | ----------------- |
| `value`     | [`Accessibility.SpeechRate`](../Accessibility/schemas/#SpeechRate) | true     | <br/>minumum: 0.1 |
| maximum: 10 |

Promise resolution:

#### Examples

Normal voice guidance speech rate

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

Doubled voice guidance speech rate

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
function rate(callback: (speed) => SpeechRate): Promise<number>
```

| Param       | Type                                                               | Required | Description       |
| ----------- | ------------------------------------------------------------------ | -------- | ----------------- |
| `speed`     | [`Accessibility.SpeechRate`](../Accessibility/schemas/#SpeechRate) | false    | <br/>minumum: 0.1 |
| maximum: 10 |

Promise resolution:

```
number
```

#### Examples

Normal voice guidance speech rate

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await rate((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Doubled voice guidance speech rate

```typescript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'

let listenerId = await rate((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

## Events

### onEnabledChanged

See: [enabled](#enabled)

### onNavigationHintsChanged

See: [navigationHints](#navigationhints)

### onRateChanged

See: [rate](#rate)

### onSpeedChanged

See: [rate](#rate)

## Private Events

### onEnabledChanged

See: [enabled](#enabled)

### onNavigationHintsChanged

See: [navigationHints](#navigationhints)

### onRateChanged

See: [rate](#rate)

### onSpeedChanged

See: [rate](#rate)

## Types
