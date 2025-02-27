---
title: Authentication

version: next
layout: default
sdk: core
---

# Authentication Module

---

Version Authentication 1.5.0-next.16

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
  - [AuthenticationTokenResult](#authenticationtokenresult)

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

[Deprecated] This method is deprecated as of since version 0.9.0. Please use `Authentication module has individual methods for each token type.` as a replacement.

```typescript
function token(
  type: TokenType,
  options: object,
): Promise<AuthenticationTokenResult>
```

---

## Types

### TokenType

```typescript
TokenType: {
    PLATFORM: 'platform',
    DEVICE: 'device',
    DISTRIBUTOR: 'distributor',
},

```

---

### AuthenticationTokenResult

```typescript
type AuthenticationTokenResult = {
  value: string
  expires?: string
  type?: string
}
```

---
