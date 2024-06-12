---
title: SecondScreen

version: next-major
layout: default
sdk: core
---

# SecondScreen Module

---

Version SecondScreen 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [device](#device)
  - [friendlyName](#friendlyname)
  - [protocols](#protocols)
- [Events](#events)
  - [closeRequest](#closerequest)
  - [friendlyNameChanged](#friendlynamechanged)
  - [launchRequest](#launchrequest)
- [Types](#types)

## Usage

To use the SecondScreen module, you can import it into your project from the Firebolt SDK:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'
```

## Overview

Methods for communicating with second screen devices

## Methods

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### device

Get the broadcasted id for the device

```typescript
function device(type: string): Promise<string>
```

Parameters:

| Param  | Type     | Required | Description                                     |
| ------ | -------- | -------- | ----------------------------------------------- |
| `type` | `string` | false    | The type of second screen protocol, e.g. "dial" |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

---

### friendlyName

Get the broadcasted friendly name for the device

To get the value of `friendlyName` call the method like this:

```typescript
function friendlyName(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function friendlyName(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### protocols

Get the supported second screen discovery protocols

```typescript
function protocols(): Promise<Types.BooleanMap>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

## Events

### closeRequest

```typescript
function listen('closeRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

---

### friendlyNameChanged

```typescript
function listen('friendlyNameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

---

### launchRequest

```typescript
function listen('launchRequest', (SecondScreenEvent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:dial |

#### Examples

---

## Types
