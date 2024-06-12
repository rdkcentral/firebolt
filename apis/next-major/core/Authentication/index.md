---
title: Authentication

version: next-major
layout: default
sdk: core
---

# Authentication Module

---

Version Authentication 0.0.0-unknown.0

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

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:token:device |

#### Examples

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

---

### token

Get a specific `type` of authentication token

```typescript
function token(type: TokenType, options: object): Promise<object>
```

Parameters:

| Param     | Type        | Required | Description                                                                      |
| --------- | ----------- | -------- | -------------------------------------------------------------------------------- |
| `type`    | `TokenType` | true     | What type of token to get <br/>values: `'platform' \| 'device' \| 'distributor'` |
| `options` | `object`    | false    | Additional options for acquiring the token.                                      |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:token:platform |

#### Examples

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
