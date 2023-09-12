---
title: BroadcastPlayer

version: pr177
layout: default
sdk: manage
---

# BroadcastPlayer Module
---
Version BroadcastPlayer 0.17.1-proposed.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [create](#create)
     - [createError](#createerror)
     - [createResponse](#createresponse)
     - [listen](#listen)
     - [once](#once)
     - [provide](#provide)
     - [provideStatus](#providestatus)
     - [status](#status)
     - [statusError](#statuserror)
     - [statusResponse](#statusresponse)
   - [Events](#events)
     - [onRequestCreate](#onrequestcreate)
     - [onRequestStatus](#onrequeststatus)
     - [statusChanged](#statuschanged)
   - [Provider Interfaces](#provider-interfaces)
     - [BroadcastPlayerProvider](#broadcastplayerprovider)
   - [Types](#types)
     - [BroadcastPlayerCreateRequest](#broadcastplayercreaterequest)
     - [BroadcastPlayerInstance](#broadcastplayerinstance)
     - [BroadcastPlayerStatus](#broadcastplayerstatus)
     - [BroadcastPlayerCreateProviderRequest](#broadcastplayercreateproviderrequest)



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
function create(request: BroadcastPlayerCreateRequest): Promise<BroadcastPlayerInstance>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `request` | [`BroadcastPlayerCreateRequest`](#broadcastplayercreaterequest) | true | The create request  |


Promise resolution:

[BroadcastPlayerInstance](#broadcastplayerinstance)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:broadcast |


#### Examples


Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

BroadcastPlayer.create({})
    .then(playerInstance => {
        console.log(playerInstance)
    })
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

### createError

*This is an private RPC method.*

Internal API for Create Provider to send back error.

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

### createResponse

*This is an private RPC method.*

Internal API for Create Provider to send back response.

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
		"response": {
			"correlationId": "123",
			"result": {
				"playerId": "123",
				"windowId": "456"
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
	"method": "BroadcastPlayer.createResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"playerId": "abc",
				"windowId": "def"
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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `BroadcastPlayer.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

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
, | `status` | [`BroadcastPlayerStatus`](#broadcastplayerstatus) | true | The status  |


Promise resolution:

```typescript
void
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:broadcast |


#### Examples


Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

BroadcastPlayer.provideStatus("123",
                              {
                                "locked": false,
                                "frequency": 695000000,
                                "signalStrength": 90,
                                "signalQuality": 90
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

### status
Gets the latest broadcast status for the given player

To get the value of `status` call the method like this:

```typescript
function status(playerId: string): Promise<BroadcastPlayerStatus>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `playerId` | `string` | true | The id of the player to get the status for  |


Promise resolution:

[BroadcastPlayerStatus](#broadcastplayerstatus)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:broadcast |


#### Examples


Default example #1

JavaScript:

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

BroadcastPlayer.status("app1:123")
    .then(playerStatus => {
        console.log(playerStatus)
    })
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

BroadcastPlayer.status("app2:456")
    .then(playerStatus => {
        console.log(playerStatus)
    })
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
function status(playerId: string, callback: (value) => BroadcastPlayerStatus): Promise<number>
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
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

status(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

status(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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
		"response": {
			"correlationId": "123",
			"result": {
				"locked": false,
				"frequency": 1,
				"signalStrength": 90,
				"signalQuality": 90
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

### statusChanged

See: [status](#status)


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
| `locked` | boolean | Whether the current media has been locked | 
| `frequency` | number | The signal frequency in hertz | 
| `signalStrength` | number | The strength of the signal from 0-100 | 
| `signalQuality` | number | The quality of the signal from 0-100 | 



#### Examples

**Register your app to provide the `xrn:firebolt:capability:player:broadcast` capability.**

```javascript
import { BroadcastPlayer } from '@firebolt-js/manage-sdk'

class MyBroadcastPlayerProvider {

    async create(parameters, session) {
        return await Promise.resolve({
            "playerId": "123",
            "windowId": "456"
        })
    }

    async status(parameters, session) {
        return await Promise.resolve({
            "locked": false,
            "frequency": 695000000,
            "signalStrength": 90,
            "signalQuality": 90
        })
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

### BroadcastPlayerCreateRequest



```typescript
type BroadcastPlayerCreateRequest = {
}
```



---
### BroadcastPlayerInstance



```typescript
type BroadcastPlayerInstance = {
  playerId: string                // The id of player which can be used to load media or control the player
  windowId: string                // The id of window which will render the media in, can be used to control on screen where the media is shown
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