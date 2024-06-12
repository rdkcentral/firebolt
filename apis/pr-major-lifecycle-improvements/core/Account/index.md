---
title: Account

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Account Module

---

Version Account 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [id](#id)
  - [uid](#uid)
- [Types](#types)

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

Capabilities:

| Role | Capability                         |
| ---- | ---------------------------------- |
| uses | xrn:firebolt:capability:account:id |

#### Examples

---

### uid

Gets a unique id for the current app & account

To get the value of `uid` call the method like this:

```typescript
function uid(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:account:uid |

#### Examples

---

## Types
