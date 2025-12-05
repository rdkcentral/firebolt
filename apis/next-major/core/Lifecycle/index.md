---
title: Lifecycle

version: next-major
layout: default
sdk: core
---

# Lifecycle Module

---

Version Lifecycle 1.8.0-next-major.4

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [close](#close)
  - [finished](#finished)
  - [listen](#listen)
  - [once](#once)
  - [ready](#ready)
  - [state](#state)
- [Events](#events)
  - [onBackground](#onbackground)
  - [onForeground](#onforeground)
  - [onInactive](#oninactive)
  - [onSuspended](#onsuspended)
  - [onUnloading](#onunloading)
- [Private Events](#private-events)
- [Types](#types)
  - [LifecycleEvent](#lifecycleevent)

## Usage

To use the Lifecycle module, you can import it into your project from the Firebolt SDK:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'
```

## Overview

Methods and events for responding to lifecycle changes in your app

## Methods

### close

Request that the platform move your app out of focus

```typescript
function close(reason: CloseReason): Promise<void>
```

Parameters:

| Param    | Type                                               | Required | Description                                                                                                    |
| -------- | -------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------- |
| `reason` | [`CloseReason`](../Lifecycle/schemas/#CloseReason) | true     | The reason the app is requesting to be closed <br/>values: `'remoteButton' \| 'userExit' \| 'done' \| 'error'` |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Close the app when the user presses back on the app home screen

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let success = await Lifecycle.close('remoteButton')
console.log(success)
```

Value of `success`:

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
  "method": "Lifecycle.close",
  "params": {
    "reason": "remoteButton"
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

Close the app when the user selects an exit menu item

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let success = await Lifecycle.close('userExit')
console.log(success)
```

Value of `success`:

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
  "method": "Lifecycle.close",
  "params": {
    "reason": "userExit"
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

### finished

Notify the platform that the app is done unloading

```typescript
function finished(): Promise<void>
```

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let results = await Lifecycle.finished()
console.log(results)
```

Value of `results`:

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
  "method": "Lifecycle.finished",
  "params": {}
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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### ready

Notify the platform that the app is ready

```typescript
function ready(): Promise<void>
```

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:ready |

#### Examples

Let the platform know that your app is ready

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let result = await Lifecycle.ready()
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
  "method": "Lifecycle.ready",
  "params": {}
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

### state

Get the current state of the app. This function is **synchronous**.

```typescript
function state(): Promise<LifecycleState>
```

Promise resolution:

[LifecycleState](../Lifecycle/schemas/#LifecycleState)

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

const state = Lifecycle.state()
console.log(state)
```

Value of `state`:

```javascript
'foreground'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Lifecycle.state",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "foreground"
}
```

</details>

---

## Events

### onBackground

```typescript
function listen('onBackground', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onBackground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "background",
		"previous": "foreground"
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
  "method": "Lifecycle.onBackground",
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

### onForeground

```typescript
function listen('onForeground', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onForeground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"Default Result": {
		"state": "foreground",
		"previous": "inactive"
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
  "method": "Lifecycle.onForeground",
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

Move to foreground via remote branded buton

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onForeground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"Default Result": {
		"state": "foreground",
		"previous": "inactive"
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
  "method": "Lifecycle.onForeground",
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

### onInactive

```typescript
function listen('onInactive', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onInactive', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "inactive",
		"previous": "initializing"
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
  "method": "Lifecycle.onInactive",
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

### onSuspended

```typescript
function listen('onSuspended', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onSuspended', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "suspended",
		"previous": "inactive"
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
  "method": "Lifecycle.onSuspended",
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

### onUnloading

```typescript
function listen('onUnloading', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onUnloading', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "unloading",
		"previous": "inactive"
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
  "method": "Lifecycle.onUnloading",
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

## Private Events

### onBackground

```typescript
function listen('onBackground', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onBackground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "background",
		"previous": "foreground"
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
  "method": "Lifecycle.onBackground",
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

### onForeground

```typescript
function listen('onForeground', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onForeground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"Default Result": {
		"state": "foreground",
		"previous": "inactive"
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
  "method": "Lifecycle.onForeground",
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

Move to foreground via remote branded buton

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onForeground', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"Default Result": {
		"state": "foreground",
		"previous": "inactive"
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
  "method": "Lifecycle.onForeground",
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

### onInactive

```typescript
function listen('onInactive', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onInactive', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "inactive",
		"previous": "initializing"
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
  "method": "Lifecycle.onInactive",
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

### onSuspended

```typescript
function listen('onSuspended', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onSuspended', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "suspended",
		"previous": "inactive"
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
  "method": "Lifecycle.onSuspended",
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

### onUnloading

```typescript
function listen('onUnloading', (LifecycleEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                | Required | Description |
| ------- | ----------------------------------- | -------- | ----------- |
| `value` | [`LifecycleEvent`](#lifecycleevent) | false    |             |

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

let listenerId = await Lifecycle.listen('onUnloading', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"value": {
		"state": "unloading",
		"previous": "inactive"
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
  "method": "Lifecycle.onUnloading",
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

## Types

### LifecycleEvent

A an object describing the previous and current states

```typescript
type LifecycleEvent = {
  state: LifecycleState // The application lifecycle state
  previous: LifecycleState // The application lifecycle state
  source?: 'voice' | 'remote' // The source of the lifecycle change.
}
```

See also:

[LifecycleState](../Lifecycle/schemas/#LifecycleState)

---
