---
title: Device

version: pr-fix-upload-artifact
layout: default
sdk: core
---

# Device Module

---

Version Device 1.5.0-fix-upload-artifact.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audio](#audio)
  - [distributor](#distributor)
  - [hdcp](#hdcp)
  - [hdr](#hdr)
  - [id](#id)
  - [listen](#listen)
  - [make](#make)
  - [model](#model)
  - [name](#name)
  - [network](#network)
  - [once](#once)
  - [platform](#platform)
  - [screenResolution](#screenresolution)
  - [sku](#sku)
  - [type](#type)
  - [uid](#uid)
  - [version](#version)
  - [videoResolution](#videoresolution)
- [Events](#events)
  - [audioChanged](#audiochanged)
  - [deviceNameChanged](#devicenamechanged)
  - [hdcpChanged](#hdcpchanged)
  - [hdrChanged](#hdrchanged)
  - [nameChanged](#namechanged)
  - [networkChanged](#networkchanged)
  - [screenResolutionChanged](#screenresolutionchanged)
  - [videoResolutionChanged](#videoresolutionchanged)
- [Types](#types)
  - [NetworkState](#networkstate)
  - [NetworkType](#networktype)
  - [HDRFormatMap](#hdrformatmap)
  - [AudioProfiles](#audioprofiles)
  - [Resolution](#resolution)
  - [NetworkInfoResult](#networkinforesult)
  - [DeviceVersion](#deviceversion)
  - [HDCPVersionMap](#hdcpversionmap)

## Usage

To use the Device module, you can import it into your project from the Firebolt SDK:

```javascript
import { Device } from '@firebolt-js/sdk'
```

## Overview

A module for querying about the device and it's capabilities.

## Methods

### audio

Get the supported audio profiles for the connected devices.

It is not recommended to use this API for visual badging on content within your app since this does not reflect the settings of the user.

To get the value of `audio` call the method like this:

```typescript
function audio(): Promise<AudioProfiles>
```

Promise resolution:

[AudioProfiles](#audioprofiles)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let supportedAudioProfiles = await Device.audio()
console.log(supportedAudioProfiles)
```

Value of `supportedAudioProfiles`:

```javascript
{
	"stereo": true,
	"dolbyDigital5.1": true,
	"dolbyDigital5.1+": true,
	"dolbyAtmos": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.audio",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "stereo": true,
    "dolbyDigital5.1": true,
    "dolbyDigital5.1+": true,
    "dolbyAtmos": true
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audio(callback: (value) => AudioProfiles): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await audio((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `supportedAudioProfiles`:

```javascript
{
	"stereo": true,
	"dolbyDigital5.1": true,
	"dolbyDigital5.1+": true,
	"dolbyAtmos": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onAudioChanged",
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
    "stereo": true,
    "dolbyDigital5.1": true,
    "dolbyDigital5.1+": true,
    "dolbyAtmos": true
  }
}
```

</details>

---

### distributor

Get the name of the entity which is distributing the current device. There can be multiple distributors which distribute the same device model.

To get the value of `distributor` call the method like this:

```typescript
function distributor(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:device:distributor |

#### Examples

Getting the distributor ID

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let distributorId = await Device.distributor()
console.log(distributorId)
```

Value of `distributorId`:

```javascript
'Company'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.distributor",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Company"
}
```

</details>

---

### hdcp

Get the negotiated HDCP profiles for a connected device.

For devices that do not require additional connections (e.g. panels), `true` will be returned for all profiles.

To get the value of `hdcp` call the method like this:

```typescript
function hdcp(): Promise<HDCPVersionMap>
```

Promise resolution:

[HDCPVersionMap](#hdcpversionmap)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDCP versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let negotiatedHdcpVersions = await Device.hdcp()
console.log(negotiatedHdcpVersions)
```

Value of `negotiatedHdcpVersions`:

```javascript
{
	"hdcp1.4": true,
	"hdcp2.2": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdcp",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "hdcp1.4": true,
    "hdcp2.2": true
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdcp(callback: (value) => HDCPVersionMap): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the negotiated HDCP versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdcp((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `negotiatedHdcpVersions`:

```javascript
{
	"hdcp1.4": true,
	"hdcp2.2": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onHdcpChanged",
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
    "hdcp1.4": true,
    "hdcp2.2": true
  }
}
```

</details>

---

### hdr

Get the negotiated HDR formats for the connected display and device

To get the value of `hdr` call the method like this:

```typescript
function hdr(): Promise<HDRFormatMap>
```

Promise resolution:

[HDRFormatMap](#hdrformatmap)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDR formats

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let negotiatedHdrFormats = await Device.hdr()
console.log(negotiatedHdrFormats)
```

Value of `negotiatedHdrFormats`:

```javascript
{
	"hdr10": true,
	"hdr10Plus": true,
	"dolbyVision": true,
	"hlg": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdr",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "hdr10": true,
    "hdr10Plus": true,
    "dolbyVision": true,
    "hlg": true
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdr(callback: (value) => HDRFormatMap): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the negotiated HDR formats

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdr((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `negotiatedHdrFormats`:

```javascript
{
	"hdr10": true,
	"hdr10Plus": true,
	"dolbyVision": true,
	"hlg": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onHdrChanged",
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
    "hdr10": true,
    "hdr10Plus": true,
    "dolbyVision": true,
    "hlg": true
  }
}
```

</details>

---

### id

Get the platform back-office device identifier

To get the value of `id` call the method like this:

```typescript
function id(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                        |
| ---- | --------------------------------- |
| uses | xrn:firebolt:capability:device:id |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let id = await Device.id()
console.log(id)
```

Value of `id`:

```javascript
'123'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.id",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "123"
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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### make

Get the manufacturer of the device model

To get the value of `make` call the method like this:

```typescript
function make(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:make |

#### Examples

Getting the device make

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let make = await Device.make()
console.log(make)
```

Value of `make`:

```javascript
'Arris'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.make",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Arris"
}
```

</details>

---

### model

Get the manufacturer designated model of the device

To get the value of `model` call the method like this:

```typescript
function model(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:device:model |

#### Examples

Getting the device model

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let model = await Device.model()
console.log(model)
```

Value of `model`:

```javascript
'xi6'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.model",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "xi6"
}
```

</details>

---

### name

The human readable name of the device

To get the value of `name` call the method like this:

```typescript
function name(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

Default example #1

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let value = await Device.name()
console.log(value)
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.name",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let value = await Device.name()
console.log(value)
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.name",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Kitchen"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function name(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await name((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onNameChanged",
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
  "result": "Living Room"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await name((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onNameChanged",
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
  "result": "Kitchen"
}
```

</details>

---

### network

Get the current network status and type

To get the value of `network` call the method like this:

```typescript
function network(): Promise<NetworkInfoResult>
```

Promise resolution:

[NetworkInfoResult](#networkinforesult)

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:network:status |

#### Examples

Getting the network info

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let networkInfo = await Device.network()
console.log(networkInfo)
```

Value of `networkInfo`:

```javascript
{
	"state": "connected",
	"type": "wifi"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.network",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "state": "connected",
    "type": "wifi"
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function network(callback: (value) => NetworkInfoResult): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the network info

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await network((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `networkInfo`:

```javascript
{
	"state": "connected",
	"type": "wifi"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onNetworkChanged",
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
    "state": "connected",
    "type": "wifi"
  }
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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

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

| Type     | Description                                                                                    |
| -------- | ---------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Device.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### platform

Get a platform identifier for the device. This API should be used to correlate metrics on the device only and cannot be guaranteed to have consistent responses across platforms.

To get the value of `platform` call the method like this:

```typescript
function platform(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the platform ID

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let platformId = await Device.platform()
console.log(platformId)
```

Value of `platformId`:

```javascript
'WPE'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.platform",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "WPE"
}
```

</details>

---

### screenResolution

Get the resolution for the graphical surface of the app.

The pairs returned will be of a [width, height] format and will correspond to the following values:

NTSC Standard Definition (SD): [720, 480]

PAL Standard Definition (SD): [720, 576]

High Definition (HD): [1280, 720]

Full HD (FHD): [1920, 1080]

4K Ultra High Definition (UHD): [3840, 2160]

**Deprecated:** Use non-Firebolt APIs specific to your platform, e.g. W3C APIs

To get the value of `screenResolution` call the method like this:

```typescript
function screenResolution(): Promise<Resolution>
```

Promise resolution:

[Resolution](#resolution)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the screen resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let screenResolution = await Device.screenResolution()
console.log(screenResolution)
```

Value of `screenResolution`:

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
  "method": "Device.screenResolution",
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

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function screenResolution(callback: (value) => Resolution): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the screen resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await screenResolution((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `screenResolution`:

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
  "method": "Device.onScreenResolutionChanged",
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

---

### sku

Get the device sku

To get the value of `sku` call the method like this:

```typescript
function sku(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                         |
| ---- | ---------------------------------- |
| uses | xrn:firebolt:capability:device:sku |

#### Examples

Getting the device sku

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let sku = await Device.sku()
console.log(sku)
```

Value of `sku`:

```javascript
'AX061AEI'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.sku",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "AX061AEI"
}
```

</details>

---

### type

Get the device type

To get the value of `type` call the method like this:

```typescript
function type(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the device type

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let deviceType = await Device.type()
console.log(deviceType)
```

Value of `deviceType`:

```javascript
'STB'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.type",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "STB"
}
```

</details>

---

### uid

Gets a unique id for the current app & device

To get the value of `uid` call the method like this:

```typescript
function uid(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                         |
| ---- | ---------------------------------- |
| uses | xrn:firebolt:capability:device:uid |

#### Examples

Getting the unique ID

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let uniqueId = await Device.uid()
console.log(uniqueId)
```

Value of `uniqueId`:

```javascript
'ee6723b8-7ab3-462c-8d93-dbf61227998e'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.uid",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "ee6723b8-7ab3-462c-8d93-dbf61227998e"
}
```

</details>

---

### version

Get the SDK, OS and other version info

To get the value of `version` call the method like this:

```typescript
function version(): Promise<DeviceVersion>
```

Promise resolution:

[DeviceVersion](#deviceversion)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the os and sdk versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let versions = await Device.version()
console.log(versions)
```

Value of `versions`:

```javascript
{
	"sdk": {
		"major": 0,
		"minor": 8,
		"patch": 0,
		"readable": "Firebolt JS SDK v0.8.0"
	},
	"api": {
		"major": 0,
		"minor": 8,
		"patch": 0,
		"readable": "Firebolt API v0.8.0"
	},
	"firmware": {
		"major": 1,
		"minor": 2,
		"patch": 3,
		"readable": "Device Firmware v1.2.3"
	},
	"os": {
		"major": 0,
		"minor": 1,
		"patch": 0,
		"readable": "Firebolt OS v0.1.0"
	},
	"debug": "Non-parsable build info for error logging only."
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.version",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "sdk": {
      "major": 0,
      "minor": 8,
      "patch": 0,
      "readable": "Firebolt JS SDK v0.8.0"
    },
    "api": {
      "major": 0,
      "minor": 8,
      "patch": 0,
      "readable": "Firebolt API v0.8.0"
    },
    "firmware": {
      "major": 1,
      "minor": 2,
      "patch": 3,
      "readable": "Device Firmware v1.2.3"
    },
    "os": {
      "major": 0,
      "minor": 1,
      "patch": 0,
      "readable": "Firebolt OS v0.1.0"
    },
    "debug": "Non-parsable build info for error logging only."
  }
}
```

</details>

---

### videoResolution

Get the maximum supported video resolution of the currently connected device and display.

The pairs returned will be of a [width, height] format and will correspond to the following values:

NTSC Standard Definition (SD): [720, 480]

PAL Standard Definition (SD): [720, 576]

High Definition (HD): [1280, 720]

Full HD (FHD): [1920, 1080]

4K Ultra High Definition (UHD): [3840, 2160]

To get the value of `videoResolution` call the method like this:

```typescript
function videoResolution(): Promise<Resolution>
```

Promise resolution:

[Resolution](#resolution)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoResolution = await Device.videoResolution()
console.log(videoResolution)
```

Value of `videoResolution`:

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
  "method": "Device.videoResolution",
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

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoResolution(callback: (value) => Resolution): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await videoResolution((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoResolution`:

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
  "method": "Device.onVideoResolutionChanged",
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

---

## Events

### audioChanged

See: [audio](#audio)

### deviceNameChanged

```typescript
function listen('deviceNameChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

Getting the device name

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

Device.listen('deviceNameChanged', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
'Living Room'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onDeviceNameChanged",
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
  "result": "Living Room"
}
```

</details>

---

### hdcpChanged

See: [hdcp](#hdcp)

### hdrChanged

See: [hdr](#hdr)

### nameChanged

See: [name](#name)

### networkChanged

See: [network](#network)

### screenResolutionChanged

See: [screenResolution](#screenresolution)

### videoResolutionChanged

See: [videoResolution](#videoresolution)

## Types

### NetworkState

The type of network that is currently active

```typescript
NetworkState: {
    CONNECTED: 'connected',
    DISCONNECTED: 'disconnected',
},

```

---

### NetworkType

The type of network that is currently active

```typescript
NetworkType: {
    WIFI: 'wifi',
    ETHERNET: 'ethernet',
    HYBRID: 'hybrid',
},

```

---

### HDRFormatMap

The type of HDR format

```typescript
type HDRFormatMap = {
  hdr10: boolean
  hdr10Plus: boolean
  dolbyVision: boolean
  hlg: boolean
}
```

---

### AudioProfiles

```typescript
type AudioProfiles = {
  stereo: boolean
  dolbyDigital5_1: boolean
  dolbyDigital5_1_plus: boolean
  dolbyAtmos: boolean
}
```

---

### Resolution

```typescript
type Resolution =
  | [
      720, // undefined Width in pixels item
      480, // undefined Height in pixels item
    ]
  | [
      720, // undefined Width in pixels item
      576, // undefined Height in pixels item
    ]
  | [
      1280, // undefined Width in pixels item
      720, // undefined Height in pixels item
    ]
  | [
      1920, // undefined Width in pixels item
      1080, // undefined Height in pixels item
    ]
  | [
      3840, // undefined Width in pixels item
      2160, // undefined Height in pixels item
    ]
```

---

### NetworkInfoResult

```typescript
type NetworkInfoResult = {
  state: NetworkState // The type of network that is currently active
  type: NetworkType // The type of network that is currently active
}
```

See also:

[NetworkState](#networkstate)
[NetworkType](#networktype)

---

### DeviceVersion

```typescript
type DeviceVersion = {
  sdk?: SemanticVersion // The Firebolt SDK version
  api: SemanticVersion // The latest Firebolt API version supported by the current device.
  firmware: SemanticVersion // The firmware version as reported by the device
  os: SemanticVersion // **Deprecated** Use `firmware`, instead.
  debug?: string // Detailed version as a string, for debugging purposes
}
```

See also:

[SemanticVersion](../Types/schemas/#SemanticVersion)

---

### HDCPVersionMap

The type of HDCP versions

```typescript
type HDCPVersionMap = {
  hdcp1_4: boolean
  hdcp2_2: boolean
}
```

---
