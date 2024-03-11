---
title: Capabilities

version: pr-feature-next-major-docs
layout: default
sdk: manage
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
enum Role {
  USE = 'use',
  MANAGE = 'manage',
  PROVIDE = 'provide',
}
```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
enum DenyReason {
  UNPERMITTED = 'unpermitted',
  UNSUPPORTED = 'unsupported',
  DISABLED = 'disabled',
  UNAVAILABLE = 'unavailable',
  GRANT_DENIED = 'grantDenied',
  UNGRANTED = 'ungranted',
}
```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean | void
}
```

---

### CapabilityInfo

```typescript
type CapabilityInfo = {
  capability?: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
  supported: boolean // Provides info whether the capability is supported
  available: boolean // Provides info whether the capability is available
  use: {
    permitted?: boolean // Provides info whether the capability is permitted
    granted?: boolean | void
  }
  manage: {
    permitted?: boolean // Provides info whether the capability is permitted
    granted?: boolean | void
  }
  provide: {
    permitted?: boolean // Provides info whether the capability is permitted
    granted?: boolean | void
  }
  details?: DenyReason[]
}
```

See also:

string
'unpermitted' | 'unsupported' | 'disabled' | 'unavailable' | 'grantDenied' | 'ungranted'

---

### Permission

A capability combined with a Role, which an app may be permitted (by a distributor) or granted (by an end user).

```typescript
type Permission = {
  role?: Role // Role provides access level for the app for a given capability.
  capability: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
}
```

See also:

'use' | 'manage' | 'provide'
string

---
