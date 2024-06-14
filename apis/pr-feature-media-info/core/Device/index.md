---
title: Device

version: pr-feature-media-info
layout: default
sdk: core
---

# Device Module

---

Version Device 1.2.0-feature-media-info.1

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audio](#audio)
  - [audioFormatSupported](#audioformatsupported)
  - [audioMode](#audiomode)
  - [distributor](#distributor)
  - [hdcp](#hdcp)
  - [hdcpVersionSupported](#hdcpversionsupported)
  - [hdr](#hdr)
  - [hdrProfile](#hdrprofile)
  - [hdrProfiles](#hdrprofiles)
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
  - [sourceFrameRateUsed](#sourceframerateused)
  - [type](#type)
  - [uid](#uid)
  - [version](#version)
  - [videoFormatSupported](#videoformatsupported)
  - [videoMode](#videomode)
  - [videoModes](#videomodes)
  - [videoResolution](#videoresolution)
- [Events](#events)
  - [audioChanged](#audiochanged)
  - [audioModeChanged](#audiomodechanged)
  - [audioOutputChanged](#audiooutputchanged)
  - [deviceNameChanged](#devicenamechanged)
  - [hdcpChanged](#hdcpchanged)
  - [hdrProfileChanged](#hdrprofilechanged)
  - [nameChanged](#namechanged)
  - [networkChanged](#networkchanged)
  - [screenResolutionChanged](#screenresolutionchanged)
  - [sourceFrameRateUsedChanged](#sourceframerateusedchanged)
  - [videoModeChanged](#videomodechanged)
  - [videoModesChanged](#videomodeschanged)
  - [videoOutputChanged](#videooutputchanged)
  - [videoResolutionChanged](#videoresolutionchanged)
- [Types](#types)
  - [HDCPVersion](#hdcpversion)
  - [NetworkState](#networkstate)
  - [NetworkType](#networktype)
  - [AudioFormatOptions](#audioformatoptions)
  - [VideoFormatOptions](#videoformatoptions)
  - [AudioProfiles](#audioprofiles)
  - [Resolution](#resolution)

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
function audio(): Promise<AudioProfiles>
```

Promise resolution:

[AudioProfiles](#audioprofiles)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

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

Default Example

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

### audioFormatSupported

Check whether content of a given audio format is supported by the device's current configuration. The result is based on the device's best possible audio output configuration. These values may change as different AV inputs or peripherals are activated or connected.

```typescript
function audioFormatSupported(
  codec: AudioCodec,
  options: AudioFormatOptions,
): Promise<boolean>
```

Parameters:

| Param     | Type                                         | Required | Description                                                                                                                                                            |
| --------- | -------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `codec`   | [`AudioCodec`](../Media/schemas/#AudioCodec) | true     | Audio codec used to check whether its supported. <br/>values: `'aac' \| 'ac3' \| 'ac4' \| 'dts-x' \| 'eac3' \| 'mpeg3' \| 'opus' \| 'truehd' \| 'unknown' \| 'vorbis'` |
| `options` | [`AudioFormatOptions`](#audioformatoptions)  | false    | Additional options to use for checking whether an audio format is supported by the device. All values must be true for the content to be playable.                     |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Check whether EAC3 codec with Atmos is supported

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let audioFormatSupported = await Device.audioFormatSupported('eac3', {
  atmos: true,
})
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
    "codec": "eac3",
    "options": {
      "atmos": true
    }
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

### audioMode

Get the current audio output mode of the device.

To get the value of `audioMode` call the method like this:

```typescript
function audioMode(): Promise<AudioMode>
```

Promise resolution:

[AudioMode](../Media/schemas/#AudioMode)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let audioMode = await Device.audioMode()
console.log(audioMode)
```

Value of `audioMode`:

```javascript
'stereo'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.audioMode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "stereo"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audioMode(callback: (value) => AudioMode): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await audioMode((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `audioMode`:

```javascript
'stereo'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onAudioModeChanged",
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
  "result": "stereo"
}
```

</details>

---

### distributor

Get the distributor ID for this device

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

Get the supported HDCP versions available for content transmission

To get the value of `hdcp` call the method like this:

```typescript
function hdcp(): Promise<BooleanMap>
```

Promise resolution:

[BooleanMap](../Types/schemas/#BooleanMap)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdcp = await Device.hdcp()
console.log(hdcp)
```

Value of `hdcp`:

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
function hdcp(callback: (value) => BooleanMap): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdcp((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdcp`:

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

### hdcpVersionSupported

Get the HDCP version supported by the device

To get the value of `hdcpVersionSupported` call the method like this:

```typescript
function hdcpVersionSupported(): Promise<HDCPVersion>
```

Promise resolution:

[HDCPVersion](#hdcpversion-1)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdcpVersionSupported = await Device.hdcpVersionSupported()
console.log(hdcpVersionSupported)
```

Value of `hdcpVersionSupported`:

```javascript
'2.2'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdcpVersionSupported",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "2.2"
}
```

</details>

---

### hdr

Returns an array of valid HDR profiles that the device supports

To get the value of `hdr` call the method like this:

```typescript
function hdr(): Promise<BooleanMap>
```

Promise resolution:

[BooleanMap](../Types/schemas/#BooleanMap)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdr = await Device.hdr()
console.log(hdr)
```

Value of `hdr`:

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

### hdrProfile

Get the current HDR profile set on the device for video output.

To get the value of `hdrProfile` call the method like this:

```typescript
function hdrProfile(): Promise<HDRProfile>
```

Promise resolution:

[HDRProfile](../Media/schemas/#HDRProfile)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdrProfile = await Device.hdrProfile()
console.log(hdrProfile)
```

Value of `hdrProfile`:

```javascript
'hdr10'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdrProfile",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "hdr10"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdrProfile(callback: (value) => HDRProfile): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await hdrProfile((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `hdrProfile`:

```javascript
'hdr10'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onHdrProfileChanged",
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
  "result": "hdr10"
}
```

</details>

---

### hdrProfiles

Get all HDR profiles supported by the device, regardless of any connected display.

To get the value of `hdrProfiles` call the method like this:

```typescript
function hdrProfiles(): Promise<HDRProfile[]>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Example with a device and display that both support HDR

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdrProfiles = await Device.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdrProfiles",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["hdr10", "hdr10plus", "hlg"]
}
```

</details>

Example with either a device or display that does not support HDR

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdrProfiles = await Device.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdrProfiles",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["sdr"]
}
```

</details>

Example where no display is present

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let hdrProfiles = await Device.hdrProfiles()
console.log(hdrProfiles)
```

Value of `hdrProfiles`:

```javascript
;['hdr10', 'hdr10plus', 'hlg']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.hdrProfiles",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": []
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

Get the device make

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

Get the device model

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
function network(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:network:status |

#### Examples

Default Example

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
function network(callback: (value) => object): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

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

Get the width and height of the current screen resolution.

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

Default Example

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

Default Example

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

### sourceFrameRateUsed

Check whether the HDMI output frame rate is set to follow the video source frame rate.

To get the value of `sourceFrameRateUsed` call the method like this:

```typescript
function sourceFrameRateUsed(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let sourceFrameRateUsed = await Device.sourceFrameRateUsed()
console.log(sourceFrameRateUsed)
```

Value of `sourceFrameRateUsed`:

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
  "method": "Device.sourceFrameRateUsed",
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
function sourceFrameRateUsed(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await sourceFrameRateUsed((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `sourceFrameRateUsed`:

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
  "method": "Device.onSourceFrameRateUsedChanged",
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
function version(): Promise<object>
```

Promise resolution:

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

### videoFormatSupported

Check whether video content of the given format is supported by the device's current configuration. These values may change as different AV inputs or peripherals are activated or connected.

```typescript
function videoFormatSupported(
  codec: VideoCodec,
  options: VideoFormatOptions,
): Promise<boolean>
```

Parameters:

| Param     | Type                                         | Required | Description                                                                                                                                                                     |
| --------- | -------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `codec`   | [`VideoCodec`](../Media/schemas/#VideoCodec) | true     | The video codec to check whether its supported by the device's current configuration. <br/>values: `'av1' \| 'avc' \| 'hevc' \| 'mpeg1' \| 'mpeg2' \| 'vp8' \| 'vp9' \| 'vp10'` |
| `options` | [`VideoFormatOptions`](#videoformatoptions)  | false    | Additional options to use for checking whether a video is supported by the device. All values must be true for the content to be playable.                                      |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Specify the video format to check

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoFormatSupported = await Device.videoFormatSupported('avc', {
  resolution: [1920, 1080],
})
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
    "codec": "avc",
    "options": {
      "resolution": [1920, 1080]
    }
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

### videoMode

Get the current video output mode of the device.

To get the value of `videoMode` call the method like this:

```typescript
function videoMode(): Promise<VideoMode>
```

Promise resolution:

[VideoMode](../Media/schemas/#VideoMode)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoMode = await Device.videoMode()
console.log(videoMode)
```

Value of `videoMode`:

```javascript
'1080p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.videoMode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "1080p60"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoMode(callback: (value) => VideoMode): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await videoMode((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoMode`:

```javascript
'1080p60'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onVideoModeChanged",
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
  "result": "1080p60"
}
```

</details>

---

### videoModes

Returns an array of all valid video output modes that the device and display together support.

To get the value of `videoModes` call the method like this:

```typescript
function videoModes(): Promise<VideoMode[]>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let videoModes = await Device.videoModes()
console.log(videoModes)
```

Value of `videoModes`:

```javascript
;[
  '720p50',
  '720p60',
  '1080i50',
  '1080i60',
  '1080p24',
  '1080p30',
  '1080p50',
  '1080p60',
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.videoModes",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    "720p50",
    "720p60",
    "1080i50",
    "1080i60",
    "1080p24",
    "1080p30",
    "1080p50",
    "1080p60"
  ]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoModes(callback: (value) => VideoMode[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await videoModes((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `videoModes`:

```javascript
;[
  '720p50',
  '720p60',
  '1080i50',
  '1080i60',
  '1080p24',
  '1080p30',
  '1080p50',
  '1080p60',
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onVideoModesChanged",
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
  "result": [
    "720p50",
    "720p60",
    "1080i50",
    "1080i60",
    "1080p24",
    "1080p30",
    "1080p50",
    "1080p60"
  ]
}
```

</details>

---

### videoResolution

Get the resolution of the current video output in pixels. Returns a zero value for width and height if no display is present.

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

Default Example

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

Default Example

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

### audioModeChanged

See: [audioMode](#audiomode)

### audioOutputChanged

```typescript
function listen('audioOutputChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

Device.listen('audioOutputChanged', (onAudioOutputChanged) => {
  console.log(onAudioOutputChanged)
})
```

Value of `onAudioOutputChanged`:

```javascript
{
	"audioMode": "stereo"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onAudioOutputChanged",
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
    "audioMode": "stereo"
  }
}
```

</details>

---

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

Default Example

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

### hdrProfileChanged

See: [hdrProfile](#hdrprofile)

### nameChanged

See: [name](#name)

### networkChanged

See: [network](#network)

### screenResolutionChanged

See: [screenResolution](#screenresolution)

### sourceFrameRateUsedChanged

See: [sourceFrameRateUsed](#sourceframerateused)

### videoModeChanged

See: [videoMode](#videomode)

### videoModesChanged

See: [videoModes](#videomodes)

### videoOutputChanged

```typescript
function listen('videoOutputChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Default Example

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

Device.listen('videoOutputChanged', (onVideoOutputChanged) => {
  console.log(onVideoOutputChanged)
})
```

Value of `onVideoOutputChanged`:

```javascript
{
	"hdrProfile": "hdr10",
	"sourceFrameRateUsed": true,
	"videoMode": "1080p60"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Device.onVideoOutputChanged",
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
    "hdrProfile": "hdr10",
    "sourceFrameRateUsed": true,
    "videoMode": "1080p60"
  }
}
```

</details>

---

### videoResolutionChanged

See: [videoResolution](#videoresolution)

## Types

### HDCPVersion

The HDCP version

```typescript
HDCPVersion: {
    HDCP_1_4: '1.4',
    HDCP_2_2: '2.2',
    HDCP_UNKNOWN: 'unknown',
},

```

---

### NetworkState

The state of the network interface

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
    ETHERNET: 'ethernet',
    HYBRID: 'hybrid',
    WIFI: 'wifi',
},

```

---

### AudioFormatOptions

Options for checking audio playback support

```typescript
type AudioFormatOptions = {
  atmos?: boolean // Whether Dolby Atmos support is being requested
  codecLevel?: string // The level of the audio codec
  codecProfile?: AudioCodecProfile // Audio codec profile
  container?: AudioContainer // Audio container
  sampleRate?: number // The sample rate of the audio, in kHz
}
```

See also:

[AudioCodecProfile](../Media/schemas/#AudioCodecProfile)
[AudioContainer](../Media/schemas/#AudioContainer)

---

### VideoFormatOptions

Options for checking video playback support

```typescript
type VideoFormatOptions = {
  atmos?: boolean // Whether Dolby Atmos support is being requested
  codecLevel?: '4.1' | '4.2' | '5.0' | '5.1' | 'high' | 'main' // The level of the video codec
  codecProfile?: 'high' | 'main' | 'main10' | 'p0' | 'p2' // The profile of the video codec
  container?: VideoContainer // Video container format
  frameRate?: number // The frame rate of the video content
  hdr?: HDRProfile // HDR profile
  resolution?: Dimensions // The dimensions specified as width and height.
}
```

See also:

[VideoContainer](../Media/schemas/#VideoContainer)
[HDRProfile](../Media/schemas/#HDRProfile)
[Dimensions](../Media/schemas/#Dimensions)

---

### AudioProfiles

```typescript
type AudioProfiles = {
  STEREO?: boolean

  DOLBY_DIGITAL_5_1?: boolean

  DOLBY_DIGITAL_7_1?: boolean

  DOLBY_DIGITAL_5_1_PLUS?: boolean

  DOLBY_DIGITAL_7_1_PLUS?: boolean

  DOLBY_ATMOS?: boolean
}
```

See also:

[BooleanMap](../Types/schemas/#BooleanMap)
[AudioProfile](../Types/schemas/#AudioProfile)

---

### Resolution

```typescript
type Resolution = [
  number, // undefined  item
  number, // undefined  item
]
```

---
