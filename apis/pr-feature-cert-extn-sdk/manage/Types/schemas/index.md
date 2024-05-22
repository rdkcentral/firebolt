---
title: Types

version: pr-feature-cert-extn-sdk
layout: default
sdk: manage
---

# Types

---

Version Types 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [AudioProfile](#audioprofile)
  - [BooleanMap](#booleanmap)
  - [SemanticVersion](#semanticversion)
  - [LocalizedString](#localizedstring)
  - [FlatMap](#flatmap)
  - [Timeout](#timeout)

## Overview

undefined

## Types

### AudioProfile

```typescript
AudioProfile Enumeration:

| key | value |
|-----|-------|
| STEREO | stereo |
| DOLBY_DIGITAL_5_1 | dolbyDigital5.1 |
| DOLBY_DIGITAL_7_1 | dolbyDigital7.1 |
| DOLBY_DIGITAL_5_1_PLUS | dolbyDigital5.1+ |
| DOLBY_DIGITAL_7_1_PLUS | dolbyDigital7.1+ |
| DOLBY_ATMOS | dolbyAtmos |

```

---

### BooleanMap

````typescript
```typescript

````

````



---

### SemanticVersion



```typescript
```typescript

````

````



---

### LocalizedString

Localized string supports either a simple `string` or a Map<string, string> of language codes to strings. When using a simple `string`, the current preferred langauge from `Localization.langauge()` is assumed.

```typescript

````

---

### FlatMap

```typescript

```

---

### Timeout

Defines the timeout in seconds. If the threshold for timeout is passed for any operation without a result it will throw an error.

```typescript

```

---
