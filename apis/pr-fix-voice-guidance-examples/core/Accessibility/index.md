---
title: Accessibility

version: pr-fix-voice-guidance-examples
layout: default
sdk: core
---

# Accessibility Module

---

Version Accessibility 1.5.0-fix-voice-guidance-examples.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audioDescriptionSettings](#audiodescriptionsettings)
  - [closedCaptions](#closedcaptions)
  - [closedCaptionsSettings](#closedcaptionssettings)
  - [highContrastUI](#highcontrastui)
  - [listen](#listen)
  - [once](#once)
  - [voiceGuidance](#voiceguidance)
  - [voiceGuidanceSettings](#voiceguidancesettings)
- [Events](#events)
  - [audioDescriptionSettingsChanged](#audiodescriptionsettingschanged)
  - [closedCaptionsSettingsChanged](#closedcaptionssettingschanged)
  - [highContrastUIChanged](#highcontrastuichanged)
  - [voiceGuidanceSettingsChanged](#voiceguidancesettingschanged)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [closedCaptionsSettingsChanged](#closedcaptionssettingschanged-1)
  - [highContrastUIChanged](#highcontrastuichanged-1)
  - [voiceGuidanceSettingsChanged](#voiceguidancesettingschanged-1)
  </details>
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

[AudioDescriptionSettings](#audiodescriptionsettings-1)

Capabilities:

| Role | Capability                                              |
| ---- | ------------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:audiodescriptions |

#### Examples

Getting the audio description settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let settings = await Accessibility.audioDescriptionSettings()
console.log(settings)
```

Value of `settings`:

```javascript
{
	"enabled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Accessibility.audioDescriptionSettings",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audioDescriptionSettings(
  callback: (value) => AudioDescriptionSettings,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the audio description settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let listenerId = await audioDescriptionSettings((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `settings`:

```javascript
{
	"enabled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Accessibility.onAudioDescriptionSettingsChanged",
  "params": {
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
    "enabled": true
  }
}
```

</details>

---

### closedCaptions

[Deprecated] This method is deprecated as of since version 0.6.0. Please use `Accessibility.closedCaptionsSettings()` as a replacement.

```typescript
function closedCaptions(): Promise<ClosedCaptionsSettings>
```

---

### closedCaptionsSettings

Get the user's preferred closed-captions settings

To get the value of `closedCaptionsSettings` call the method like this:

```typescript
function closedCaptionsSettings(): Promise<ClosedCaptionsSettings>
```

Promise resolution:

[ClosedCaptionsSettings](../Accessibility/schemas/#ClosedCaptionsSettings)

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Getting the closed captions settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let closedCaptionsSettings = await Accessibility.closedCaptionsSettings()
console.log(closedCaptionsSettings)
```

Value of `closedCaptionsSettings`:

```javascript
{
	"enabled": true,
	"styles": {
		"fontFamily": "monospaced_sanserif",
		"fontSize": 1,
		"fontColor": "#ffffff",
		"fontEdge": "none",
		"fontEdgeColor": "#7F7F7F",
		"fontOpacity": 100,
		"backgroundColor": "#000000",
		"backgroundOpacity": 100,
		"textAlign": "center",
		"textAlignVertical": "middle",
		"windowColor": "white",
		"windowOpacity": 50
	},
	"preferredLanguages": [
		"eng",
		"spa"
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
  "method": "Accessibility.closedCaptionsSettings",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "styles": {
      "fontFamily": "monospaced_sanserif",
      "fontSize": 1,
      "fontColor": "#ffffff",
      "fontEdge": "none",
      "fontEdgeColor": "#7F7F7F",
      "fontOpacity": 100,
      "backgroundColor": "#000000",
      "backgroundOpacity": 100,
      "textAlign": "center",
      "textAlignVertical": "middle",
      "windowColor": "white",
      "windowOpacity": 50
    },
    "preferredLanguages": ["eng", "spa"]
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function closedCaptionsSettings(
  callback: (value) => ClosedCaptionsSettings,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the closed captions settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let listenerId = await closedCaptionsSettings((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `closedCaptionsSettings`:

```javascript
{
	"enabled": true,
	"styles": {
		"fontFamily": "monospaced_sanserif",
		"fontSize": 1,
		"fontColor": "#ffffff",
		"fontEdge": "none",
		"fontEdgeColor": "#7F7F7F",
		"fontOpacity": 100,
		"backgroundColor": "#000000",
		"backgroundOpacity": 100,
		"textAlign": "center",
		"textAlignVertical": "middle",
		"windowColor": "white",
		"windowOpacity": 50
	},
	"preferredLanguages": [
		"eng",
		"spa"
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
  "method": "Accessibility.onClosedCaptionsSettingsChanged",
  "params": {
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
    "enabled": true,
    "styles": {
      "fontFamily": "monospaced_sanserif",
      "fontSize": 1,
      "fontColor": "#ffffff",
      "fontEdge": "none",
      "fontEdgeColor": "#7F7F7F",
      "fontOpacity": 100,
      "backgroundColor": "#000000",
      "backgroundOpacity": 100,
      "textAlign": "center",
      "textAlignVertical": "middle",
      "windowColor": "white",
      "windowOpacity": 50
    },
    "preferredLanguages": ["eng", "spa"]
  }
}
```

</details>

---

### highContrastUI

The user's preference for a high-contrast UI

To get the value of `highContrastUI` call the method like this:

```typescript
function highContrastUI(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:highcontrastui |

#### Examples

High-contrast UI mode is enabled

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let highContrastUI = await Accessibility.highContrastUI()
console.log(highContrastUI)
```

Value of `highContrastUI`:

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
  "method": "Accessibility.highContrastUI",
  "params": {}
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

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function highContrastUI(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

High-contrast UI mode is enabled

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let listenerId = await highContrastUI((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `highContrastUI`:

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
  "method": "Accessibility.onHighContrastUIChanged",
  "params": {
    "listen": true
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

### voiceGuidance

[Deprecated] This method is deprecated as of since version 0.6.0. Please use `Accessibility.voiceGuidanceSettings()` as a replacement.

```typescript
function voiceGuidance(): Promise<VoiceGuidanceSettings>
```

---

### voiceGuidanceSettings

Get the user's preferred voice guidance settings

To get the value of `voiceGuidanceSettings` call the method like this:

```typescript
function voiceGuidanceSettings(): Promise<VoiceGuidanceSettings>
```

Promise resolution:

[VoiceGuidanceSettings](../Accessibility/schemas/#VoiceGuidanceSettings)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:voiceguidance |

#### Examples

Getting the voice guidance settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let settings = await Accessibility.voiceGuidanceSettings()
console.log(settings)
```

Value of `settings`:

```javascript
{
	"enabled": true,
	"navigationHints": true,
	"rate": 1
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Accessibility.voiceGuidanceSettings",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "navigationHints": true,
    "rate": 1
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function voiceGuidanceSettings(
  callback: (value) => VoiceGuidanceSettings,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the voice guidance settings

JavaScript:

```javascript
import { Accessibility } from '@firebolt-js/sdk'

let listenerId = await voiceGuidanceSettings((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `settings`:

```javascript
{
	"enabled": true,
	"navigationHints": true,
	"rate": 1
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Accessibility.onVoiceGuidanceSettingsChanged",
  "params": {
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
    "enabled": true,
    "navigationHints": true,
    "rate": 1
  }
}
```

</details>

---

## Events

### audioDescriptionSettingsChanged

See: [audioDescriptionSettings](#audiodescriptionsettings)

### closedCaptionsSettingsChanged

See: [closedCaptionsSettings](#closedcaptionssettings)

### highContrastUIChanged

See: [highContrastUI](#highcontrastui)

### voiceGuidanceSettingsChanged

See: [voiceGuidanceSettings](#voiceguidancesettings)

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### audioDescriptionSettingsChanged

See: [audioDescriptionSettings](#audiodescriptionsettings)

### closedCaptionsSettingsChanged

See: [closedCaptionsSettings](#closedcaptionssettings)

### highContrastUIChanged

See: [highContrastUI](#highcontrastui)

### voiceGuidanceSettingsChanged

See: [voiceGuidanceSettings](#voiceguidancesettings)

</details>

## Types

### AudioDescriptionSettings

```typescript
type AudioDescriptionSettings = {
  enabled: boolean // Whether or not audio descriptions should be enabled by default
}
```

---
