---
title: Profile

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Profile Module

---

Version Profile 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [approveContentRating](#approvecontentrating)
  - [approvePurchase](#approvepurchase)
  - [flags](#flags)
- [Types](#types)

## Usage

To use the Profile module, you can import it into your project from the Firebolt SDK:

```javascript
import { Profile } from '@firebolt-js/sdk'
```

## Overview

Methods for getting information about the current user/account profile

## Methods

### approveContentRating

Verifies that the current profile should have access to mature/adult content.

```typescript
function approveContentRating(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:approve:content |

#### Examples

---

### approvePurchase

Verifies that the current profile should have access to making purchases.

```typescript
function approvePurchase(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:approve:purchase |

#### Examples

---

### flags

Get a map of profile flags for the current session.

```typescript
function flags(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:profile:flags |

#### Examples

---

## Types
