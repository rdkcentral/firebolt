---
title: Capabilities

version: pr-fix-ci-coverage-report-compilation
layout: default
sdk: manage
---

# Capabilities

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [Capability](#capability)
  - [CapPermissionStatus](#cappermissionstatus)
  - [CapabilityInfo](#capabilityinfo)
  - [Permission](#permission)

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
type Capability = string
```

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean
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
    granted?: boolean
  }
  manage: {
    permitted?: boolean // Provides info whether the capability is permitted
    granted?: boolean
  }
  provide: {
    permitted?: boolean // Provides info whether the capability is permitted
    granted?: boolean
  }
  details?: DenyReason[] // Reasons why a Capability might not be invokable
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
  role?: Role // Role provides access level for the app for a given capability.
  capability: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
}
```

See also:

[Role](#role)
[Capability](#capability)

---
