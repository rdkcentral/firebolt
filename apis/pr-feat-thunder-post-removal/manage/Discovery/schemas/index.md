---
title: Discovery

version: pr-feat-thunder-post-removal
layout: default
sdk: manage
---

# Discovery

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [InterestType](#interesttype)
  - [InterestReason](#interestreason)
  - [EntityInfoResult](#entityinforesult)
  - [PurchasedContentResult](#purchasedcontentresult)

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
  expires: string
  entity: EntityInfo // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  related?: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

---

### PurchasedContentResult

```typescript
type PurchasedContentResult = {
  expires: string
  totalCount: number
  entries: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

---
