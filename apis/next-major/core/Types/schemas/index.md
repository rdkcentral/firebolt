---
title: Types

version: next-major
layout: default
sdk: core
---

# Types

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [AudioProfile](#audioprofile)
  - [SemanticVersion](#semanticversion)
  - [BooleanMap](#booleanmap)
  - [FlatMap](#flatmap)
  - [LocalizedString](#localizedstring)

## Types

### AudioProfile

```typescript
AudioProfile: {
    STEREO: 'stereo',
    DOLBY_DIGITAL_5_1: 'dolbyDigital5.1',
    DOLBY_DIGITAL_5_1_PLUS: 'dolbyDigital5.1+',
    DOLBY_ATMOS: 'dolbyAtmos',
},

```

---

### SemanticVersion

```typescript
type SemanticVersion = {
  major: number
  minor: number
  patch: number
  readable: string
}
```

---

### BooleanMap

```typescript
type BooleanMap = [property: string]: boolean
```

---

### FlatMap

```typescript
type FlatMap = [property: string]: string | number | boolean
```

---

### LocalizedString

Localized string supports either a simple `string` or a Map<string, string> of language codes to strings. When using a simple `string`, the current preferred langauge from `Localization.langauge()` is assumed.

```typescript
type LocalizedString = string | object
```

---
