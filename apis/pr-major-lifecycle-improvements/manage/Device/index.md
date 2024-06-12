---
title: Device

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# Device Module

---

Version Device 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [name](#name)
  - [provision](#provision)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [deviceNameChanged](#devicenamechanged)
  - [nameChanged](#namechanged)
- [Types](#types)

## Usage

To use the Device module, you can import it into your project from the Firebolt SDK:

```javascript
import { Device } from '@firebolt-js/manage-sdk'
```

## Overview

A module for querying about the device and it's capabilities.

## Methods

### name

The human readable name of the device

To get the value of `name` call the method like this:

```typescript
function name(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

---

To set the value of `name` call the method like this:

```typescript
function name(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description              |
| ------- | -------- | -------- | ------------------------ |
| `value` | `string` | true     | the device friendly-name |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function name(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### provision

Used by a distributor to push provision info to firebolt.

```typescript
function provision(
  accountId: string,
  deviceId: string,
  distributorId: string,
): Promise<void>
```

Parameters:

| Param           | Type     | Required | Description                                                             |
| --------------- | -------- | -------- | ----------------------------------------------------------------------- |
| `accountId`     | `string` | true     | The id of the account that is device is attached to in the back office. |
| `deviceId`      | `string` | true     | The id of the device in the back office.                                |
| `distributorId` | `string` | false    | The id of the distributor in the back office.                           |

Promise resolution:

Capabilities:

| Role    | Capability                                                                                                              |
| ------- | ----------------------------------------------------------------------------------------------------------------------- |
| manages | xrn:firebolt:capability:account:id<br/>xrn:firebolt:capability:device:id<br/>xrn:firebolt:capability:device:distributor |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### deviceNameChanged

```typescript
function listen('deviceNameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

---

### nameChanged

```typescript
function listen('nameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

---

## Types
