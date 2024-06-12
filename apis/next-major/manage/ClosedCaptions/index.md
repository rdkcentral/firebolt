---
title: ClosedCaptions

version: next-major
layout: default
sdk: manage
---

# ClosedCaptions Module

---

Version ClosedCaptions 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [backgroundColor](#backgroundcolor)
  - [backgroundOpacity](#backgroundopacity)
  - [enabled](#enabled)
  - [fontColor](#fontcolor)
  - [fontEdge](#fontedge)
  - [fontEdgeColor](#fontedgecolor)
  - [fontFamily](#fontfamily)
  - [fontOpacity](#fontopacity)
  - [fontSize](#fontsize)
  - [preferredLanguages](#preferredlanguages)
  - [textAlign](#textalign)
  - [textAlignVertical](#textalignvertical)
  - [windowColor](#windowcolor)
  - [windowOpacity](#windowopacity)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [backgroundColorChanged](#backgroundcolorchanged)
  - [backgroundOpacityChanged](#backgroundopacitychanged)
  - [enabledChanged](#enabledchanged)
  - [fontColorChanged](#fontcolorchanged)
  - [fontEdgeChanged](#fontedgechanged)
  - [fontEdgeColorChanged](#fontedgecolorchanged)
  - [fontFamilyChanged](#fontfamilychanged)
  - [fontOpacityChanged](#fontopacitychanged)
  - [fontSizeChanged](#fontsizechanged)
  - [preferredLanguagesChanged](#preferredlanguageschanged)
  - [textAlignChanged](#textalignchanged)
  - [textAlignVerticalChanged](#textalignverticalchanged)
  - [windowColorChanged](#windowcolorchanged)
  - [windowOpacityChanged](#windowopacitychanged)
- [Types](#types)

## Usage

To use the ClosedCaptions module, you can import it into your project from the Firebolt SDK:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing closed-captions Settings.

## Methods

### backgroundColor

The preferred background color for displaying closed-captions, .

To get the value of `backgroundColor` call the method like this:

```typescript
function backgroundColor(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `backgroundColor` call the method like this:

```typescript
function backgroundColor(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function backgroundColor(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### backgroundOpacity

The preferred opacity for displaying closed-captions backgrounds.

To get the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(value: number): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `number` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function backgroundOpacity(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### enabled

Whether or not closed-captions are enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

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

### fontColor

The preferred font color for displaying closed-captions.

To get the value of `fontColor` call the method like this:

```typescript
function fontColor(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontColor` call the method like this:

```typescript
function fontColor(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontColor(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### fontEdge

The preferred font edge style for displaying closed-captions.

To get the value of `fontEdge` call the method like this:

```typescript
function fontEdge(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontEdge` call the method like this:

```typescript
function fontEdge(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontEdge(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### fontEdgeColor

The preferred font edge color for displaying closed-captions.

To get the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontEdgeColor(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### fontFamily

The preferred font family for displaying closed-captions.

To get the value of `fontFamily` call the method like this:

```typescript
function fontFamily(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontFamily` call the method like this:

```typescript
function fontFamily(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontFamily(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### fontOpacity

The preferred opacity for displaying closed-captions characters.

To get the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(value: number): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `number` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontOpacity(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### fontSize

The preferred font size for displaying closed-captions.

To get the value of `fontSize` call the method like this:

```typescript
function fontSize(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `fontSize` call the method like this:

```typescript
function fontSize(value: number): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `number` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontSize(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### preferredLanguages

A prioritized list of ISO 639-2/B codes for the preferred closed captions languages on this device.

To get the value of `preferredLanguages` call the method like this:

```typescript
function preferredLanguages(): Promise<string[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `preferredLanguages` call the method like this:

```typescript
function preferredLanguages(value: string[]): Promise<void>
```

Parameters:

| Param   | Type       | Required | Description                             |
| ------- | ---------- | -------- | --------------------------------------- |
| `value` | `string[]` | true     | the preferred closed captions languages |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function preferredLanguages(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### textAlign

The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlign` call the method like this:

```typescript
function textAlign(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `textAlign` call the method like this:

```typescript
function textAlign(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function textAlign(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### textAlignVertical

The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function textAlignVertical(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### windowColor

The preferred window color for displaying closed-captions, .

To get the value of `windowColor` call the method like this:

```typescript
function windowColor(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `windowColor` call the method like this:

```typescript
function windowColor(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function windowColor(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### windowOpacity

The preferred window opacity for displaying closed-captions backgrounds.

To get the value of `windowOpacity` call the method like this:

```typescript
function windowOpacity(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

To set the value of `windowOpacity` call the method like this:

```typescript
function windowOpacity(value: number): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `number` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function windowOpacity(callback: (value) => null): Promise<number>
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

| Type     | Description                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------------ |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

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

| Type     | Description                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------------ |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

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

| Type     | Description                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------------ |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

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

| Type     | Description                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------------ |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### backgroundColorChanged

```typescript
function listen('backgroundColorChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### backgroundOpacityChanged

```typescript
function listen('backgroundOpacityChanged', (number) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### enabledChanged

```typescript
function listen('enabledChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontColorChanged

```typescript
function listen('fontColorChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontEdgeChanged

```typescript
function listen('fontEdgeChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontEdgeColorChanged

```typescript
function listen('fontEdgeColorChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontFamilyChanged

```typescript
function listen('fontFamilyChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontOpacityChanged

```typescript
function listen('fontOpacityChanged', (number) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### fontSizeChanged

```typescript
function listen('fontSizeChanged', (number) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### preferredLanguagesChanged

```typescript
function listen('preferredLanguagesChanged', (string[]) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### textAlignChanged

```typescript
function listen('textAlignChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### textAlignVerticalChanged

```typescript
function listen('textAlignVerticalChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### windowColorChanged

```typescript
function listen('windowColorChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

### windowOpacityChanged

```typescript
function listen('windowOpacityChanged', (number) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

---

## Types
