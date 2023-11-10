---
title: Player

version: pr206
layout: default
sdk: manage
---

# Player Module
---
Version Player 1.0.0

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
     - [status](#status)
     - [stop](#stop)
   - [Events](#events)
     - [progressChanged](#progresschanged)
     - [statusChanged](#statuschanged)
   - [Types](#types)
     - [LoadRequest](#loadrequest)
     - [PlayerMediaSession](#playermediasession)
     - [PlayerStatus](#playerstatus)
     - [PlayerProgress](#playerprogress)



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

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module  pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### load

Loads content in a player and starts a media session

```typescript
function load(playerId: string, request: LoadRequest): Promise<PlayerMediaSession>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to load content in  |
| `request` | [`LoadRequest`](#loadrequest) | true | The load request  |


Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.load("app1:123", {"locator":"https://cdn.rdkcentral.com/media/assets/asset.hls"})
    .then(mediaSession => {
        console.log(mediaSession)
    })
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

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Player.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### play

Starts playing the content that was last loaded

```typescript
function play(playerId: string): Promise<PlayerMediaSession>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to start playing  |


Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.play("app1:123")
    .then(mediaSession => {
        console.log(mediaSession)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to get the progress for  |


Promise resolution:

[PlayerProgress](#playerprogress)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.progress("app1:123")
    .then(playerProgress => {
        console.log(playerProgress)
    })
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

Player.progress("app2:456")
    .then(playerProgress => {
        console.log(playerProgress)
    })
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
function progress(playerId: string, callback: (value) => PlayerProgress): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to get the progress for  |


Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

progress(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

progress(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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


### status
Gets the latest status for the given player

To get the value of `status` call the method like this:

```typescript
function status(playerId: string): Promise<PlayerStatus>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to get the status for  |


Promise resolution:

[PlayerStatus](#playerstatus)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.status("app1:123")
    .then(playerStatus => {
        console.log(playerStatus)
    })
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

Player.status("app2:456")
    .then(playerStatus => {
        console.log(playerStatus)
    })
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
function status(playerId: string, callback: (value) => PlayerStatus): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to get the status for  |


Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

status(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

status(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to stop  |


Promise resolution:

[PlayerMediaSession](#playermediasession)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.stop("app1:123")
    .then(mediaSession => {
        console.log(mediaSession)
    })
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

## Events

### progressChanged

See: [progress](#progress)

### statusChanged

See: [status](#status)



## Types

### LoadRequest



```typescript
type LoadRequest = {
  locator: string     // A locator to the content to load
  metadata?: {
  }
  autoPlay?: boolean  // Start playing immediately on load without needing to call Player.play
}
```



---
### PlayerMediaSession



```typescript
type PlayerMediaSession = {
  mediaSessionId: string     // The id of media session that was started, when the content was loaded. This should be a new value on each load
}
```



---
### PlayerStatus



```typescript
type PlayerStatus = {
  mediaSessionId: string                                                                                                                                                                              // The id of media session that is currently loaded
  state: 'IDLE' | 'PENDING' | 'PLAYING' | 'BLOCKED' | 'FAILED'                                                                                                                                        // The state of the player
  blockedReason?: 'NO_NETWORK' | 'CONTENT_NOT_FOUND' | 'DRM_ERROR' | 'NOT_ENTITLED' | 'GEO_BLOCKED' | 'CHANNEL_NOT_SCANNED' | 'NO_SIGNAL' | 'TECHNICAL_FAULT' | 'CHANNEL_OFF_AIR' | 'PLAYER_FAILURE'  // The state of the player
}
```



---
### PlayerProgress



```typescript
type PlayerProgress = {
  speed: number          // The playback speed as a multiplier
  startPosition: number  // The position that the media starts at in milliseconds
  position: number       // The current position in milliseconds
  endPosition: number    // The position that the media stops at in milliseconds
  liveSyncTime: string   // The time to sync to live
}
```



---