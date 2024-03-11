---
title: Keyboard

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Keyboard Module

---

Version Keyboard 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [emailError](#emailerror)
  - [emailFocus](#emailfocus)
  - [emailResponse](#emailresponse)
  - [passwordError](#passworderror)
  - [passwordFocus](#passwordfocus)
  - [passwordResponse](#passwordresponse)
  - [provide](#provide)
  - [standardError](#standarderror)
  - [standardFocus](#standardfocus)
  - [standardResponse](#standardresponse)
- [Events](#events)
  - [onRequestEmail](#onrequestemail)
  - [onRequestPassword](#onrequestpassword)
  - [onRequestStandard](#onrequeststandard)
- [Provider Interfaces](#provider-interfaces)
  - [KeyboardInputProvider](#keyboardinputprovider)
- [Types](#types)
  - [KeyboardResult](#keyboardresult)
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

### emailError

_This is an private RPC method._

Internal API for Email Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Email Provider to request focus for UX purposes.

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Email Provider to send back response.

Parameters:

| Param           | Type                                | Required | Description |
| --------------- | ----------------------------------- | -------- | ----------- |
| `correlationId` | `string`                            | true     |             |
| `result`        | [`KeyboardResult`](#keyboardresult) | true     |             |

Result:

```typescript
null
```

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
    "result": {
      "text": "email@address.com"
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

### passwordError

_This is an private RPC method._

Internal API for Password Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Password Provider to request focus for UX purposes.

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Password Provider to send back response.

Parameters:

| Param           | Type                                | Required | Description |
| --------------- | ----------------------------------- | -------- | ----------- |
| `correlationId` | `string`                            | true     |             |
| `result`        | [`KeyboardResult`](#keyboardresult) | true     |             |

Result:

```typescript
null
```

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
    "result": {
      "text": "password"
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

### standardError

_This is an private RPC method._

Internal API for Standard Provider to send back error.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |
| `error`         | `object` | true     |             |

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Standard Provider to request focus for UX purposes.

Result:

```typescript
null
```

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

_This is an private RPC method._

Internal API for Standard Provider to send back response.

Parameters:

| Param           | Type                                | Required | Description |
| --------------- | ----------------------------------- | -------- | ----------- |
| `correlationId` | `string`                            | true     |             |
| `result`        | [`KeyboardResult`](#keyboardresult) | true     |             |

Result:

```typescript
null
```

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
    "result": {
      "text": "username"
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

### onRequestEmail

_This is an private RPC method._

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

_This is an private RPC method._

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

_This is an private RPC method._

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

## Provider Interfaces

### KeyboardInputProvider

The provider interface for the `xrn:firebolt:capability:input:keyboard` capability.

```typescript

```

Usage:

```typescript
Keyboard.provide('xrn:firebolt:capability:input:keyboard', provider: KeyboardInputProvider | object)
```

#### standard

Registers as a provider for when the user should be shown a standard keyboard.

```typescript
function standard(
  parameters?: KeyboardParameters,
  session?: FocusableProviderSession,
): Promise<KeyboardResult>
```

Provider methods always have two arguments:

| Param        | Type                                        | Required | Summary |
| ------------ | ------------------------------------------- | -------- | ------- |
| `parameters` | [`KeyboardParameters`](#keyboardparameters) | false    |         |
| `session`    | `FocusableProviderSession`                  | false    |         |

| Parameters Property | Type     | Required | Summary                                                                     |
| ------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| `message`           | `string` | true     | The message to display to the user so the user knows what they are entering |

```typescript
type KeyboardParameters = {
  message: string // The message to display to the user so the user knows what they are entering
}
```

Promise resolution:

| Property   | Type    | Description                                                                              |
| ---------- | ------- | ---------------------------------------------------------------------------------------- |
| `text`     | string  | The text the user entered into the keyboard                                              |
| `canceled` | boolean | Whether the user canceled entering text before they were finished typing on the keyboard |

#### password

Registers as a provider for when the user should be shown a password keyboard, with dots for each character entered.

```typescript
function password(
  parameters?: KeyboardParameters,
  session?: FocusableProviderSession,
): Promise<KeyboardResult>
```

Provider methods always have two arguments:

| Param        | Type                                        | Required | Summary |
| ------------ | ------------------------------------------- | -------- | ------- |
| `parameters` | [`KeyboardParameters`](#keyboardparameters) | false    |         |
| `session`    | `FocusableProviderSession`                  | false    |         |

| Parameters Property | Type     | Required | Summary                                                                     |
| ------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| `message`           | `string` | true     | The message to display to the user so the user knows what they are entering |

```typescript
type KeyboardParameters = {
  message: string // The message to display to the user so the user knows what they are entering
}
```

Promise resolution:

| Property   | Type    | Description                                                                              |
| ---------- | ------- | ---------------------------------------------------------------------------------------- |
| `text`     | string  | The text the user entered into the keyboard                                              |
| `canceled` | boolean | Whether the user canceled entering text before they were finished typing on the keyboard |

#### email

Registers as a provider for when the user should be shown a keyboard optimized for email address entry.

```typescript
function email(
  parameters?: KeyboardParameters,
  session?: FocusableProviderSession,
): Promise<KeyboardResult>
```

Provider methods always have two arguments:

| Param        | Type                                        | Required | Summary |
| ------------ | ------------------------------------------- | -------- | ------- |
| `parameters` | [`KeyboardParameters`](#keyboardparameters) | false    |         |
| `session`    | `FocusableProviderSession`                  | false    |         |

| Parameters Property | Type     | Required | Summary                                                                     |
| ------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| `message`           | `string` | true     | The message to display to the user so the user knows what they are entering |

```typescript
type KeyboardParameters = {
  message: string // The message to display to the user so the user knows what they are entering
}
```

Promise resolution:

| Property   | Type    | Description                                                                              |
| ---------- | ------- | ---------------------------------------------------------------------------------------- |
| `text`     | string  | The text the user entered into the keyboard                                              |
| `canceled` | boolean | Whether the user canceled entering text before they were finished typing on the keyboard |

#### Examples

**Register your app to provide the `xrn:firebolt:capability:input:keyboard` capability.**

```javascript
import { Keyboard } from '@firebolt-js/manage-sdk'

class MyKeyboardInputProvider {
  async standard(parameters, session) {
    return {
      text: 'username',
    }
  }

  async password(parameters, session) {
    return {
      text: 'password',
    }
  }

  async email(parameters, session) {
    return {
      text: 'email@address.com',
    }
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
    "correlationId": "abc",
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
    "correlationId": "abc",
    "result": {
      "text": "username"
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

**Asynchronous event to initiate password()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "abc",
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
    "correlationId": "abc",
    "result": {
      "text": "password"
    }
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
    "correlationId": "abc",
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
    "correlationId": "abc",
    "result": {
      "text": "email@address.com"
    }
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

### KeyboardResult

```typescript
type KeyboardResult = {
  text: string // The text the user entered into the keyboard
  canceled?: boolean // Whether the user canceled entering text before they were finished typing on the keyboard
}
```

---

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
  parameters: KeyboardParameters
}
```

See also:

[KeyboardParameters](#keyboardparameters)

---
