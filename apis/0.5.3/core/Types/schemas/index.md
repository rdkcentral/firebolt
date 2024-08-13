---
title: Types

version: 0.5.3
layout: default
sdk: core
---
# Types Schema
---
Version 0.5.3


## JSON-Schema
This document was generated from a JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [types.json](https://github.com/rdkcentral/firebolt-openrpc/blob/feature/badger-parity/src/schemas/types.json) |

## Table of Contents
 
 - Schemas
    - [SemanticVersion](#semanticversion)
    - [AudioProfile](#audioprofile)
    - [BooleanMap](#booleanmap)
    - [FlatMap](#flatmap)
    - [LocalizedString](#localizedstring)
    - [ListenResponse](#listenresponse)

## Schemas

### SemanticVersion

```typescript
type SemanticVersion = {
  major: bigint
  minor: bigint
  patch: bigint
  readable: string
}
```




<details markdown="1" >
<summary>Examples:</summary>

```json
```

</details>

---

### AudioProfile

```typescript
type AudioProfile = 'stereo' | 'dolbyDigital5.1' | 'dolbyDigital7.1' | 'dolbyDigital5.1+' | 'dolbyDigital7.1+' | 'dolbyAtmos'
```




<details markdown="1" >
<summary>Examples:</summary>

```json
```

</details>

---

### BooleanMap

```typescript
type BooleanMap = {
}
```




<details markdown="1" >
<summary>Examples:</summary>

```json
```

</details>

---

### FlatMap

```typescript
type FlatMap = {
}
```




<details markdown="1" >
<summary>Examples:</summary>

```json
```

</details>

---

### LocalizedString

```typescript
type LocalizedString = string | object
```




<details markdown="1" >
<summary>Examples:</summary>

```json
"A simple string, with no language code"

{
  "en": "This is english",
  "es": "esto es español"
}
```

</details>

#### Details

Localized string supports either a simple `string` or a Map<string, string> of language codes to strings. When using a simple `string`, the current preferred langauge from `Localization.langauge()` is assumed.

---

### ListenResponse

```typescript
type ListenResponse = {
  event: string
  listening: boolean
}
```




<details markdown="1" >
<summary>Examples:</summary>

```json
```

</details>

---


