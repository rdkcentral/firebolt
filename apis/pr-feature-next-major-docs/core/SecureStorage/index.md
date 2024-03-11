---
title: SecureStorage

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# SecureStorage Module

---

Version SecureStorage 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [clear](#clear)
  - [get](#get)
  - [remove](#remove)
  - [set](#set)
- [Types](#types)
  - [StorageScope](#storagescope)
  - [StorageOptions](#storageoptions)

## Usage

To use the SecureStorage module, you can import it into your project from the Firebolt SDK:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'
```

## Overview

A module for storing and retrieving secure data owned by the app

## Methods

### clear

Clears all the secure data values

```typescript
function clear(scope: StorageScope): Promise<void>
```

Parameters:

| Param   | Type                            | Required | Description                                                     |
| ------- | ------------------------------- | -------- | --------------------------------------------------------------- |
| `scope` | [`StorageScope`](#storagescope) | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

Clears all the data values of storage

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let success = await SecureStorage.clear('account')
console.log(success)
```

Value of `success`:

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
  "method": "SecureStorage.clear",
  "params": {
    "scope": "account"
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

### get

Get stored value by key

```typescript
function get(scope: StorageScope, key: string): Promise<string | null>
```

Parameters:

| Param   | Type                            | Required | Description                                                     |
| ------- | ------------------------------- | -------- | --------------------------------------------------------------- |
| `scope` | [`StorageScope`](#storagescope) | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |
| `key`   | `string`                        | true     | Key to get                                                      |

Promise resolution:

```typescript
string | null
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

Successfully retrieve a refresh token with key authRefreshToken

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let value = await SecureStorage.get('device', 'authRefreshToken')
console.log(value)
```

Value of `value`:

```javascript
'VGhpcyBub3QgYSByZWFsIHRva2VuLgo='
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecureStorage.get",
  "params": {
    "scope": "device",
    "key": "authRefreshToken"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "VGhpcyBub3QgYSByZWFsIHRva2VuLgo="
}
```

</details>

Attempt to retrieve a key with no value set

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let value = await SecureStorage.get('account', 'authRefreshToken')
console.log(value)
```

Value of `value`:

```javascript
'VGhpcyBub3QgYSByZWFsIHRva2VuLgo='
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "SecureStorage.get",
  "params": {
    "scope": "account",
    "key": "authRefreshToken"
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

### remove

Remove a secure data value

```typescript
function remove(scope: StorageScope, key: string): Promise<void>
```

Parameters:

| Param   | Type                            | Required | Description                                                    |
| ------- | ------------------------------- | -------- | -------------------------------------------------------------- |
| `scope` | [`StorageScope`](#storagescope) | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`   | `string`                        | true     | Key to remove                                                  |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

Remove the value with key authRefreshToken for device

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let success = await SecureStorage.remove('device', 'authRefreshToken')
console.log(success)
```

Value of `success`:

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
  "method": "SecureStorage.remove",
  "params": {
    "scope": "device",
    "key": "authRefreshToken"
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

Remove the value with key authRefreshToken for account

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let success = await SecureStorage.remove('account', 'authRefreshToken')
console.log(success)
```

Value of `success`:

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
  "method": "SecureStorage.remove",
  "params": {
    "scope": "account",
    "key": "authRefreshToken"
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

### set

Set or update a secure data value

```typescript
function set(
  scope: StorageScope,
  key: string,
  value: string,
  options?: StorageOptions,
): Promise<void>
```

Parameters:

| Param     | Type                                | Required | Description                                                    |
| --------- | ----------------------------------- | -------- | -------------------------------------------------------------- |
| `scope`   | [`StorageScope`](#storagescope)     | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`     | `string`                            | true     | Key to set                                                     |
| `value`   | `string`                            | true     | Value to set                                                   |
| `options` | [`StorageOptions`](#storageoptions) | false    | Optional parameters to set                                     |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

Set a refresh token with name authRefreshToken with optional paramter

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let success = await SecureStorage.set(
  'device',
  'authRefreshToken',
  'VGhpcyBub3QgYSByZWFsIHRva2VuLgo=',
  { ttl: 600 },
)
console.log(success)
```

Value of `success`:

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
  "method": "SecureStorage.set",
  "params": {
    "scope": "device",
    "key": "authRefreshToken",
    "value": "VGhpcyBub3QgYSByZWFsIHRva2VuLgo=",
    "options": {
      "ttl": 600
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

</details>

Set a refresh token with name authRefreshToken without optional parameter

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/sdk'

let success = await SecureStorage.set(
  'account',
  'authRefreshToken',
  'VGhpcyBub3QgYSByZWFsIHRva2VuLgo=',
  null,
)
console.log(success)
```

Value of `success`:

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
  "method": "SecureStorage.set",
  "params": {
    "scope": "account",
    "key": "authRefreshToken",
    "value": "VGhpcyBub3QgYSByZWFsIHRva2VuLgo="
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

### StorageScope

The scope of the data

```typescript
enum StorageScope {
  DEVICE = 'device',
  ACCOUNT = 'account',
}
```

---

### StorageOptions

```typescript
type StorageOptions = {
  ttl: number // Seconds from set time before the data expires and is removed
}
```

---
