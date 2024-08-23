---
title: Discovery

version: pr-trigger-build
layout: default
sdk: discovery
---

# Discovery

---

Version Discovery 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [InterestType](#interesttype)
  - [InterestReason](#interestreason)
  - [EntityInfoResult](#entityinforesult)
  - [PurchasedContentResult](#purchasedcontentresult)

## Overview

undefined

## Types

### InterestType

```typescript
InterestType: {
    INTEREST: 'interest',
    DISINTEREST: 'disinterest',
},

```

---

### InterestReason

```typescript
InterestReason: {
    PLAYLIST: 'playlist',
    REACTION: 'reaction',
    RECORDING: 'recording',
},

```

---

### EntityInfoResult

The result for an `entityInfo()` push or pull.

```typescript
type EntityInfoResult = {
  EXPIRES: string
  ENTITY: EntityInfo // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  RELATED?: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

---

### PurchasedContentResult

```typescript
type PurchasedContentResult = {
  EXPIRES: string
  TOTAL_COUNT: number
  ENTRIES: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

---
