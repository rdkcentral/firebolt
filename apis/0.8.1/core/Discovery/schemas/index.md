---
title: Discovery

version: 0.8.1
layout: default
sdk: core
---
# Discovery Schema
---
Version 0.8.1


## JSON-Schema
This document was generated from a JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [discovery.json](https://github.com/rdkcentral/firebolt-openrpc/blob/feature/badger-parity/src/schemas/discovery.json) |

## Table of Contents
 
 - Schemas
    - [PurchasedContentResult](#purchasedcontentresult)
    - [EntityInfoResult](#entityinforesult)


## Schemas

### PurchasedContentResult

```typescript
type PurchasedContentResult = {
  expires: string
  totalCount: number
  entries: EntityInfo[]
}
```

See also: 

 - [EntityInfo](../Entertainment/schemas/#entityinfo)






---

### EntityInfoResult

```typescript
type EntityInfoResult = {
  expires: string
  entity: EntityInfo       // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  related?: EntityInfo[]
}
```

See also: 

 - [EntityInfo](../Entertainment/schemas/#entityinfo)




#### Details

The result for an `entityInfo()` push or pull.


---


