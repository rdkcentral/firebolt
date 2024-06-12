---
title: PinChallenge

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# PinChallenge Module

---

Version PinChallenge 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [provide](#provide)
- [Provider Interfaces](#provider-interfaces)
  - [PinChallenge](#pinchallenge)
- [Types](#types)
  - [ResultReason](#resultreason)
  - [ChallengeRequestor](#challengerequestor)
  - [PinChallengeResult](#pinchallengeresult)

## Usage

To use the PinChallenge module, you can import it into your project from the Firebolt SDK:

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'
```

## Overview

A module for registering as a provider for a user grant in which the user is prompted for a pin for access to a capability

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

| Role     | Capability                                     |
| -------- | ---------------------------------------------- |
| provides | xrn:firebolt:capability:usergrant:pinchallenge |

#### Examples

---

## Provider Interfaces

### PinChallenge

The provider interface for the `PinChallenge` capability.

```typescript
interface PinChallenge {
  challenge(
    requestor: ChallengeRequestor,
    pinSpace: 'purchase' | 'content',
    capability?: string,
    session: FocusableProviderSession,
  ): Promise<PinChallengeResult>
}
```

Usage:

```typescript
PinChallenge.provide('PinChallenge', provider: PinChallenge | object)
```

#### Examples

**Register your app to provide the `PinChallenge` capability.**

```javascript
import { PinChallenge } from '@firebolt-js/manage-sdk'

class MyPinChallenge {

    async PinChallenge.challenge(parameters, session) {
        return {
            "granted": true,
            "reason": "correctPin"
        }
    }

}

PinChallenge.provide('PinChallenge', new MyPinChallenge())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "PinChallenge.onRequestPinChallenge.challenge",
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
    "event": "PinChallenge.onRequestPinChallenge.challenge"
  }
}
```

**Asynchronous event to initiate PinChallenge.challenge()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": "xrn:firebolt:capability:commerce::purchase"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "PinChallenge.PinChallenge.challengeResponse",
  "params": {
    "correlationId": "",
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
enum ResultReason {
  NO_PIN_REQUIRED = 'noPinRequired',
  NO_PIN_REQUIRED_WINDOW = 'noPinRequiredWindow',
  EXCEEDED_PIN_FAILURES = 'exceededPinFailures',
  CORRECT_PIN = 'correctPin',
  CANCELLED = 'cancelled',
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

### PinChallengeResult

```typescript
type PinChallengeResult = {
  granted: boolean
  reason: ResultReason // The reason for the result of challenging the user
}
```

See also:

ResultReason

---
