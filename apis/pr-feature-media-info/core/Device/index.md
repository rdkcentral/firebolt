---
title: Device

version: pr-feature-media-info
layout: default
sdk: core
---

# Device Module

---

Version Device 1.2.0-feature-media-info.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audio](#audio)
  - [audioFormatPossible](#audioformatpossible)
  - [audioFormatSupported](#audioformatsupported)
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
  - [supportedResolutions](#supportedresolutions)
  - [type](#type)
  - [uid](#uid)
  - [version](#version)
  - [videoFormatPossible](#videoformatpossible)
  - [videoFormatSupported](#videoformatsupported)
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
  - [VideoFormat](#videoformat)
  - [VideoFormatResolution](#videoformatresolution)
  - [AudioFormat](#audioformat)
  - [AudioChannels](#audiochannels)
  - [DeviceResolution](#deviceresolution)
  - [NetworkState](#networkstate)
  - [NetworkType](#networktype)
  - [Resolution](#resolution)
  - [AudioProfiles](#audioprofiles)

## Usage

To use the Device module, you can import it into your project from the Firebolt SDK:

```javascript
import { Device } from '@firebolt-js/sdk'
```

## Overview

A module for querying about the device and it's capabilities.

## Methods

### audio

Get the supported audio profiles

To get the value of `audio` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:device:info |


#### Examples


Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let supportedAudioProfiles = await Device.audio()
console.log(supportedAudioProfiles)
````

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
function audio(callback: (value) => ): Promise<number>
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

### audioFormatPossible

Check whether content of a given audio format and channel output is supported by the device regardless of its configuration. These values will never change without a restart of the device.

```typescript
${method.signature}
```

Parameters:

| Param      | Type | Required | Description                                                                                                                                                                                                         |
| ---------- | ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `format`   | ``   | true     | Audio format used to check whether its supported. values: `'AAC' \| 'AC3' \| 'AC4' \| 'DOLBY_MAT' \| 'DTS' \| 'DTS_X' \| 'EAC3' \| 'MPEG' \| 'MPEG1' \| 'MPEG2' \| 'MPEG4' \| 'OPUS' \| 'OGG' \| 'TRUEHD' \| 'WAV'` |
| `channels` | ``   | false    | An audio channels value used to check whether its supported. values: `'MONO' \| 'STEREO' \| 'SURROUND' \| 'SURROUND_5_1' \| 'SURROUND_7_1'`                                                                         |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Specify the audio format and channel to check

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let audioFormatPossible = await Device.audioFormatPossible('AAC', 'MONO')
console.log(audioFormatPossible)
```

Value of `audioFormatPossible`:

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
  "method": "Device.audioFormatPossible",
  "params": {
    "format": "AAC",
    "channels": "MONO"
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

### audioFormatSupported

Check whether content of a given audio format and channel output is supported by the device's current configuration. These values may change as different AV inputs are activated or connected.

```typescript
${method.signature}
```

Parameters:

| Param      | Type | Required | Description                                                                                                                                                                                                         |
| ---------- | ---- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `format`   | ``   | true     | Audio format used to check whether its supported. values: `'AAC' \| 'AC3' \| 'AC4' \| 'DOLBY_MAT' \| 'DTS' \| 'DTS_X' \| 'EAC3' \| 'MPEG' \| 'MPEG1' \| 'MPEG2' \| 'MPEG4' \| 'OPUS' \| 'OGG' \| 'TRUEHD' \| 'WAV'` |
| `channels` | ``   | false    | An audio channels value used to check whether its supported. values: `'MONO' \| 'STEREO' \| 'SURROUND' \| 'SURROUND_5_1' \| 'SURROUND_7_1'`                                                                         |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Specify the audio format and channel to check

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let audioFormatSupported = await Device.audioFormatSupported('AAC', 'MONO')
console.log(audioFormatSupported)
```

Value of `audioFormatSupported`:

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
  "method": "Device.audioFormatSupported",
  "params": {
    "format": "AAC",
    "channels": "MONO"
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

### distributor

Get the distributor ID for this device

To get the value of `distributor` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

```typescript
string
```

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

Get the supported HDCP profiles

To get the value of `hdcp` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:device:info |


#### Examples


Getting the supported HDCP profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let supportedHdcpProfiles = await Device.hdcp()
console.log(supportedHdcpProfiles)
````

Value of `supportedHdcpProfiles`:

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
function hdcp(callback: (value) => ): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the supported HDCP profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdcp((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `supportedHdcpProfiles`:

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

Returns an array of valid HDR profiles that the device supports

To get the value of `hdr` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:device:info |


#### Examples


The supported HDR profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let supportedHdrProfiles = await Device.hdr()
console.log(supportedHdrProfiles)
````

Value of `supportedHdrProfiles`:

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
function hdr(callback: (value) => ): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

The supported HDR profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdr((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `supportedHdrProfiles`:

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
${method.signature}
```

Promise resolution:

```typescript
string
```

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

Get the device make

To get the value of `make` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

```typescript
string
```

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

Get the device model

To get the value of `model` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

```typescript
string
```

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
${method.signature}
```

Promise resolution:

```typescript
string
```

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
${method.signature}
```

Promise resolution:

| Property | Type | Description |
| -------- | ---- | ----------- |
| `state`  |      |             |
| `type`   |      |             |

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
function network(callback: (value) => | Property | Type | Description |
|----------|------|-------------|
| `${property}` | [${type}](${type.link}) | ${description} |
): Promise<number>
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

Get the platform ID for this device

To get the value of `platform` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

```typescript
string
```

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

Get the current screen resolution

To get the value of `screenResolution` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:device:info |


#### Examples


Getting the screen resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let screenResolution = await Device.screenResolution()
console.log(screenResolution)
````

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
function screenResolution(callback: (value) => ): Promise<number>
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
${method.signature}
```

Promise resolution:

```typescript
string
```

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

### supportedResolutions

Returns an array of valid resolutions that the device supports, regardless of any connected display.

```typescript
${method.signature}
```

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let resolutions = await Device.supportedResolutions()
console.log(resolutions)
```

Value of `resolutions`:

```javascript
;[
  '1080p24',
  '1080i25',
  '1080p30',
  '1080i50',
  '1080p50',
  '1080p60',
  '2160p30',
  '2160p50',
  '2160p60',
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.supportedResolutions",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    "1080p24",
    "1080i25",
    "1080p30",
    "1080i50",
    "1080p50",
    "1080p60",
    "2160p30",
    "2160p50",
    "2160p60"
  ]
}
```

</details>

---

### type

Get the device type

To get the value of `type` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

```typescript
string
```

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
${method.signature}
```

Promise resolution:

```typescript
string
```

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
${method.signature}
```

Promise resolution:

| Property   | Type   | Description                                                      |
| ---------- | ------ | ---------------------------------------------------------------- |
| `sdk`      |        | The Firebolt SDK version                                         |
| `api`      |        | The lateset Firebolt API version supported by the curent device. |
| `firmware` |        | The device firmware version.                                     |
| `os`       |        | **Deprecated** Use firmware instead                              |
| `debug`    | string | Detail version as a string, for debugging purposes               |

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

### videoFormatPossible

Check whether content of a given a video format and resolution is supported by the device regardless of its configuration. These values will never change without a restart of the device.

```typescript
${method.signature}
```

Parameters:

| Param        | Type | Required | Description                                                                                                                                                                                                                                                                                         |
| ------------ | ---- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `format`     | ``   | true     | The video format used to check whether its supported by the device. values: `'av1' \| 'dolbyVision' \| 'h263' \| 'h264' \| 'h265' \| 'h265M10' \| 'mpeg' \| 'vp8' \| 'vp9' \| 'vp9_p2' \| 'vp10' \| 'vc1'`                                                                                          |
| `resolution` | ``   | false    | The video resolution used to check whether its supported by the device. values: `'480i' \| '480p' \| '576i' \| '576p' \| '576p50' \| '720p' \| '720p50' \| '1080i' \| '1080p' \| '1080p24' \| '1080i25' \| '1080p30' \| '1080i50' \| '1080p50' \| '1080p60' \| '2160p30' \| '2160p50' \| '2160p60'` |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Specify the video format and resolution to check.

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoFormatPossible = await Device.videoFormatPossible('av1', '1080i')
console.log(videoFormatPossible)
```

Value of `videoFormatPossible`:

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
  "method": "Device.videoFormatPossible",
  "params": {
    "format": "av1",
    "resolution": "1080i"
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

### videoFormatSupported

Check whether content of a given a video format and resolution is supported by the device's current configuration. These values may change as different AV inputs are activated or connected.

```typescript
${method.signature}
```

Parameters:

| Param        | Type | Required | Description                                                                                                                                                                                                                                                                                                                 |
| ------------ | ---- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `format`     | ``   | true     | The video format used to check whether its supported by the device's current configuration. values: `'av1' \| 'dolbyVision' \| 'h263' \| 'h264' \| 'h265' \| 'h265M10' \| 'mpeg' \| 'vp8' \| 'vp9' \| 'vp9_p2' \| 'vp10' \| 'vc1'`                                                                                          |
| `resolution` | ``   | false    | The video resolution used to check whether its supported by the device's current configuration. values: `'480i' \| '480p' \| '576i' \| '576p' \| '576p50' \| '720p' \| '720p50' \| '1080i' \| '1080p' \| '1080p24' \| '1080i25' \| '1080p30' \| '1080i50' \| '1080p50' \| '1080p60' \| '2160p30' \| '2160p50' \| '2160p60'` |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Specify the video format and resolution to check

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoFormatSupported = await Device.videoFormatSupported('av1', '1080i')
console.log(videoFormatSupported)
```

Value of `videoFormatSupported`:

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
  "method": "Device.videoFormatSupported",
  "params": {
    "format": "av1",
    "resolution": "1080i"
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

### videoResolution

Get the current video resolution

To get the value of `videoResolution` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:device:info |


#### Examples


Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoResolution = await Device.videoResolution()
console.log(videoResolution)
````

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
function videoResolution(callback: (value) => ): Promise<number>
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

```typescript
string
```

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

### VideoFormat

The video format supported by the platform

```typescript
VideoFormat Enumeration:

| key | value |
|-----|-------|
| AV_1 | av1 |
| DOLBY_VISION | dolbyVision |
| H_263 | h263 |
| H_264 | h264 |
| H_265 | h265 |
| H_265M10 | h265M10 |
| MPEG | mpeg |
| VP_8 | vp8 |
| VP_9 | vp9 |
| VP_9_P_2 | vp9_p2 |
| VP_10 | vp10 |
| VC_1 | vc1 |

```

---

### VideoFormatResolution

```typescript
VideoFormatResolution Enumeration:

| key | value |
|-----|-------|
| V480I | 480i |
| V480P | 480p |
| V576I | 576i |
| V576P | 576p |
| V576P_50 | 576p50 |
| V720P | 720p |
| V720P_50 | 720p50 |
| V1080I | 1080i |
| V1080P | 1080p |
| V1080P_24 | 1080p24 |
| V1080I_25 | 1080i25 |
| V1080P_30 | 1080p30 |
| V1080I_50 | 1080i50 |
| V1080P_50 | 1080p50 |
| V1080P_60 | 1080p60 |
| V2160P_30 | 2160p30 |
| V2160P_50 | 2160p50 |
| V2160P_60 | 2160p60 |

```

---

### AudioFormat

The audio format supported by the platform

```typescript
AudioFormat Enumeration:

| key | value |
|-----|-------|
| AAC | AAC |
| AC3 | AC3 |
| AC4 | AC4 |
| DOLBY_MAT | DOLBY_MAT |
| DTS | DTS |
| DTS_X | DTS_X |
| EAC3 | EAC3 |
| MPEG | MPEG |
| MPEG1 | MPEG1 |
| MPEG2 | MPEG2 |
| MPEG4 | MPEG4 |
| OPUS | OPUS |
| OGG | OGG |
| TRUEHD | TRUEHD |
| WAV | WAV |

```

---

### AudioChannels

The audio channels supported by the platform

```typescript
AudioChannels Enumeration:

| key | value |
|-----|-------|
| MONO | MONO |
| STEREO | STEREO |
| SURROUND | SURROUND |
| SURROUND_5_1 | SURROUND_5_1 |
| SURROUND_7_1 | SURROUND_7_1 |

```

---

### DeviceResolution

The list of resolutions supported by the device

```typescript
DeviceResolution Enumeration:

| key | value |
|-----|-------|
| V1080P_24 | 1080p24 |
| V1080I_25 | 1080i25 |
| V1080P_30 | 1080p30 |
| V1080I_50 | 1080i50 |
| V1080P_50 | 1080p50 |
| V1080P_60 | 1080p60 |
| V2160P_30 | 2160p30 |
| V2160P_50 | 2160p50 |
| V2160P_60 | 2160p60 |

```

---

### NetworkState

The type of network that is currently active

```typescript
NetworkState Enumeration:

| key | value |
|-----|-------|
| CONNECTED | connected |
| DISCONNECTED | disconnected |

```

---

### NetworkType

The type of network that is currently active

```typescript
NetworkType Enumeration:

| key | value |
|-----|-------|
| WIFI | wifi |
| ETHERNET | ethernet |
| HYBRID | hybrid |

```

---

### Resolution

````typescript
```typescript

````

````



---

### AudioProfiles



```typescript
```typescript

````

```

See also:




---
```
