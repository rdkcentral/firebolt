---
title: Keyboard

version: pr-build-npm-audit
layout: default
sdk: manage
---

# Keyboard Module

---

Version Keyboard 1.5.0-build-npm-audit.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [provide](#provide)
- [Private Methods](#private-methods)<details markdown="1"  ontoggle="document.getElementById('private-methods-details').open=this.open"><summary>Show</summary>
  - [emailFocus](#emailfocus)
  - [emailResponse](#emailresponse)
  - [passwordError](#passworderror)
  - [passwordFocus](#passwordfocus)
  - [passwordResponse](#passwordresponse)
  - [standardError](#standarderror)
  - [standardFocus](#standardfocus)
  - [standardResponse](#standardresponse)
  </details>
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [onRequestPassword](#onrequestpassword)
  - [onRequestStandard](#onrequeststandard)
  </details>
- [Provider Interfaces](#provider-interfaces)
  - [KeyboardInputProvider](#keyboardinputprovider)
- [Types](#types)
  - [KeyboardParameters](#keyboardparameters)
  - [KeyboardProviderRequest](#keyboardproviderrequest)

## Usage

To use the Keyboard module, you can import it into your project from the Firebolt SDK:

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for prompting users to enter text with task-oriented UX

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

### emailError

_This is a private RPC method._

Internal API for Email Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example 1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.emailError",
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

### emailFocus

_This is a private RPC method._

Internal API for Email Provider to request focus for UX purposes.

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.emailFocus",
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

### emailResponse

_This is a private RPC method._

Internal API for Email Provider to send back response.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `result`        | `string` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.emailResponse",
  "params": {
    "correlationId": "123",
    "result": "email@address.com"
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

### passwordError

_This is a private RPC method._

Internal API for Password Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example 1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.passwordError",
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

### passwordFocus

_This is a private RPC method._

Internal API for Password Provider to request focus for UX purposes.

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.passwordFocus",
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

### passwordResponse

_This is a private RPC method._

Internal API for Password Provider to send back response.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `result`        | `string` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.passwordResponse",
  "params": {
    "correlationId": "123",
    "result": "password"
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

### standardError

_This is a private RPC method._

Internal API for Standard Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example 1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.standardError",
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

### standardFocus

_This is a private RPC method._

Internal API for Standard Provider to request focus for UX purposes.

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.standardFocus",
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

### standardResponse

_This is a private RPC method._

Internal API for Standard Provider to send back response.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `result`        | `string` | true     |             |

Result:

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.standardResponse",
  "params": {
    "correlationId": "123",
    "result": "username"
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

### onRequestEmail

_This is a private RPC method._

Registers as a provider for when the user should be shown a keyboard optimized for email address entry.

Parameters:

| Param    | Type      | Required | Description |
| -------- | --------- | -------- | ----------- |
| `listen` | `boolean` | true     |             |

Result:

[KeyboardProviderRequest](#keyboardproviderrequest)

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Default Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.onRequestEmail",
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
      "message": "Enter your user name."
    }
  }
}
```

---

### onRequestPassword

_This is a private RPC method._

Registers as a provider for when the user should be shown a password keyboard, with dots for each character entered.

Parameters:

| Param    | Type      | Required | Description |
| -------- | --------- | -------- | ----------- |
| `listen` | `boolean` | true     |             |

Result:

[KeyboardProviderRequest](#keyboardproviderrequest)

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Default Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.onRequestPassword",
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
      "message": "Enter your user name."
    }
  }
}
```

---

### onRequestStandard

_This is a private RPC method._

Registers as a provider for when the user should be shown a standard keyboard.

Parameters:

| Param    | Type      | Required | Description |
| -------- | --------- | -------- | ----------- |
| `listen` | `boolean` | true     |             |

Result:

[KeyboardProviderRequest](#keyboardproviderrequest)

Capabilities:

| Role     | Capability                             |
| -------- | -------------------------------------- |
| provides | xrn:firebolt:capability:input:keyboard |

#### Examples

Default Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.onRequestStandard",
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
      "message": "Enter your user name."
    }
  }
}
```

---

</details>

## Provider Interfaces

### KeyboardInputProvider

The provider interface for the `xrn:firebolt:capability:input:keyboard` capability.

```typescript

```

Usage:

```typescript
Keyboard.provide('xrn:firebolt:capability:input:keyboard', provider: KeyboardInputProvider | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:input:keyboard` capability.**

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'

class MyKeyboardInputProvider {
  async standard(parameters, session) {
    return 'username'
  }

  async password(parameters, session) {
    return 'password'
  }

  async email(parameters, session) {
    return 'email@address.com'
  }
}

Keyboard.provide(
  'xrn:firebolt:capability:input:keyboard',
  new MyKeyboardInputProvider(),
)
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Keyboard.onRequestStandard",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Keyboard.onRequestPassword",
    "params": {
        "listen": true
    }
}

{
    "id": 3,
    "method": "Keyboard.onRequestEmail",
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
        "event": "Keyboard.onRequestStandard"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Keyboard.onRequestPassword"
    }

}

{
    "id": 3,
    "result": {
        "listening": true,
        "event": "Keyboard.onRequestEmail"
    }

}

```

**Asynchronous event to initiate standard()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": undefined,
    "parameters": {
      "message": "Enter your user name."
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 4,
  "method": "Keyboard.standardResponse",
  "params": {
    "correlationId": undefined,
    "result": "username"
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

**Asynchronous event to initiate password()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": undefined,
    "parameters": {
      "message": "Enter your user name."
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 5,
  "method": "Keyboard.passwordResponse",
  "params": {
    "correlationId": undefined,
    "result": "password"
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

**Asynchronous event to initiate email()**

Event Response:

```json
{
  "id": 3,
  "result": {
    "correlationId": undefined,
    "parameters": {
      "message": "Enter your user name."
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 6,
  "method": "Keyboard.emailResponse",
  "params": {
    "correlationId": undefined,
    "result": "email@address.com"
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

### KeyboardParameters

```typescript
type KeyboardParameters = {
  message: string // The message to display to the user so the user knows what they are entering
}
```

---

### KeyboardProviderRequest

```typescript
type KeyboardProviderRequest = {
  correlationId: string // An id to correlate the provider response with this request
  parameters: KeyboardParameters // The request to start a keyboard session
}
```

See also:

[KeyboardParameters](#keyboardparameters)

---
