---
title: Capabilities

version: next-major
layout: default
sdk: manage
---

# Capabilities

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [Role](#role)
  - [Capability](#capability)
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

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

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
