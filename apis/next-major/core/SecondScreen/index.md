---
title: SecondScreen

version: next-major
layout: default
sdk: core
---

# SecondScreen Module

---

Version SecondScreen 0.0.0-unknown.0

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
  - [closeRequest](#closerequest)
  - [friendlyNameChanged](#friendlynamechanged)
  - [launchRequest](#launchrequest)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [friendlyNameChanged](#friendlynamechanged-1)
  - [launchRequest](#launchrequest-1)
  </details>
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
function ${method.alternative}(${event.signature.params}${if.context}, ${end.if.context}callback: (value) => string): Promise<number>
```

${event.params}

Promise resolution:

```
number
```

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

### closeRequest

```typescript
function listen('closeRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('closeRequest', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onCloseRequest",
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
  "result": null
}
```

</details>

---

### friendlyNameChanged

```typescript
function listen('friendlyNameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('friendlyNameChanged', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onFriendlyNameChanged",
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
  "result": null
}
```

</details>

---

### launchRequest

```typescript
function listen('launchRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('launchRequest', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onLaunchRequest",
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
  "result": null
}
```

</details>

---

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### closeRequest

```typescript
function listen('closeRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('closeRequest', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onCloseRequest",
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
  "result": null
}
```

</details>

---

### friendlyNameChanged

```typescript
function listen('friendlyNameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('friendlyNameChanged', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onFriendlyNameChanged",
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
  "result": null
}
```

</details>

---

### launchRequest

```typescript
function listen('launchRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

Default Example

JavaScript:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('launchRequest', (result) => {
  console.log(result)
})
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
  "method": "SecondScreen.onLaunchRequest",
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
  "result": null
}
```

</details>

---

</details>

## Types
