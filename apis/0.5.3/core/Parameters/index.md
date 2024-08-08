---
title: Parameters

version: 0.5.3
layout: default
sdk: core
---

# Parameters Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [parameters.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/parameters.json) |


## Table of Contents
- [Parameters Module](#parameters-module)
  - [OpenRPC](#openrpc)
  - [Table of Contents](#table-of-contents)
  - [Usage](#usage)
  - [Overview](#overview)
  - [Events](#events)
  - [Methods](#methods)
    - [initialization](#initialization)
      - [Promise Resolution](#promise-resolution)
      - [Examples](#examples)
        - [Default Example](#default-example)
          - [Request](#request)
          - [Response](#response)
  - [Schemas](#schemas)
    - [AppInitialization](#appinitialization)

<span></span>

## Usage
To use the Parameters module, you can import it into your project from the Firebolt SDK:

```javascript
import { Parameters } from '@firebolt-js/sdk'
```
## Overview
Methods for getting initialization parameters for an app cold launch.

## Events


## Methods
### initialization
Returns any initialization parameters for the app, e.g. initialial `NavigationIntent`.

```typescript
function initialization(): Promise<AppInitialization>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`AppInitialization`](#appinitialization) | The initialization parameters. |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Parameters } from '@firebolt-js/sdk'

Parameters.initialization()
    .then(init => {
        console.log(init)
    })
```
Value of `init`

```javascript
{
  "lmt": 0,
  "us_privacy": "1-Y-",
  "discovery": {
    "navigateTo": {
      "action": "entity",
      "data": {
        "entityId": "abc"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "parameters.initialization",
  "params": {}
}
```

###### Response

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
          "entityId": "abc"
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



## Schemas

### AppInitialization

```typescript
type AppInitialization = {
  us_privacy?: string                  // The IAB US Privacy string.
  lmt?: bigint                         // The IAB limit ad tracking opt out value.
  discovery?: {
    navigateTo?: NavigationIntent      // A Firebolt compliant representation of a user intention to navigate to a specific place in an app.
  }
  secondScreen?: {
    launchRequest?: SecondScreenEvent  // An a message notification from a second screen device
  }
}
```

See also: 

 - [NavigationIntent](../schemas/intents#/definitions/navigationintent)
 - [SecondScreenEvent](../schemas/secondscreen#/definitions/secondscreenevent)



---


