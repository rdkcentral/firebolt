---
title: Accessibility

version: next-major
layout: default
sdk: core
---

# Accessibility Module

---

Version Accessibility 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audioDescriptionSettings](#audiodescriptionsettings)
  - [closedCaptions](#closedcaptions)
  - [closedCaptionsSettings](#closedcaptionssettings)
  - [voiceGuidance](#voiceguidance)
  - [voiceGuidanceSettings](#voiceguidancesettings)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [audioDescriptionSettingsChanged](#audiodescriptionsettingschanged)
  - [closedCaptionsSettingsChanged](#closedcaptionssettingschanged)
  - [voiceGuidanceSettingsChanged](#voiceguidancesettingschanged)
- [Types](#types)
  - [AudioDescriptionSettings](#audiodescriptionsettings-1)

## Usage

To use the Accessibility module, you can import it into your project from the Firebolt SDK:

```javascript
import { Accessibility } from '@firebolt-js/sdk'
```

## Overview

The `Accessibility` module provides access to the user/device settings for closed captioning and voice guidance.

Apps **SHOULD** attempt o respect these settings, rather than manage and persist seprate settings, which would be different per-app.

## Methods

### audioDescriptionSettings

Get the user's preferred audio description settings

To get the value of `audioDescriptionSettings` call the method like this:

```typescript
function audioDescriptionSettings(): Promise<AudioDescriptionSettings>
```

Promise resolution:

Capabilities:

| Role | Capability                                              |
| ---- | ------------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:audiodescriptions |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audioDescriptionSettings(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### closedCaptions

Get the user's preferred closed-captions settings

```typescript
function closedCaptions(): Promise<ClosedCaptionsSettings>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### closedCaptionsSettings

Get the user's preferred closed-captions settings

To get the value of `closedCaptionsSettings` call the method like this:

```typescript
function closedCaptionsSettings(): Promise<ClosedCaptionsSettings>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function closedCaptionsSettings(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### voiceGuidance

Get the user's preferred voice guidance settings

```typescript
function voiceGuidance(): Promise<VoiceGuidanceSettings>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

### voiceGuidanceSettings

Get the user's preferred voice guidance settings

To get the value of `voiceGuidanceSettings` call the method like this:

```typescript
function voiceGuidanceSettings(): Promise<VoiceGuidanceSettings>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function voiceGuidanceSettings(callback: (value) => null): Promise<number>
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

| Type     | Description                                                                                           |
| -------- | ----------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### audioDescriptionSettingsChanged

```typescript
function listen('audioDescriptionSettingsChanged', (AudioDescriptionSettings) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                              |
| ---- | ------------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:audiodescriptions |

#### Examples

---

### closedCaptionsSettingsChanged

```typescript
function listen('closedCaptionsSettingsChanged', (ClosedCaptionsSettings) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### voiceGuidanceSettingsChanged

```typescript
function listen('voiceGuidanceSettingsChanged', (VoiceGuidanceSettings) => void): Promise<number>
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

### AudioDescriptionSettings

```typescript
type AudioDescriptionSettings = {
  enabled: boolean // Whether or not audio descriptions should be enabled by default
}
```

---
