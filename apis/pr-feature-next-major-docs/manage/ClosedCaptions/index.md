---
title: ClosedCaptions

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# ClosedCaptions Module

---

Version ClosedCaptions 1.1.1-feature-next-major-docs.0

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

```typescript
type Color = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.backgroundColor(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundColorChanged",
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
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundColorChanged",
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
  "result": "#ffffff"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundColorChanged",
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
  "result": null
}
```

</details>

---

### backgroundOpacity

The preferred opacity for displaying closed-captions backgrounds.

To get the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(): Promise<number>
```

Promise resolution:

```typescript
type Opacity = number
```

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

```typescript
null
```

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

let result = await ClosedCaptions.backgroundOpacity(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
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
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
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
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await backgroundOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onBackgroundOpacityChanged",
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
  "result": null
}
```

</details>

---

### enabled

Whether or not closed-captions are enabled.

To get the value of `enabled` call the method like this:

```typescript
function enabled(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

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

```typescript
null
```

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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onEnabledChanged",
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

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await enabled((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onEnabledChanged",
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
  "result": false
}
```

</details>

---

### fontColor

The preferred font color for displaying closed-captions.

To get the value of `fontColor` call the method like this:

```typescript
function fontColor(): Promise<string>
```

Promise resolution:

```typescript
type Color = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontColor(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontColorChanged",
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
  "result": "#ffffff"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontColorChanged",
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
  "result": "#000000"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontColorChanged",
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
  "result": null
}
```

</details>

---

### fontEdge

The preferred font edge style for displaying closed-captions.

To get the value of `fontEdge` call the method like this:

```typescript
function fontEdge(): Promise<string>
```

Promise resolution:

```typescript
type FontEdge = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontEdge(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdge((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeChanged",
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
  "result": "none"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdge((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeChanged",
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
  "result": "uniform"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdge((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeChanged",
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
  "result": null
}
```

</details>

---

### fontEdgeColor

The preferred font edge color for displaying closed-captions.

To get the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(): Promise<string>
```

Promise resolution:

```typescript
type Color = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontEdgeColor(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdgeColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeColorChanged",
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
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdgeColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeColorChanged",
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
  "result": "#ffffff"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontEdgeColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontEdgeColorChanged",
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
  "result": null
}
```

</details>

---

### fontFamily

The preferred font family for displaying closed-captions.

To get the value of `fontFamily` call the method like this:

```typescript
function fontFamily(): Promise<string>
```

Promise resolution:

```typescript
type FontFamily = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontFamily(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontFamily((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontFamilyChanged",
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
  "result": "monospaced_sanserif"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontFamily((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontFamilyChanged",
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
  "result": "cursive"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontFamily((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontFamilyChanged",
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
  "result": null
}
```

</details>

---

### fontOpacity

The preferred opacity for displaying closed-captions characters.

To get the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(): Promise<number>
```

Promise resolution:

```typescript
type Opacity = number
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontOpacity(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontOpacityChanged",
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
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontOpacityChanged",
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
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontOpacityChanged",
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
  "result": null
}
```

</details>

---

### fontSize

The preferred font size for displaying closed-captions.

To get the value of `fontSize` call the method like this:

```typescript
function fontSize(): Promise<number>
```

Promise resolution:

```typescript
type FontSize = number
```

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

```typescript
null
```

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

let result = await ClosedCaptions.fontSize(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontSize((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontSizeChanged",
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
  "result": 1
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontSize((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontSizeChanged",
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
  "result": 1
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await fontSize((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onFontSizeChanged",
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
  "result": null
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

```typescript
string[]
```

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

```typescript
null
```

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

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await preferredLanguages((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
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
  "result": ["spa", "eng"]
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await preferredLanguages((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onPreferredLanguagesChanged",
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
  "result": ["eng", "spa"]
}
```

</details>

---

### textAlign

The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlign` call the method like this:

```typescript
function textAlign(): Promise<string>
```

Promise resolution:

```typescript
type HorizontalAlignment = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.textAlign(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlign((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignChanged",
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
  "result": "center"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlign((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignChanged",
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
  "result": "left"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlign((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignChanged",
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
  "result": null
}
```

</details>

---

### textAlignVertical

The preferred horizontal alignment for displaying closed-captions characters.

To get the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(): Promise<string>
```

Promise resolution:

```typescript
type VerticalAlignment = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.textAlignVertical(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlignVertical((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
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
  "result": "middle"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlignVertical((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
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
  "result": "top"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await textAlignVertical((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onTextAlignVerticalChanged",
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
  "result": null
}
```

</details>

---

### windowColor

The preferred window color for displaying closed-captions, .

To get the value of `windowColor` call the method like this:

```typescript
function windowColor(): Promise<string>
```

Promise resolution:

```typescript
type Color = string
```

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

```typescript
null
```

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

let result = await ClosedCaptions.windowColor(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowColorChanged",
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
  "result": "#000000"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowColorChanged",
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
  "result": "white"
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowColor((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowColorChanged",
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
  "result": null
}
```

</details>

---

### windowOpacity

The preferred window opacity for displaying closed-captions backgrounds.

To get the value of `windowOpacity` call the method like this:

```typescript
function windowOpacity(): Promise<number>
```

Promise resolution:

```typescript
type Opacity = number
```

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

```typescript
null
```

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

let result = await ClosedCaptions.windowOpacity(null)
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

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowOpacityChanged",
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
  "result": 99
}
```

</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowOpacityChanged",
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
  "result": 100
}
```

</details>

Default example #3

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

let listenerId = await windowOpacity((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "ClosedCaptions.onWindowOpacityChanged",
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
  "result": null
}
```

</details>

---

## Events

### backgroundColorChanged

See: [backgroundColor](#backgroundcolor)

### backgroundOpacityChanged

See: [backgroundOpacity](#backgroundopacity)

### enabledChanged

See: [enabled](#enabled)

### fontColorChanged

See: [fontColor](#fontcolor)

### fontEdgeChanged

See: [fontEdge](#fontedge)

### fontEdgeColorChanged

See: [fontEdgeColor](#fontedgecolor)

### fontFamilyChanged

See: [fontFamily](#fontfamily)

### fontOpacityChanged

See: [fontOpacity](#fontopacity)

### fontSizeChanged

See: [fontSize](#fontsize)

### preferredLanguagesChanged

See: [preferredLanguages](#preferredlanguages)

### textAlignChanged

See: [textAlign](#textalign)

### textAlignVerticalChanged

See: [textAlignVertical](#textalignvertical)

### windowColorChanged

See: [windowColor](#windowcolor)

### windowOpacityChanged

See: [windowOpacity](#windowopacity)
