---
title: Metrics

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# Metrics Module

---

Version Metrics 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [event](#event)
- [Types](#types)
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [EventObject](#eventobject)

## Usage

To use the Metrics module, you can import it into your project from the Firebolt SDK:

```javascript
import { Metrics } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for sending metrics

## Methods

### event

Inform the platform of 1st party distributor metrics.

```typescript
function event(schema: string, data: EventObject): Promise<null>
```

Parameters:

| Param    | Type          | Required | Description                                        |
| -------- | ------------- | -------- | -------------------------------------------------- |
| `schema` | `string`      | true     | The schema URI of the metric type <br/>format: uri |
| `data`   | `EventObject` | true     | A JSON payload conforming the the provided schema  |

Promise resolution:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:metrics:distributor |

#### Examples

---

## Types

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### EventObject

```typescript
type EventObject = {}
```

See also:

EventObjectPrimitives
EventObject

---
