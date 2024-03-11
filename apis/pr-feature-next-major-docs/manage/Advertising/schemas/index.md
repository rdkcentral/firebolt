---
title: Advertising

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Advertising

---

Version Advertising 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [SkipRestriction](#skiprestriction)

## Overview

undefined

## Types

### SkipRestriction

The advertisement skip restriction.

Applies to fast-forward/rewind (e.g. trick mode), seeking over an entire opportunity (e.g. jump), seeking out of what's currently playing, and "Skip this ad..." features. Seeking over multiple ad opportunities only requires playback of the _last_ opportunity, not all opportunities, preceding the seek destination.

| Value        | Description                                                                    |
| ------------ | ------------------------------------------------------------------------------ |
| none         | No fast-forward, jump, or skip restrictions                                    |
| adsUnwatched | Restrict fast-forward, jump, and skip for unwatched ad opportunities only.     |
| adsAll       | Restrict fast-forward, jump, and skip for all ad opportunities                 |
| all          | Restrict fast-forward, jump, and skip for all ad opportunities and all content |

Namespace: `xrn:advertising:policy:skipRestriction:`

```typescript
enum SkipRestriction {
  NONE = 'none',
  ADS_UNWATCHED = 'adsUnwatched',
  ADS_ALL = 'adsAll',
  ALL = 'all',
}
```

---
