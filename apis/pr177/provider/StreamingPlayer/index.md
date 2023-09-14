---
title: StreamingPlayer

version: pr177
layout: default
sdk: provider
---

# StreamingPlayer Module
---
Version StreamingPlayer 0.17.1-proposed.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [createError](#createerror)
     - [createResponse](#createresponse)
     - [provide](#provide)
   - [Events](#events)
     - [onRequestCreate](#onrequestcreate)
   - [Provider Interfaces](#provider-interfaces)
     - [CreateProvider](#createprovider)
   - [Types](#types)
     - [StreamingPlayerInstance](#streamingplayerinstance)
     - [StreamingPlayerCreateRequest](#streamingplayercreaterequest)
     - [StreamingPlayerCreateProviderRequest](#streamingplayercreateproviderrequest)



## Usage
To use the StreamingPlayer module, you can import it into your project from the Firebolt SDK:

```javascript
import { StreamingPlayer } from '@firebolt-js/provider-sdk'
```


## Overview
 A module for controlling and accessing media over streaming

## Methods

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
| provides | xrn:firebolt:capability:player:streaming |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "StreamingPlayer.createError",
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
| provides | xrn:firebolt:capability:player:streaming |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "StreamingPlayer.createResponse",
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
	"method": "StreamingPlayer.createResponse",
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

## Events

### onRequestCreate

*This is an private RPC method.*

Registers as a provider for creating player instances

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[StreamingPlayerCreateProviderRequest](#streamingplayercreateproviderrequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:player:streaming |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "StreamingPlayer.onRequestCreate",
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


## Provider Interfaces

### CreateProvider
The provider interface for the `xrn:firebolt:capability:player:streaming` capability.

```typescript

```

Usage:

```typescript
StreamingPlayer.provide('xrn:firebolt:capability:player:streaming', provider: CreateProvider | object)
```

#### create

Registers as a provider for creating player instances

```typescript
function create(parameters?: StreamingPlayerCreateRequest, session?: ProviderSession): Promise<StreamingPlayerInstance>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | [`StreamingPlayerCreateRequest`](#streamingplayercreaterequest) | false |   |
| `session` | `ProviderSession` | false |   |




Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `playerId` | string | The id of player which can be used to load media or control the player | 
| `windowId` | string | The id of window which will render the media in, can be used to control on screen where the media is shown | 



#### Examples

**Register your app to provide the `xrn:firebolt:capability:player:streaming` capability.**

```javascript
import { StreamingPlayer } from '@firebolt-js/provider-sdk'

class MyCreateProvider {

    async create(parameters, session) {
        return await Promise.resolve({
            "playerId": "123",
            "windowId": "456"
        })
    }

}

StreamingPlayer.provide('xrn:firebolt:capability:player:streaming', new MyCreateProvider())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "StreamingPlayer.onRequestCreate",
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
        "event": "StreamingPlayer.onRequestCreate"
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
    "id": 2,
    "method": "StreamingPlayer.createResponse",
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
    "id": 2,
    "result": true
}
```




</details>



## Types

### StreamingPlayerInstance



```typescript
type StreamingPlayerInstance = {
  playerId: string                // The id of player which can be used to load media or control the player
  windowId: string                // The id of window which will render the media in, can be used to control on screen where the media is shown
}
```



---
### StreamingPlayerCreateRequest



```typescript
type StreamingPlayerCreateRequest = {
}
```



---
### StreamingPlayerCreateProviderRequest



```typescript
type StreamingPlayerCreateProviderRequest = {
  correlationId: string                        // An id to correlate the provider response with this request
  parameters: StreamingPlayerCreateRequest
}
```

See also: 

[StreamingPlayerCreateRequest](#streamingplayercreaterequest)

---