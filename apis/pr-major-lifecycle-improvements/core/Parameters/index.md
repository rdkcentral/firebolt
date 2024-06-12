---
title: Parameters

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Parameters Module

---

Version Parameters 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [initialization](#initialization)
- [Types](#types)
  - [AppInitialization](#appinitialization)

## Usage

To use the Parameters module, you can import it into your project from the Firebolt SDK:

```javascript
import { Parameters } from '@firebolt-js/sdk'
```

## Overview

Methods for getting initialization parameters for an app cold launch.

## Methods

### initialization

Returns any initialization parameters for the app, e.g. initialial `NavigationIntent`.

```typescript
function initialization(): Promise<AppInitialization>
```

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

---

## Types

### AppInitialization

```typescript
type AppInitialization = {
  us_privacy?: string // The IAB US Privacy string.
  lmt?: number // The IAB limit ad tracking opt out value.
  discovery?: object
  secondScreen?: object
}
```

See also:

Intents.NavigationIntent
SecondScreen.SecondScreenEvent

---
