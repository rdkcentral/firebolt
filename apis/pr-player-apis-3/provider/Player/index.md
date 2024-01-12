---
title: Player

version: pr-player-apis-3
layout: default
sdk: provider
---

# Player Module
---
Version Player 1.0.1-player-apis-3.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [loadError](#loaderror)
     - [loadResponse](#loadresponse)
     - [playError](#playerror)
     - [playResponse](#playresponse)
     - [progressError](#progresserror)
     - [progressResponse](#progressresponse)
     - [provide](#provide)
     - [provideProgress](#provideprogress)
     - [provideStatus](#providestatus)
     - [setAudioTrackError](#setaudiotrackerror)
     - [setAudioTrackResponse](#setaudiotrackresponse)
     - [setCaptionsTrackError](#setcaptionstrackerror)
     - [setCaptionsTrackResponse](#setcaptionstrackresponse)
     - [setPositionError](#setpositionerror)
     - [setPositionResponse](#setpositionresponse)
     - [setSpeedError](#setspeederror)
     - [setSpeedResponse](#setspeedresponse)
     - [statusError](#statuserror)
     - [statusResponse](#statusresponse)
     - [stopError](#stoperror)
     - [stopResponse](#stopresponse)
     - [tracksError](#trackserror)
     - [tracksResponse](#tracksresponse)
   - [Events](#events)
     - [onRequestLoad](#onrequestload)
     - [onRequestPlay](#onrequestplay)
     - [onRequestProgress](#onrequestprogress)
     - [onRequestSetAudioTrack](#onrequestsetaudiotrack)
     - [onRequestSetCaptionsTrack](#onrequestsetcaptionstrack)
     - [onRequestSetPosition](#onrequestsetposition)
     - [onRequestSetSpeed](#onrequestsetspeed)
     - [onRequestStatus](#onrequeststatus)
     - [onRequestStop](#onrequeststop)
     - [onRequestTracks](#onrequesttracks)
   - [Provider Interfaces](#provider-interfaces)
     - [BasePlayerProvider](#baseplayerprovider)
   - [Types](#types)
     - [PlayerMediaSession](#playermediasession)
     - [LoadRequest](#loadrequest)
     - [PlayerStatus](#playerstatus)
     - [PlayerProgress](#playerprogress)
     - [PlayerSetPositionRequest](#playersetpositionrequest)
     - [PlayerSetSpeedRequest](#playersetspeedrequest)
     - [AudioTrack](#audiotrack)
     - [PlayerSetAudioTrackRequest](#playersetaudiotrackrequest)
     - [PlayerSetCaptionsTrackRequest](#playersetcaptionstrackrequest)
     - [PlayerLoadRequest](#playerloadrequest)
     - [PlayerSetPositionProviderRequest](#playersetpositionproviderrequest)
     - [PlayerSetSpeedProviderRequest](#playersetspeedproviderrequest)
     - [CaptionsTrack](#captionstrack)
     - [PlayerTracks](#playertracks)
     - [PlayerSetAudioTrackProviderRequest](#playersetaudiotrackproviderrequest)
     - [PlayerSetCaptionsTrackProviderRequest](#playersetcaptionstrackproviderrequest)
     - [PlayerLoadProviderRequest](#playerloadproviderrequest)



## Usage
To use the Player module, you can import it into your project from the Firebolt SDK:

```javascript
import { Player } from '@firebolt-js/provider-sdk'
```


## Overview
 A module for providing and using media player capabilities. This handles operations that would be associated with any player generically

## Methods

### loadError

*This is an private RPC method.*

Internal API for Load Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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
| `correlationId` | `string` | true |   |
| `result` | [`PlayerMediaSession`](#playermediasession) | true |   |


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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess1"
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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess2"
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

### playError

*This is an private RPC method.*

Internal API for Play Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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
| `correlationId` | `string` | true |   |
| `result` | [`PlayerMediaSession`](#playermediasession) | true |   |


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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess1"
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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess2"
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

### progressError

*This is an private RPC method.*

Internal API for Progress Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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
| `correlationId` | `string` | true |   |
| `result` | [`PlayerProgress`](#playerprogress) | true |   |


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
| `progress` | [`PlayerProgress`](#playerprogress) | true | The progress  |


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
import { Player } from '@firebolt-js/provider-sdk'

let providedResponse = await Player.provideProgress("123",
                       {
                         "speed": 1,
                         "startPosition": 0,
                         "position": 5000,
                         "endPosition": 3600000,
                         "liveSyncTime": "2021-04-23T18:25:43.511Z"
                       })
console.log(providedResponse)
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
| `status` | [`PlayerStatus`](#playerstatus) | true | The status  |


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
import { Player } from '@firebolt-js/provider-sdk'

let providedResponse = await Player.provideStatus("123",
                     {
                       "mediaSessionId": "sess2",
                       "state": "BLOCKED",
                       "blockedReason": "CONTENT_NOT_FOUND"
                     })
console.log(providedResponse)
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

### setAudioTrackError

*This is an private RPC method.*

Internal API for SetAudioTrack Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
	"method": "Player.setAudioTrackError",
	"params": {
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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

### setAudioTrackResponse

*This is an private RPC method.*

Internal API for SetAudioTrack Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | `void` | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.setAudioTrackResponse",
	"params": {
		"correlationId": "123",
		"result": null
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

### setCaptionsTrackError

*This is an private RPC method.*

Internal API for SetCaptionsTrack Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
	"method": "Player.setCaptionsTrackError",
	"params": {
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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

### setCaptionsTrackResponse

*This is an private RPC method.*

Internal API for SetCaptionsTrack Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | `void` | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.setCaptionsTrackResponse",
	"params": {
		"correlationId": "123",
		"result": null
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

### setPositionError

*This is an private RPC method.*

Internal API for SetPosition Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
	"method": "Player.setPositionError",
	"params": {
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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

### setPositionResponse

*This is an private RPC method.*

Internal API for SetPosition Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | `void` | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.setPositionResponse",
	"params": {
		"correlationId": "123",
		"result": null
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

### setSpeedError

*This is an private RPC method.*

Internal API for SetSpeed Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
	"method": "Player.setSpeedError",
	"params": {
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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

### setSpeedResponse

*This is an private RPC method.*

Internal API for SetSpeed Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | `void` | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.setSpeedResponse",
	"params": {
		"correlationId": "123",
		"result": null
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

### statusError

*This is an private RPC method.*

Internal API for Status Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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
| `correlationId` | `string` | true |   |
| `result` | [`PlayerStatus`](#playerstatus) | true |   |


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
		"correlationId": "123",
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
		"correlationId": "123",
		"result": {
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



---

### stopError

*This is an private RPC method.*

Internal API for Stop Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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
| `correlationId` | `string` | true |   |
| `result` | [`PlayerMediaSession`](#playermediasession) | true |   |


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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess1"
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
		"correlationId": "123",
		"result": {
			"mediaSessionId": "sess2"
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

### tracksError

*This is an private RPC method.*

Internal API for Tracks Provider to send back error.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `error` | `object` | true |   |


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
	"method": "Player.tracksError",
	"params": {
		"correlationId": "123",
		"error": {
			"code": 1,
			"message": "Error"
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

### tracksResponse

*This is an private RPC method.*

Internal API for Tracks Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | [`PlayerTracks`](#playertracks) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.tracksResponse",
	"params": {
		"correlationId": "123",
		"result": {
			"audio": [
				{
					"trackId": "Audio1",
					"language": "en",
					"audioDescription": false,
					"type": "PCM",
					"selected": true
				},
				{
					"trackId": "Audio2",
					"language": "es",
					"audioDescription": true,
					"type": "AC3",
					"selected": false
				}
			],
			"captions": [
				{
					"trackId": "CC1",
					"language": "en",
					"selected": true
				},
				{
					"trackId": "CC2",
					"name": "ClosedCaptions2",
					"selected": false
				}
			]
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
			"playerId": "123",
			"request": {
				"locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
			}
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
			"playerId": "123"
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

### onRequestSetAudioTrack

*This is an private RPC method.*

Registers as a provider for setting the audio track

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerSetAudioTrackProviderRequest](#playersetaudiotrackproviderrequest)

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
	"method": "Player.onRequestSetAudioTrack",
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
			"playerId": "123",
			"trackId": "Audio1"
		}
	}
}
```



---

### onRequestSetCaptionsTrack

*This is an private RPC method.*

Registers as a provider for setting the captions track

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerSetCaptionsTrackProviderRequest](#playersetcaptionstrackproviderrequest)

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
	"method": "Player.onRequestSetCaptionsTrack",
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
			"playerId": "123",
			"trackId": "CC1"
		}
	}
}
```



---

### onRequestSetPosition

*This is an private RPC method.*

Registers as a provider for when media position should be set

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerSetPositionProviderRequest](#playersetpositionproviderrequest)

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
	"method": "Player.onRequestSetPosition",
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
			"playerId": "123",
			"position": 10000
		}
	}
}
```



---

### onRequestSetSpeed

*This is an private RPC method.*

Registers as a provider for when media speed should be set

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerSetSpeedProviderRequest](#playersetspeedproviderrequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:base |


#### Examples


Set Speed to 2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestSetSpeed",
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
			"playerId": "123",
			"speed": 2
		}
	}
}
```


Set Speed to 0.5

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestSetSpeed",
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
			"playerId": "123",
			"speed": 0.5
		}
	}
}
```


Set Speed to -2

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestSetSpeed",
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
			"playerId": "123",
			"speed": -2
		}
	}
}
```


Set Speed to 0

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Player.onRequestSetSpeed",
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
			"playerId": "123",
			"speed": 0
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
			"playerId": "123"
		}
	}
}
```



---

### onRequestTracks

*This is an private RPC method.*

Registers as a provider for when player tracks needs to be provided

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
	"method": "Player.onRequestTracks",
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




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to load the locator into  |
| `request` | [`LoadRequest`](#loadrequest) | true |   |


```typescript
type PlayerLoadRequest = {
  playerId: string          // The id of the player instance to load the locator into
  request: LoadRequest
}
```



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




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```



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




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```



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




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```



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




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```



Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `speed` | number | The playback speed as a multiplier | 
| `startPosition` | number | The position that the media starts at in milliseconds | 
| `position` | number | The current position in milliseconds | 
| `endPosition` | number | The position that the media stops at in milliseconds | 
| `liveSyncTime` | string | The time to sync to live | 

#### setPosition

Registers as a provider for when media position should be set

```typescript
function setPosition(parameters?: PlayerSetPositionRequest, session?: ProviderSession): Promise<void>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerSetPositionRequest`](#playersetpositionrequest) | false |   |
| `session` | `ProviderSession` | false |   |




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to set the position for  |
| `position` | `number` | true | The position the player should seek to in milliseconds <br/>minumum: 0 |


```typescript
type PlayerSetPositionRequest = {
  playerId: string                 // The id of the player to set the position for
  position: number                 // The position the player should seek to in milliseconds
}
```



Promise resolution:

```typescript
void
```
#### setSpeed

Registers as a provider for when media speed should be set

```typescript
function setSpeed(parameters?: PlayerSetSpeedRequest, session?: ProviderSession): Promise<void>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerSetSpeedRequest`](#playersetspeedrequest) | false |   |
| `session` | `ProviderSession` | false |   |




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to set the speed for  |
| `speed` | `number` | true | The speed to set as a multiplier of the default speed. Negative values would cause the media to rewind. Use 0 to pause  |


```typescript
type PlayerSetSpeedRequest = {
  playerId: string              // The id of the player to set the speed for
  speed: number                 // The speed to set as a multiplier of the default speed. Negative values would cause the media to rewind. Use 0 to pause
}
```



Promise resolution:

```typescript
void
```
#### tracks

Registers as a provider for when player tracks needs to be provided

```typescript
function tracks(parameters?: PlayerRequest, session?: ProviderSession): Promise<PlayerTracks>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerRequest`](../Player/schemas/#PlayerRequest) | false |   |
| `session` | `ProviderSession` | false |   |




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player instance to play in  |


```typescript
type PlayerRequest = {
  playerId: string      // The id of the player instance to play in
}
```



Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `audio` | AudioTrack[] | The list of audio tracks | 
| `captions` | CaptionsTrack[] | The list of captions tracks | 

#### setAudioTrack

Registers as a provider for setting the audio track

```typescript
function setAudioTrack(parameters?: PlayerSetAudioTrackRequest, session?: ProviderSession): Promise<void>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerSetAudioTrackRequest`](#playersetaudiotrackrequest) | false |   |
| `session` | `ProviderSession` | false |   |




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to set the track for  |
| `trackId` | `string` | true | The id of the track to use for audio  |


```typescript
type PlayerSetAudioTrackRequest = {
  playerId: string                   // The id of the player to set the track for
  trackId: string                    // The id of the track to use for audio
}
```



Promise resolution:

```typescript
void
```
#### setCaptionsTrack

Registers as a provider for setting the captions track

```typescript
function setCaptionsTrack(parameters?: PlayerSetCaptionsTrackRequest, session?: ProviderSession): Promise<void>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`PlayerSetCaptionsTrackRequest`](#playersetcaptionstrackrequest) | false |   |
| `session` | `ProviderSession` | false |   |




| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to set the track for  |
| `trackId` | `string` | false | The id of the track to use for captions. Leave off to turn off captions  |


```typescript
type PlayerSetCaptionsTrackRequest = {
  playerId: string                      // The id of the player to set the track for
  trackId?: string                      // The id of the track to use for captions. Leave off to turn off captions
}
```



Promise resolution:

```typescript
void
```


#### Examples

**Register your app to provide the `xrn:firebolt:capability:player:base` capability.**

```javascript
import { Player } from '@firebolt-js/provider-sdk'

class MyBasePlayerProvider {

    async load(parameters, session) {
        return {
            "mediaSessionId": "sess1"
        }
    }

    async play(parameters, session) {
        return {
            "mediaSessionId": "sess1"
        }
    }

    async stop(parameters, session) {
        return {
            "mediaSessionId": "sess1"
        }
    }

    async status(parameters, session) {
        return {
            "mediaSessionId": "sess1",
            "state": "IDLE"
        }
    }

    async progress(parameters, session) {
        return {
            "speed": 1,
            "startPosition": 0,
            "position": 5000,
            "endPosition": 3600000,
            "liveSyncTime": "2021-04-23T18:25:43.511Z"
        }
    }

    async setPosition(parameters, session) {
        return null
    }

    async setSpeed(parameters, session) {
        return null
    }

    async tracks(parameters, session) {
        return {
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

    async setAudioTrack(parameters, session) {
        return null
    }

    async setCaptionsTrack(parameters, session) {
        return null
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

{
    "id": 6,
    "method": "Player.onRequestSetPosition",
    "params": {
        "listen": true
    }
}

{
    "id": 7,
    "method": "Player.onRequestSetSpeed",
    "params": {
        "listen": true
    }
}

{
    "id": 8,
    "method": "Player.onRequestTracks",
    "params": {
        "listen": true
    }
}

{
    "id": 9,
    "method": "Player.onRequestSetAudioTrack",
    "params": {
        "listen": true
    }
}

{
    "id": 10,
    "method": "Player.onRequestSetCaptionsTrack",
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

{
    "id": 6,
    "result": {
        "listening": true,
        "event": "Player.onRequestSetPosition"
    }            
 
}

{
    "id": 7,
    "result": {
        "listening": true,
        "event": "Player.onRequestSetSpeed"
    }            
 
}

{
    "id": 8,
    "result": {
        "listening": true,
        "event": "Player.onRequestTracks"
    }            
 
}

{
    "id": 9,
    "result": {
        "listening": true,
        "event": "Player.onRequestSetAudioTrack"
    }            
 
}

{
    "id": 10,
    "result": {
        "listening": true,
        "event": "Player.onRequestSetCaptionsTrack"
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
            "playerId": "123",
            "request": {
                "locator": "https://cdn.rdkcentral.com/media/assets/asset.hls"
            }
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 11,
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
    "id": 11,
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
            "playerId": "123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 12,
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
    "id": 12,
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
            "playerId": "123"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 13,
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
    "id": 13,
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
    "id": 14,
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
    "id": 14,
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
    "id": 15,
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
    "id": 15,
    "result": true
}
```



**Asynchronous event to initiate setPosition()**

Event Response:

```json
{
    "id": 6,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123",
            "position": 10000
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 16,
    "method": "Player.setPositionResponse",
    "params": {
        "correlationId": "abc",
        "result": null
    }
}
```

Response:

```json
{
    "id": 16,
    "result": true
}
```



**Asynchronous event to initiate setSpeed()**

Event Response:

```json
{
    "id": 7,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123",
            "speed": 2
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 17,
    "method": "Player.setSpeedResponse",
    "params": {
        "correlationId": "abc",
        "result": null
    }
}
```

Response:

```json
{
    "id": 17,
    "result": true
}
```



**Asynchronous event to initiate tracks()**

Event Response:

```json
{
    "id": 8,
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
    "id": 18,
    "method": "Player.tracksResponse",
    "params": {
        "correlationId": "abc",
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
}
```

Response:

```json
{
    "id": 18,
    "result": true
}
```



**Asynchronous event to initiate setAudioTrack()**

Event Response:

```json
{
    "id": 9,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123",
            "trackId": "Audio1"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 19,
    "method": "Player.setAudioTrackResponse",
    "params": {
        "correlationId": "abc",
        "result": null
    }
}
```

Response:

```json
{
    "id": 19,
    "result": true
}
```



**Asynchronous event to initiate setCaptionsTrack()**

Event Response:

```json
{
    "id": 10,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "playerId": "123",
            "trackId": "CC1"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 20,
    "method": "Player.setCaptionsTrackResponse",
    "params": {
        "correlationId": "abc",
        "result": null
    }
}
```

Response:

```json
{
    "id": 20,
    "result": true
}
```




</details>



## Types

### PlayerMediaSession



```typescript
type PlayerMediaSession = {
  mediaSessionId: string     // The id of media session that was started, when the content was loaded. This should be a new value on each load
}
```



---
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
### PlayerSetPositionRequest



```typescript
type PlayerSetPositionRequest = {
  playerId: string                 // The id of the player to set the position for
  position: number                 // The position the player should seek to in milliseconds
}
```



---
### PlayerSetSpeedRequest



```typescript
type PlayerSetSpeedRequest = {
  playerId: string              // The id of the player to set the speed for
  speed: number                 // The speed to set as a multiplier of the default speed. Negative values would cause the media to rewind. Use 0 to pause
}
```



---
### AudioTrack



```typescript
type AudioTrack = {
  trackId: string                       // The id of the track
  language: string
  audioDescription: boolean             // Whether this track supports audio description
  type: 'PCM' | 'AC3' | 'EAC3' | 'AAC'  // The type of track
  selected: boolean                     // Whether this track is currently selected
}
```



---
### PlayerSetAudioTrackRequest



```typescript
type PlayerSetAudioTrackRequest = {
  playerId: string                   // The id of the player to set the track for
  trackId: string                    // The id of the track to use for audio
}
```



---
### PlayerSetCaptionsTrackRequest



```typescript
type PlayerSetCaptionsTrackRequest = {
  playerId: string                      // The id of the player to set the track for
  trackId?: string                      // The id of the track to use for captions. Leave off to turn off captions
}
```



---
### PlayerLoadRequest



```typescript
type PlayerLoadRequest = {
  playerId: string          // The id of the player instance to load the locator into
  request: LoadRequest
}
```

See also: 

[LoadRequest](#loadrequest)

---
### PlayerSetPositionProviderRequest



```typescript
type PlayerSetPositionProviderRequest = {
  correlationId: string                    // An id to correlate the provider response with this request
  parameters: PlayerSetPositionRequest
}
```

See also: 

[PlayerSetPositionRequest](#playersetpositionrequest)

---
### PlayerSetSpeedProviderRequest



```typescript
type PlayerSetSpeedProviderRequest = {
  correlationId: string                 // An id to correlate the provider response with this request
  parameters: PlayerSetSpeedRequest
}
```

See also: 

[PlayerSetSpeedRequest](#playersetspeedrequest)

---
### CaptionsTrack



```typescript
type CaptionsTrack = {
  trackId: string       // The id of the track
  language?: string
  name?: string         // The name of track
  selected: boolean     // Whether this track is currently selected
}
```



---
### PlayerTracks



```typescript
type PlayerTracks = {
  audio: AudioTrack[]        // The list of audio tracks
  captions: CaptionsTrack[]  // The list of captions tracks
}
```

See also: 

[AudioTrack](#audiotrack)
[CaptionsTrack](#captionstrack)

---
### PlayerSetAudioTrackProviderRequest



```typescript
type PlayerSetAudioTrackProviderRequest = {
  correlationId: string                      // An id to correlate the provider response with this request
  parameters: PlayerSetAudioTrackRequest
}
```

See also: 

[PlayerSetAudioTrackRequest](#playersetaudiotrackrequest)

---
### PlayerSetCaptionsTrackProviderRequest



```typescript
type PlayerSetCaptionsTrackProviderRequest = {
  correlationId: string                         // An id to correlate the provider response with this request
  parameters: PlayerSetCaptionsTrackRequest
}
```

See also: 

[PlayerSetCaptionsTrackRequest](#playersetcaptionstrackrequest)

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