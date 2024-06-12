---
title: Lifecycle

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Lifecycle

---

Version 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [LifecycleState](#lifecyclestate)
  - [CloseReason](#closereason)
  - [CreateParameters](#createparameters)

## Overview

undefined

## Types

### LifecycleState

The application lifecycle state

```typescript
enum LifecycleState {
  INITIALIZING = 'initializing',
  INACTIVE = 'inactive',
  FOREGROUND = 'foreground',
  BACKGROUND = 'background',
  UNLOADING = 'unloading',
  SUSPENDED = 'suspended',
}
```

---

### CloseReason

The application close reason

```typescript
enum CloseReason {
  REMOTE_BUTTON = 'remoteButton',
  USER_EXIT = 'userExit',
  DONE = 'done',
  ERROR = 'error',
}
```

---

### CreateParameters

A an object describing the initialization parameters passed to an app during the create method.

```typescript
type CreateParameters = {
  preload: boolean
  preloadReason?: 'boot' | 'restart' | 'user'
}
```

---
