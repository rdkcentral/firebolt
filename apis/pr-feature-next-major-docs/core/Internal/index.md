---
title: Internal

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Internal Module

---

Version Internal 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Methods](#methods)
  - [initialize](#initialize)

## Overview

Internal methods for SDK / FEE integration

## Methods

### initialize

_This is an private RPC method._

Initialize the SDK / FEE session.

Parameters:

| Param     | Type                                                   | Required | Description                      |
| --------- | ------------------------------------------------------ | -------- | -------------------------------- |
| `version` | [`SemanticVersion`](../Types/schemas/#SemanticVersion) | true     | The semantic version of the SDK. |

Result:

| Property  | Type                                                 | Description                      |
| --------- | ---------------------------------------------------- | -------------------------------- |
| `version` | [SemanticVersion](../Types/schemas/#SemanticVersion) | The semantic version of the FEE. |

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:initialize |

#### Examples

Default Example

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Internal.initialize",
  "params": {
    "version": {
      "major": 1,
      "minor": 0,
      "patch": 0,
      "readable": "Firebolt SDK 1.0.0"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "version": {
      "major": 1,
      "minor": 0,
      "patch": 0,
      "readable": "Firebolt FEE 1.0.0"
    }
  }
}
```

---
