---
title: Internal

version: pr-feat-change-initialization
layout: default
sdk: core
---

# Internal Module

---

Version Internal 1.8.0-feat-change-initialization.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Private Methods](#private-methods)<details markdown="1"  ontoggle="document.getElementById('private-methods-details').open=this.open"><summary>Show</summary>
  </details>
- [Types](#types)
  - [InitializeResult](#initializeresult)

## Overview

Internal methods for SDK / FEE integration

## Private Methods

<details markdown="1"  id="private-methods-details">
  <summary>View</summary>

### initialize

_This is a private RPC method._

Initialize the SDK / FEE session.

Parameters:

| Param     | Type                                                   | Required | Description                      |
| --------- | ------------------------------------------------------ | -------- | -------------------------------- |
| `version` | [`SemanticVersion`](../Types/schemas/#SemanticVersion) | true     | The semantic version of the SDK. |

Result:

[InitializeResult](#initializeresult)

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

</details>

## Types

### InitializeResult

```typescript
type InitializeResult = {
  version: SemanticVersion // The semantic version of the FEE.
}
```

See also:

[SemanticVersion](../Types/schemas/#SemanticVersion)

---
