---
title: Advertising

version: next-major
layout: default
sdk: manage
---

# Advertising Module

---

Version Advertising 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [resetIdentifier](#resetidentifier)
  - [skipRestriction](#skiprestriction)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [skipRestrictionChanged](#skiprestrictionchanged)
- [Types](#types)

## Usage

To use the Advertising module, you can import it into your project from the Firebolt SDK:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'
```

## Overview

A module for platform provided advertising settings and functionality.

## Methods

### resetIdentifier

Resets a user's identifier in the ad platform so that the advertising id that apps get will be a new value

```typescript
function resetIdentifier(): Promise<void>
```

Promise resolution:

Capabilities:

| Role    | Capability                                     |
| ------- | ---------------------------------------------- |
| manages | xrn:firebolt:capability:advertising:identifier |

#### Examples

---

### skipRestriction

Set the value for AdPolicy.skipRestriction

To get the value of `skipRestriction` call the method like this:

```typescript
function skipRestriction(): Promise<SkipRestriction>
```

Promise resolution:

Capabilities:

| Role    | Capability                                        |
| ------- | ------------------------------------------------- |
| manages | xrn:firebolt:capability:advertising:configuration |

#### Examples

---

To set the value of `skipRestriction` call the method like this:

```typescript
function skipRestriction(value: SkipRestriction): Promise<void>
```

Parameters:

| Param   | Type              | Required | Description |
| ------- | ----------------- | -------- | ----------- |
| `value` | `SkipRestriction` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function skipRestriction(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### skipRestrictionChanged

```typescript
function listen('skipRestrictionChanged', (SkipRestriction) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role    | Capability                                        |
| ------- | ------------------------------------------------- |
| manages | xrn:firebolt:capability:advertising:configuration |

#### Examples

---

## Types
