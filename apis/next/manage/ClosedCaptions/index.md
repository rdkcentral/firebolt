---
title: ClosedCaptions

version: next
layout: default
sdk: manage
---

# ClosedCaptions Module
---
Version ClosedCaptions 0.12.0-next.4

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
     - [textAlign](#textalign)
     - [textAlignVertical](#textalignvertical)
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
     - [textAlignChanged](#textalignchanged)
     - [textAlignVerticalChanged](#textalignverticalchanged)



## Usage
To use the ClosedCaptions module, you can import it into your project from the Firebolt SDK:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'
```


## Overview
 A module for managing closed-captions Settings.

## Methods

### backgroundColor
The prefered background color for displaying closed-captions, .

To get the value of `backgroundColor` call the method like this:

```typescript
function backgroundColor(): Promise<string>
```



Promise resolution:

```typescript
type Color = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.backgroundColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#000000"
```
<details>
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

ClosedCaptions.backgroundColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#000000"
```
<details>
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


---

To set the value of `backgroundColor` call the method like this:

```typescript
function backgroundColor(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.backgroundColor("#000000")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.backgroundColor("#ffffff")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function backgroundColor(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

backgroundColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#000000"
```
<details>
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

backgroundColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#000000"
```
<details>
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


---


### backgroundOpacity
The prefered opacity for displaying closed-captions backgrounds.

To get the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(): Promise<number>
```



Promise resolution:

```typescript
type Opacity = number
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.backgroundOpacity()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
99
```
<details>
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

ClosedCaptions.backgroundOpacity()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
99
```
<details>
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


---

To set the value of `backgroundOpacity` call the method like this:

```typescript
function backgroundOpacity(value: number): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `number` | true |  <br/>minumum: 0
maximum: 100 |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.backgroundOpacity(99)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.backgroundOpacity(100)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function backgroundOpacity(callback: (value) => number): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

backgroundOpacity(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
99
```
<details>
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

backgroundOpacity(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
99
```
<details>
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.enabled()
    .then(enabled => {
        console.log(enabled)
    })
```

Value of `enabled`:

```javascript
true
```
<details>
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

ClosedCaptions.enabled()
    .then(enabled => {
        console.log(enabled)
    })
```

Value of `enabled`:

```javascript
true
```
<details>
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.enabled(true)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.enabled(false)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

${if.javascript}

```typescript
function enabled(callback: (value) => boolean): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

enabled(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `enabled`:

```javascript
true
```
<details>
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

enabled(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `enabled`:

```javascript
true
```
<details>
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
The prefered font color for displaying closed-captions.

To get the value of `fontColor` call the method like this:

```typescript
function fontColor(): Promise<string>
```



Promise resolution:

```typescript
type Color = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#ffffff"
```
<details>
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

ClosedCaptions.fontColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#ffffff"
```
<details>
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


---

To set the value of `fontColor` call the method like this:

```typescript
function fontColor(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontColor("#ffffff")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.fontColor("#000000")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function fontColor(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#ffffff"
```
<details>
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

fontColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#ffffff"
```
<details>
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


---


### fontEdge
The prefered font edge style for displaying closed-captions.

To get the value of `fontEdge` call the method like this:

```typescript
function fontEdge(): Promise<string>
```



Promise resolution:

```typescript
type FontEdge = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontEdge()
    .then(edge => {
        console.log(edge)
    })
```

Value of `edge`:

```javascript
"none"
```
<details>
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

ClosedCaptions.fontEdge()
    .then(edge => {
        console.log(edge)
    })
```

Value of `edge`:

```javascript
"none"
```
<details>
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
	"result": "solid"
}
```
</details>


---

To set the value of `fontEdge` call the method like this:

```typescript
function fontEdge(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontEdge("none")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.fontEdge("solid")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "ClosedCaptions.setFontEdge",
	"params": {
		"value": "solid"
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

${if.javascript}

```typescript
function fontEdge(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontEdge(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `edge`:

```javascript
"none"
```
<details>
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

fontEdge(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `edge`:

```javascript
"none"
```
<details>
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
	"result": "solid"
}
```
</details>


---


### fontEdgeColor
The prefered font edge color for displaying closed-captions.

To get the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(): Promise<string>
```



Promise resolution:

```typescript
type Color = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontEdgeColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#000000"
```
<details>
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

ClosedCaptions.fontEdgeColor()
    .then(color => {
        console.log(color)
    })
```

Value of `color`:

```javascript
"#000000"
```
<details>
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


---

To set the value of `fontEdgeColor` call the method like this:

```typescript
function fontEdgeColor(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontEdgeColor("#000000")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.fontEdgeColor("#ffffff")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function fontEdgeColor(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontEdgeColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#000000"
```
<details>
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

fontEdgeColor(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `color`:

```javascript
"#000000"
```
<details>
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


---


### fontFamily
The prefered font family for displaying closed-captions.

To get the value of `fontFamily` call the method like this:

```typescript
function fontFamily(): Promise<string>
```



Promise resolution:

```typescript
type FontFamily = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontFamily()
    .then(family => {
        console.log(family)
    })
```

Value of `family`:

```javascript
"monospace"
```
<details>
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
	"result": "monospace"
}
```
</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontFamily()
    .then(family => {
        console.log(family)
    })
```

Value of `family`:

```javascript
"monospace"
```
<details>
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


---

To set the value of `fontFamily` call the method like this:

```typescript
function fontFamily(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontFamily("monospace")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "ClosedCaptions.setFontFamily",
	"params": {
		"value": "monospace"
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

ClosedCaptions.fontFamily("cursive")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function fontFamily(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontFamily(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `family`:

```javascript
"monospace"
```
<details>
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
	"result": "monospace"
}
```
</details>

Default example #2

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontFamily(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `family`:

```javascript
"monospace"
```
<details>
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


---


### fontOpacity
The prefered opacity for displaying closed-captions characters.

To get the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(): Promise<number>
```



Promise resolution:

```typescript
type Opacity = number
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontOpacity()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
99
```
<details>
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

ClosedCaptions.fontOpacity()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
99
```
<details>
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


---

To set the value of `fontOpacity` call the method like this:

```typescript
function fontOpacity(value: number): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `number` | true |  <br/>minumum: 0
maximum: 100 |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontOpacity(99)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.fontOpacity(100)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function fontOpacity(callback: (value) => number): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontOpacity(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
99
```
<details>
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

fontOpacity(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
99
```
<details>
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


---


### fontSize
The prefered font size for displaying closed-captions.

To get the value of `fontSize` call the method like this:

```typescript
function fontSize(): Promise<number>
```



Promise resolution:

```typescript
type FontSize = number
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontSize()
    .then(size => {
        console.log(size)
    })
```

Value of `size`:

```javascript
1
```
<details>
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

ClosedCaptions.fontSize()
    .then(size => {
        console.log(size)
    })
```

Value of `size`:

```javascript
1
```
<details>
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


---

To set the value of `fontSize` call the method like this:

```typescript
function fontSize(value: number): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `number` | true |  <br/>minumum: 0 |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.fontSize(1)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.fontSize(1)
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function fontSize(callback: (value) => number): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

fontSize(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `size`:

```javascript
1
```
<details>
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

fontSize(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `size`:

```javascript
1
```
<details>
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


---


### listen

To listen to a specific event pass the event name as the first parameter:

```typescript
listen(event: string, callback: (data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module  pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
```

The `once` method will only pass the next instance of this event, and then dicard the listener you provided.

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `ClosedCaptions.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.












### textAlign
The prefered horizontal alignment for displaying closed-captions characters.

To get the value of `textAlign` call the method like this:

```typescript
function textAlign(): Promise<string>
```



Promise resolution:

```typescript
type HorizontalAlignment = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.textAlign()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
"center"
```
<details>
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

ClosedCaptions.textAlign()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
"center"
```
<details>
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


---

To set the value of `textAlign` call the method like this:

```typescript
function textAlign(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.textAlign("center")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.textAlign("left")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function textAlign(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

textAlign(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
"center"
```
<details>
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

textAlign(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
"center"
```
<details>
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


---


### textAlignVertical
The prefered horizontal alignment for displaying closed-captions characters.

To get the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(): Promise<string>
```



Promise resolution:

```typescript
type VerticalAlignment = string
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:accessibility:closedcaptions |


#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.textAlignVertical()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
"middle"
```
<details>
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

ClosedCaptions.textAlignVertical()
    .then(opacity => {
        console.log(opacity)
    })
```

Value of `opacity`:

```javascript
"middle"
```
<details>
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


---

To set the value of `textAlignVertical` call the method like this:

```typescript
function textAlignVertical(value: string): Promise<void>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `string` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

ClosedCaptions.textAlignVertical("middle")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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

ClosedCaptions.textAlignVertical("top")
    .then(result => {
        console.log(result)
    })
```

Value of `result`:

```javascript
null
```
<details>
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


---


To subscribe to notifications when the value changes, call the method like this:

${if.javascript}

```typescript
function textAlignVertical(callback: (value) => string): Promise<number>
```

${end.if.javascript}



Promise resolution:

```
number
```

#### Examples


Default example #1

JavaScript:

```javascript
import { ClosedCaptions } from '@firebolt-js/manage-sdk'

textAlignVertical(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
"middle"
```
<details>
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

textAlignVertical(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
```

Value of `opacity`:

```javascript
"middle"
```
<details>
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

### textAlignChanged

See: [textAlign](#textalign)

### textAlignVerticalChanged

See: [textAlignVertical](#textalignvertical)



