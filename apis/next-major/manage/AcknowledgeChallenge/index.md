---
title: AcknowledgeChallenge

version: next-major
layout: default
sdk: manage
---

# AcknowledgeChallenge Module

---

Version AcknowledgeChallenge 1.8.0-next-major.3

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [provide](#provide)
- [Provider Interfaces](#provider-interfaces)
  - [AcknowledgeChallenge](#acknowledgechallenge)
- [Types](#types)
  - [ChallengeRequestor](#challengerequestor)
  - [GrantResult](#grantresult)

## Usage

To use the AcknowledgeChallenge module, you can import it into your project from the Firebolt SDK:

```javascript
import { AcknowledgeChallenge } from '@firebolt-js/manage-sdk'
```

## Overview

A module for registering as a provider for a user grant in which the user confirms access to a capability

## Methods

### provide

undefined

```typescript
function provide(enabled: boolean): Promise<null>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Promise resolution:

Capabilities:

| Role     | Capability                                             |
| -------- | ------------------------------------------------------ |
| provides | xrn:firebolt:capability:usergrant:acknowledgechallenge |

#### Examples

Default example

JavaScript:

```javascript
import { AcknowledgeChallenge } from '@firebolt-js/manage-sdk'

let result = await AcknowledgeChallenge.provide(true)
console.log(result)
```

Value of `result`:

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
  "method": "AcknowledgeChallenge.provide",
  "params": {
    "enabled": true
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

## Provider Interfaces

### AcknowledgeChallenge

The provider interface for the `xrn:firebolt:capability:usergrant:acknowledgechallenge` capability.

```typescript
interface AcknowledgeChallenge {
  challenge(
    capability: string,
    requestor: ChallengeRequestor,
    session: FocusableProviderSession,
  ): Promise<GrantResult>
}
```

Usage:

```typescript
AcknowledgeChallenge.provide('xrn:firebolt:capability:usergrant:acknowledgechallenge', provider: AcknowledgeChallenge | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:usergrant:acknowledgechallenge` capability.**

```javascript
import { AcknowledgeChallenge } from '@firebolt-js/manage-sdk'

class MyAcknowledgeChallenge {

    async AcknowledgeChallenge.challenge(parameters, session) {
        ${if.provider.interface.example.result}return {
            "granted": true
        }${end.if.provider.interface.example.result}
    }

}

AcknowledgeChallenge.provide('xrn:firebolt:capability:usergrant:acknowledgechallenge', new MyAcknowledgeChallenge())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "AcknowledgeChallenge.onRequestAcknowledgeChallenge.challenge",
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
    "event": "AcknowledgeChallenge.onRequestAcknowledgeChallenge.challenge"
  }
}
```

**Asynchronous event to initiate AcknowledgeChallenge.challenge()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": "xrn:firebolt:capability:localization::postal-code"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "AcknowledgeChallenge.AcknowledgeChallenge.challengeResponse",
  "params": {
    "correlationId": "",
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

### ChallengeRequestor

```typescript
type ChallengeRequestor = {
  id: string // The id of the app that requested the challenge
  name: string // The name of the app that requested the challenge
}
```

---

### GrantResult

```typescript
type GrantResult = {
  granted: boolean
}
```

---
