---
title: SecondScreen

version: 1.6.0
layout: default
sdk: manage
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
