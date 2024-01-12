---
title: BroadcastPlayer

version: pr-player-apis-3
layout: default
sdk: provider
---

# BroadcastPlayer Module
---
Version BroadcastPlayer 1.0.1-player-apis-3.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [createError](#createerror)
     - [createResponse](#createresponse)
     - [provide](#provide)
     - [provideStatus](#providestatus)
     - [statusError](#statuserror)
     - [statusResponse](#statusresponse)
   - [Events](#events)
     - [onRequestCreate](#onrequestcreate)
     - [onRequestStatus](#onrequeststatus)
   - [Provider Interfaces](#provider-interfaces)
     - [BroadcastPlayerProvider](#broadcastplayerprovider)
   - [Types](#types)
     - [BroadcastPlayerInstance](#broadcastplayerinstance)
     - [BroadcastPlayerCreateRequest](#broadcastplayercreaterequest)
     - [BroadcastPlayerStatus](#broadcastplayerstatus)
     - [BroadcastPlayerCreateProviderRequest](#broadcastplayercreateproviderrequest)



## Usage
To use the BroadcastPlayer module, you can import it into your project from the Firebolt SDK:

```javascript
import { BroadcastPlayer } from '@firebolt-js/provider-sdk'
```


## Overview
 A module for controlling and accessing media over broadcast

## Methods

### createError

*This is an private RPC method.*

Internal API for Create Provider to send back error.

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
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.createError",
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

### createResponse

*This is an private RPC method.*

Internal API for Create Provider to send back response.

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `correlationId` | `string` | true |   |
| `result` | [`BroadcastPlayerInstance`](#broadcastplayerinstance) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.createResponse",
	"params": {
		"correlationId": "123",
		"result": {
			"playerId": "123",
			"windowId": "456"
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
	"method": "BroadcastPlayer.createResponse",
	"params": {
		"correlationId": "123",
		"result": {
			"playerId": "abc",
			"windowId": "def"
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

### provideStatus

Tells listeners the current broadcast status of a player

```typescript
function provideStatus(playerId: string, status: BroadcastPlayerStatus): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player the status is for  |
| `status` | [`BroadcastPlayerStatus`](#broadcastplayerstatus) | true | The status  |


Promise resolution:

```typescript
void
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/provider-sdk'

let providedResponse = await BroadcastPlayer.provideStatus("123",
                              {
                                "locked": false,
                                "frequency": 695000000,
                                "signalStrength": 90,
                                "signalQuality": 90
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
	"method": "BroadcastPlayer.provideStatus",
	"params": {
		"playerId": "123",
		"status": {
			"locked": false,
			"frequency": 695000000,
			"signalStrength": 90,
			"signalQuality": 90
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
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.statusError",
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
| `result` | [`BroadcastPlayerStatus`](#broadcastplayerstatus) | true |   |


Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.statusResponse",
	"params": {
		"correlationId": "123",
		"result": {
			"locked": false,
			"frequency": 1,
			"signalStrength": 90,
			"signalQuality": 90
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

### onRequestCreate

*This is an private RPC method.*

Registers as a provider for creating player instances

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[BroadcastPlayerCreateProviderRequest](#broadcastplayercreateproviderrequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.onRequestCreate",
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
		"parameters": {}
	}
}
```



---

### onRequestStatus

*This is an private RPC method.*

Registers as a provider for when broadcast player status needs to be provided

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PlayerProviderRequest](../Player/schemas/#PlayerProviderRequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:broadcast |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "BroadcastPlayer.onRequestStatus",
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

### BroadcastPlayerProvider
The provider interface for the `xrn:firebolt:capability:player:broadcast` capability.

```typescript

```

Usage:

```typescript
BroadcastPlayer.provide('xrn:firebolt:capability:player:broadcast', provider: BroadcastPlayerProvider | object)
```

#### create

Registers as a provider for creating player instances

```typescript
function create(parameters?: BroadcastPlayerCreateRequest, session?: ProviderSession): Promise<BroadcastPlayerInstance>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`BroadcastPlayerCreateRequest`](#broadcastplayercreaterequest) | false |   |
| `session` | `ProviderSession` | false |   |




Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `playerId` | string | The id of player which can be used to load media or control the player | 
| `windowId` | string | The id of window which will render the media in, can be used to control on screen where the media is shown | 

#### status

Registers as a provider for when broadcast player status needs to be provided

```typescript
function status(parameters?: PlayerRequest, session?: ProviderSession): Promise<BroadcastPlayerStatus>
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
| `locked` | boolean | Whether the current media has been locked | 
| `frequency` | number | The signal frequency in hertz | 
| `signalStrength` | number | The strength of the signal from 0-100 | 
| `signalQuality` | number | The quality of the signal from 0-100 | 



#### Examples

**Register your app to provide the `xrn:firebolt:capability:player:broadcast` capability.**

```javascript
import { BroadcastPlayer } from '@firebolt-js/provider-sdk'

class MyBroadcastPlayerProvider {

    async create(parameters, session) {
        return {
            "playerId": "123",
            "windowId": "456"
        }
    }

    async status(parameters, session) {
        return {
            "locked": false,
            "frequency": 695000000,
            "signalStrength": 90,
            "signalQuality": 90
        }
    }

}

BroadcastPlayer.provide('xrn:firebolt:capability:player:broadcast', new MyBroadcastPlayerProvider())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "BroadcastPlayer.onRequestCreate",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "BroadcastPlayer.onRequestStatus",
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
        "event": "BroadcastPlayer.onRequestCreate"
    }            
 
}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "BroadcastPlayer.onRequestStatus"
    }            
 
}

```



**Asynchronous event to initiate create()**

Event Response:

```json
{
    "id": 1,
    "result": {
        "correlationId": "abc",
        "parameters": {}
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 3,
    "method": "BroadcastPlayer.createResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "playerId": "123",
            "windowId": "456"
        }
    }
}
```

Response:

```json
{
    "id": 3,
    "result": true
}
```



**Asynchronous event to initiate status()**

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
    "id": 4,
    "method": "BroadcastPlayer.statusResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "locked": false,
            "frequency": 695000000,
            "signalStrength": 90,
            "signalQuality": 90
        }
    }
}
```

Response:

```json
{
    "id": 4,
    "result": true
}
```




</details>



## Types

### BroadcastPlayerInstance



```typescript
type BroadcastPlayerInstance = {
  playerId: string                // The id of player which can be used to load media or control the player
  windowId: string                // The id of window which will render the media in, can be used to control on screen where the media is shown
}
```



---
### BroadcastPlayerCreateRequest



```typescript
type BroadcastPlayerCreateRequest = {
}
```



---
### BroadcastPlayerStatus



```typescript
type BroadcastPlayerStatus = {
  locked: boolean               // Whether the current media has been locked
  frequency: number             // The signal frequency in hertz
  signalStrength: number        // The strength of the signal from 0-100
  signalQuality: number         // The quality of the signal from 0-100
}
```



---
### BroadcastPlayerCreateProviderRequest



```typescript
type BroadcastPlayerCreateProviderRequest = {
  correlationId: string                        // An id to correlate the provider response with this request
  parameters: BroadcastPlayerCreateRequest
}
```

See also: 

[BroadcastPlayerCreateRequest](#broadcastplayercreaterequest)

---