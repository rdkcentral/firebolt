---
title: Capabilities

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Capabilities Module

---

Version Capabilities 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [available](#available)
  - [granted](#granted)
  - [info](#info)
  - [permitted](#permitted)
  - [request](#request)
  - [supported](#supported)
  - [listen](#listen)
  - [once](#once)
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

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `capability` | `Capability` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### granted

Returns whether the current App has a user grant for passed capability and role.

```typescript
function granted(
  capability: Capability,
  options: CapabilityOption,
): Promise<boolean>
```

Parameters:

| Param        | Type               | Required | Description        |
| ------------ | ------------------ | -------- | ------------------ |
| `capability` | `Capability`       | true     |                    |
| `options`    | `CapabilityOption` | false    | Capability options |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### info

Returns an array of CapabilityInfo objects for the passed in capabilities.

```typescript
function info(capabilities: Capability[]): Promise<CapabilityInfo[]>
```

Parameters:

| Param          | Type           | Required | Description |
| -------------- | -------------- | -------- | ----------- |
| `capabilities` | `Capability[]` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### permitted

Returns whether the current App has permission to the passed capability and role.

```typescript
function permitted(
  capability: Capability,
  options: CapabilityOption,
): Promise<boolean>
```

Parameters:

| Param        | Type               | Required | Description        |
| ------------ | ------------------ | -------- | ------------------ |
| `capability` | `Capability`       | true     |                    |
| `options`    | `CapabilityOption` | false    | Capability options |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

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

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:request |

#### Examples

---

### supported

Returns whether the platform supports the passed capability.

```typescript
function supported(capability: Capability): Promise<boolean>
```

Parameters:

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `capability` | `Capability` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

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

## Events

### available

```typescript
function listen('available', capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `capability` | `Capability` | true     |             |

Event value:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### granted

```typescript
function listen('granted', role: Role, capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `role`       | `Role`       | true     |             |
| `capability` | `Capability` | true     |             |

Event value:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### revoked

```typescript
function listen('revoked', role: Role, capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `role`       | `Role`       | true     |             |
| `capability` | `Capability` | true     |             |

Event value:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

### unavailable

```typescript
function listen('unavailable', capability: Capability, (CapabilityInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type         | Required | Description |
| ------------ | ------------ | -------- | ----------- |
| `capability` | `Capability` | true     |             |

Event value:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:capabilities:info |

#### Examples

---

## Types

### CapabilityOption

```typescript
type CapabilityOption = {
  role?: Role // Role provides access level for the app for a given capability.
}
```

See also:

Role

---
