---
title: Capabilities

version: pr-feature-user-interest
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
Role Enumeration:

| key | value |
|-----|-------|
| USE | use |
| MANAGE | manage |
| PROVIDE | provide |

```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
DenyReason Enumeration:

| key | value |
|-----|-------|
| UNPERMITTED | unpermitted |
| UNSUPPORTED | unsupported |
| DISABLED | disabled |
| UNAVAILABLE | unavailable |
| GRANT_DENIED | grantDenied |
| UNGRANTED | ungranted |

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

````typescript
```typescript

````

````

See also:




---

### Permission

A capability combined with a Role, which an app may be permitted (by a distributor) or granted (by an end user).

```typescript
```typescript

````

```

See also:




---
```
