---
title: Lifecycle

version: next-major
layout: default
sdk: core
---

# Lifecycle

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [LifecycleState](#lifecyclestate)
  - [CloseReason](#closereason)

## Types

### LifecycleState

The application lifecycle state

```typescript
LifecycleState: {
    INITIALIZING: 'initializing',
    INACTIVE: 'inactive',
    FOREGROUND: 'foreground',
    BACKGROUND: 'background',
    UNLOADING: 'unloading',
    SUSPENDED: 'suspended',
},

```

---

### CloseReason

The application close reason

```typescript
CloseReason: {
    REMOTE_BUTTON: 'remoteButton',
    USER_EXIT: 'userExit',
    DONE: 'done',
    ERROR: 'error',
},

```

---
