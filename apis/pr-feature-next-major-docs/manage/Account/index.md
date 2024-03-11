---
title: Account

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Account Module

---

Version Account 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [session](#session)
- [Types](#types)
  - [Token](#token)
  - [Expiry](#expiry)

## Usage

To use the Account module, you can import it into your project from the Firebolt SDK:

```javascript
import { Account } from '@firebolt-js/manage-sdk'
```

## Overview

A module for querying about the device account.

## Methods

### session

Used by a distributor to push Session token to firebolt.

```typescript
function session(token: string, expiresIn: number): Promise<void>
```

Parameters:

| Param       | Type     | Required | Description     |
| ----------- | -------- | -------- | --------------- |
| `token`     | `string` | true     |                 |
| `expiresIn` | `number` | true     | <br/>minumum: 1 |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                            |
| ------- | ------------------------------------- |
| manages | xrn:firebolt:capability:token:account |

#### Examples

Default Example

JavaScript:

```javascript
import { Account } from '@firebolt-js/manage-sdk'

let result = await Account.session(
  'RmlyZWJvbHQgTWFuYWdlIFNESyBSb2NrcyEhIQ==',
  84000,
)
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
  "method": "Account.session",
  "params": {
    "token": "RmlyZWJvbHQgTWFuYWdlIFNESyBSb2NrcyEhIQ==",
    "expiresIn": 84000
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

## Types

### Token

Encoded token provided by the Distributor for Device Authentication.

```typescript
type Token = string
```

---

### Expiry

Number of secs before the token expires

```typescript
type Expiry = number
```

---
