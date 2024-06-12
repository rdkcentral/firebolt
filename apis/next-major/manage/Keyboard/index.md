---
title: Keyboard

version: next-major
layout: default
sdk: manage
---

# Keyboard Module

---

Version Keyboard 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [provide](#provide)
- [Provider Interfaces](#provider-interfaces)
  - [Keyboard](#keyboard)
- [Types](#types)
  - [EmailUsage](#emailusage)

## Usage

To use the Keyboard module, you can import it into your project from the Firebolt SDK:

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for prompting users to enter text with task-oriented UX

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

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

---

## Provider Interfaces

### Keyboard

The provider interface for the `Keyboard` capability.

```typescript
interface Keyboard {
  email(
    type: EmailUsage,
    message?: string,
    session: ProviderSession,
  ): Promise<string>
  password(message?: string, session: ProviderSession): Promise<string>
  standard(message: string, session: ProviderSession): Promise<string>
}
```

Usage:

```typescript
Keyboard.provide('Keyboard', provider: Keyboard | object)
```

#### Examples

**Register your app to provide the `Keyboard` capability.**

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'

class MyKeyboard {

    async Keyboard.email(parameters, session) {
        return "user@domain.com"
    }

    async Keyboard.password(parameters, session) {
        return "abc123"
    }

    async Keyboard.standard(parameters, session) {
        return "Living Room"
    }

}

Keyboard.provide('Keyboard', new MyKeyboard())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Keyboard.onRequestKeyboard.email",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Keyboard.onRequestKeyboard.password",
    "params": {
        "listen": true
    }
}

{
    "id": 3,
    "method": "Keyboard.onRequestKeyboard.standard",
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
        "event": "Keyboard.onRequestKeyboard.email"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Keyboard.onRequestKeyboard.password"
    }

}

{
    "id": 3,
    "result": {
        "listening": true,
        "event": "Keyboard.onRequestKeyboard.standard"
    }

}

```

**Asynchronous event to initiate Keyboard.email()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": "signIn"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 4,
  "method": "Keyboard.Keyboard.emailResponse",
  "params": {
    "correlationId": "",
    "result": "user@domain.com"
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

**Asynchronous event to initiate Keyboard.password()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "",
    "parameters": "Enter your password"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 5,
  "method": "Keyboard.Keyboard.passwordResponse",
  "params": {
    "correlationId": "",
    "result": "abc123"
  }
}
```

Response:

```json
{
  "id": 5,
  "result": true
}
```

**Asynchronous event to initiate Keyboard.standard()**

Event Response:

```json
{
  "id": 3,
  "result": {
    "correlationId": "",
    "parameters": "Enter the name you'd like to associate with this device"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 6,
  "method": "Keyboard.Keyboard.standardResponse",
  "params": {
    "correlationId": "",
    "result": "Living Room"
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

</details>

## Types

### EmailUsage

```typescript
enum EmailUsage {
  SIGN_IN = 'signIn',
  SIGN_UP = 'signUp',
}
```

---
