---
title: Advertising

version: 0.8.1
layout: default
sdk: core
---
# Advertising Schema
---
Version 0.8.1


## JSON-Schema
This document was generated from a JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [advertising.json](https://github.com/rdkcentral/firebolt-openrpc/blob/feature/badger-parity/src/schemas/advertising.json) |

## Table of Contents
 
 - Schemas
    - [SkipRestriction](#skiprestriction)


## Schemas

### SkipRestriction

```typescript
type SkipRestriction = 'none' | 'adsUnwatched' | 'adsAll' | 'all'
```




<details>
  <summary><b>Examples</b></summary>

```json
```

</details>


#### Details

The advertisement skip restriction.

Applies to fast-forward/rewind (e.g. trick mode), seeking over an entire opportunity (e.g. jump), seeking out of what's currently playing, and "Skip this ad..." features. Seeking over multiple ad opportunities only requires playback of the _last_ opportunity, not all opportunities, preceding the seek destination.

| Value        | Description                                                                    |
|--------------|--------------------------------------------------------------------------------|
| none         |No fast-forward, jump, or skip restrictions                                    |
| adsUnwatched | Restrict fast-forward, jump, and skip for unwatched ad opportunities only.     |
| adsAll       | Restrict fast-forward, jump, and skip for all ad opportunities                 |
| all          | Restrict fast-forward, jump, and skip for all ad opportunities and all content |

Namespace: `xrn:advertising:policy:skipRestriction:`




---


