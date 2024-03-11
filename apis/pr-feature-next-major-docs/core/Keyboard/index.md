---
title: Keyboard

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Keyboard Module

---

Version Keyboard 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [email](#email)
  - [password](#password)
  - [standard](#standard)
- [Types](#types)
  - [EmailUsage](#emailusage)

## Usage

To use the Keyboard module, you can import it into your project from the Firebolt SDK:

```javascript
import { Keyboard } from '@firebolt-js/sdk'
```

## Overview

Methods for prompting users to enter text with task-oriented UX

## Methods

### email

Prompt the user for their email address with a simplified list of choices.

```typescript
function email(type: EmailUsage, message?: string): Promise<string>
```

Parameters:

| Param     | Type                        | Required | Description                                                                                   |
| --------- | --------------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `type`    | [`EmailUsage`](#emailusage) | true     | Why the email is being requested, e.g. sign on or sign up <br/>values: `'signIn' \| 'signUp'` |
| `message` | `string`                    | false    | The message to display while prompting                                                        |

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

Prompt the user to select or type an email address

JavaScript:

```javascript
import { Keyboard } from '@firebolt-js/sdk'

let email = await Keyboard.email(
  'signIn',
  'Enter your email to sign into this app',
)
console.log(email)
```

Value of `email`:

```javascript
'user@domain.com'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.email",
  "params": {
    "type": "signIn",
    "message": "Enter your email to sign into this app"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "user@domain.com"
}
```

</details>

Prompt the user to type an email address to sign up

JavaScript:

```javascript
import { Keyboard } from '@firebolt-js/sdk'

let email = await Keyboard.email(
  'signUp',
  'Enter your email to sign up for this app',
)
console.log(email)
```

Value of `email`:

```javascript
'user@domain.com'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.email",
  "params": {
    "type": "signUp",
    "message": "Enter your email to sign up for this app"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "user@domain.com"
}
```

</details>

---

### password

Show the password entry keyboard, with typing obfuscated from visibility

```typescript
function password(message?: string): Promise<string>
```

Parameters:

| Param     | Type     | Required | Description                            |
| --------- | -------- | -------- | -------------------------------------- |
| `message` | `string` | false    | The message to display while prompting |

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

Prompt the user to enter their password

JavaScript:

```javascript
import { Keyboard } from '@firebolt-js/sdk'

let value = await Keyboard.password('Enter your password')
console.log(value)
```

Value of `value`:

```javascript
'abc123'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.password",
  "params": {
    "message": "Enter your password"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "abc123"
}
```

</details>

---

### standard

Show the standard platform keyboard, and return the submitted value

```typescript
function standard(message: string): Promise<string>
```

Parameters:

| Param     | Type     | Required | Description                            |
| --------- | -------- | -------- | -------------------------------------- |
| `message` | `string` | true     | The message to display while prompting |

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

Prompt the user for an arbitrary string

JavaScript:

```javascript
import { Keyboard } from '@firebolt-js/sdk'

let value = await Keyboard.standard(
  "Enter the name you'd like to associate with this device",
)
console.log(value)
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Keyboard.standard",
  "params": {
    "message": "Enter the name you'd like to associate with this device"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>

---

## Types

### EmailUsage

```typescript
enum EmailUsage {
  SIGN_IN = 'signIn',
  SIGN_UP = 'signUp',
}
```

---
