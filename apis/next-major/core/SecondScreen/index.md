---
title: SecondScreen

version: next-major
layout: default
sdk: core
---

# SecondScreen Module

---

Version SecondScreen 1.8.0-next-major.3

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [device](#device)
  - [friendlyName](#friendlyname)
  - [listen](#listen)
  - [once](#once)
  - [protocols](#protocols)
- [Events](#events)
  - [onCloseRequest](#oncloserequest)
  - [onFriendlyNameChanged](#onfriendlynamechanged)
  - [onLaunchRequest](#onlaunchrequest)
- [Private Events](#private-events)
- [Types](#types)

## Usage

To use the SecondScreen module, you can import it into your project from the Firebolt SDK:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'
```

## Overview

Methods for communicating with second screen devices

## Methods

### device

Get the broadcasted id for the device

```typescript
function device(type: string): Promise<string>
```

Parameters:

| Param  | Type     | Required | Description                                     |
| ------ | -------- | -------- | ----------------------------------------------- |
| `type` | `string` | false    | The type of second screen protocol, e.g. "dial" |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let deviceId = await SecondScreen.device()
console.log(deviceId)
```

Value of `deviceId`:

```javascript
'device-id'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecondScreen.device",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "device-id"
}
```

</details>

---

### friendlyName

Get the broadcasted friendly name for the device

To get the value of `friendlyName` call the method like this:

```typescript
function friendlyName(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let friendlyName = await SecondScreen.friendlyName()
console.log(friendlyName)
```

Value of `friendlyName`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecondScreen.friendlyName",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function friendlyName(callback: (friendlyName) => string): Promise<number>
```

| Param          | Type     | Required | Description              |
| -------------- | -------- | -------- | ------------------------ |
| `friendlyName` | `string` | false    | the device friendly-name |

Promise resolution:

```
number
```

#### Examples

Default Example

```typescript
import { SecondScreen } from '@firebolt-js/sdk'

let listenerId = await friendlyName((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecondScreen.onFriendlyNameChanged",
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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### protocols

Get the supported second screen discovery protocols

```typescript
function protocols(): Promise<BooleanMap>
```

Promise resolution:

[BooleanMap](../Types/schemas/#BooleanMap)

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:secondscreen:protocol |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let protocols = await SecondScreen.protocols()
console.log(protocols)
```

Value of `protocols`:

```javascript
{"dial1.7":true}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecondScreen.protocols",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "dial1.7": true
  }
}
```

</details>

---

## Events

### onCloseRequest

```typescript
function listen('onCloseRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param               | Type                                                              | Required | Description |
| ------------------- | ----------------------------------------------------------------- | -------- | ----------- |
| `closeRequestEvent` | [`SecondScreenEvent`](../SecondScreen/schemas/#SecondScreenEvent) | false    |             |

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let listenerId = await SecondScreen.listen('onCloseRequest', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"closeRequestEvent": {
		"type": "dial",
		"version": "1.7"
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
  "method": "SecondScreen.onCloseRequest",
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

### onFriendlyNameChanged

See: [friendlyName](#friendlyname)

### onLaunchRequest

```typescript
function listen('onLaunchRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param                | Type                                                              | Required | Description                                                                                       |
| -------------------- | ----------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------- |
| `launchRequestEvent` | [`SecondScreenEvent`](../SecondScreen/schemas/#SecondScreenEvent) | false    | Dispatched when a second screen device on the local network has requested this app to be launched |

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let listenerId = await SecondScreen.listen('onLaunchRequest', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"launchRequestEvent": {
		"type": "dial",
		"version": "1.7",
		"data": "{\"code\":\"AQDPQZiQcb3KQ7gY7yy5tHTMbbkGHR9Zjp-KL53H3eKBZIeAt7O9UKYPu6B21l2UZVmIqkFXDXBmXvK4g2e3EgZtjMNmKPsTltgnRl95DImtOXjSpWtTjSaOkW4w1kZKUTwLKdwVWTzBVH8ERHorvLU6vCGOVHxXt65LNwdl5HKRweShVC1V9QsyvRnQS61ov0UclmrH_xZML2Bt-Q-rZFjey5MjwupIb4x4f53XUJMhjHpDHoIUKrjpdPDQvK2a\",\"friendlyName\":\"Operator_TX061AEI\",\"UDN\":\"608fef11-2800-482a-962b-23a6690c93c1\"}"
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
  "method": "SecondScreen.onLaunchRequest",
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

### onCloseRequest

```typescript
function listen('onCloseRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param               | Type                                                              | Required | Description |
| ------------------- | ----------------------------------------------------------------- | -------- | ----------- |
| `closeRequestEvent` | [`SecondScreenEvent`](../SecondScreen/schemas/#SecondScreenEvent) | false    |             |

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let listenerId = await SecondScreen.listen('onCloseRequest', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"closeRequestEvent": {
		"type": "dial",
		"version": "1.7"
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
  "method": "SecondScreen.onCloseRequest",
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

### onFriendlyNameChanged

See: [friendlyName](#friendlyname)

### onLaunchRequest

```typescript
function listen('onLaunchRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param                | Type                                                              | Required | Description                                                                                       |
| -------------------- | ----------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------- |
| `launchRequestEvent` | [`SecondScreenEvent`](../SecondScreen/schemas/#SecondScreenEvent) | false    | Dispatched when a second screen device on the local network has requested this app to be launched |

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

let listenerId = await SecondScreen.listen('onLaunchRequest', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"launchRequestEvent": {
		"type": "dial",
		"version": "1.7",
		"data": "{\"code\":\"AQDPQZiQcb3KQ7gY7yy5tHTMbbkGHR9Zjp-KL53H3eKBZIeAt7O9UKYPu6B21l2UZVmIqkFXDXBmXvK4g2e3EgZtjMNmKPsTltgnRl95DImtOXjSpWtTjSaOkW4w1kZKUTwLKdwVWTzBVH8ERHorvLU6vCGOVHxXt65LNwdl5HKRweShVC1V9QsyvRnQS61ov0UclmrH_xZML2Bt-Q-rZFjey5MjwupIb4x4f53XUJMhjHpDHoIUKrjpdPDQvK2a\",\"friendlyName\":\"Operator_TX061AEI\",\"UDN\":\"608fef11-2800-482a-962b-23a6690c93c1\"}"
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
  "method": "SecondScreen.onLaunchRequest",
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
