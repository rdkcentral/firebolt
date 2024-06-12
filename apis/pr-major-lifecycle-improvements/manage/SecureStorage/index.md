---
title: SecureStorage

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# SecureStorage Module

---

Version SecureStorage 0.0.0-unknown.0

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

| Param   | Type           | Required | Description                                                     |
| ------- | -------------- | -------- | --------------------------------------------------------------- |
| `appId` | `string`       | true     | appId for which values are removed                              |
| `scope` | `StorageScope` | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |

Promise resolution:

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

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

| Param   | Type           | Required | Description                                                     |
| ------- | -------------- | -------- | --------------------------------------------------------------- |
| `appId` | `string`       | true     | appId for which values are removed                              |
| `scope` | `StorageScope` | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |
| `key`   | `string`       | true     | Key to remove                                                   |

Promise resolution:

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

---

### setForApp

Set or update a secure data value for a specific app.

```typescript
function setForApp(
  appId: string,
  scope: StorageScope,
  key: string,
  value: string,
  options: StorageOptions,
): Promise<void>
```

Parameters:

| Param     | Type             | Required | Description                                                    |
| --------- | ---------------- | -------- | -------------------------------------------------------------- |
| `appId`   | `string`         | true     | appId for which value is being set                             |
| `scope`   | `StorageScope`   | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`     | `string`         | true     | Key to set                                                     |
| `value`   | `string`         | true     | Value to set                                                   |
| `options` | `StorageOptions` | false    | Optional parameters to set                                     |

Promise resolution:

Capabilities:

| Role    | Capability                             |
| ------- | -------------------------------------- |
| manages | xrn:firebolt:capability:storage:secure |

#### Examples

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
