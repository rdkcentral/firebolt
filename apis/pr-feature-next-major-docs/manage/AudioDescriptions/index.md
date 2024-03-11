---
title: AudioDescriptions

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# AudioDescriptions Module

---

Version AudioDescriptions 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [enabled](#enabled)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [enabledChanged](#enabledchanged)

## Usage

To use the AudioDescriptions module, you can import it into your project from the Firebolt SDK:

```javascript
import { AudioDescriptions } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing audio-description Settings.

## Methods

### enabled

Whether or not audio-descriptions are enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                              |
| ---- | ------------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:audiodescriptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

let enabled = await AudioDescriptions.enabled()
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
  "method": "AudioDescriptions.enabled",
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
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

let enabled = await AudioDescriptions.enabled()
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
  "method": "AudioDescriptions.enabled",
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
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

let result = await AudioDescriptions.enabled(true)
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
  "method": "AudioDescriptions.setEnabled",
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
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

let result = await AudioDescriptions.enabled(false)
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
  "method": "AudioDescriptions.setEnabled",
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
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

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
  "method": "AudioDescriptions.onEnabledChanged",
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
import { AudioDescriptions } from '@firebolt-js/manage-sdk'

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
  "method": "AudioDescriptions.onEnabledChanged",
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

| Type     | Description                                                                                               |
| -------- | --------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioDescriptions.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioDescriptions.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioDescriptions.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `AudioDescriptions.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### enabledChanged

See: [enabled](#enabled)
