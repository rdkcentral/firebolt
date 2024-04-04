---
title: Lifecycle

version: pr-feature-media-access
layout: default
sdk: manage
---

# Lifecycle

---

Version Lifecycle 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [CloseReason](#closereason)
  - [LifecycleState](#lifecyclestate)

## Overview

undefined

## Types

### CloseReason

The application close reason

```typescript
CloseReason Enumeration:

| key | value |
|-----|-------|
| REMOTE_BUTTON | remoteButton |
| USER_EXIT | userExit |
| DONE | done |
| ERROR | error |

```

---

### LifecycleState

The application lifecycle state

```typescript
LifecycleState Enumeration:

| key | value |
|-----|-------|
| INITIALIZING | initializing |
| INACTIVE | inactive |
| FOREGROUND | foreground |
| BACKGROUND | background |
| UNLOADING | unloading |
| SUSPENDED | suspended |

```

---
