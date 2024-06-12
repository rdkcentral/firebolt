---
title: VoiceGuidance

version: next-major
layout: default
sdk: manage
---

# VoiceGuidance Module

---

Version VoiceGuidance 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [enabled](#enabled)
  - [speed](#speed)
- [Events](#events)
  - [enabledChanged](#enabledchanged)
  - [speedChanged](#speedchanged)
- [Types](#types)

## Usage

To use the VoiceGuidance module, you can import it into your project from the Firebolt SDK:

```javascript
import { VoiceGuidance } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing voice-guidance Settings.

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `VoiceGuidance.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### enabled

Whether or not voice-guidance is enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

To set the value of `enabled` call the method like this:

```typescript
function enabled(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function enabled(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### speed

The speed at which voice guidance speech will be read back to the user.

To get the value of `speed` call the method like this:

```typescript
function speed(): Promise<Accessibility.VoiceSpeed>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

To set the value of `speed` call the method like this:

```typescript
function speed(value: Accessibility.VoiceSpeed): Promise<void>
```

Parameters:

| Param   | Type                       | Required | Description |
| ------- | -------------------------- | -------- | ----------- |
| `value` | `Accessibility.VoiceSpeed` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function speed(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

## Events

### enabledChanged

```typescript
function listen('enabledChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

### speedChanged

```typescript
function listen('speedChanged', (Accessibility.VoiceSpeed) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

## Types
