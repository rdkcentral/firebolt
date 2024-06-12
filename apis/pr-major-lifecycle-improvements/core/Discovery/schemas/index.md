---
title: Discovery

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Discovery

---

Version 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [InterestType](#interesttype)
  - [InterestReason](#interestreason)
  - [PurchasedContentResult](#purchasedcontentresult)
  - [EntityInfoResult](#entityinforesult)

## Overview

undefined

## Types

### InterestType

```typescript
enum InterestType {
  INTEREST = 'interest',
  DISINTEREST = 'disinterest',
}
```

---

### InterestReason

```typescript
enum InterestReason {
  PLAYLIST = 'playlist',
  REACTION = 'reaction',
  RECORDING = 'recording',
}
```

---

### PurchasedContentResult

```typescript
type PurchasedContentResult = {
  expires: string
  totalCount: number
  entries: Entertainment.EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

Entertainment.EntityInfo

---

### EntityInfoResult

The result for an `entityInfo()` push or pull.

```typescript
type EntityInfoResult = {
  expires: string
  entity: Entertainment.EntityInfo // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  related?: Entertainment.EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

Entertainment.EntityInfo

---
