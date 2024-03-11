---
title: Authentication

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Authentication Module

---

Version Authentication 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [device](#device)
  - [root](#root)
  - [session](#session)
  - [token](#token)
- [Types](#types)
  - [TokenType](#tokentype)

## Usage

To use the Authentication module, you can import it into your project from the Firebolt SDK:

```javascript
import { Authentication } from '@firebolt-js/sdk'
```

## Overview

A module for acquiring authentication tokens.

## Methods

### device

Get a device token scoped to the current app.

```typescript
function device(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:token:device |

#### Examples

Acquire a Firebolt device identity token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.device()
console.log(token)
```

Value of `token`:

```javascript
'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.device",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

</details>

---

### root

Get a root device token.

```typescript
function root(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                         |
| ---- | ---------------------------------- |
| uses | xrn:firebolt:capability:token:root |

#### Examples

Acquire a Firebolt root device identity token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.root()
console.log(token)
```

Value of `token`:

```javascript
'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.root",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

</details>

---

### session

Get a destributor session token.

```typescript
function session(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:token:session |

#### Examples

Acquire a distributor session token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.session()
console.log(token)
```

Value of `token`:

```javascript
'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.session",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

</details>

---

### token

Get a specific `type` of authentication token

```typescript
function token(type: TokenType, options?: object): Promise<object>
```

Parameters:

| Param     | Type                      | Required | Description                                                                      |
| --------- | ------------------------- | -------- | -------------------------------------------------------------------------------- |
| `type`    | [`TokenType`](#tokentype) | true     | What type of token to get <br/>values: `'platform' \| 'device' \| 'distributor'` |
| `options` | `object`                  | false    | Additional options for acquiring the token.                                      |

Promise resolution:

| Property  | Type   | Description |
| --------- | ------ | ----------- |
| `value`   | string |             |
| `expires` | string |             |
| `type`    | string |             |

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:token:platform |

#### Examples

Acquire a Firebolt platform token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.token('platform', null)
console.log(token)
```

Value of `token`:

```javascript
{
	"value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
	"expires": "2022-04-23T18:25:43.511Z",
	"type": "platform"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.token",
  "params": {
    "type": "platform"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "expires": "2022-04-23T18:25:43.511Z",
    "type": "platform"
  }
}
```

</details>

Acquire a Firebolt device identity token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.token('device', null)
console.log(token)
```

Value of `token`:

```javascript
{
	"value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
	"expires": "2022-04-23T18:25:43.511Z",
	"type": "platform"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.token",
  "params": {
    "type": "device"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "expires": "2022-04-23T18:25:43.511Z",
    "type": "device"
  }
}
```

</details>

Acquire a Firebolt distributor token

JavaScript:

```javascript
import { Authentication } from '@firebolt-js/sdk'

let token = await Authentication.token('distributor', { clientId: 'xyz' })
console.log(token)
```

Value of `token`:

```javascript
{
	"value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
	"expires": "2022-04-23T18:25:43.511Z",
	"type": "platform"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Authentication.token",
  "params": {
    "type": "distributor",
    "options": {
      "clientId": "xyz"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "expires": "2022-04-23T18:25:43.511Z",
    "type": "distributor",
    "data": {
      "tid": "EB00E9230AB2A35F57DB4EFDDC4908F6446D38F08F4FF0BD57FE6A61E21EEFD9",
      "scope": "scope"
    }
  }
}
```

</details>

---

## Types

### TokenType

```typescript
enum TokenType {
  PLATFORM = 'platform',
  DEVICE = 'device',
  DISTRIBUTOR = 'distributor',
}
```

---
