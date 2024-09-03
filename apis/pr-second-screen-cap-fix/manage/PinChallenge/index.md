---
title: PinChallenge

version: pr-second-screen-cap-fix
layout: default
sdk: manage
---

# PinChallenge Module

---

Version PinChallenge 1.4.0-second-screen-cap-fix.0

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
  - [ResultReason](#resultreason)
  - [ChallengeRequestor](#challengerequestor)
  - [PinChallengeResult](#pinchallengeresult)
  - [PinChallenge](#pinchallenge)
  - [PinChallengeProviderRequest](#pinchallengeproviderrequest)

## Usage

To use the PinChallenge module, you can import it into your project from the Firebolt SDK:

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'
```

## Overview

A module for registering as a provider for a user grant in which the user is prompted for a pin for access to a capability

## Methods

### challengeError

_This is an private RPC method._

Internal API for Challenge Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

Capabilities:

| Role     | Capability                                     |
| -------- | ---------------------------------------------- |
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

### challengeFocus

_This is an private RPC method._

Internal API for Challenge Provider to request focus for UX purposes.

Result:

Capabilities:

| Role     | Capability                                     |
| -------- | ---------------------------------------------- |
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

_This is an private RPC method._

Internal API for Challenge Provider to send back response.

Parameters:

| Param           | Type                                        | Required | Description |
| --------------- | ------------------------------------------- | -------- | ----------- |
| `correlationId` | `string`                                    | true     |             |
| `result`        | [`PinChallengeResult`](#pinchallengeresult) | true     |             |

Result:

Capabilities:

| Role     | Capability                                     |
| -------- | ---------------------------------------------- |
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
    "correlationId": "123",
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
    "correlationId": "123",
    "result": {
      "granted": false,
      "reason": "exceededPinFailures"
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

Example #3

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "PinChallenge.challengeResponse",
  "params": {
    "correlationId": "123",
    "result": {
      "granted": null,
      "reason": "cancelled"
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

| Param        | Type     | Required | Summary                                      |
| ------------ | -------- | -------- | -------------------------------------------- |
| `capability` | `string` | Yes      | The capability that is being provided.       |
| `provider`   | `any`    | Yes      | An implementation of the required interface. |

See [Provider Interfaces](#provider-interfaces) for each capabilities interface definition.

## Events

### onRequestChallenge

_This is an private RPC method._

Registers as a provider for when the user should be challenged in order to confirm access to a capability through a pin prompt

Parameters:

| Param    | Type      | Required | Description |
| -------- | --------- | -------- | ----------- |
| `listen` | `boolean` | true     |             |

Result:

[PinChallengeProviderRequest](#pinchallengeproviderrequest)

Capabilities:

| Role     | Capability                                     |
| -------- | ---------------------------------------------- |
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

#### Examples

**Register your app to provide the `xrn:firebolt:capability:usergrant:pinchallenge` capability.**

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'

class MyChallengeProvider {
  async challenge(parameters, session) {
    return {
      granted: true,
      reason: 'correctPin',
    }
  }
}

PinChallenge.provide(
  'xrn:firebolt:capability:usergrant:pinchallenge',
  new MyChallengeProvider(),
)
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
    "correlationId": undefined,
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
    "correlationId": undefined,
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

### ResultReason

The reason for the result of challenging the user

```typescript
ResultReason: {
    NO_PIN_REQUIRED: 'noPinRequired',
    NO_PIN_REQUIRED_WINDOW: 'noPinRequiredWindow',
    EXCEEDED_PIN_FAILURES: 'exceededPinFailures',
    CORRECT_PIN: 'correctPin',
    CANCELLED: 'cancelled',
},

```

---

### ChallengeRequestor

```typescript
type ChallengeRequestor = {
  id: string // The id of the app that requested the challenge
  name: string // The name of the app that requested the challenge
}
```

---

### PinChallengeResult

```typescript
type PinChallengeResult = {
  granted: boolean
  reason: ResultReason // The reason for the result of challenging the user
}
```

See also:

[ResultReason](#resultreason)

---

### PinChallenge

```typescript
type PinChallenge = {
  pinSpace: 'purchase' | 'content' // The pin space that this challenge is for
  capability?: string // The capability that is gated by a pin challenge
  requestor: ChallengeRequestor // The identity of which app is requesting access to this capability
}
```

See also:

[ChallengeRequestor](#challengerequestor)

---

### PinChallengeProviderRequest

```typescript
type PinChallengeProviderRequest = {
  parameters: PinChallenge // The result of the provider response.
  correlationId: string // The id that was passed in to the event that triggered a provider method to be called
}
```

See also:

[ProviderRequest](../Types/schemas/#ProviderRequest)
[PinChallenge](#pinchallenge-1)

---
