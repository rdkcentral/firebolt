---
title: Accessibility
---

# Accessibility Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [accessibility.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/accessibility.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)
    - [closedCaptionsSettingsChanged](#losedcaptionssettingschanged)
    - [voiceGuidanceSettingsChanged](#oiceguidancesettingschanged)
 - [Methods](#methods)
    - [closedCaptions](#closedcaptions)
    - [voiceGuidance](#voiceguidance)
 - [Schemas](#schemas)
    - [ClosedCaptionsStyles](#closedcaptionsstyles)
    - [ClosedCaptionsSettings](#closedcaptionssettings)
    - [VoiceGuidanceSettings](#voiceguidancesettings)

<span></span>

## Usage
To use the Accessibility module, you can import it into your project from the Firebolt SDK:

```javascript
import { Accessibility } from '@firebolt-js/sdk'
```
## Overview
The `Accessibility` module provides access to the user/device settings for closed captioning and voice guidance.

Apps **SHOULD** attempt o respect these settings, rather than manage and persist seprate settings, which would be different per-app.

## Events
### closedCaptionsSettingsChanged
Subscribe to notifications with the user's preferred closed-captions settings

```typescript
// listen to closedCaptionsSettingsChanged
Accessibility.listen('closedCaptionsSettingsChanged', (data: ClosedCaptionsSettings) => void): Promise<bigint>

// listen to closedCaptionsSettingsChanged once
Accessibility.once('closedCaptionsSettingsChanged', (data: ClosedCaptionsSettings) => void): Promise<bigint>

// clear a listener
Accessibility.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`ClosedCaptionsSettings`](#closedcaptionssettings) | the closed captions settings |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

#### Examples

##### Getting the closed captions settings
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Accessibility } from '@firebolt-js/sdk'

Accessibility.listen('closedCaptionsSettingsChanged', settings => {
  console.log(settings)
})
```
Value of `settings`

```javascript
{
  "enabled": true,
  "styles": {
    "fontFamily": "Monospace sans-serif",
    "fontSize": 1,
    "fontColor": "#ffffff",
    "fontEdge": "none",
    "fontEdgeColor": "#7F7F7F",
    "fontOpacity": 100,
    "backgroundColor": "#000000",
    "backgroundOpacity": 100,
    "textAlign": "center",
    "textAlignVertical": "middle"
  }
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

<h6>Request</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "accessibility.onClosedCaptionsSettingsChanged",
  "params": {}
}
```

<h6>Response</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "styles": {
      "fontFamily": "Monospace sans-serif",
      "fontSize": 1,
      "fontColor": "#ffffff",
      "fontEdge": "none",
      "fontEdgeColor": "#7F7F7F",
      "fontOpacity": 100,
      "backgroundColor": "#000000",
      "backgroundOpacity": 100,
      "textAlign": "center",
      "textAlignVertical": "middle"
    }
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Accessibility.listen('closedCaptionsSettingsChanged', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Accessibility.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Accessibility.once('closedCaptionsSettingsChanged', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Accessibility.clear('closedCaptionsSettingsChanged')
```
</details>

---

### voiceGuidanceSettingsChanged
Subscribe to notifications with the user's preferred voice guidance settings

```typescript
// listen to voiceGuidanceSettingsChanged
Accessibility.listen('voiceGuidanceSettingsChanged', (data: VoiceGuidanceSettings) => void): Promise<bigint>

// listen to voiceGuidanceSettingsChanged once
Accessibility.once('voiceGuidanceSettingsChanged', (data: VoiceGuidanceSettings) => void): Promise<bigint>

// clear a listener
Accessibility.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`VoiceGuidanceSettings`](#voiceguidancesettings) | the voice guidance settings |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Accessibility.clear(id)` |

#### Examples

##### Getting the voice guidance settings
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Accessibility } from '@firebolt-js/sdk'

Accessibility.listen('voiceGuidanceSettingsChanged', settings => {
  console.log(settings)
})
```
Value of `settings`

```javascript
{
  "enabled": true,
  "speed": 5
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

<h6>Request</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "accessibility.onVoiceGuidanceSettingsChanged",
  "params": {}
}
```

<h6>Response</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "speed": 5
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Accessibility.listen('voiceGuidanceSettingsChanged', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Accessibility.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Accessibility.once('voiceGuidanceSettingsChanged', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Accessibility.clear('voiceGuidanceSettingsChanged')
```
</details>

---



## Methods
### closedCaptions
Get the user's preferred closed-captions settings

```typescript
function closedCaptions(): Promise<ClosedCaptionsSettings>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`ClosedCaptionsSettings`](#closedcaptionssettings) | the closed captions settings |


---

#### Examples

##### Getting the closed captions settings
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Accessibility } from '@firebolt-js/sdk'

Accessibility.closedCaptions()
    .then(closedCaptionsSettings => {
        console.log(closedCaptionsSettings)
    })
```
Value of `closedCaptionsSettings`

```javascript
{
  "enabled": true,
  "styles": {
    "fontFamily": "Monospace sans-serif",
    "fontSize": 1,
    "fontColor": "#ffffff",
    "fontEdge": "none",
    "fontEdgeColor": "#7F7F7F",
    "fontOpacity": 100,
    "backgroundColor": "#000000",
    "backgroundOpacity": 100,
    "textAlign": "center",
    "textAlignVertical": "middle"
  }
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "accessibility.closedCaptions",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "styles": {
      "fontFamily": "Monospace sans-serif",
      "fontSize": 1,
      "fontColor": "#ffffff",
      "fontEdge": "none",
      "fontEdgeColor": "#7F7F7F",
      "fontOpacity": 100,
      "backgroundColor": "#000000",
      "backgroundOpacity": 100,
      "textAlign": "center",
      "textAlignVertical": "middle"
    }
  }
}
```

</details>




---

### voiceGuidance
Get the user's preferred voice guidance settings

```typescript
function voiceGuidance(): Promise<VoiceGuidanceSettings>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`VoiceGuidanceSettings`](#voiceguidancesettings) | the voice guidance settings |


---

#### Examples

##### Getting the voice guidance settings
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Accessibility } from '@firebolt-js/sdk'

Accessibility.voiceGuidance()
    .then(settings => {
        console.log(settings)
    })
```
Value of `settings`

```javascript
{
  "enabled": true,
  "speed": 5
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "accessibility.voiceGuidance",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "speed": 5
  }
}
```

</details>




---



## Schemas

### ClosedCaptionsStyles

```typescript
type ClosedCaptionsStyles = {
  fontFamily?: string
  fontSize?: number
  fontColor?: string
  fontEdge?: string
  fontEdgeColor?: string
  fontOpacity?: number
  backgroundColor?: string
  backgroundOpacity?: number
  textAlign?: string
  textAlignVertical?: string
}
```



#### Details

The default styles to use when displaying closed-captions

---

### ClosedCaptionsSettings

```typescript
type ClosedCaptionsSettings = {
  enabled: boolean               // Whether or not closed-captions should be enabled by default
  styles: ClosedCaptionsStyles   // The default styles to use when displaying closed-captions
}
```





---

### VoiceGuidanceSettings

```typescript
type VoiceGuidanceSettings = {
  enabled: boolean              // Whether or not voice guidance should be enabled by default
  speed: number                 // The speed at which voice guidance speech will be read back to the user
}
```





---


