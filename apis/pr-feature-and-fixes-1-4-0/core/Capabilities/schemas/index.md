---
title: Capabilities

version: pr-feature-and-fixes-1-4-0
layout: default
sdk: core
---

# Capabilities

---

Version Capabilities 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [Capability](#capability)
  - [CapPermissionStatus](#cappermissionstatus)
  - [CapabilityInfo](#capabilityinfo)
  - [Permission](#permission)

## Overview

undefined

## Types

### Role

Role provides access level for the app for a given capability.

```typescript
Role: {
    USE: 'use',
    MANAGE: 'manage',
    PROVIDE: 'provide',
},

```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
DenyReason: {
    UNPERMITTED: 'unpermitted',
    UNSUPPORTED: 'unsupported',
    DISABLED: 'disabled',
    UNAVAILABLE: 'unavailable',
    GRANT_DENIED: 'grantDenied',
    UNGRANTED: 'ungranted',
},

```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript

```

---

### CapPermissionStatus

```typescript

```

---

### CapabilityInfo

```typescript
type CapabilityInfo = {
  CAPABILITY?: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
  SUPPORTED: boolean // Provides info whether the capability is supported
  AVAILABLE: boolean // Provides info whether the capability is available
  USE: object
  MANAGE: object
  PROVIDE: object
  DETAILS?: DenyReason[] // Reasons why a Capability might not be invokable
}
```

See also:

[Capability](#capability)
[DenyReason](#denyreason)

---

### Permission

A capability combined with a Role, which an app may be permitted (by a distributor) or granted (by an end user).

```typescript
type Permission = {
  ROLE?: Role // Role provides access level for the app for a given capability.
  CAPABILITY: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
}
```

See also:

[Role](#role)
[Capability](#capability)

---
