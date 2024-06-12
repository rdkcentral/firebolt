---
title: SecureStorage

version: next-major
layout: default
sdk: core
---

# SecureStorage Module

---

Version SecureStorage 0.0.0-unknown.0

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

| Param   | Type           | Required | Description                                                     |
| ------- | -------------- | -------- | --------------------------------------------------------------- |
| `scope` | `StorageScope` | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

---

### get

Get stored value by key

```typescript
function get(scope: StorageScope, key: string): Promise<string | null>
```

Parameters:

| Param   | Type           | Required | Description                                                     |
| ------- | -------------- | -------- | --------------------------------------------------------------- |
| `scope` | `StorageScope` | true     | The scope of the key/value <br/>values: `'device' \| 'account'` |
| `key`   | `string`       | true     | Key to get                                                      |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

---

### remove

Remove a secure data value

```typescript
function remove(scope: StorageScope, key: string): Promise<void>
```

Parameters:

| Param   | Type           | Required | Description                                                    |
| ------- | -------------- | -------- | -------------------------------------------------------------- |
| `scope` | `StorageScope` | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`   | `string`       | true     | Key to remove                                                  |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

#### Examples

---

### set

Set or update a secure data value

```typescript
function set(
  scope: StorageScope,
  key: string,
  value: string,
  options: StorageOptions,
): Promise<void>
```

Parameters:

| Param     | Type             | Required | Description                                                    |
| --------- | ---------------- | -------- | -------------------------------------------------------------- |
| `scope`   | `StorageScope`   | true     | The scope of the data key <br/>values: `'device' \| 'account'` |
| `key`     | `string`         | true     | Key to set                                                     |
| `value`   | `string`         | true     | Value to set                                                   |
| `options` | `StorageOptions` | false    | Optional parameters to set                                     |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:storage:secure |

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
