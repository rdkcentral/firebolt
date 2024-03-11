---
title: SecureStorage

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# SecureStorage Module

---

Version SecureStorage 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [clearForApp](#clearforapp)
  - [removeForApp](#removeforapp)
  - [setForApp](#setforapp)
- [Types](#types)
  - [StorageScope](#storagescope)
  - [StorageOptions](#storageoptions)

## Usage

To use the SecureStorage module, you can import it into your project from the Firebolt SDK:

```javascript
import { SecureStorage } from '@firebolt-js/manage-sdk'
```

## Overview

A module for storing and retrieving secure data owned by the app

## Methods

### clearForApp

Clears all the secure data values for a specific app

```typescript
function clearForApp(appId: string, scope: StorageScope): Promise<void>
```

Parameters:

| Param   | Type                            | Required | Description                                                     |
| ------- | ------------------------------- | -------- | --------------------------------------------------------------- |
| `appId` | `string`                        | true     | appId for which values are removed                              |
| `scope` | [`StorageScope`](#storagescope) | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

Clears all the secure data values for appId foo

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/manage-sdk'

let success = await SecureStorage.clearForApp('foo', 'account')
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
  "method": "SecureStorage.clearForApp",
  "params": {
    "appId": "foo",
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

### removeForApp

Removes single data value for a specific app.

```typescript
function removeForApp(
  appId: string,
  scope: StorageScope,
  key: string,
): Promise<void>
```

Parameters:

| Param   | Type                            | Required | Description                                                     |
| ------- | ------------------------------- | -------- | --------------------------------------------------------------- |
| `appId` | `string`                        | true     | appId for which values are removed                              |
| `scope` | [`StorageScope`](#storagescope) | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |
| `key`   | `string`                        | true     | Key to remove                                                   |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

Removes authRefreshToken for appId foo

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/manage-sdk'

let success = await SecureStorage.removeForApp(
  'foo',
  'account',
  'authRefreshToken',
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
  "method": "SecureStorage.removeForApp",
  "params": {
    "appId": "foo",
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

### setForApp

Set or update a secure data value for a specific app.

```typescript
function setForApp(
  appId: string,
  scope: StorageScope,
  key: string,
  value: string,
  options?: StorageOptions,
): Promise<void>
```

Parameters:

| Param     | Type                                | Required | Description                                                    |
| --------- | ----------------------------------- | -------- | -------------------------------------------------------------- |
| `appId`   | `string`                            | true     | appId for which value is being set                             |
| `scope`   | [`StorageScope`](#storagescope)     | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`     | `string`                            | true     | Key to set                                                     |
| `value`   | `string`                            | true     | Value to set                                                   |
| `options` | [`StorageOptions`](#storageoptions) | false    | Optional parameters to set                                     |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

Set a refresh token with name authRefreshToken with optional parameter for appId foo

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/manage-sdk'

let success = await SecureStorage.setForApp(
  'foo',
  'device',
  'authRefreshToken',
  'VGhpcyBub3QgYSByZWFsIHRva2VuLgo=',
  {
    ttl: 600,
  },
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
  "method": "SecureStorage.setForApp",
  "params": {
    "appId": "foo",
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

Set a refresh token with name authRefreshToken without optional parameter for appId foo

JavaScript:

```javascript
import { SecureStorage } from '@firebolt-js/manage-sdk'

let success = await SecureStorage.setForApp(
  'foo',
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
  "method": "SecureStorage.setForApp",
  "params": {
    "appId": "foo",
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
