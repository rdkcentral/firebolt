---
title: PinChallenge

version: 0.12.0
layout: default
sdk: manage
---

# PinChallenge Module
---
Version PinChallenge 0.12.0

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [challengeError](#challengeerror)
     - [challengeFocus](#challengefocus)
     - [challengeResponse](#challengeresponse)
     - [provide](#provide)
   - [Events](#events)
     - [onRequestChallenge](#onrequestchallenge)
   - [Provider Interfaces](#provider-interfaces)
     - [ChallengeProvider](#challengeprovider)
   - [Types](#types)
     - [PinChallengeResult](#pinchallengeresult)
     - [PinChallengeProviderRequest](#pinchallengeproviderrequest)
     - [ResultReason](#resultreason)
     - [PinChallenge](#pinchallenge)
     - [ChallengeRequestor](#challengerequestor)



## Usage
To use the PinChallenge module, you can import it into your project from the Firebolt SDK:

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'
```


## Overview
 A module for registering as a provider for a user grant in which the user is prompted for a pin for access to a capability

## Methods

### challengeError

*This is an private RPC method.*

Internal API for Challenge Provider to send back error.

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
| provides | xrn:firebolt:capability:usergrant:pinchallenge |


#### Examples


Example 1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "PinChallenge.challengeError",
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

### challengeFocus

*This is an private RPC method.*

Internal API for Challenge Provider to request focus for UX purposes.



Result:

```typescript
null
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:usergrant:pinchallenge |


#### Examples


Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "PinChallenge.challengeFocus",
	"params": {}
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

### challengeResponse

*This is an private RPC method.*

Internal API for Challenge Provider to send back response.

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
| provides | xrn:firebolt:capability:usergrant:pinchallenge |


#### Examples


Example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "PinChallenge.challengeResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"granted": true,
				"reason": "correctPin"
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
	"method": "PinChallenge.challengeResponse",
	"params": {
		"response": {
			"correlationId": "123",
			"result": {
				"granted": false,
				"reason": "cancelled"
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

### onRequestChallenge

*This is an private RPC method.*

Registers as a provider for when the user should be challenged in order to confirm access to a capability through a pin prompt

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `listen` | `boolean` | true |   |


Result:

[PinChallengeProviderRequest](#pinchallengeproviderrequest)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| provides | xrn:firebolt:capability:usergrant:pinchallenge |


#### Examples


Default Example

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "PinChallenge.onRequestChallenge",
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
			"capability": "xrn:firebolt:capability:commerce::purchase",
			"requestor": {
				"id": "ReferenceApp",
				"name": "Firebolt Reference App"
			},
			"pinSpace": "purchase"
		}
	}
}
```



---


## Provider Interfaces

### ChallengeProvider
The provider interface for the `xrn:firebolt:capability:usergrant:pinchallenge` capability.

```typescript

```

Usage:

```typescript
PinChallenge.provide('xrn:firebolt:capability:usergrant:pinchallenge', provider: ChallengeProvider | object)
```

#### challenge

Registers as a provider for when the user should be challenged in order to confirm access to a capability through a pin prompt

```typescript
function challenge(parameters?: PinChallenge, session?: FocusableProviderSession): Promise<PinChallengeResult>
```

Provider methods always have two arguments:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `parameters` | `PinChallenge` | false |   |
| `session` | `FocusableProviderSession` | false |   |


${if.provider.params}

| Parameters Property    | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `pinSpace` | `'purchase' | 'content'` | true | The pin space that this challenge is for <br/>values: `'purchase' \| 'content'` |
| `capability` | `string` | false | The capability that is gated by a pin challenge  |
| `requestor` | [`ChallengeRequestor`](#challengerequestor) | true |   |


```typescript
type PinChallenge = object
```

${end.if.provider.params}

Promise resolution:

| Property | Type | Description |
|----------|------|-------------|
| `granted` | boolean | Whether the user succeeded in the pin challenge | 
| `reason` | 'noPinRequired' | 'noPinRequiredWindow' | 'exceededPinFailures' | 'correctPin' | 'cancelled' | The reason for the result of challenging the user | 



#### Examples

**Register your app to provide the `xrn:firebolt:capability:usergrant:pinchallenge` capability.**

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'

class MyChallengeProvider {

    async challenge(parameters, session) {
        return await Promise.resolve({
            "granted": true,
            "reason": "correctPin"
        })
    }

}

PinChallenge.provide('xrn:firebolt:capability:usergrant:pinchallenge', new MyChallengeProvider())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "PinChallenge.onRequestChallenge",
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
        "event": "PinChallenge.onRequestChallenge"
    }            
 
}

```



**Asynchronous event to initiate challenge()**

Event Response:

```json
{
    "id": 1,
    "result": {
        "correlationId": "abc",
        "parameters": {
            "capability": "xrn:firebolt:capability:commerce::purchase",
            "requestor": {
                "id": "ReferenceApp",
                "name": "Firebolt Reference App"
            },
            "pinSpace": "purchase"
        }
    }
}
```

**App initiated response to event**

Request:

```json
{
    "id": 2,
    "method": "PinChallenge.challengeResponse",
    "params": {
        "correlationId": "abc",
        "result": {
            "granted": true,
            "reason": "correctPin"
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

### PinChallengeResult



```typescript
type PinChallengeResult = {
  granted: boolean           // Whether the user succeeded in the pin challenge
  reason: ResultReason       // The reason for the result of challenging the user
}
```

See also: 

'noPinRequired' | 'noPinRequiredWindow' | 'exceededPinFailures' | 'correctPin' | 'cancelled'

---

### PinChallengeProviderRequest



```typescript
type PinChallengeProviderRequest = {
  parameters: PinChallenge
  correlationId: string               // The id that was passed in to the event that triggered a provider method to be called
}
```

See also: 

[ProviderRequest](../Types/schemas/#ProviderRequest)
[PinChallenge](#pinchallenge-1)

---

### ResultReason

The reason for the result of challenging the user

```typescript
enum ResultReason {
	NO_PIN_REQUIRED = 'noPinRequired',
	NO_PIN_REQUIRED_WINDOW = 'noPinRequiredWindow',
	EXCEEDED_PIN_FAILURES = 'exceededPinFailures',
	CORRECT_PIN = 'correctPin',
	CANCELLED = 'cancelled'
}

```



---

### PinChallenge



```typescript
type PinChallenge = {
  pinSpace: 'purchase' | 'content'  // The pin space that this challenge is for
  capability?: string               // The capability that is gated by a pin challenge
  requestor: ChallengeRequestor
}
```

See also: 

[ChallengeRequestor](#challengerequestor)

---

### ChallengeRequestor



```typescript
type ChallengeRequestor = {
  id: string                 // The id of the app that requested the challenge
  name: string               // The name of the app that requested the challenge
}
```



---