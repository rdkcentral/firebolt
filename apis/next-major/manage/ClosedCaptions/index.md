---
title: ClosedCaptions

version: next-major
layout: default
sdk: manage
---

# ClosedCaptions Module

---

Version ClosedCaptions 1.8.0-next-major.2

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
  - [listen](#listen)
  - [once](#once)
  - [preferredLanguages](#preferredlanguages)
  - [textAlign](#textalign)
  - [textAlignVertical](#textalignvertical)
  - [windowColor](#windowcolor)
  - [windowOpacity](#windowopacity)
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
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [backgroundOpacityChanged](#backgroundopacitychanged-1)
  - [enabledChanged](#enabledchanged-1)
  - [fontColorChanged](#fontcolorchanged-1)
  - [fontEdgeChanged](#fontedgechanged-1)
  - [fontEdgeColorChanged](#fontedgecolorchanged-1)
  - [fontFamilyChanged](#fontfamilychanged-1)
  - [fontOpacityChanged](#fontopacitychanged-1)
  - [fontSizeChanged](#fontsizechanged-1)
  - [preferredLanguagesChanged](#preferredlanguageschanged-1)
  - [textAlignChanged](#textalignchanged-1)
  - [textAlignVerticalChanged](#textalignverticalchanged-1)
  - [windowColorChanged](#windowcolorchanged-1)
  - [windowOpacityChanged](#windowopacitychanged-1)
  </details>
- [Types](#types)
  - [EDIDVersion](#edidversion)
  - [WifiSecurityMode](#wifisecuritymode)
  - [AudioProfile](#audioprofile)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [OfferingType](#offeringtype)
  - [MusicType](#musictype)
  - [ProgramType](#programtype)
  - [WifiSignalStrength](#wifisignalstrength)
  - [WifiFrequency](#wififrequency)
  - [AccessPoint](#accesspoint)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [SpeechRate](#speechrate)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [FontFamily](#fontfamily-1)
  - [FontSize](#fontsize-1)
  - [Color](#color)
  - [FontEdge](#fontedge-1)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ISO639_2Language](#isolanguage)
  - [Capability](#capability)
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [CapPermissionStatus](#cappermissionstatus)
  - [EventObject](#eventobject)
  - [EntityDetails](#entitydetails)
  - [Entity](#entity)
  - [Metadata](#metadata)
  - [ProgramEntity](#programentity)
  - [MusicEntity](#musicentity)
  - [ChannelEntity](#channelentity)
  - [UntypedEntity](#untypedentity)
  - [PlaylistEntity](#playlistentity)
  - [MovieEntity](#movieentity)
  - [TVEpisodeEntity](#tvepisodeentity)
  - [TVSeasonEntity](#tvseasonentity)
  - [TVSeriesEntity](#tvseriesentity)
  - [AdditionalEntity](#additionalentity)
  - [PlayableEntity](#playableentity)
  - [WayToWatch](#waytowatch)
  - [AppInfo](#appinfo)
  - [ContentIdentifiers](#contentidentifiers)
  - [ContentRating](#contentrating)
- [United States](#united-states)
- [Canada](#canada)
  - [GrantState](#grantstate)
  - [HDMIPortId](#hdmiportid)
  - [EntityInfo](#entityinfo)
  - [AgePolicy](#agepolicy)
  - [HomeIntent](#homeintent)
  - [LaunchIntent](#launchintent)
  - [EntityIntent](#entityintent)
  - [PlaybackIntent](#playbackintent)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [TuneIntent](#tuneintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlayQueryIntent](#playqueryintent)
  - [Intent](#intent)
  - [IntentProperties](#intentproperties)
  - [ResultReason](#resultreason)

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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.backgroundColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.backgroundColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#ffffff"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.backgroundColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundColor",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundColor('#000000')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundColor",
  "params": {
    "value": "#000000"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundColor('#ffffff')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundColor",
  "params": {
    "value": "#ffffff"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundColor()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundColor",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function backgroundColor(callback: (value) => string): Promise<number>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### backgroundOpacity
The preferred opacity for displaying closed-captions backgrounds.

To get the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(): Promise<number>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.backgroundOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.backgroundOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.backgroundOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.backgroundOpacity",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundOpacity(99)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundOpacity",
  "params": {
    "value": 99
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundOpacity(100)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundOpacity",
  "params": {
    "value": 100
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.backgroundOpacity()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setBackgroundOpacity",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function backgroundOpacity(callback: (value) => number): Promise<number>
```

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### enabled
Whether or not closed-captions are enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let enabled = await ClosedCaptions.enabled()
console.log(enabled)
```

Value of `enabled`:

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
  "method": "ClosedCaptions.enabled",
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let enabled = await ClosedCaptions.enabled()
console.log(enabled)
```

Value of `enabled`:

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
  "method": "ClosedCaptions.enabled",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.enabled(true)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setEnabled",
  "params": {
    "value": true
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.enabled(false)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setEnabled",
  "params": {
    "value": false
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function enabled(callback: (value) => boolean): Promise<number>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', result => {
  console.log(result)
})
````

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontColor
The preferred font color for displaying closed-captions.

To get the value of `fontColor` call the method like this:

```typescript
function fontColor(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontColor()
console.log(color)
```

Value of `color`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#ffffff"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontColor()
console.log(color)
```

Value of `color`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#000000"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontColor()
console.log(color)
```

Value of `color`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontColor",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontColor('#ffffff')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontColor",
  "params": {
    "value": "#ffffff"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontColor('#000000')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontColor",
  "params": {
    "value": "#000000"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontColor()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontColor",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontColor(callback: (value) => string): Promise<number>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontEdge
The preferred font edge style for displaying closed-captions.

To get the value of `fontEdge` call the method like this:

```typescript
function fontEdge(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let edge = await ClosedCaptions.fontEdge()
console.log(edge)
```

Value of `edge`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdge",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "none"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let edge = await ClosedCaptions.fontEdge()
console.log(edge)
```

Value of `edge`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdge",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "uniform"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let edge = await ClosedCaptions.fontEdge()
console.log(edge)
```

Value of `edge`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdge",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdge('none')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdge",
  "params": {
    "value": "none"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdge('uniform')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdge",
  "params": {
    "value": "uniform"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdge()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdge",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontEdge(callback: (value) => string): Promise<number>
```

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `edge` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontEdgeColor
The preferred font edge color for displaying closed-captions.

To get the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontEdgeColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdgeColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontEdgeColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdgeColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#ffffff"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.fontEdgeColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontEdgeColor",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdgeColor('#000000')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdgeColor",
  "params": {
    "value": "#000000"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdgeColor('#ffffff')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdgeColor",
  "params": {
    "value": "#ffffff"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontEdgeColor()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontEdgeColor",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontEdgeColor(callback: (value) => string): Promise<number>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'fontEdgeColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontFamily
The preferred font family for displaying closed-captions.

To get the value of `fontFamily` call the method like this:

```typescript
function fontFamily(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let family = await ClosedCaptions.fontFamily()
console.log(family)
```

Value of `family`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontFamily",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "monospaced_sanserif"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let family = await ClosedCaptions.fontFamily()
console.log(family)
```

Value of `family`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontFamily",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "cursive"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let family = await ClosedCaptions.fontFamily()
console.log(family)
```

Value of `family`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontFamily",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontFamily('monospaced_sanserif')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontFamily",
  "params": {
    "value": "monospaced_sanserif"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontFamily('cursive')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontFamily",
  "params": {
    "value": "cursive"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontFamily()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontFamily",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontFamily(callback: (value) => string): Promise<number>
```

Parameters:

| Param    | Type     | Required | Description |
| -------- | -------- | -------- | ----------- |
| `family` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontOpacity
The preferred opacity for displaying closed-captions characters.

To get the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(): Promise<number>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.fontOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.fontOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.fontOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontOpacity",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontOpacity(99)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontOpacity",
  "params": {
    "value": 99
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontOpacity(100)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontOpacity",
  "params": {
    "value": 100
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontOpacity()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontOpacity",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontOpacity(callback: (value) => number): Promise<number>
```

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### fontSize
The preferred font size for displaying closed-captions.

To get the value of `fontSize` call the method like this:

```typescript
function fontSize(): Promise<number>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let size = await ClosedCaptions.fontSize()
console.log(size)
```

Value of `size`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontSize",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 1
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let size = await ClosedCaptions.fontSize()
console.log(size)
```

Value of `size`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontSize",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 1
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let size = await ClosedCaptions.fontSize()
console.log(size)
```

Value of `size`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.fontSize",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontSize(1)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontSize",
  "params": {
    "value": 1
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontSize(1)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontSize",
  "params": {
    "value": 1
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.fontSize()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setFontSize",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function fontSize(callback: (value) => number): Promise<number>
```

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `size` | `number` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### listen

To listen to a specific event pass the event name as the first parameter:

```typescript
listen(event: string, callback: (data: any) => void): Promise<number>
````

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

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let languages = await ClosedCaptions.preferredLanguages()
console.log(languages)
```

Value of `languages`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.preferredLanguages",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["spa", "eng"]
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let languages = await ClosedCaptions.preferredLanguages()
console.log(languages)
```

Value of `languages`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.preferredLanguages",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["eng", "spa"]
}
```

</details>

---

To set the value of `preferredLanguages` call the method like this:

```typescript
function preferredLanguages(value: string[]): Promise<void>
```

Parameters:

| Param   | Type       | Required | Description                                                      |
| ------- | ---------- | -------- | ---------------------------------------------------------------- |
| `value` | `string[]` | true     | the preferred closed captions languages <br/>pattern: ^[a-z]{3}$ |

Promise resolution:

#### Examples

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.preferredLanguages(['spa', 'eng'])
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setPreferredLanguages",
  "params": {
    "value": ["spa", "eng"]
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

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.preferredLanguages(['eng', 'spa'])
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setPreferredLanguages",
  "params": {
    "value": ["eng", "spa"]
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function preferredLanguages(callback: (value) => string[]): Promise<number>
```

Parameters:

| Param       | Type       | Required | Description                                                      |
| ----------- | ---------- | -------- | ---------------------------------------------------------------- |
| `languages` | `string[]` | false    | the preferred closed captions languages <br/>pattern: ^[a-z]{3}$ |

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'preferredLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('preferredLanguagesChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### textAlign
The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlign` call the method like this:

```typescript
function textAlign(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlign()
console.log(alignment)
```

Value of `alignment`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlign",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "center"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlign()
console.log(alignment)
```

Value of `alignment`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlign",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "left"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlign()
console.log(alignment)
```

Value of `alignment`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlign",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlign('center')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlign",
  "params": {
    "value": "center"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlign('left')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlign",
  "params": {
    "value": "left"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlign()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlign",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function textAlign(callback: (value) => string): Promise<number>
```

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### textAlignVertical
The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlignVertical()
console.log(alignment)
```

Value of `alignment`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlignVertical",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "middle"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlignVertical()
console.log(alignment)
```

Value of `alignment`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlignVertical",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "top"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let alignment = await ClosedCaptions.textAlignVertical()
console.log(alignment)
```

Value of `alignment`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.textAlignVertical",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlignVertical('middle')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlignVertical",
  "params": {
    "value": "middle"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlignVertical('top')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlignVertical",
  "params": {
    "value": "top"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.textAlignVertical()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setTextAlignVertical",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function textAlignVertical(callback: (value) => string): Promise<number>
```

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'textAlignVerticalChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### windowColor
The preferred window color for displaying closed-captions, .

To get the value of `windowColor` call the method like this:

```typescript
function windowColor(): Promise<string>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.windowColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.windowColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowColor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "white"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let color = await ClosedCaptions.windowColor()
console.log(color)
```

Value of `color`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowColor",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowColor('#000000')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowColor",
  "params": {
    "value": "#000000"
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowColor('white')
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowColor",
  "params": {
    "value": "white"
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowColor()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowColor",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function windowColor(callback: (value) => string): Promise<number>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### windowOpacity
The preferred window opacity for displaying closed-captions backgrounds.

To get the value of `windowOpacity` call the method like this:

```typescript
function windowOpacity(): Promise<number>
````

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.windowOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.windowOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowOpacity",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let opacity = await ClosedCaptions.windowOpacity()
console.log(opacity)
```

Value of `opacity`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.windowOpacity",
  "params": {}
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

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowOpacity(99)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowOpacity",
  "params": {
    "value": 99
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowOpacity(100)
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowOpacity",
  "params": {
    "value": 100
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

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let result = await ClosedCaptions.windowOpacity()
console.log(result)
```

Value of `result`:

```javascript
null
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.setWindowOpacity",
  "params": {
    "value": null
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function windowOpacity(callback: (value) => number): Promise<number>
```

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'windowOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---



## Events

### backgroundColorChanged





```typescript
function listen('backgroundColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### backgroundOpacityChanged





```typescript
function listen('backgroundOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### enabledChanged





```typescript
function listen('enabledChanged', (boolean) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', result => {
  console.log(result)
})
````

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontColorChanged





```typescript
function listen('fontColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontEdgeChanged





```typescript
function listen('fontEdgeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `edge` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontEdgeColorChanged





```typescript
function listen('fontEdgeColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'fontEdgeColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontFamilyChanged





```typescript
function listen('fontFamilyChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type     | Required | Description |
| -------- | -------- | -------- | ----------- |
| `family` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontOpacityChanged





```typescript
function listen('fontOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontSizeChanged





```typescript
function listen('fontSizeChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `size` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### preferredLanguagesChanged





```typescript
function listen('preferredLanguagesChanged', (string[]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type       | Required | Description                                                      |
| ----------- | ---------- | -------- | ---------------------------------------------------------------- |
| `languages` | `string[]` | false    | the preferred closed captions languages <br/>pattern: ^[a-z]{3}$ |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'preferredLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('preferredLanguagesChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### textAlignChanged





```typescript
function listen('textAlignChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### textAlignVerticalChanged





```typescript
function listen('textAlignVerticalChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'textAlignVerticalChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### windowColorChanged





```typescript
function listen('windowColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### windowOpacityChanged





```typescript
function listen('windowOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'windowOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


## Private Events
<details markdown="1"  id="private-events-details">
  <summary>View</summary>

  ### backgroundColorChanged





```typescript
function listen('backgroundColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### backgroundOpacityChanged





```typescript
function listen('backgroundOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'backgroundOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('backgroundOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### enabledChanged





```typescript
function listen('enabledChanged', (boolean) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('enabledChanged', result => {
  console.log(result)
})
````

Value of `result`:

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
  "method": "ClosedCaptions.onEnabledChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontColorChanged





```typescript
function listen('fontColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#ffffff'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontEdgeChanged





```typescript
function listen('fontEdgeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `edge` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontEdgeColorChanged





```typescript
function listen('fontEdgeColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'fontEdgeColorChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontEdgeColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontEdgeColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontFamilyChanged





```typescript
function listen('fontFamilyChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type     | Required | Description |
| -------- | -------- | -------- | ----------- |
| `family` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontFamilyChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'monospaced_sanserif'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontFamilyChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontOpacityChanged





```typescript
function listen('fontOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### fontSizeChanged





```typescript
function listen('fontSizeChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description |
| ------ | -------- | -------- | ----------- |
| `size` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('fontSizeChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
1
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onFontSizeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### preferredLanguagesChanged





```typescript
function listen('preferredLanguagesChanged', (string[]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type       | Required | Description                                                      |
| ----------- | ---------- | -------- | ---------------------------------------------------------------- |
| `languages` | `string[]` | false    | the preferred closed captions languages <br/>pattern: ^[a-z]{3}$ |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'preferredLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('preferredLanguagesChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### textAlignChanged





```typescript
function listen('textAlignChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'center'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### textAlignVerticalChanged





```typescript
function listen('textAlignVerticalChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type     | Required | Description |
| ----------- | -------- | -------- | ----------- |
| `alignment` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'textAlignVerticalChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('textAlignVerticalChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'middle'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### windowColorChanged





```typescript
function listen('windowColorChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `color` | `string` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowColorChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
'#000000'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowColorChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### windowOpacityChanged





```typescript
function listen('windowOpacityChanged', (number) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param     | Type     | Required | Description |
| --------- | -------- | -------- | ----------- |
| `opacity` | `number` | false    |             |

Event value:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen(
  'windowOpacityChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await ClosedCaptions.listen('windowOpacityChanged', result => {
  console.log(result)
})
````

Value of `result`:

```javascript
99
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ClosedCaptions.onWindowOpacityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

</details>


## Types

### EDIDVersion



```typescript
EDIDVersion: {
    V1_4: '1.4',
    V2_0: '2.0',
    UNKNOWN: 'unknown',
},

````

---

### WifiSecurityMode

Security Mode supported for Wifi

```typescript
WifiSecurityMode: {
    NONE: 'none',
    WEP_64: 'wep64',
    WEP_128: 'wep128',
    WPA_PSK_TKIP: 'wpaPskTkip',
    WPA_PSK_AES: 'wpaPskAes',
    WPA_2PSK_TKIP: 'wpa2PskTkip',
    WPA_2PSK_AES: 'wpa2PskAes',
    WPA_ENTERPRISE_TKIP: 'wpaEnterpriseTkip',
    WPA_ENTERPRISE_AES: 'wpaEnterpriseAes',
    WPA_2ENTERPRISE_TKIP: 'wpa2EnterpriseTkip',
    WPA_2ENTERPRISE_AES: 'wpa2EnterpriseAes',
    WPA_2PSK: 'wpa2Psk',
    WPA_2ENTERPRISE: 'wpa2Enterprise',
    WPA_3PSK_AES: 'wpa3PskAes',
    WPA_3SAE: 'wpa3Sae',
},

```

---

### AudioProfile

```typescript
AudioProfile: {
    STEREO: 'stereo',
    DOLBY_DIGITAL_5_1: 'dolbyDigital5.1',
    DOLBY_DIGITAL_5_1_PLUS: 'dolbyDigital5.1+',
    DOLBY_ATMOS: 'dolbyAtmos',
},

```

---

### Role

Role provides access level for the app for a given capability.

```typescript
Role: {
    USE: 'use',
    MANAGE: 'manage',
    PROVIDE: 'provide',
},

```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
DenyReason: {
    UNPERMITTED: 'unpermitted',
    UNSUPPORTED: 'unsupported',
    DISABLED: 'disabled',
    UNAVAILABLE: 'unavailable',
    GRANT_DENIED: 'grantDenied',
    UNGRANTED: 'ungranted',
},

```

---

### OfferingType

The offering type of the WayToWatch.

```typescript
OfferingType: {
    FREE: 'free',
    SUBSCRIBE: 'subscribe',
    BUY: 'buy',
    RENT: 'rent',
},

```

---

### MusicType

In the case of a music `entityType`, specifies the type of music entity.

```typescript
MusicType: {
    SONG: 'song',
    ALBUM: 'album',
},

```

---

### ProgramType

In the case of a program `entityType`, specifies the program type.

```typescript
ProgramType: {
    MOVIE: 'movie',
    EPISODE: 'episode',
    SEASON: 'season',
    SERIES: 'series',
    OTHER: 'other',
    PREVIEW: 'preview',
    EXTRA: 'extra',
    CONCERT: 'concert',
    SPORTING_EVENT: 'sportingEvent',
    ADVERTISEMENT: 'advertisement',
    MUSIC_VIDEO: 'musicVideo',
    MINISODE: 'minisode',
},

```

---

### WifiSignalStrength

Strength of Wifi signal, value is negative based on RSSI specification.

```typescript
type WifiSignalStrength = number
```

---

### WifiFrequency

Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.

```typescript
type WifiFrequency = number
```

---

### AccessPoint

Properties of a scanned wifi list item.

```typescript
type AccessPoint = {
  ssid?: string // Name of the wifi.
  securityMode?: WifiSecurityMode // Security Mode supported for Wifi
  signalStrength?: WifiSignalStrength // Strength of Wifi signal, value is negative based on RSSI specification.
  frequency?: WifiFrequency // Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.
}
```

See also:

[WifiSecurityMode](#wifisecuritymode)
[WifiSignalStrength](#wifisignalstrength)
[WifiFrequency](#wififrequency)

---

### HDMISignalStatus

```typescript
HDMISignalStatus: {
    NONE: 'none',
    STABLE: 'stable',
    UNSTABLE: 'unstable',
    UNSUPPORTED: 'unsupported',
    UNKNOWN: 'unknown',
},

```

---

### SpeechRate

```typescript
type SpeechRate = number
```

---

### ClosedCaptionsStyles

The default styles to use when displaying closed-captions

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
  windowColor?: string
  windowOpacity?: number
}
```

---

### FontFamily

```typescript
FontFamily: {
    MONOSPACED_SERIF: 'monospaced_serif',
    PROPORTIONAL_SERIF: 'proportional_serif',
    MONOSPACED_SANSERIF: 'monospaced_sanserif',
    PROPORTIONAL_SANSERIF: 'proportional_sanserif',
    SMALLCAPS: 'smallcaps',
    CURSIVE: 'cursive',
    CASUAL: 'casual',
},

```

---

### FontSize

```typescript
type FontSize = number
```

---

### Color

```typescript
type Color = string
```

---

### FontEdge

```typescript
FontEdge: {
    NONE: 'none',
    RAISED: 'raised',
    DEPRESSED: 'depressed',
    UNIFORM: 'uniform',
    DROP_SHADOW_LEFT: 'drop_shadow_left',
    DROP_SHADOW_RIGHT: 'drop_shadow_right',
},

```

---

### Opacity

```typescript
type Opacity = number
```

---

### HorizontalAlignment

```typescript
type HorizontalAlignment = string
```

---

### VerticalAlignment

```typescript
type VerticalAlignment = string
```

---

### ISO639_2Language

```typescript
type ISO639_2Language = string
```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

---

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean
}
```

---

### EventObject

```typescript
type EventObject = [property: string]: EventObjectPrimitives | EventObjectPrimitives | EventObject[] | EventObject
```

See also:

[EventObjectPrimitives](#eventobjectprimitives)
[EventObject](#eventobject-1)

---

### EntityDetails

```typescript
type EntityDetails = {
  identifiers:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  info?: Metadata
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entity.Metadata
Entertainment.WayToWatch

---

### Entity

```typescript
type Entity =
  | ProgramEntity
  | MusicEntity
  | ChannelEntity
  | UntypedEntity
  | PlaylistEntity
```

See also:

Entity.ProgramEntity
Entity.MusicEntity
Entity.ChannelEntity
Entity.UntypedEntity
Entity.PlaylistEntity

---

### Metadata

```typescript
type Metadata = {
  title?: string // Title of the entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
}
```

See also:

Entertainment.ContentRating

---

### ProgramEntity

```typescript
type ProgramEntity =
  | MovieEntity
  | TVEpisodeEntity
  | TVSeasonEntity
  | TVSeriesEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.TVSeasonEntity
Entity.TVSeriesEntity
Entity.AdditionalEntity

---

### MusicEntity

```typescript
type MusicEntity = {
  entityType: 'music'
  musicType: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  entityId: string
}
```

See also:

Entertainment.MusicType

---

### ChannelEntity

```typescript
type ChannelEntity = {
  entityType: 'channel'
  channelType: 'streaming' | 'overTheAir'
  entityId: string // ID of the channel, in the target App's scope.
  appContentData?: string
}
```

---

### UntypedEntity

```typescript
type UntypedEntity = {
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlaylistEntity

A Firebolt compliant representation of a Playlist entity.

```typescript
type PlaylistEntity = {
  entityType: 'playlist'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### MovieEntity

A Firebolt compliant representation of a Movie entity.

```typescript
type MovieEntity = {
  entityType: 'program'
  programType: 'movie'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVEpisodeEntity

A Firebolt compliant representation of a TV Episode entity.

```typescript
type TVEpisodeEntity = {
  entityType: 'program'
  programType: 'episode'
  entityId: string
  seriesId: string
  seasonId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeasonEntity

A Firebolt compliant representation of a TV Season entity.

```typescript
type TVSeasonEntity = {
  entityType: 'program'
  programType: 'season'
  entityId: string
  seriesId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeriesEntity

A Firebolt compliant representation of a TV Series entity.

```typescript
type TVSeriesEntity = {
  entityType: 'program'
  programType: 'series'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### AdditionalEntity

A Firebolt compliant representation of the remaining program entity types.

```typescript
type AdditionalEntity = {
  entityType: 'program'
  programType:
    | 'concert'
    | 'sportingEvent'
    | 'preview'
    | 'other'
    | 'advertisement'
    | 'musicVideo'
    | 'minisode'
    | 'extra'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlayableEntity

```typescript
type PlayableEntity =
  | MovieEntity
  | TVEpisodeEntity
  | PlaylistEntity
  | MusicEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.PlaylistEntity
Entity.MusicEntity
Entity.AdditionalEntity

---

### WayToWatch

A WayToWatch describes a way to watch a video program. It may describe a single
streamable asset or a set of streamable assets. For example, an app provider may
describe HD, SD, and UHD assets as individual WayToWatch objects or rolled into
a single WayToWatch.

If the WayToWatch represents a single streamable asset, the provided
ContentIdentifiers must be sufficient to play back the specific asset when sent
via a playback intent or deep link. If the WayToWatch represents multiple
streamable assets, the provided ContentIdentifiers must be sufficient to
playback one of the assets represented with no user action. In this scenario,
the app SHOULD choose the best asset for the user based on their device and
settings. The ContentIdentifiers MUST also be sufficient for navigating the user
to the appropriate entity or detail screen via an entity intent.

The app should set the `entitled` property to indicate if the user can watch, or
not watch, the asset without making a purchase. If the entitlement is known to
expire at a certain time (e.g., a rental), the app should also provide the
`entitledExpires` property. If the entitlement is not expired, the UI will use
the `entitled` property to display watchable assets to the user, adjust how
assets are presented to the user, and how intents into the app are generated.
For example, the the Aggregated Experience could render a "Watch" button for an
entitled asset versus a "Subscribe" button for an non-entitled asset.

The app should set the `offeringType` to define how the content may be
authorized. The UI will use this to adjust how content is presented to the user.

A single WayToWatch cannot represent streamable assets available via multiple
purchase paths. If, for example, an asset has both Buy, Rent and Subscription
availability, the three different entitlement paths MUST be represented as
multiple WayToWatch objects.

`price` should be populated for WayToWatch objects with `buy` or `rent`
`offeringType`. If the WayToWatch represents a set of assets with various price
points, the `price` provided must be the lowest available price.

```typescript
type WayToWatch = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  expires?: string // Time when the WayToWatch is no longer available.
  entitled?: boolean // Specify if the user is entitled to watch the entity.
  entitledExpires?: string // Time when the entity is no longer entitled.
  offeringType?: OfferingType // The offering type of the WayToWatch.
  hasAds?: boolean // True if the streamable asset contains ads.
  price?: number // For "buy" and "rent" WayToWatch, the price to buy or rent in the user's preferred currency.
  videoQuality?: 'SD' | 'HD' | 'UHD'[] // List of the video qualities available via the WayToWatch.
  audioProfile: AudioProfile[] // List of the audio types available via the WayToWatch.
  audioLanguages?: string[] // List of audio track languages available on the WayToWatch. The first is considered the primary language. Languages are expressed as ISO 639 1/2 codes.
  closedCaptions?: string[] // List of languages for which closed captions are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  subtitles?: string[] // List of languages for which subtitles are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  audioDescriptions?: string[] // List of languages for which audio descriptions (DVD) as available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.OfferingType
Types.AudioProfile

---

### AppInfo

Information about an app that a grant was for

```typescript
type AppInfo = {
  id: string
  title?: string
}
```

---

### ContentIdentifiers

The ContentIdentifiers object is how the app identifies an entity or asset to
the Firebolt platform. These ids are used to look up metadata and deep link into
the app.

Apps do not need to provide all ids. They only need to provide the minimum
required to target a playable stream or an entity detail screen via a deep link.
If an id isn't needed to get to those pages, it doesn't need to be included.

```typescript
type ContentIdentifiers = {
  assetId?: string // Identifies a particular playable asset. For example, the HD version of a particular movie separate from the UHD version.
  entityId?: string // Identifies an entity, such as a Movie, TV Series or TV Episode.
  seasonId?: string // The TV Season for a TV Episode.
  seriesId?: string // The TV Series for a TV Episode or TV Season.
  appContentData?: string // App-specific content identifiers.
}
```

---

### ContentRating

A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.

## United States

`US-Movie` (MPAA):

Ratings: `NR`, `G`, `PG`, `PG13`, `R`, `NC17`

Advisories: `AT`, `BN`, `SL`, `SS`, `N`, `V`

`US-TV` (Vchip):

Ratings: `TVY`, `TVY7`, `TVG`, `TVPG`, `TV14`, `TVMA`

Advisories: `FV`, `D`, `L`, `S`, `V`

## Canada

`CA-Movie` (OFRB):

Ratings: `G`, `PG`, `14A`, `18A`, `R`, `E`

`CA-TV` (AGVOT)

Ratings: `E`, `C`, `C8`, `G`, `PG`, `14+`, `18+`

Advisories: `C`, `C8`, `G`, `PG`, `14+`, `18+`

`CA-Movie-Fr` (Canadian French language movies):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

`CA-TV-Fr` (Canadian French language TV):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

```typescript
type ContentRating = {
  scheme:
    | 'CA-Movie'
    | 'CA-TV'
    | 'CA-Movie-Fr'
    | 'CA-TV-Fr'
    | 'US-Movie'
    | 'US-TV' // The rating scheme.
  rating: string // The content rating.
  advisories?: string[] // Optional list of subratings or content advisories.
}
```

---

### GrantState

The state the grant is in

```typescript
GrantState: {
    GRANTED: 'granted',
    DENIED: 'denied',
},

```

---

### HDMIPortId

```typescript
type HDMIPortId = string
```

---

### EntityInfo

An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.

Additionally, EntityInfo objects must specify a properly formed
ContentIdentifiers object, `entityType`, and `title`. The app should provide
the `synopsis` property for a good user experience if the content
metadata is not available another way.

The ContentIdentifiers must be sufficient for navigating the user to the
appropriate entity or detail screen via a `detail` intent or deep link.

EntityInfo objects must provide at least one WayToWatch object when returned as
part of an `entityInfo` method and a streamable asset is available to the user.
It is optional for the `purchasedContent` method, but recommended because the UI
may use those data.

```typescript
type EntityInfo = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  title: string // Title of the entity.
  entityType: 'program' | 'music' // The type of the entity, e.g. `program` or `music`.
  programType?: ProgramType // In the case of a program `entityType`, specifies the program type.
  musicType?: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.ProgramType
Entertainment.MusicType
Entertainment.ContentRating
Entertainment.WayToWatch

---

### AgePolicy

The policy that describes various age groups to which content is directed. See distributor documentation for further details.

```typescript
type AgePolicy = string | 'app:adult' | 'app:child' | 'app:teen'
```

---

### HomeIntent

A Firebolt compliant representation of a user intention to navigate an app to it's home screen, and bring that app to the foreground if needed.

```typescript
type HomeIntent = {
  action: 'home'
  context: object
}
```

---

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: 'launch'
  context: object
}
```

---

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: 'entity'
  data:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  context: object
}
```

---

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: 'playback'
  data: PlayableEntity
  context: object
}
```

See also:

Entity.PlayableEntity

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  action: 'search'
  data?: object
  context: object
}
```

---

### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  action: 'section'
  data: object
  context: object
}
```

---

### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  action: 'tune'
  data: object
  context: object
}
```

See also:

Entity.ChannelEntity

---

### PlayEntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlayEntityIntent = {
  action: 'play-entity'
  data: object
  context: object
}
```

See also:

Entity.PlayableEntity

---

### PlayQueryIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for an abstract query to be searched for and played by the app.

```typescript
type PlayQueryIntent = {
  action: 'play-query'
  data: object
  context: object
}
```

See also:

Entertainment.ProgramType
Entertainment.MusicType

---

### Intent

A Firebolt compliant representation of a user intention.

```typescript
type Intent = {
  action: string
  context: object
}
```

See also:

Policies.AgePolicy

---

### IntentProperties

```typescript
type IntentProperties = {}
```

---

### ResultReason

The reason for the result of challenging the user

```typescript
ResultReason: {
    NO_PIN_REQUIRED: 'noPinRequired',
    NO_PIN_REQUIRED_WINDOW: 'noPinRequiredWindow',
    EXCEEDED_PIN_FAILURES: 'exceededPinFailures',
    CORRECT_PIN: 'correctPin',
    CANCELLED: 'cancelled',
},

```

---
