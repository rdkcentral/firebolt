---
title: Parameters

version: next
layout: default
sdk: core
---

# Parameters Module

---

Version Parameters 1.5.0-next.8

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

[AppInitialization](#appinitialization)

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

Default Example

JavaScript:

```javascript
import { Parameters } from '@firebolt-js/sdk'

let init = await Parameters.initialization()
console.log(init)
```

Value of `init`:

```javascript
{
	"lmt": 0,
	"us_privacy": "1-Y-",
	"discovery": {
		"navigateTo": {
			"action": "entity",
			"data": {
				"entityId": "abc",
				"entityType": "program",
				"programType": "movie"
			},
			"context": {
				"source": "voice"
			}
		}
	}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Parameters.initialization",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "lmt": 0,
    "us_privacy": "1-Y-",
    "discovery": {
      "navigateTo": {
        "action": "entity",
        "data": {
          "entityId": "abc",
          "entityType": "program",
          "programType": "movie"
        },
        "context": {
          "source": "voice"
        }
      }
    }
  }
}
```

</details>

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

[NavigationIntent](../Intents/schemas/#NavigationIntent)
[SecondScreenEvent](../SecondScreen/schemas/#SecondScreenEvent)

---
