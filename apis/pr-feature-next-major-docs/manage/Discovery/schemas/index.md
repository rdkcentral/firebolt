---
title: Discovery

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Discovery

---

Version Discovery 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [EntityInfoResult](#entityinforesult)
  - [PurchasedContentResult](#purchasedcontentresult)

## Overview

undefined

## Types

### EntityInfoResult

The result for an `entityInfo()` push or pull.

```typescript
type EntityInfoResult = {
  expires: string
  entity: EntityInfo // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  related?: EntityInfo[]
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
  entries: EntityInfo[]
}
```

See also:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

---
