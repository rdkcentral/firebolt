---
title: Account

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Account Module

---

Version Account 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [id](#id)
  - [uid](#uid)

## Usage

To use the Account module, you can import it into your project from the Firebolt SDK:

```javascript
import { Account } from '@firebolt-js/sdk'
```

## Overview

A module for querying about the device account.

## Methods

### id

Get the platform back-office account identifier

To get the value of `id` call the method like this:

```typescript
function id(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                         |
| ---- | ---------------------------------- |
| uses | xrn:firebolt:capability:account:id |

#### Examples

Default Example

JavaScript:

```javascript
import { Account } from '@firebolt-js/sdk'

let id = await Account.id()
console.log(id)
```

Value of `id`:

```javascript
'123'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Account.id",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "123"
}
```

</details>

---

### uid

Gets a unique id for the current app & account

To get the value of `uid` call the method like this:

```typescript
function uid(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:account:uid |

#### Examples

Getting the unique ID

JavaScript:

```javascript
import { Account } from '@firebolt-js/sdk'

let uniqueId = await Account.uid()
console.log(uniqueId)
```

Value of `uniqueId`:

```javascript
'ee6723b8-7ab3-462c-8d93-dbf61227998e'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Account.uid",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "ee6723b8-7ab3-462c-8d93-dbf61227998e"
}
```

</details>

---
