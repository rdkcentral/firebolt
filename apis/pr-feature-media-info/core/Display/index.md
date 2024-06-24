---
title: Display

version: pr-feature-media-info
layout: default
sdk: core
---

# Display Module

---

Version Display 1.2.0-feature-media-info.4

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [colorDepth](#colordepth)
  - [colorimetry](#colorimetry)
  - [hdrProfiles](#hdrprofiles)
  - [listen](#listen)
  - [manufacturer](#manufacturer)
  - [once](#once)
  - [productName](#productname)
  - [refreshRate](#refreshrate)
  - [resolution](#resolution)
  - [resolutionName](#resolutionname)
  - [size](#size)
  - [sourcePhysicalAddress](#sourcephysicaladdress)
- [Events](#events)
  - [colorDepthChanged](#colordepthchanged)
  - [colorimetryChanged](#colorimetrychanged)
  - [hdrProfilesChanged](#hdrprofileschanged)
  - [manufacturerChanged](#manufacturerchanged)
  - [productNameChanged](#productnamechanged)
  - [refreshRateChanged](#refreshratechanged)
  - [resolutionChanged](#resolutionchanged)
  - [resolutionNameChanged](#resolutionnamechanged)
  - [sizeChanged](#sizechanged)
  - [sourcePhysicalAddressChanged](#sourcephysicaladdresschanged)
- [Types](#types)

## Usage

To use the Display module, you can import it into your project from the Firebolt SDK:

```javascript
import { Display } from '@firebolt-js/sdk'
```

## Overview

A module for querying various aspects of the current (or built-in) display on a device

## Methods

### colorDepth

Get the maximum color depth supported by the display panel.

To get the value of `colorDepth` call the method like this:

```typescript
function colorDepth(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorDepth = await Display.colorDepth()
console.log(colorDepth)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.colorDepth",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 10
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorDepth = await Display.colorDepth()
console.log(colorDepth)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.colorDepth",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 0
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function colorDepth(callback: (value) => number): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await colorDepth((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onColorDepthChanged",
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
  "result": 10
}
```

</details>

Example with no display

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await colorDepth((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorDepth`:

```javascript
10
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onColorDepthChanged",
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
  "result": 0
}
```

</details>

---

### colorimetry

Get all colorimetry values from the display panel.

To get the value of `colorimetry` call the method like this:

```typescript
function colorimetry(): Promise<Colorimetry[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let colorimetry = await Display.colorimetry()
console.log(colorimetry)
```

Value of `colorimetry`:

```javascript
;['BT2020RGB', 'BT2020YCC', 'xvYCC601', 'xvYCC709']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.colorimetry",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["BT2020RGB", "BT2020YCC", "xvYCC601", "xvYCC709"]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function colorimetry(callback: (value) => Colorimetry[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await colorimetry((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `colorimetry`:

```javascript
;['BT2020RGB', 'BT2020YCC', 'xvYCC601', 'xvYCC709']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onColorimetryChanged",
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
  "result": ["BT2020RGB", "BT2020YCC", "xvYCC601", "xvYCC709"]
}
```

</details>

---

### hdrProfiles

Get all HDR profiles supported by the display.

To get the value of `hdrProfiles` call the method like this:

```typescript
function hdrProfiles(): Promise<HDRProfile[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let hdrProfiles = await Display.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['dolbyVision', 'hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.hdrProfiles",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["dolbyVision", "hdr10", "hdr10plus", "hlg"]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdrProfiles(callback: (value) => HDRProfile[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await hdrProfiles((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdrProfiles`:

```javascript
;['dolbyVision', 'hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onHdrProfilesChanged",
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
  "result": ["dolbyVision", "hdr10", "hdr10plus", "hlg"]
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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Display.clear(id)` |

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Display.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### manufacturer

Get the manufacturer of the display device.

To get the value of `manufacturer` call the method like this:

```typescript
function manufacturer(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let manufacturer = await Display.manufacturer()
console.log(manufacturer)
```

Value of `manufacturer`:

```javascript
'Samsung Electric Company'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.manufacturer",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Samsung Electric Company"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function manufacturer(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await manufacturer((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `manufacturer`:

```javascript
'Samsung Electric Company'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onManufacturerChanged",
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
  "result": "Samsung Electric Company"
}
```

</details>

---

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Display.clear(id)` |

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Display.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### productName

Get the product/model name of the display device.

To get the value of `productName` call the method like this:

```typescript
function productName(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let productName = await Display.productName()
console.log(productName)
```

Value of `productName`:

```javascript
'Q80A'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.productName",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Q80A"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function productName(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await productName((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `productName`:

```javascript
'Q80A'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onProductNameChanged",
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
  "result": "Q80A"
}
```

</details>

---

### refreshRate

Get the native refresh rate of the display device.

To get the value of `refreshRate` call the method like this:

```typescript
function refreshRate(): Promise<number>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let refreshRate = await Display.refreshRate()
console.log(refreshRate)
```

Value of `refreshRate`:

```javascript
60
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.refreshRate",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": 60
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function refreshRate(callback: (value) => number): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await refreshRate((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `refreshRate`:

```javascript
60
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onRefreshRateChanged",
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
  "result": 60
}
```

</details>

---

### resolution

Get the resolution of the display device in pixels. Returns a zero value for width and height if no display is present.

To get the value of `resolution` call the method like this:

```typescript
function resolution(): Promise<Dimensions>
```

Promise resolution:

[Dimensions](../Media/schemas/#Dimensions)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolution = await Display.resolution()
console.log(resolution)
```

Value of `resolution`:

```javascript
;[1920, 1080]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.resolution",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [1920, 1080]
}
```

</details>

No Display Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolution = await Display.resolution()
console.log(resolution)
```

Value of `resolution`:

```javascript
;[1920, 1080]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.resolution",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [0, 0]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function resolution(callback: (value) => Dimensions): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await resolution((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `resolution`:

```javascript
;[1920, 1080]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onResolutionChanged",
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
  "result": [1920, 1080]
}
```

</details>

No Display Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await resolution((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `resolution`:

```javascript
;[1920, 1080]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onResolutionChanged",
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
  "result": [0, 0]
}
```

</details>

---

### resolutionName

Get a user-friendly resolution name of the display device.

To get the value of `resolutionName` call the method like this:

```typescript
function resolutionName(): Promise<ResolutionName>
```

Promise resolution:

[ResolutionName](../Media/schemas/#ResolutionName)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let resolutionName = await Display.resolutionName()
console.log(resolutionName)
```

Value of `resolutionName`:

```javascript
'uhd'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.resolutionName",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "uhd"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function resolutionName(callback: (value) => ResolutionName): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await resolutionName((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `resolutionName`:

```javascript
'uhd'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onResolutionNameChanged",
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
  "result": "uhd"
}
```

</details>

---

### size

Get the width and height of the display panel (in centimeters).

To get the value of `size` call the method like this:

```typescript
function size(): Promise<Dimensions>
```

Promise resolution:

[Dimensions](../Media/schemas/#Dimensions)

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let size = await Display.size()
console.log(size)
```

Value of `size`:

```javascript
;[157, 91]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.size",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [157, 91]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function size(callback: (value) => Dimensions): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await size((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `size`:

```javascript
;[157, 91]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onSizeChanged",
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
  "result": [157, 91]
}
```

</details>

---

### sourcePhysicalAddress

Get the source physical address of the display device.

To get the value of `sourcePhysicalAddress` call the method like this:

```typescript
function sourcePhysicalAddress(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:display:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let sourcePhysicalAddress = await Display.sourcePhysicalAddress()
console.log(sourcePhysicalAddress)
```

Value of `sourcePhysicalAddress`:

```javascript
'3.0.0.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.sourcePhysicalAddress",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "3.0.0.0"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function sourcePhysicalAddress(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Display } from '@firebolt-js/sdk'

let listenerId = await sourcePhysicalAddress((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `sourcePhysicalAddress`:

```javascript
'3.0.0.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Display.onSourcePhysicalAddressChanged",
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
  "result": "3.0.0.0"
}
```

</details>

---

## Events

### colorDepthChanged

See: [colorDepth](#colordepth)

### colorimetryChanged

See: [colorimetry](#colorimetry)

### hdrProfilesChanged

See: [hdrProfiles](#hdrprofiles)

### manufacturerChanged

See: [manufacturer](#manufacturer)

### productNameChanged

See: [productName](#productname)

### refreshRateChanged

See: [refreshRate](#refreshrate)

### resolutionChanged

See: [resolution](#resolution)

### resolutionNameChanged

See: [resolutionName](#resolutionname)

### sizeChanged

See: [size](#size)

### sourcePhysicalAddressChanged

See: [sourcePhysicalAddress](#sourcephysicaladdress)

## Types
