---
title: Player

version: pr177
layout: default
sdk: manage
---

# Player Module
---
Version Player 0.17.1-proposed.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [listen](#listen)
     - [load](#load)
     - [loadError](#loaderror)
     - [loadResponse](#loadresponse)
     - [once](#once)
     - [play](#play)
     - [playError](#playerror)
     - [playResponse](#playresponse)
     - [progress](#progress)
     - [progressError](#progresserror)
     - [progressResponse](#progressresponse)
     - [provide](#provide)
     - [provideProgress](#provideprogress)
     - [provideStatus](#providestatus)
     - [status](#status)
     - [statusError](#statuserror)
     - [statusResponse](#statusresponse)
     - [stop](#stop)
     - [stopError](#stoperror)
     - [stopResponse](#stopresponse)
   - [Events](#events)
     - [progressChanged](#progresschanged)
     - [onRequestLoad](#onrequestload)
     - [onRequestPlay](#onrequestplay)
     - [onRequestProgress](#onrequestprogress)
     - [onRequestStatus](#onrequeststatus)
     - [onRequestStop](#onrequeststop)
     - [statusChanged](#statuschanged)
   - [Provider Interfaces](#provider-interfaces)
     - [BasePlayerProvider](#baseplayerprovider)
   - [Types](#types)
     - [PlayerLoadRequest](#playerloadrequest)
     - [PlayerMediaSession](#playermediasession)
     - [PlayerStatus](#playerstatus)
     - [PlayerProgress](#playerprogress)
     - [PlayerLoadProviderRequest](#playerloadproviderrequest)



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
function load(request: PlayerLoadRequest): Promise<PlayerMediaSession>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `request` | [`PlayerLoadRequest`](#playerloadrequest) | true | The load request  |


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

Player.load({
              "playerId": "app1:123",
              "locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
            })
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
		"request": {
			"playerId": "app1:123",
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

### loadError

*This is an private RPC method.*

Internal API for Load Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `error` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.loadError",
	"params": {
		"error": {
			"correlationId": "123",
			"result": {
				"code": 1,
				"message": "Error"
			}
		}
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



---

### loadResponse

*This is an private RPC method.*

Internal API for Load Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `response` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.loadResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess1"
			}
		}
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


Example #2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.loadResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess2"
			}
		}
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
function play(playerId: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to start playing  |


Promise resolution:

```typescript
void
```

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
    .then(playResponse => {
        console.log(playResponse)
    })
```

Value of `playResponse`:

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
	"result": null
}
```
</details>


---

### playError

*This is an private RPC method.*

Internal API for Play Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `error` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.playError",
	"params": {
		"error": {
			"correlationId": "123",
			"result": {
				"code": 1,
				"message": "Error"
			}
		}
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



---

### playResponse

*This is an private RPC method.*

Internal API for Play Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `response` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.playResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess1"
			}
		}
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


Example #2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.playResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess2"
			}
		}
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


### progressError

*This is an private RPC method.*

Internal API for Progress Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `error` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.progressError",
	"params": {
		"error": {
			"correlationId": "123",
			"result": {
				"code": 1,
				"message": "Error"
			}
		}
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



---

### progressResponse

*This is an private RPC method.*

Internal API for Progress Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `response` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.progressResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"speed": 1,
				"startPosition": 0,
				"position": 5000,
				"endPosition": 3600000,
				"liveSyncTime": "2021-04-23T18:25:43.511Z"
			}
		}
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


Example #2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.progressResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"speed": 3,
				"startPosition": 5000,
				"position": 10000,
				"endPosition": 3600000,
				"liveSyncTime": "2021-04-23T18:25:43.511Z"
			}
		}
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



---

### provide

To provide a specific capability to the platform. See [Provider Interfaces](#provider-interfaces) for a list of interfaces available to provide in this module.

```typescript
provide(capability: string, provider: any): void
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `capability` | `string` | Yes | The capability that is being provided. |
| `provider` | `any` | Yes | An implementation of the required interface. |

See [Provider Interfaces](#provider-interfaces) for each capabilities interface definition.

### provideProgress

Tells listeners the current progress of a player

```typescript
function provideProgress(playerId: string, progress: PlayerProgress): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player the progress is for  |
, | `progress` | [`PlayerProgress`](#playerprogress) | true | The progress  |


Promise resolution:

```typescript
void
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.provideProgress("123",
                       {
                         "speed": 1,
                         "startPosition": 0,
                         "position": 5000,
                         "endPosition": 3600000,
                         "liveSyncTime": "2021-04-23T18:25:43.511Z"
                       })
    .then(providedResponse => {
        console.log(providedResponse)
    })
```

Value of `providedResponse`:

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
	"method": "Player.provideProgress",
	"params": {
		"playerId": "123",
		"progress": {
			"speed": 1,
			"startPosition": 0,
			"position": 5000,
			"endPosition": 3600000,
			"liveSyncTime": "2021-04-23T18:25:43.511Z"
		}
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

### provideStatus

Tells listeners the current status of a player

```typescript
function provideStatus(playerId: string, status: PlayerStatus): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player the status is for  |
, | `status` | [`PlayerStatus`](#playerstatus) | true | The status  |


Promise resolution:

```typescript
void
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default example #1

JavaScript:

```javascript
import { Player } from '@firebolt-js/manage-sdk'

Player.provideStatus("123",
                     {
                       "mediaSessionId": "sess2",
                       "state": "BLOCKED",
                       "blockedReason": "CONTENT_NOT_FOUND"
                     })
    .then(providedResponse => {
        console.log(providedResponse)
    })
```

Value of `providedResponse`:

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
	"method": "Player.provideStatus",
	"params": {
		"playerId": "123",
		"status": {
			"mediaSessionId": "sess2",
			"state": "BLOCKED",
			"blockedReason": "CONTENT_NOT_FOUND"
		}
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


### statusError

*This is an private RPC method.*

Internal API for Status Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `error` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.statusError",
	"params": {
		"error": {
			"correlationId": "123",
			"result": {
				"code": 1,
				"message": "Error"
			}
		}
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



---

### statusResponse

*This is an private RPC method.*

Internal API for Status Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `response` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.statusResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess1",
				"state": "IDLE"
			}
		}
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


Example #2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.statusResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess2",
				"state": "BLOCKED",
				"blockedReason": "CONTENT_NOT_FOUND"
			}
		}
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



---

### stop

Stops playing the content that was last loaded

```typescript
function stop(playerId: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to stop  |


Promise resolution:

```typescript
void
```

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
    .then(stopResponse => {
        console.log(stopResponse)
    })
```

Value of `stopResponse`:

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
	"result": null
}
```
</details>


---

### stopError

*This is an private RPC method.*

Internal API for Stop Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `error` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.stopError",
	"params": {
		"error": {
			"correlationId": "123",
			"result": {
				"code": 1,
				"message": "Error"
			}
		}
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



---

### stopResponse

*This is an private RPC method.*

Internal API for Stop Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `response` | [`ProviderResponse`](../Types/schemas/#ProviderResponse) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.stopResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess1"
			}
		}
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


Example #2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.stopResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"mediaSessionId": "sess2"
			}
		}
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



---

## Events

### progressChanged

See: [progress](#progress)

### onRequestLoad

*This is an private RPC method.*

Registers as a provider for when new media should be loaded into the player

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerLoadProviderRequest](#playerloadproviderrequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestLoad",
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
		"correlationId": "abc",
		"parameters": {
			"playerId": "app1:123",
			"locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
		}
	}
}
```



---

### onRequestPlay

*This is an private RPC method.*

Registers as a provider for when media should start playing

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerProviderRequest](../Player/schemas/#PlayerProviderRequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestPlay",
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
		"correlationId": "abc",
		"parameters": {
			"playerId": "app1:123"
		}
	}
}
```



---

### onRequestProgress

*This is an private RPC method.*

Registers as a provider for when player progress needs to be provided

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerProviderRequest](../Player/schemas/#PlayerProviderRequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestProgress",
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
		"correlationId": "abc",
		"parameters": {
			"playerId": "123"
		}
	}
}
```



---

### onRequestStatus

*This is an private RPC method.*

Registers as a provider for when player status needs to be provided

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerProviderRequest](../Player/schemas/#PlayerProviderRequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestStatus",
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
		"correlationId": "abc",
		"parameters": {
			"playerId": "123"
		}
	}
}
```



---

### onRequestStop

*This is an private RPC method.*

Registers as a provider for when media should stop playing

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerProviderRequest](../Player/schemas/#PlayerProviderRequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestStop",
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
		"correlationId": "abc",
		"parameters": {
			"playerId": "app1:123"
		}
	}
}
```



---

### statusChanged

See: [status](#status)


## Provider Interfaces

### BasePlayerProvider
The provider interface for the `xrn:firebolt:capability:player:base` capability.

```typescript

```

Usage:

```typescript
Player.provide('xrn:firebolt:capability:player:base', provider: BasePlayerProvider | object)
```

#### load

Registers as a provider for when new media should be loaded into the player

```typescript
function load(parameters?: PlayerLoadRequest, session?: ProviderSession): Promise<PlayerMediaSession>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerLoadRequest`](#playerloadrequest) | false |   |
| `session` | `ProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to load the locator into  |
| `locator` | `string` | true | A locator to the content to load <br/>format: uri |
| `metadata` | `object` | false | An opaque set of metadata that will be relevant to the player.  |
| `autoPlay` | `boolean` | false | Start playing immediately on load without needing to call Player.play  |


```typescript
type PlayerLoadRequest = {
  playerId: string          // The id of the player instance to load the locator into
  locator: string           // A locator to the content to load
  metadata?: {
  }
  autoPlay?: boolean        // Start playing immediately on load without needing to call Player.play
}
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `mediaSessionId` | string | The id of media session that was started, when the content was loaded. This should be a new value on each load | 

#### play

Registers as a provider for when media should start playing

```typescript
function play(parameters?: PlayerRequest, session?: ProviderSession): Promise<PlayerMediaSession>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerRequest`](../Player/schemas/#PlayerRequest) | false |   |
| `session` | `ProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `mediaSessionId` | string | The id of media session that was started, when the content was loaded. This should be a new value on each load | 

#### stop

Registers as a provider for when media should stop playing

```typescript
function stop(parameters?: PlayerRequest, session?: ProviderSession): Promise<PlayerMediaSession>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerRequest`](../Player/schemas/#PlayerRequest) | false |   |
| `session` | `ProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `mediaSessionId` | string | The id of media session that was started, when the content was loaded. This should be a new value on each load | 

#### status

Registers as a provider for when player status needs to be provided

```typescript
function status(parameters?: PlayerRequest, session?: ProviderSession): Promise<PlayerStatus>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerRequest`](../Player/schemas/#PlayerRequest) | false |   |
| `session` | `ProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `mediaSessionId` | string | The id of media session that is currently loaded | 
| `state` | 'IDLE' | 'PENDING' | 'PLAYING' | 'BLOCKED' | 'FAILED' | The state of the player | 
| `blockedReason` | 'NO_NETWORK' | 'CONTENT_NOT_FOUND' | 'DRM_ERROR' | 'NOT_ENTITLED' | 'GEO_BLOCKED' | 'CHANNEL_NOT_SCANNED' | 'NO_SIGNAL' | 'TECHNICAL_FAULT' | 'CHANNEL_OFF_AIR' | 'PLAYER_FAILURE' | The state of the player | 

#### progress

Registers as a provider for when player progress needs to be provided

```typescript
function progress(parameters?: PlayerRequest, session?: ProviderSession): Promise<PlayerProgress>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerRequest`](../Player/schemas/#PlayerRequest) | false |   |
| `session` | `ProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `speed` | number | The playback speed as a multiplier | 
| `startPosition` | number | The position that the media starts at in milliseconds | 
| `position` | number | The current position in milliseconds | 
| `endPosition` | number | The position that the media stops at in milliseconds | 
| `liveSyncTime` | string | The time to sync to live | 



#### Examples

**Register your app to provide the `xrn:firebolt:capability:player:base` capability.**

```javascript
import { Player } from '@firebolt-js/manage-sdk'

class MyBasePlayerProvider {

    async load(parameters, session) {
        return await Promise.resolve({
            "mediaSessionId": "sess1"
        })
    }

    async play(parameters, session) {
        return await Promise.resolve({
            "mediaSessionId": "sess1"
        })
    }

    async stop(parameters, session) {
        return await Promise.resolve({
            "mediaSessionId": "sess1"
        })
    }

    async status(parameters, session) {
        return await Promise.resolve({
            "mediaSessionId": "sess1",
            "state": "IDLE"
        })
    }

    async progress(parameters, session) {
        return await Promise.resolve({
            "speed": 1,
            "startPosition": 0,
            "position": 5000,
            "endPosition": 3600000,
            "liveSyncTime": "2021-04-23T18:25:43.511Z"
        })
    }

}

Player.provide('xrn:firebolt:capability:player:base', new MyBasePlayerProvider())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Player.onRequestLoad",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Player.onRequestPlay",
    "params": {
        "listen": true
    }
}

{
    "id": 3,
    "method": "Player.onRequestStop",
    "params": {
        "listen": true
    }
}

{
    "id": 4,
    "method": "Player.onRequestStatus",
    "params": {
        "listen": true
    }
}

{
    "id": 5,
    "method": "Player.onRequestProgress",
    "params": {
        "listen": true
    }
}

```

Response:

```json

{
    "id": 1,
    "result": {
        "listening": true,
        "event": "Player.onRequestLoad"
    }            
 
}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Player.onRequestPlay"
    }            
 
}

{
    "id": 3,
    "result": {
        "listening": true,
        "event": "Player.onRequestStop"
    }            
 
}

{
    "id": 4,
    "result": {
        "listening": true,
        "event": "Player.onRequestStatus"
    }            
 
}

{
    "id": 5,
    "result": {
        "listening": true,
        "event": "Player.onRequestProgress"
    }            
 
}

```



**Asynchronous event to initiate load()**

Event Response:

```json
{
    "id": 1,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "app1:123",
            "locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 6,
    "method": "Player.loadResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "mediaSessionId": "sess1"
        }
    }
}
```

Response:

```json
{
    "id": 6,
    "result": true
}
```



**Asynchronous event to initiate play()**

Event Response:

```json
{
    "id": 2,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "app1:123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 7,
    "method": "Player.playResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "mediaSessionId": "sess1"
        }
    }
}
```

Response:

```json
{
    "id": 7,
    "result": true
}
```



**Asynchronous event to initiate stop()**

Event Response:

```json
{
    "id": 3,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "app1:123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 8,
    "method": "Player.stopResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "mediaSessionId": "sess1"
        }
    }
}
```

Response:

```json
{
    "id": 8,
    "result": true
}
```



**Asynchronous event to initiate status()**

Event Response:

```json
{
    "id": 4,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 9,
    "method": "Player.statusResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "mediaSessionId": "sess1",
            "state": "IDLE"
        }
    }
}
```

Response:

```json
{
    "id": 9,
    "result": true
}
```



**Asynchronous event to initiate progress()**

Event Response:

```json
{
    "id": 5,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 10,
    "method": "Player.progressResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "speed": 1,
            "startPosition": 0,
            "position": 5000,
            "endPosition": 3600000,
            "liveSyncTime": "2021-04-23T18:25:43.511Z"
        }
    }
}
```

Response:

```json
{
    "id": 10,
    "result": true
}
```




</details>



## Types

### PlayerLoadRequest



```typescript
type PlayerLoadRequest = {
  playerId: string          // The id of the player instance to load the locator into
  locator: string           // A locator to the content to load
  metadata?: {
  }
  autoPlay?: boolean        // Start playing immediately on load without needing to call Player.play
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
### PlayerLoadProviderRequest



```typescript
type PlayerLoadProviderRequest = {
  correlationId: string             // An id to correlate the provider response with this request
  parameters: PlayerLoadRequest
}
```

See also: 

[PlayerLoadRequest](#playerloadrequest)

---