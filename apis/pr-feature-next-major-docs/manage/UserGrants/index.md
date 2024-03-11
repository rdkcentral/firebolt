---
title: UserGrants

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# UserGrants Module

---

Version UserGrants 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [app](#app)
  - [capability](#capability)
  - [clear](#clear)
  - [deny](#deny)
  - [device](#device)
  - [grant](#grant)
  - [request](#request)
- [Types](#types)
  - [AppInfo](#appinfo)
  - [GrantModificationOptions](#grantmodificationoptions)
  - [RequestOptions](#requestoptions)
  - [GrantState](#grantstate)
  - [GrantInfo](#grantinfo)

## Usage

To use the UserGrants module, you can import it into your project from the Firebolt SDK:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing grants given by the user

## Methods

### app

Get all granted and denied user grants for the given app

```typescript
function app(appId: string): Promise<object[]>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `appId` | `string` | true     |             |

Promise resolution:

```typescript
object[]
```

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.app('certapp')
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: {
      id: 'certapp',
      title: 'Firebolt Certification',
    },
    state: 'granted',
    capability: 'xrn:firebolt:capability:data:app-usage',
    role: 'use',
    lifespan: 'seconds',
    expires: '2022-12-14T20:20:39+00:00',
  },
  {
    app: {
      id: 'certapp',
      title: 'Firebolt Certification',
    },
    state: 'denied',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'appActive',
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "UserGrants.app",
  "params": {
    "appId": "certapp"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "app": {
        "id": "certapp",
        "title": "Firebolt Certification"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:data:app-usage",
      "role": "use",
      "lifespan": "seconds",
      "expires": "2022-12-14T20:20:39+00:00"
    },
    {
      "app": {
        "id": "certapp",
        "title": "Firebolt Certification"
      },
      "state": "denied",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "appActive"
    }
  ]
}
```

</details>

---

### capability

Get all granted and denied user grants for the given capability

```typescript
function capability(capability: Capability): Promise<object[]>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Promise resolution:

```typescript
object[]
```

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.capability(
  'xrn:firebolt:capability:localization:postal-code',
)
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "UserGrants.capability",
  "params": {
    "capability": "xrn:firebolt:capability:localization:postal-code"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

### clear

Clears the grant for a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function clear(
  role: Role,
  capability: Capability,
  options?: object,
): Promise<void>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | [`Role`](../Capabilities/schemas/#Role)             | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                                            | false    |                                                                        |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.clear(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
console.log(result)
```

Value of `result`:

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
  "method": "UserGrants.clear",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### deny

Denies a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function deny(
  role: Role,
  capability: Capability,
  options?: object,
): Promise<void>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | [`Role`](../Capabilities/schemas/#Role)             | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                                            | false    |                                                                        |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.deny(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
console.log(result)
```

Value of `result`:

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
  "method": "UserGrants.deny",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### device

Get all granted and denied user grants for the device

```typescript
function device(): Promise<object[]>
```

Promise resolution:

```typescript
object[]
```

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.device()
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "UserGrants.device",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

### grant

Grants a given capability to a specific app, if appropriate. Calling this results in a persisted active grant that lasts for the duration of the grant policy lifespan.

```typescript
function grant(
  role: Role,
  capability: Capability,
  options?: object,
): Promise<void>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | [`Role`](../Capabilities/schemas/#Role)             | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                                            | false    |                                                                        |

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.grant(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
console.log(result)
```

Value of `result`:

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
  "method": "UserGrants.grant",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### request

Requests Firebolt to carry out a set of user grants for a given application such that the user grant provider is notified or an existing user grant is reused.

```typescript
function request(
  appId: string,
  permissions: Permission[],
  options?: RequestOptions,
): Promise<object[]>
```

Parameters:

| Param         | Type                                | Required | Description     |
| ------------- | ----------------------------------- | -------- | --------------- |
| `appId`       | `string`                            | true     |                 |
| `permissions` | `Permission[]`                      | true     |                 |
| `options`     | [`RequestOptions`](#requestoptions) | false    | Request options |

Promise resolution:

```typescript
object[]
```

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default result #1

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.request(
  'certapp',
  [
    {
      role: 'use',
      capability: 'xrn:firebolt:capability:localization:postal-code',
    },
  ],
  null,
)
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: {
      id: 'certapp',
      title: 'Certification App',
    },
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "UserGrants.request",
  "params": {
    "appId": "certapp",
    "permissions": [
      {
        "role": "use",
        "capability": "xrn:firebolt:capability:localization:postal-code"
      }
    ]
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "app": {
        "id": "certapp",
        "title": "Certification App"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

Default result #2

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.request(
  'certapp',
  [
    {
      role: 'use',
      capability: 'xrn:firebolt:capability:localization:postal-code',
    },
  ],
  {
    force: true,
  },
)
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: {
      id: 'certapp',
      title: 'Certification App',
    },
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "UserGrants.request",
  "params": {
    "appId": "certapp",
    "permissions": [
      {
        "role": "use",
        "capability": "xrn:firebolt:capability:localization:postal-code"
      }
    ],
    "options": {
      "force": true
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "app": {
        "id": "certapp",
        "title": "Certification App"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

## Types

### AppInfo

Information about an app that a grant was for

```typescript
type AppInfo = {
  id: string
  title?: string
}
```

---

### GrantModificationOptions

Options when modifying any grant

```typescript
type GrantModificationOptions = {
  appId?: string
}
```

---

### RequestOptions

```typescript
type RequestOptions = {
  force?: boolean // Whether to force for user grant even if the previous decision stored
}
```

---

### GrantState

The state the grant is in

```typescript
enum GrantState {
  GRANTED = 'granted',
  DENIED = 'denied',
}
```

---

### GrantInfo

Information about a grant given by a user

```typescript
type GrantInfo = {
  app?: {
    id: string
    title?: string
  }
  state: 'granted' | 'denied' // The state the grant is in
  capability: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
  role: Role // Role provides access level for the app for a given capability.
  lifespan: 'once' | 'forever' | 'appActive' | 'powerActive' | 'seconds'
  expires?: string
}
```

See also:

string
'use' | 'manage' | 'provide'

---
