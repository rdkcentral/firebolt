---
title: AcknowledgeChallenge

version: 1.7.0
layout: default
sdk: manage
---

# AcknowledgeChallenge Module

---

Version AcknowledgeChallenge 1.7.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [provide](#provide)
- [Private Methods](#private-methods)<details markdown="1"  ontoggle="document.getElementById('private-methods-details').open=this.open"><summary>Show</summary>
  - [challengeFocus](#challengefocus)
  - [challengeResponse](#challengeresponse)
  </details>
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  </details>
- [Provider Interfaces](#provider-interfaces)
  - [ChallengeProvider](#challengeprovider)
- [Types](#types)
  - [GrantResult](#grantresult)
  - [ChallengeRequestor](#challengerequestor)
  - [Challenge](#challenge)
  - [ChallengeProviderRequest](#challengeproviderrequest)

## Usage

To use the AcknowledgeChallenge module, you can import it into your project from the Firebolt SDK:

```javascript
import { AcknowledgeChallenge } from '@firebolt-js/manage-sdk'
```

## Overview

A module for registering as a provider for a user grant in which the user confirms access to a capability

## Methods

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

## Private Methods

<details markdown="1"  id="private-methods-details">
  <summary>View</summary>

### challengeError

_This is a private RPC method._

Internal API for Challenge Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

Capabilities:

| Role     | Capability                                             |
| -------- | ------------------------------------------------------ |
| provides | xrn:firebolt:capability:usergrant:acknowledgechallenge |

#### Examples

Example 1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AcknowledgeChallenge.challengeError",
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

_This is a private RPC method._

Internal API for Challenge Provider to request focus for UX purposes.

Result:

Capabilities:

| Role     | Capability                                             |
| -------- | ------------------------------------------------------ |
| provides | xrn:firebolt:capability:usergrant:acknowledgechallenge |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AcknowledgeChallenge.challengeFocus",
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

_This is a private RPC method._

Internal API for Challenge Provider to send back response.

Parameters:

| Param           | Type                          | Required | Description |
| --------------- | ----------------------------- | -------- | ----------- |
| `correlationId` | `string`                      | true     |             |
| `result`        | [`GrantResult`](#grantresult) | true     |             |

Result:

Capabilities:

| Role     | Capability                                             |
| -------- | ------------------------------------------------------ |
| provides | xrn:firebolt:capability:usergrant:acknowledgechallenge |

#### Examples

Example #1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AcknowledgeChallenge.challengeResponse",
  "params": {
    "correlationId": "123",
    "result": {
      "granted": true
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
  "method": "AcknowledgeChallenge.challengeResponse",
  "params": {
    "correlationId": "123",
    "result": {
      "granted": false
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
  "method": "AcknowledgeChallenge.challengeResponse",
  "params": {
    "correlationId": "123",
    "result": {
      "granted": null
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

</details>

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### onRequestChallenge

_This is a private RPC method._

Registers as a provider for when the user should be challenged in order to confirm access to a capability

Parameters:

| Param    | Type      | Required | Description |
| -------- | --------- | -------- | ----------- |
| `listen` | `boolean` | true     |             |

Result:

[ChallengeProviderRequest](#challengeproviderrequest)

Capabilities:

| Role     | Capability                                             |
| -------- | ------------------------------------------------------ |
| provides | xrn:firebolt:capability:usergrant:acknowledgechallenge |

#### Examples

Default Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "AcknowledgeChallenge.onRequestChallenge",
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
      "capability": "xrn:firebolt:capability:localization::postal-code",
      "requestor": {
        "id": "ReferenceApp",
        "name": "Firebolt Reference App"
      }
    }
  }
}
```

---

</details>

## Provider Interfaces

### ChallengeProvider

The provider interface for the `xrn:firebolt:capability:usergrant:acknowledgechallenge` capability.

```typescript

```

Usage:

```typescript
AcknowledgeChallenge.provide('xrn:firebolt:capability:usergrant:acknowledgechallenge', provider: ChallengeProvider | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:usergrant:acknowledgechallenge` capability.**

```javascript
import { AcknowledgeChallenge } from '@firebolt-js/manage-sdk'

class MyChallengeProvider {
  async challenge(parameters, session) {
    return {
      granted: true,
    }
  }
}

AcknowledgeChallenge.provide(
  'xrn:firebolt:capability:usergrant:acknowledgechallenge',
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
  "method": "AcknowledgeChallenge.onRequestChallenge",
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
    "event": "AcknowledgeChallenge.onRequestChallenge"
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
      "capability": "xrn:firebolt:capability:localization::postal-code",
      "requestor": {
        "id": "ReferenceApp",
        "name": "Firebolt Reference App"
      }
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "AcknowledgeChallenge.challengeResponse",
  "params": {
    "correlationId": undefined,
    "result": {
      "granted": true
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

### GrantResult

```typescript
type GrantResult = {
  granted: boolean
}
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

### Challenge

```typescript
type Challenge = {
  capability: string // The capability that is being requested by the user to approve
  requestor: ChallengeRequestor // The identity of which app is requesting access to this capability
}
```

See also:

[ChallengeRequestor](#challengerequestor)

---

### ChallengeProviderRequest

```typescript
type ChallengeProviderRequest = {
  parameters: Challenge // The result of the provider response.
  correlationId: string // The id that was passed in to the event that triggered a provider method to be called
}
```

See also:

[ProviderRequest](../Types/schemas/#ProviderRequest)
[Challenge](#challenge-1)

---
