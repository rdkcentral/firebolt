---
title: Metrics

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Metrics Module

---

Version Metrics 1.1.1-feature-next-major-docs.0

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

| Param    | Type                            | Required | Description                                        |
| -------- | ------------------------------- | -------- | -------------------------------------------------- |
| `schema` | `string`                        | true     | The schema URI of the metric type <br/>format: uri |
| `data`   | [`EventObject`](#eventobject-1) | true     | A JSON payload conforming the the provided schema  |

Promise resolution:

```typescript
null
```

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:metrics:distributor |

#### Examples

Send foo event

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/manage-sdk'

let results = await Metrics.event('http://meta.rdkcentral.com/some/schema', {
  foo: 'foo',
})
console.log(results)
```

Value of `results`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Metrics.event",
  "params": {
    "schema": "http://meta.rdkcentral.com/some/schema",
    "data": {
      "foo": "foo"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

---

## Types

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### EventObject

```typescript
type EventObject = {
  [property: string]:
    | EventObjectPrimitives
    | EventObjectPrimitives
    | EventObject[]
    | EventObject
}
```

See also:

string | number | number | boolean | null
[EventObject](#eventobject-1)

---
