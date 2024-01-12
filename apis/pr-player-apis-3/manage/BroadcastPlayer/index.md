---
title: BroadcastPlayer

version: pr-player-apis-3
layout: default
sdk: manage
---

# BroadcastPlayer Module

---

Version BroadcastPlayer 1.0.1-player-apis-3.1

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [create](#create)
  - [listen](#listen)
  - [once](#once)
  - [status](#status)
- [Events](#events)
  - [statusChanged](#statuschanged)
- [Types](#types)
  - [BroadcastPlayerCreateRequest](#broadcastplayercreaterequest)
  - [BroadcastPlayerInstance](#broadcastplayerinstance)
  - [BroadcastPlayerStatus](#broadcastplayerstatus)

## Usage

To use the BroadcastPlayer module, you can import it into your project from the Firebolt SDK:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'
```

## Overview

A module for controlling and accessing media over broadcast

## Methods

### create

Creates an instance of a player that can be used to play media over broadcast. Player instance that is created should also provide firebolt capability 'xrn:firebolt:capability:player:base'. If there is no provider running but there is a provider in the catalog, it will be launched.

```typescript
function create(
  request: BroadcastPlayerCreateRequest,
): Promise<BroadcastPlayerInstance>
```

Parameters:

| Param     | Type                                                            | Required | Description        |
| --------- | --------------------------------------------------------------- | -------- | ------------------ |
| `request` | [`BroadcastPlayerCreateRequest`](#broadcastplayercreaterequest) | true     | The create request |

Promise resolution:

[BroadcastPlayerInstance](#broadcastplayerinstance)

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:player:broadcast |

#### Examples

Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

let playerInstance = await BroadcastPlayer.create({})
console.log(playerInstance)
```

Value of `playerInstance`:

```javascript
{
	"playerId": "123",
	"windowId": "456"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "BroadcastPlayer.create",
  "params": {
    "request": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "playerId": "123",
    "windowId": "456"
  }
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

| Type     | Description                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

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

| Type     | Description                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

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

| Type     | Description                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

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

| Type     | Description                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### status

Gets the latest broadcast status for the given player

To get the value of `status` call the method like this:

```typescript
function status(playerId: string): Promise<BroadcastPlayerStatus>
```

Parameters:

| Param      | Type     | Required | Description                                |
| ---------- | -------- | -------- | ------------------------------------------ |
| `playerId` | `string` | true     | The id of the player to get the status for |

Promise resolution:

[BroadcastPlayerStatus](#broadcastplayerstatus)

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:player:broadcast |

#### Examples

Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

let playerStatus = await BroadcastPlayer.status('app1:123')
console.log(playerStatus)
```

Value of `playerStatus`:

```javascript
{
	"locked": false,
	"frequency": 695000000,
	"signalStrength": 90,
	"signalQuality": 90
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "BroadcastPlayer.status",
  "params": {
    "playerId": "app1:123"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "locked": false,
    "frequency": 695000000,
    "signalStrength": 90,
    "signalQuality": 90
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

let playerStatus = await BroadcastPlayer.status('app2:456')
console.log(playerStatus)
```

Value of `playerStatus`:

```javascript
{
	"locked": false,
	"frequency": 695000000,
	"signalStrength": 90,
	"signalQuality": 90
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "BroadcastPlayer.status",
  "params": {
    "playerId": "app2:456"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "locked": true,
    "frequency": 695000000,
    "signalStrength": 23,
    "signalQuality": 55
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function status(
  playerId: string,
  callback: (value) => BroadcastPlayerStatus,
): Promise<number>
```

Parameters:

| Param      | Type     | Required | Description                                |
| ---------- | -------- | -------- | ------------------------------------------ |
| `playerId` | `string` | true     | The id of the player to get the status for |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerStatus`:

```javascript
{
	"locked": false,
	"frequency": 695000000,
	"signalStrength": 90,
	"signalQuality": 90
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "BroadcastPlayer.onStatusChanged",
  "params": {
    "playerId": "app1:123",
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
    "locked": false,
    "frequency": 695000000,
    "signalStrength": 90,
    "signalQuality": 90
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerStatus`:

```javascript
{
	"locked": false,
	"frequency": 695000000,
	"signalStrength": 90,
	"signalQuality": 90
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "BroadcastPlayer.onStatusChanged",
  "params": {
    "playerId": "app2:456",
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
    "locked": true,
    "frequency": 695000000,
    "signalStrength": 23,
    "signalQuality": 55
  }
}
```

</details>

---

## Events

### statusChanged

See: [status](#status)

## Types

### BroadcastPlayerCreateRequest

```typescript
type BroadcastPlayerCreateRequest = {}
```

---

### BroadcastPlayerInstance

```typescript
type BroadcastPlayerInstance = {
  playerId: string // The id of player which can be used to load media or control the player
  windowId: string // The id of window which will render the media in, can be used to control on screen where the media is shown
}
```

---

### BroadcastPlayerStatus

```typescript
type BroadcastPlayerStatus = {
  locked: boolean // Whether the current media has been locked
  frequency: number // The signal frequency in hertz
  signalStrength: number // The strength of the signal from 0-100
  signalQuality: number // The quality of the signal from 0-100
}
```

---
