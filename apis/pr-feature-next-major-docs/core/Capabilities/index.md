---
title: Capabilities

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Capabilities Module

---

Version Capabilities 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [available](#available)
  - [granted](#granted)
  - [info](#info)
  - [listen](#listen)
  - [once](#once)
  - [permitted](#permitted)
  - [request](#request)
  - [supported](#supported)
- [Events](#events)
  - [available](#available-1)
  - [granted](#granted-1)
  - [revoked](#revoked)
  - [unavailable](#unavailable)
- [Types](#types)
  - [CapabilityOption](#capabilityoption)

## Usage

To use the Capabilities module, you can import it into your project from the Firebolt SDK:

```javascript
import { Capabilities } from '@firebolt-js/sdk'
```

## Overview

The Capabilities module provides information about which discreet unit of functionality is enabled for the apps.

## Methods

### available

Returns whether a capability is available now.

```typescript
function available(capability: Capability): Promise<boolean>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Device Token.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let available = await Capabilities.available(
  'xrn:firebolt:capability:token:device',
)
console.log(available)
```

Value of `available`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.available",
  "params": {
    "capability": "xrn:firebolt:capability:token:device"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Unavailable Platform token.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let available = await Capabilities.available(
  'xrn:firebolt:capability:token:platform',
)
console.log(available)
```

Value of `available`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.available",
  "params": {
    "capability": "xrn:firebolt:capability:token:platform"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>

---

### granted

Returns whether the current App has a user grant for passed capability and role.

```typescript
function granted(
  capability: Capability,
  options?: CapabilityOption,
): Promise<boolean | void>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | [`CapabilityOption`](#capabilityoption)             | false    | Capability options                                                     |

Promise resolution:

```typescript
boolean | void
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Default capabilities without grants.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let granted = await Capabilities.granted(
  'xrn:firebolt:capability:input:keyboard',
  null,
)
console.log(granted)
```

Value of `granted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.granted",
  "params": {
    "capability": "xrn:firebolt:capability:input:keyboard"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Get Postal code without grants.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let granted = await Capabilities.granted(
  'xrn:firebolt:capability:localization:postal-code',
  null,
)
console.log(granted)
```

Value of `granted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.granted",
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
  "result": false
}
```

</details>

Get Postal code with grants.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let granted = await Capabilities.granted(
  'xrn:firebolt:capability:localization:postal-code',
  null,
)
console.log(granted)
```

Value of `granted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.granted",
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
  "result": null
}
```

</details>

---

### info

Returns an array of CapabilityInfo objects for the passed in capabilities.

```typescript
function info(capabilities: Capability[]): Promise<CapabilityInfo[]>
```

Parameters:

| Param          | Type           | Required | Description                                                            |
| -------------- | -------------- | -------- | ---------------------------------------------------------------------- |
| `capabilities` | `Capability[]` | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Promise resolution:

```typescript
CapabilityInfo[]
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Default result

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let info = await Capabilities.info([
  'xrn:firebolt:capability:device:model',
  'xrn:firebolt:capability:input:keyboard',
  'xrn:firebolt:capability:protocol:bluetoothle',
  'xrn:firebolt:capability:token:device',
  'xrn:firebolt:capability:token:platform',
  'xrn:firebolt:capability:protocol:moca',
  'xrn:firebolt:capability:wifi:scan',
  'xrn:firebolt:capability:localization:postal-code',
  'xrn:firebolt:capability:localization:locality',
])
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    capability: 'xrn:firebolt:capability:device:model',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
  },
  {
    capability: 'xrn:firebolt:capability:input:keyboard',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
  },
  {
    capability: 'xrn:firebolt:capability:protocol:bluetoothle',
    supported: false,
    available: false,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['unsupported'],
  },
  {
    capability: 'xrn:firebolt:capability:token:device',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
  },
  {
    capability: 'xrn:firebolt:capability:token:platform',
    supported: true,
    available: false,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['unavailable'],
  },
  {
    capability: 'xrn:firebolt:capability:protocol:moca',
    supported: true,
    available: false,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['disabled', 'unavailable'],
  },
  {
    capability: 'xrn:firebolt:capability:wifi:scan',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['unpermitted'],
  },
  {
    capability: 'xrn:firebolt:capability:localization:postal-code',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: null,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['ungranted'],
  },
  {
    capability: 'xrn:firebolt:capability:localization:postal-code',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['ungranted'],
  },
  {
    capability: 'xrn:firebolt:capability:localization:locality',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
    details: ['grantDenied', 'ungranted'],
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
  "method": "Capabilities.info",
  "params": {
    "capabilities": [
      "xrn:firebolt:capability:device:model",
      "xrn:firebolt:capability:input:keyboard",
      "xrn:firebolt:capability:protocol:bluetoothle",
      "xrn:firebolt:capability:token:device",
      "xrn:firebolt:capability:token:platform",
      "xrn:firebolt:capability:protocol:moca",
      "xrn:firebolt:capability:wifi:scan",
      "xrn:firebolt:capability:localization:postal-code",
      "xrn:firebolt:capability:localization:locality"
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
      "capability": "xrn:firebolt:capability:device:model",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      }
    },
    {
      "capability": "xrn:firebolt:capability:input:keyboard",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      }
    },
    {
      "capability": "xrn:firebolt:capability:protocol:bluetoothle",
      "supported": false,
      "available": false,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["unsupported"]
    },
    {
      "capability": "xrn:firebolt:capability:token:device",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      }
    },
    {
      "capability": "xrn:firebolt:capability:token:platform",
      "supported": true,
      "available": false,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["unavailable"]
    },
    {
      "capability": "xrn:firebolt:capability:protocol:moca",
      "supported": true,
      "available": false,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["disabled", "unavailable"]
    },
    {
      "capability": "xrn:firebolt:capability:wifi:scan",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["unpermitted"]
    },
    {
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": null
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["ungranted"]
    },
    {
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["ungranted"]
    },
    {
      "capability": "xrn:firebolt:capability:localization:locality",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      },
      "details": ["grantDenied", "ungranted"]
    }
  ]
}
```

</details>

---

### listen

To listen to a specific event pass the event name as the first parameter:

```typescript
listen(event: string, callback: (data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Capabilities.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Capabilities.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
```

The `once` method will only pass the next instance of this event, and then dicard the listener you provided.

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Capabilities.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Capabilities.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### permitted

Returns whether the current App has permission to the passed capability and role.

```typescript
function permitted(
  capability: Capability,
  options?: CapabilityOption,
): Promise<boolean>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | [`CapabilityOption`](#capabilityoption)             | false    | Capability options                                                     |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Keyboard

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let permitted = await Capabilities.permitted(
  'xrn:firebolt:capability:input:keyboard',
  null,
)
console.log(permitted)
```

Value of `permitted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.permitted",
  "params": {
    "capability": "xrn:firebolt:capability:input:keyboard"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Keyboard incorrect manage role capability

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let permitted = await Capabilities.permitted(
  'xrn:firebolt:capability:input:keyboard',
  { role: 'manage' },
)
console.log(permitted)
```

Value of `permitted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.permitted",
  "params": {
    "capability": "xrn:firebolt:capability:input:keyboard",
    "options": {
      "role": "manage"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>

Wifi scan not permitted capability

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let permitted = await Capabilities.permitted(
  'xrn:firebolt:capability:wifi:scan',
  null,
)
console.log(permitted)
```

Value of `permitted`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.permitted",
  "params": {
    "capability": "xrn:firebolt:capability:wifi:scan"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>

---

### request

Requests grants for all capability/role combinations in the roles array.

```typescript
function request(grants: Permission[]): Promise<CapabilityInfo[]>
```

Parameters:

| Param    | Type           | Required | Description |
| -------- | -------------- | -------- | ----------- |
| `grants` | `Permission[]` | true     |             |

Promise resolution:

```typescript
CapabilityInfo[]
```

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:request |

#### Examples

Default result

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let request = await Capabilities.request([
  { role: 'use', capability: 'xrn:firebolt:capability:commerce:purchase' },
])
console.log(request)
```

Value of `request`:

```javascript
;[
  {
    capability: 'xrn:firebolt:capability:commerce:purchase',
    supported: true,
    available: true,
    use: {
      permitted: true,
      granted: true,
    },
    manage: {
      permitted: true,
      granted: true,
    },
    provide: {
      permitted: true,
      granted: true,
    },
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
  "method": "Capabilities.request",
  "params": {
    "grants": [
      {
        "role": "use",
        "capability": "xrn:firebolt:capability:commerce:purchase"
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
      "capability": "xrn:firebolt:capability:commerce:purchase",
      "supported": true,
      "available": true,
      "use": {
        "permitted": true,
        "granted": true
      },
      "manage": {
        "permitted": true,
        "granted": true
      },
      "provide": {
        "permitted": true,
        "granted": true
      }
    }
  ]
}
```

</details>

---

### supported

Returns whether the platform supports the passed capability.

```typescript
function supported(capability: Capability): Promise<boolean>
```

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Wifi scan supported capability

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let supported = await Capabilities.supported(
  'xrn:firebolt:capability:wifi:scan',
)
console.log(supported)
```

Value of `supported`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.supported",
  "params": {
    "capability": "xrn:firebolt:capability:wifi:scan"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

BLE protocol unsupported capability

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

let supported = await Capabilities.supported(
  'xrn:firebolt:capability:protocol:bluetoothle',
)
console.log(supported)
```

Value of `supported`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.supported",
  "params": {
    "capability": "xrn:firebolt:capability:protocol:bluetoothle"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>

---

## Events

### available

```typescript
function listen('available', capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Event value:

[CapabilityInfo](../Capabilities/schemas/#CapabilityInfo)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Platform token is available

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

Capabilities.listen('available', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
{
	"capability": "xrn:firebolt:capability:token:platform",
	"supported": true,
	"available": true,
	"use": {
		"permitted": true,
		"granted": true
	},
	"manage": {
		"permitted": true,
		"granted": true
	},
	"provide": {
		"permitted": true,
		"granted": true
	},
	"details": [
		"unpermitted"
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.onAvailable",
  "params": {
    "capability": "xrn:firebolt:capability:token:platform",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "capability": "xrn:firebolt:capability:token:platform",
    "supported": true,
    "available": true,
    "use": {
      "permitted": true,
      "granted": true
    },
    "manage": {
      "permitted": true,
      "granted": true
    },
    "provide": {
      "permitted": true,
      "granted": true
    },
    "details": ["unpermitted"]
  }
}
```

</details>

---

### granted

```typescript
function listen('granted', role: Role, capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | [`Role`](../Capabilities/schemas/#Role)             | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Event value:

[CapabilityInfo](../Capabilities/schemas/#CapabilityInfo)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Postal code granted

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

Capabilities.listen('granted', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
{
	"capability": "xrn:firebolt:capability:localization:postal-code",
	"supported": true,
	"available": true,
	"use": {
		"permitted": true,
		"granted": true
	},
	"manage": {
		"permitted": true,
		"granted": true
	},
	"provide": {
		"permitted": true,
		"granted": true
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
  "method": "Capabilities.onGranted",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "supported": true,
    "available": true,
    "use": {
      "permitted": true,
      "granted": true
    },
    "manage": {
      "permitted": true,
      "granted": true
    },
    "provide": {
      "permitted": true,
      "granted": true
    }
  }
}
```

</details>

---

### revoked

```typescript
function listen('revoked', role: Role, capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | [`Role`](../Capabilities/schemas/#Role)             | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Event value:

[CapabilityInfo](../Capabilities/schemas/#CapabilityInfo)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Postal code revoked

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

Capabilities.listen('revoked', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
{
	"capability": "xrn:firebolt:capability:localization:postal-code",
	"supported": true,
	"available": true,
	"use": {
		"permitted": true,
		"granted": true
	},
	"manage": {
		"permitted": true,
		"granted": true
	},
	"provide": {
		"permitted": true,
		"granted": true
	},
	"details": [
		"grantDenied"
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.onRevoked",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "supported": true,
    "available": true,
    "use": {
      "permitted": true,
      "granted": true
    },
    "manage": {
      "permitted": true,
      "granted": true
    },
    "provide": {
      "permitted": true,
      "granted": true
    },
    "details": ["grantDenied"]
  }
}
```

</details>

---

### unavailable

```typescript
function listen('unavailable', capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type                                                | Required | Description                                                            |
| ------------ | --------------------------------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | [`Capability`](../Capabilities/schemas/#Capability) | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Event value:

[CapabilityInfo](../Capabilities/schemas/#CapabilityInfo)

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

Platform token is unavailable.

JavaScript:

```javascript
import { Capabilities } from '@firebolt-js/sdk'

Capabilities.listen('unavailable', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
{
	"capability": "xrn:firebolt:capability:token:platform",
	"supported": true,
	"available": false,
	"use": {
		"permitted": true,
		"granted": true
	},
	"manage": {
		"permitted": true,
		"granted": true
	},
	"provide": {
		"permitted": true,
		"granted": true
	},
	"details": [
		"unavailable"
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Capabilities.onUnavailable",
  "params": {
    "capability": "xrn:firebolt:capability:token:platform",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "capability": "xrn:firebolt:capability:token:platform",
    "supported": true,
    "available": false,
    "use": {
      "permitted": true,
      "granted": true
    },
    "manage": {
      "permitted": true,
      "granted": true
    },
    "provide": {
      "permitted": true,
      "granted": true
    },
    "details": ["unavailable"]
  }
}
```

</details>

---

## Types

### CapabilityOption

```typescript
type CapabilityOption = {
  role?: Role // Role provides access level for the app for a given capability.
}
```

See also:

'use' | 'manage' | 'provide'

---
