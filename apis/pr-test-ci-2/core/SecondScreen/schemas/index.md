---
title: SecondScreen

version: pr-test-ci-2
layout: default
sdk: core
---

# SecondScreen

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [SecondScreenEvent](#secondscreenevent)

## Types

### SecondScreenEvent

An a message notification from a second screen device

```typescript
type SecondScreenEvent = {
  type: 'dial'
  version?: string
  data?: string
}
```

---