---
title: Discovery

version: next-major
layout: default
sdk: discovery
---

# Discovery

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [InterestType](#interesttype)
  - [InterestReason](#interestreason)
  - [InterestResult](#interestresult)

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

### InterestResult

```typescript
type InterestResult = {
  appId: string
  entity: EntityDetails
}
```

See also:

[Entity.EntityDetails](../Entity/schemas/#EntityDetails)

---
