---
title: Player

version: pr-player-apis-3
layout: default
sdk: manage
---

# Player Module

---

Version Player 1.0.1-player-apis-3.1

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [load](#load)
  - [once](#once)
  - [play](#play)
  - [progress](#progress)
  - [setAudioTrack](#setaudiotrack)
  - [setCaptionsTrack](#setcaptionstrack)
  - [setPosition](#setposition)
  - [setSpeed](#setspeed)
  - [status](#status)
  - [stop](#stop)
  - [tracks](#tracks)
- [Events](#events)
  - [progressChanged](#progresschanged)
  - [statusChanged](#statuschanged)
- [Types](#types)
  - [LoadRequest](#loadrequest)
  - [PlayerMediaSession](#playermediasession)
  - [PlayerStatus](#playerstatus)
  - [PlayerProgress](#playerprogress)
  - [AudioTrack](#audiotrack)
  - [CaptionsTrack](#captionstrack)
  - [PlayerTracks](#playertracks)

## Usage

To use the Player module, you can import it into your project from the Firebolt SDK:

```javascript
import { Player } from '@firebolt-js/manage-sdk'
```

## Overview

A module for providing and using media player capabilities. This handles operations that would be associated with any player generically

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### load

Loads content in a player and starts a media session

```typescript
function load(
  playerId: string,
  request: LoadRequest,
): Promise<PlayerMediaSession>
```

Parameters:

| Param      | Type                          | Required | Description                             |
| ---------- | ----------------------------- | -------- | --------------------------------------- |
| `playerId` | `string`                      | true     | The id of the player to load content in |
| `request`  | [`LoadRequest`](#loadrequest) | true     | The load request                        |

Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let mediaSession = await Player.load('app1:123', {
  locator: 'https://cdn.rdkcentral.com/media/assets/asset.hls',
})
console.log(mediaSession)
```

Value of `mediaSession`:

```javascript
{
	"mediaSessionId": "sess1"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.load",
  "params": {
    "playerId": "app1:123",
    "request": {
      "locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "mediaSessionId": "sess1"
  }
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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### play

Starts playing the content that was last loaded

```typescript
function play(playerId: string): Promise<PlayerMediaSession>
```

Parameters:

| Param      | Type     | Required | Description                           |
| ---------- | -------- | -------- | ------------------------------------- |
| `playerId` | `string` | true     | The id of the player to start playing |

Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let mediaSession = await Player.play('app1:123')
console.log(mediaSession)
```

Value of `mediaSession`:

```javascript
{
	"mediaSessionId": "sess1"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.play",
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
    "mediaSessionId": "sess1"
  }
}
```

</details>

---

### progress

Gets the latest progress for the given player

To get the value of `progress` call the method like this:

```typescript
function progress(playerId: string): Promise<PlayerProgress>
```

Parameters:

| Param      | Type     | Required | Description                                  |
| ---------- | -------- | -------- | -------------------------------------------- |
| `playerId` | `string` | true     | The id of the player to get the progress for |

Promise resolution:

[PlayerProgress](#playerprogress)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let playerProgress = await Player.progress('app1:123')
console.log(playerProgress)
```

Value of `playerProgress`:

```javascript
{
	"speed": 1,
	"startPosition": 0,
	"position": 5000,
	"endPosition": 3600000,
	"liveSyncTime": "2021-04-23T18:25:43.511Z"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.progress",
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
    "speed": 1,
    "startPosition": 0,
    "position": 5000,
    "endPosition": 3600000,
    "liveSyncTime": "2021-04-23T18:25:43.511Z"
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let playerProgress = await Player.progress('app2:456')
console.log(playerProgress)
```

Value of `playerProgress`:

```javascript
{
	"speed": 1,
	"startPosition": 0,
	"position": 5000,
	"endPosition": 3600000,
	"liveSyncTime": "2021-04-23T18:25:43.511Z"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.progress",
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
    "speed": 3,
    "startPosition": 5000,
    "position": 10000,
    "endPosition": 3600000,
    "liveSyncTime": "2021-05-23T18:25:43.511Z"
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function progress(
  playerId: string,
  callback: (value) => PlayerProgress,
): Promise<number>
```

Parameters:

| Param      | Type     | Required | Description                                  |
| ---------- | -------- | -------- | -------------------------------------------- |
| `playerId` | `string` | true     | The id of the player to get the progress for |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let listenerId = await progress((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerProgress`:

```javascript
{
	"speed": 1,
	"startPosition": 0,
	"position": 5000,
	"endPosition": 3600000,
	"liveSyncTime": "2021-04-23T18:25:43.511Z"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.onProgressChanged",
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
    "speed": 1,
    "startPosition": 0,
    "position": 5000,
    "endPosition": 3600000,
    "liveSyncTime": "2021-04-23T18:25:43.511Z"
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let listenerId = await progress((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerProgress`:

```javascript
{
	"speed": 1,
	"startPosition": 0,
	"position": 5000,
	"endPosition": 3600000,
	"liveSyncTime": "2021-04-23T18:25:43.511Z"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.onProgressChanged",
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
    "speed": 3,
    "startPosition": 5000,
    "position": 10000,
    "endPosition": 3600000,
    "liveSyncTime": "2021-05-23T18:25:43.511Z"
  }
}
```

</details>

---

### setAudioTrack

Selects the given audio track

```typescript
function setAudioTrack(playerId: string, trackId: string): Promise<void>
```

Parameters:

| Param      | Type     | Required | Description                               |
| ---------- | -------- | -------- | ----------------------------------------- |
| `playerId` | `string` | true     | The id of the player to set the track for |
| `trackId`  | `string` | true     | The id of the track to select             |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setAudioTrackResult = await Player.setAudioTrack('app1:123', 'Audio1')
console.log(setAudioTrackResult)
```

Value of `setAudioTrackResult`:

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
  "method": "Player.setAudioTrack",
  "params": {
    "playerId": "app1:123",
    "trackId": "Audio1"
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

### setCaptionsTrack

Selects the given captions track

```typescript
function setCaptionsTrack(playerId: string, trackId: string): Promise<void>
```

Parameters:

| Param      | Type     | Required | Description                               |
| ---------- | -------- | -------- | ----------------------------------------- |
| `playerId` | `string` | true     | The id of the player to set the track for |
| `trackId`  | `string` | true     | The id of the track to select             |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setCaptionsTrackResult = await Player.setCaptionsTrack('app1:123', 'CC1')
console.log(setCaptionsTrackResult)
```

Value of `setCaptionsTrackResult`:

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
  "method": "Player.setCaptionsTrack",
  "params": {
    "playerId": "app1:123",
    "trackId": "CC1"
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

### setPosition

Tells the player to set its position to the given offset in the media

```typescript
function setPosition(playerId: string, position: number): Promise<void>
```

Parameters:

| Param      | Type     | Required | Description                                                            |
| ---------- | -------- | -------- | ---------------------------------------------------------------------- |
| `playerId` | `string` | true     | The id of the player to set the position for                           |
| `position` | `number` | true     | The position the player should seek to in milliseconds <br/>minumum: 0 |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setPositionResponse = await Player.setPosition('app1:123', 10000)
console.log(setPositionResponse)
```

Value of `setPositionResponse`:

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
  "method": "Player.setPosition",
  "params": {
    "playerId": "app1:123",
    "position": 10000
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

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setPositionResponse = await Player.setPosition('app1:123', 600000)
console.log(setPositionResponse)
```

Value of `setPositionResponse`:

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
  "method": "Player.setPosition",
  "params": {
    "playerId": "app1:123",
    "position": 600000
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

### setSpeed

Tells the player to set its speed

```typescript
function setSpeed(playerId: string, speed: number): Promise<void>
```

Parameters:

| Param      | Type     | Required | Description                                                                                                            |
| ---------- | -------- | -------- | ---------------------------------------------------------------------------------------------------------------------- |
| `playerId` | `string` | true     | The id of the player to set the position for                                                                           |
| `speed`    | `number` | true     | The speed to set as a multiplier of the default speed. Negative values would cause the media to rewind. Use 0 to pause |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Set speed to 2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setSpeedResponse = await Player.setSpeed('app1:123', 2)
console.log(setSpeedResponse)
```

Value of `setSpeedResponse`:

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
  "method": "Player.setSpeed",
  "params": {
    "playerId": "app1:123",
    "speed": 2
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

Set speed to 0.5

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setSpeedResponse = await Player.setSpeed('app1:123', 0.5)
console.log(setSpeedResponse)
```

Value of `setSpeedResponse`:

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
  "method": "Player.setSpeed",
  "params": {
    "playerId": "app1:123",
    "speed": 0.5
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

Set speed to -2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setSpeedResponse = await Player.setSpeed('app1:123', -2)
console.log(setSpeedResponse)
```

Value of `setSpeedResponse`:

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
  "method": "Player.setSpeed",
  "params": {
    "playerId": "app1:123",
    "speed": -2
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

Set speed to 0

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let setSpeedResponse = await Player.setSpeed('app1:123', 0)
console.log(setSpeedResponse)
```

Value of `setSpeedResponse`:

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
  "method": "Player.setSpeed",
  "params": {
    "playerId": "app1:123",
    "speed": 0
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

### status

Gets the latest status for the given player

To get the value of `status` call the method like this:

```typescript
function status(playerId: string): Promise<PlayerStatus>
```

Parameters:

| Param      | Type     | Required | Description                                |
| ---------- | -------- | -------- | ------------------------------------------ |
| `playerId` | `string` | true     | The id of the player to get the status for |

Promise resolution:

[PlayerStatus](#playerstatus)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let playerStatus = await Player.status('app1:123')
console.log(playerStatus)
```

Value of `playerStatus`:

```javascript
{
	"mediaSessionId": "sess1",
	"state": "PLAYING"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.status",
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
    "mediaSessionId": "sess1",
    "state": "PLAYING"
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let playerStatus = await Player.status('app2:456')
console.log(playerStatus)
```

Value of `playerStatus`:

```javascript
{
	"mediaSessionId": "sess1",
	"state": "PLAYING"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.status",
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
    "mediaSessionId": "sess1",
    "state": "BLOCKED",
    "blockedReason": "CONTENT_NOT_FOUND"
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function status(
  playerId: string,
  callback: (value) => PlayerStatus,
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
import { Player } from '@firebolt-js/manage-sdk'

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerStatus`:

```javascript
{
	"mediaSessionId": "sess1",
	"state": "PLAYING"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.onStatusChanged",
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
    "mediaSessionId": "sess1",
    "state": "PLAYING"
  }
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let listenerId = await status((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `playerStatus`:

```javascript
{
	"mediaSessionId": "sess1",
	"state": "PLAYING"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.onStatusChanged",
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
    "mediaSessionId": "sess1",
    "state": "BLOCKED",
    "blockedReason": "CONTENT_NOT_FOUND"
  }
}
```

</details>

---

### stop

Stops playing the content that was last loaded

```typescript
function stop(playerId: string): Promise<PlayerMediaSession>
```

Parameters:

| Param      | Type     | Required | Description                  |
| ---------- | -------- | -------- | ---------------------------- |
| `playerId` | `string` | true     | The id of the player to stop |

Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let mediaSession = await Player.stop('app1:123')
console.log(mediaSession)
```

Value of `mediaSession`:

```javascript
{
	"mediaSessionId": "sess1"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.stop",
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
    "mediaSessionId": "sess1"
  }
}
```

</details>

---

### tracks

Gets the supported tracks for the current playing media

```typescript
function tracks(playerId: string): Promise<PlayerTracks>
```

Parameters:

| Param      | Type     | Required | Description                                |
| ---------- | -------- | -------- | ------------------------------------------ |
| `playerId` | `string` | true     | The id of the player to get the tracks for |

Promise resolution:

[PlayerTracks](#playertracks)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:player:base |

#### Examples

Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

let playerTracks = await Player.tracks('app1:123')
console.log(playerTracks)
```

Value of `playerTracks`:

```javascript
{
	"audio": [
		{
			"trackId": "123",
			"language": "en",
			"audioDescription": false,
			"type": "PCM",
			"selected": true
		}
	],
	"captions": [
		{
			"trackId": "123",
			"language": "en",
			"name": "CC1",
			"selected": true
		}
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Player.tracks",
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
    "audio": [
      {
        "trackId": "123",
        "language": "en",
        "audioDescription": false,
        "type": "PCM",
        "selected": true
      }
    ],
    "captions": [
      {
        "trackId": "123",
        "language": "en",
        "name": "CC1",
        "selected": true
      }
    ]
  }
}
```

</details>

---

## Events

### progressChanged

See: [progress](#progress)

### statusChanged

See: [status](#status)

## Types

### LoadRequest

```typescript
type LoadRequest = {
  locator: string // A locator to the content to load
  metadata?: {}
  autoPlay?: boolean // Start playing immediately on load without needing to call Player.play
}
```

---

### PlayerMediaSession

```typescript
type PlayerMediaSession = {
  mediaSessionId: string // The id of media session that was started, when the content was loaded. This should be a new value on each load
}
```

---

### PlayerStatus

```typescript
type PlayerStatus = {
  mediaSessionId: string // The id of media session that is currently loaded
  state: 'IDLE' | 'PENDING' | 'PLAYING' | 'BLOCKED' | 'FAILED' // The state of the player
  blockedReason?:
    | 'NO_NETWORK'
    | 'CONTENT_NOT_FOUND'
    | 'DRM_ERROR'
    | 'NOT_ENTITLED'
    | 'GEO_BLOCKED'
    | 'CHANNEL_NOT_SCANNED'
    | 'NO_SIGNAL'
    | 'TECHNICAL_FAULT'
    | 'CHANNEL_OFF_AIR'
    | 'PLAYER_FAILURE' // The state of the player
}
```

---

### PlayerProgress

```typescript
type PlayerProgress = {
  speed: number // The playback speed as a multiplier
  startPosition: number // The position that the media starts at in milliseconds
  position: number // The current position in milliseconds
  endPosition: number // The position that the media stops at in milliseconds
  liveSyncTime: string // The time to sync to live
}
```

---

### AudioTrack

```typescript
type AudioTrack = {
  trackId: string // The id of the track
  language: string
  audioDescription: boolean // Whether this track supports audio description
  type: 'PCM' | 'AC3' | 'EAC3' | 'AAC' // The type of track
  selected: boolean // Whether this track is currently selected
}
```

---

### CaptionsTrack

```typescript
type CaptionsTrack = {
  trackId: string // The id of the track
  language?: string
  name?: string // The name of track
  selected: boolean // Whether this track is currently selected
}
```

---

### PlayerTracks

```typescript
type PlayerTracks = {
  audio: AudioTrack[] // The list of audio tracks
  captions: CaptionsTrack[] // The list of captions tracks
}
```

See also:

[AudioTrack](#audiotrack)
[CaptionsTrack](#captionstrack)

---
