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

Default example

JavaScript:

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'

let result = await Keyboard.provide(true)
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
  "method": "Keyboard.provide",
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

### Keyboard

The provider interface for the `xrn:firebolt:capability:input:keyboard` capability.

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
Keyboard.provide('xrn:firebolt:capability:input:keyboard', provider: Keyboard | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:input:keyboard` capability.**

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'

class MyKeyboard {

    async Keyboard.email(parameters, session) {
        ${if.provider.interface.example.result}return "user@domain.com"${end.if.provider.interface.example.result}
    }

    async Keyboard.password(parameters, session) {
        ${if.provider.interface.example.result}return "abc123"${end.if.provider.interface.example.result}
    }

    async Keyboard.standard(parameters, session) {
        ${if.provider.interface.example.result}return "Living Room"${end.if.provider.interface.example.result}
    }

}

Keyboard.provide('xrn:firebolt:capability:input:keyboard', new MyKeyboard())
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
EmailUsage: {
    SIGN_IN: 'signIn',
    SIGN_UP: 'signUp',
},

```

---
