---
title: UserGrants

version: next-major
layout: default
sdk: manage
---

# UserGrants Module

---

Version UserGrants 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [app](#app)
  - [capability](#capability)
  - [clear](#clear)
  - [deny](#deny)
  - [device](#device)
  - [grant](#grant)
  - [request](#request)
- [Types](#types)
  - [RequestOptions](#requestoptions)

## Usage

To use the UserGrants module, you can import it into your project from the Firebolt SDK:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing grants given by the user

## Methods

### app

Get all granted and denied user grants for the given app

```typescript
function app(appId: string): Promise<object[]>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `appId` | `string` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

---

### capability

Get all granted and denied user grants for the given capability

```typescript
function capability(capability: Capabilities.Capability): Promise<object[]>
```

Parameters:

| Param        | Type                      | Required | Description |
| ------------ | ------------------------- | -------- | ----------- |
| `capability` | `Capabilities.Capability` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

---

### clear

Clears the grant for a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function clear(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description |
| ------------ | ------------------------- | -------- | ----------- |
| `role`       | `Capabilities.Role`       | true     |             |
| `capability` | `Capabilities.Capability` | true     |             |
| `options`    | `object`                  | false    |             |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

---

### deny

Denies a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function deny(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description |
| ------------ | ------------------------- | -------- | ----------- |
| `role`       | `Capabilities.Role`       | true     |             |
| `capability` | `Capabilities.Capability` | true     |             |
| `options`    | `object`                  | false    |             |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

---

### device

Get all granted and denied user grants for the device

```typescript
function device(): Promise<object[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

---

### grant

Grants a given capability to a specific app, if appropriate. Calling this results in a persisted active grant that lasts for the duration of the grant policy lifespan.

```typescript
function grant(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description |
| ------------ | ------------------------- | -------- | ----------- |
| `role`       | `Capabilities.Role`       | true     |             |
| `capability` | `Capabilities.Capability` | true     |             |
| `options`    | `object`                  | false    |             |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

---

### request

Requests Firebolt to carry out a set of user grants for a given application such that the user grant provider is notified or an existing user grant is reused.

```typescript
function request(
  appId: string,
  permissions: Capabilities.Permission[],
  options: RequestOptions,
): Promise<object[]>
```

Parameters:

| Param         | Type                        | Required | Description     |
| ------------- | --------------------------- | -------- | --------------- |
| `appId`       | `string`                    | true     |                 |
| `permissions` | `Capabilities.Permission[]` | true     |                 |
| `options`     | `RequestOptions`            | false    | Request options |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

---

## Types

### RequestOptions

```typescript
type RequestOptions = {
  force?: boolean // Whether to force for user grant even if the previous decision stored
}
```

---
