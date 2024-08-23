---
title: SecondScreen

version: pr-app-passthrough-additions
layout: default
sdk: discovery
---

# SecondScreen

---

Version SecondScreen 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [SecondScreenEvent](#secondscreenevent)

## Overview

undefined

## Types

### SecondScreenEvent

An a message notification from a second screen device

```typescript
type SecondScreenEvent = {
  TYPE: 'dial'
  VERSION?: string
  DATA?: string
}
```

---
