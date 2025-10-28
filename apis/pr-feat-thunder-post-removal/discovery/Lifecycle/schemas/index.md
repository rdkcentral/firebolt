---
title: Lifecycle

version: pr-feat-thunder-post-removal
layout: default
sdk: discovery
---

# Lifecycle

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [CloseReason](#closereason)
  - [LifecycleState](#lifecyclestate)

## Types

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
