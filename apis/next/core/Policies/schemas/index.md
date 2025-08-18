---
title: Policies

version: next
layout: default
sdk: core
---

# Policies

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [AgePolicy](#agepolicy)

## Types

### AgePolicy

The policy that describes various age groups to which content is directed. See distributor documentation for further details.

```typescript
type AgePolicy = string | 'app:adult' | 'app:child' | 'app:teen'
```

---
