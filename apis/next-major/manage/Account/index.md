---
title: Account

version: next-major
layout: default
sdk: manage
---

# Account Module

---

Version Account 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [session](#session)
- [Types](#types)

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

Capabilities:

| Role    | Capability                            |
| ------- | ------------------------------------- |
| manages | xrn:firebolt:capability:token:account |

#### Examples

---

## Types
