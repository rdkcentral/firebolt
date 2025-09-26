---
title: Device

version: next-major
layout: default
sdk: core
---

# Device Module

---

Version Device 1.8.0-next-major.2

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
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [deviceNameChanged](#devicenamechanged-1)
  - [hdcpChanged](#hdcpchanged-1)
  - [hdrChanged](#hdrchanged-1)
  - [nameChanged](#namechanged-1)
  - [networkChanged](#networkchanged-1)
  - [screenResolutionChanged](#screenresolutionchanged-1)
  - [videoResolutionChanged](#videoresolutionchanged-1)
  </details>
- [Types](#types)
  - [NetworkType](#networktype)
  - [NetworkState](#networkstate)
  - [EDIDVersion](#edidversion)
  - [WifiSecurityMode](#wifisecuritymode)
  - [AudioProfile](#audioprofile)
  - [SkipRestriction](#skiprestriction)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [OfferingType](#offeringtype)
  - [MusicType](#musictype)
  - [ProgramType](#programtype)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [EventObject](#eventobject)
  - [AudioProfiles](#audioprofiles)
  - [WifiSignalStrength](#wifisignalstrength)
  - [WifiFrequency](#wififrequency)
  - [SemanticVersion](#semanticversion)
  - [HDRFormatMap](#hdrformatmap)
  - [SpeechRate](#speechrate)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [FontFamily](#fontfamily)
  - [FontSize](#fontsize)
  - [Color](#color)
  - [FontEdge](#fontedge)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ISO639_2Language](#isolanguage)
  - [HDCPVersionMap](#hdcpversionmap)
  - [Capability](#capability)
  - [DeviceVersion](#deviceversion)
  - [CapPermissionStatus](#cappermissionstatus)
  - [NetworkInfoResult](#networkinforesult)
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
  - [Availability](#availability)
  - [ContentIdentifiers](#contentidentifiers)
  - [ContentRating](#contentrating)
- [United States](#united-states)
- [Canada](#canada)
  - [HDMIPortId](#hdmiportid)
  - [Resolution](#resolution)
  - [Entitlement](#entitlement)
  - [EntityInfo](#entityinfo)
  - [AgePolicy](#agepolicy)
  - [NavigationIntent](#navigationintent)
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
  - [SecondScreenEvent](#secondscreenevent)
  - [LifecycleState](#lifecyclestate)

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
{"stereo":true,"dolbyDigital5.1":true,"dolbyDigital5.1+":true,"dolbyAtmos":true}
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

Parameters:

| Param                    | Type                              | Required | Description                  |
| ------------------------ | --------------------------------- | -------- | ---------------------------- |
| `supportedAudioProfiles` | [`AudioProfiles`](#audioprofiles) | false    | the supported audio profiles |

Promise resolution:

```
number
```

#### Examples

Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('audioChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### distributor
Get the name of the entity which is distributing the current device. There can be multiple distributors which distribute the same device model.

To get the value of `distributor` call the method like this:

```typescript
function distributor(): Promise<string>
````

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
{"hdcp1.4":true,"hdcp2.2":true}
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

Parameters:

| Param                    | Type                                | Required | Description                  |
| ------------------------ | ----------------------------------- | -------- | ---------------------------- |
| `negotiatedHdcpVersions` | [`HDCPVersionMap`](#hdcpversionmap) | false    | the negotiated HDCP versions |

Promise resolution:

```
number
```

#### Examples

Getting the negotiated HDCP versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdcpChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### hdr
Get the negotiated HDR formats for the connected display and device

To get the value of `hdr` call the method like this:

```typescript
function hdr(): Promise<HDRFormatMap>
````

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
{"hdr10":true,"hdr10Plus":true,"dolbyVision":true,"hlg":true}
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

Parameters:

| Param                  | Type                            | Required | Description                |
| ---------------------- | ------------------------------- | -------- | -------------------------- |
| `negotiatedHdrFormats` | [`HDRFormatMap`](#hdrformatmap) | false    | the negotiated HDR formats |

Promise resolution:

```
number
```

#### Examples

Getting the negotiated HDR formats

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdrChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### id
Get the platform back-office device identifier

To get the value of `id` call the method like this:

```typescript
function id(): Promise<string>
````

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
{
	"Default Result": [
		1920,
		1080
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
  "method": "Device.id",
  "params": {}
}
```

Response:

```json
{
  "Default Result": [1920, 1080]
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

Parameters:

| Param   | Type     | Required | Description              |
| ------- | -------- | -------- | ------------------------ |
| `value` | `string` | false    | the device friendly-name |

Promise resolution:

```
number
```

#### Examples

Getting the device name

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('deviceNameChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"Default Result": "Living Room"
}
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### network
Get the current network status and type

To get the value of `network` call the method like this:

```typescript
function network(): Promise<NetworkInfoResult>
````

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
{"state":"connected","type":"wifi"}
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

Parameters:

| Param         | Type                                      | Required | Description         |
| ------------- | ----------------------------------------- | -------- | ------------------- |
| `networkInfo` | [`NetworkInfoResult`](#networkinforesult) | false    | the status and type |

Promise resolution:

```
number
```

#### Examples

Getting the network info

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('networkChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
````

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
function screenResolution(): Promise<
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
>
```

Promise resolution:

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
function  W3C APIs(callback: (value) => [
    720, // undefined Width in pixels item
    480 // undefined Height in pixels item
] | [
    720, // undefined Width in pixels item
    576 // undefined Height in pixels item
] | [
    1280, // undefined Width in pixels item
    720 // undefined Height in pixels item
] | [
    1920, // undefined Width in pixels item
    1080 // undefined Height in pixels item
] | [
    3840, // undefined Width in pixels item
    2160 // undefined Height in pixels item
]): Promise<number>
```

Parameters:

| Param              | Type | Required | Description |
| ------------------ | ---- | -------- | ----------- |
| `screenResolution` | [`[  |

    720, // undefined Width in pixels item
    480 // undefined Height in pixels item

] | [
720, // undefined Width in pixels item
576 // undefined Height in pixels item
] | [
1280, // undefined Width in pixels item
720 // undefined Height in pixels item
] | [
1920, // undefined Width in pixels item
1080 // undefined Height in pixels item
] | [
3840, // undefined Width in pixels item
2160 // undefined Height in pixels item
]`](#) | false | the resolution |

Promise resolution:

```
number
```

#### Examples

Getting the screen resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('screenResolutionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### sku
Get the device sku

To get the value of `sku` call the method like this:

```typescript
function sku(): Promise<string>
````

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
{"sdk":{"major":0,"minor":8,"patch":0,"readable":"Firebolt JS SDK v0.8.0"},"api":{"major":0,"minor":8,"patch":0,"readable":"Firebolt API v0.8.0"},"firmware":{"major":1,"minor":2,"patch":3,"readable":"Device Firmware v1.2.3"},"os":{"major":0,"minor":1,"patch":0,"readable":"Firebolt OS v0.1.0"},"debug":"Non-parsable build info for error logging only."}
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
function videoResolution(): Promise<
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
>
```

Promise resolution:

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
function videoResolution(
  callback: (value) =>
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
      ],
): Promise<number>
```

Parameters:

| Param             | Type | Required | Description |
| ----------------- | ---- | -------- | ----------- |
| `videoResolution` | [`[  |

    720, // undefined Width in pixels item
    480 // undefined Height in pixels item

] | [
720, // undefined Width in pixels item
576 // undefined Height in pixels item
] | [
1280, // undefined Width in pixels item
720 // undefined Height in pixels item
] | [
1920, // undefined Width in pixels item
1080 // undefined Height in pixels item
] | [
3840, // undefined Width in pixels item
2160 // undefined Height in pixels item
]`](#) | false | the resolution |

Promise resolution:

```
number
```

#### Examples

Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('videoResolutionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---



## Events

### audioChanged





```typescript
function listen('audioChanged', (AudioProfiles) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                    | Type                              | Required | Description                  |
| ------------------------ | --------------------------------- | -------- | ---------------------------- |
| `supportedAudioProfiles` | [`AudioProfiles`](#audioprofiles) | false    | the supported audio profiles |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('audioChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### deviceNameChanged


[Deprecated] This method is deprecated as of since version 0.6.0. Please use `name` as a replacement.



---

### hdcpChanged





```typescript
function listen('hdcpChanged', (HDCPVersionMap) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                    | Type                                | Required | Description                  |
| ------------------------ | ----------------------------------- | -------- | ---------------------------- |
| `negotiatedHdcpVersions` | [`HDCPVersionMap`](#hdcpversionmap) | false    | the negotiated HDCP versions |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDCP versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdcpChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### hdrChanged





```typescript
function listen('hdrChanged', (HDRFormatMap) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                  | Type                            | Required | Description                |
| ---------------------- | ------------------------------- | -------- | -------------------------- |
| `negotiatedHdrFormats` | [`HDRFormatMap`](#hdrformatmap) | false    | the negotiated HDR formats |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDR formats

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdrChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### nameChanged





```typescript
function listen('nameChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description              |
| ------- | -------- | -------- | ------------------------ |
| `value` | `string` | false    | the device friendly-name |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

Default example #1

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('nameChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('nameChanged', result => {
  console.log(result)
})
````

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### networkChanged





```typescript
function listen('networkChanged', (NetworkInfoResult) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param         | Type                                      | Required | Description         |
| ------------- | ----------------------------------------- | -------- | ------------------- |
| `networkInfo` | [`NetworkInfoResult`](#networkinforesult) | false    | the status and type |

Event value:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:network:status |

#### Examples

Getting the network info

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('networkChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### screenResolutionChanged


[Deprecated] This method is deprecated as of since version 1.4.0. Please use ` W3C APIs` as a replacement.



---

### videoResolutionChanged





```typescript
function listen('videoResolutionChanged', ([
    720, // undefined Width in pixels item
    480 // undefined Height in pixels item
] | [
    720, // undefined Width in pixels item
    576 // undefined Height in pixels item
] | [
    1280, // undefined Width in pixels item
    720 // undefined Height in pixels item
] | [
    1920, // undefined Width in pixels item
    1080 // undefined Height in pixels item
] | [
    3840, // undefined Width in pixels item
    2160 // undefined Height in pixels item
]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param             | Type | Required | Description |
| ----------------- | ---- | -------- | ----------- |
| `videoResolution` | [`[  |

    720, // undefined Width in pixels item
    480 // undefined Height in pixels item

] | [
720, // undefined Width in pixels item
576 // undefined Height in pixels item
] | [
1280, // undefined Width in pixels item
720 // undefined Height in pixels item
] | [
1920, // undefined Width in pixels item
1080 // undefined Height in pixels item
] | [
3840, // undefined Width in pixels item
2160 // undefined Height in pixels item
]`](#) | false | the resolution |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('videoResolutionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


## Private Events
<details markdown="1"  id="private-events-details">
  <summary>View</summary>

  ### audioChanged





```typescript
function listen('audioChanged', (AudioProfiles) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                    | Type                              | Required | Description                  |
| ------------------------ | --------------------------------- | -------- | ---------------------------- |
| `supportedAudioProfiles` | [`AudioProfiles`](#audioprofiles) | false    | the supported audio profiles |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the supported audio profiles

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('audioChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### deviceNameChanged


[Deprecated] This method is deprecated as of since version 0.6.0. Please use `name` as a replacement.



---

### hdcpChanged





```typescript
function listen('hdcpChanged', (HDCPVersionMap) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                    | Type                                | Required | Description                  |
| ------------------------ | ----------------------------------- | -------- | ---------------------------- |
| `negotiatedHdcpVersions` | [`HDCPVersionMap`](#hdcpversionmap) | false    | the negotiated HDCP versions |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDCP versions

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdcpChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### hdrChanged





```typescript
function listen('hdrChanged', (HDRFormatMap) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param                  | Type                            | Required | Description                |
| ---------------------- | ------------------------------- | -------- | -------------------------- |
| `negotiatedHdrFormats` | [`HDRFormatMap`](#hdrformatmap) | false    | the negotiated HDR formats |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the negotiated HDR formats

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('hdrChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### nameChanged





```typescript
function listen('nameChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param   | Type     | Required | Description              |
| ------- | -------- | -------- | ------------------------ |
| `value` | `string` | false    | the device friendly-name |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

Default example #1

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('nameChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('nameChanged', result => {
  console.log(result)
})
````

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### networkChanged





```typescript
function listen('networkChanged', (NetworkInfoResult) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param         | Type                                      | Required | Description         |
| ------------- | ----------------------------------------- | -------- | ------------------- |
| `networkInfo` | [`NetworkInfoResult`](#networkinforesult) | false    | the status and type |

Event value:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:network:status |

#### Examples

Getting the network info

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('networkChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### screenResolutionChanged


[Deprecated] This method is deprecated as of since version 1.4.0. Please use ` W3C APIs` as a replacement.



---

### videoResolutionChanged





```typescript
function listen('videoResolutionChanged', ([
    720, // undefined Width in pixels item
    480 // undefined Height in pixels item
] | [
    720, // undefined Width in pixels item
    576 // undefined Height in pixels item
] | [
    1280, // undefined Width in pixels item
    720 // undefined Height in pixels item
] | [
    1920, // undefined Width in pixels item
    1080 // undefined Height in pixels item
] | [
    3840, // undefined Width in pixels item
    2160 // undefined Height in pixels item
]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param             | Type | Required | Description |
| ----------------- | ---- | -------- | ----------- |
| `videoResolution` | [`[  |

    720, // undefined Width in pixels item
    480 // undefined Height in pixels item

] | [
720, // undefined Width in pixels item
576 // undefined Height in pixels item
] | [
1280, // undefined Width in pixels item
720 // undefined Height in pixels item
] | [
1920, // undefined Width in pixels item
1080 // undefined Height in pixels item
] | [
3840, // undefined Width in pixels item
2160 // undefined Height in pixels item
]`](#) | false | the resolution |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

Getting the video resolution

JavaScript:

```javascript
import { Device } from '@firebolt-js/sdk'

let listenerId = await Device.listen('videoResolutionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

</details>


## Types

### NetworkType

The type of network that is currently active

```typescript
NetworkType: {
    WIFI: 'wifi',
    ETHERNET: 'ethernet',
    HYBRID: 'hybrid',
},

````

---

### NetworkState

The type of network that is currently active

```typescript
NetworkState: {
    CONNECTED: 'connected',
    DISCONNECTED: 'disconnected',
},

```

---

### EDIDVersion

```typescript
EDIDVersion: {
    V1_4: '1.4',
    V2_0: '2.0',
    UNKNOWN: 'unknown',
},

```

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

### SkipRestriction

The advertisement skip restriction.

Applies to fast-forward/rewind (e.g. trick mode), seeking over an entire opportunity (e.g. jump), seeking out of what's currently playing, and "Skip this ad..." features. Seeking over multiple ad opportunities only requires playback of the _last_ opportunity, not all opportunities, preceding the seek destination.

| Value        | Description                                                                    |
| ------------ | ------------------------------------------------------------------------------ |
| none         | No fast-forward, jump, or skip restrictions                                    |
| adsUnwatched | Restrict fast-forward, jump, and skip for unwatched ad opportunities only.     |
| adsAll       | Restrict fast-forward, jump, and skip for all ad opportunities                 |
| all          | Restrict fast-forward, jump, and skip for all ad opportunities and all content |

Namespace: `xrn:advertising:policy:skipRestriction:`

```typescript
SkipRestriction: {
    NONE: 'none',
    ADS_UNWATCHED: 'adsUnwatched',
    ADS_ALL: 'adsAll',
    ALL: 'all',
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

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
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

### SemanticVersion

```typescript
type SemanticVersion = {
  major: number
  minor: number
  patch: number
  readable: string
}
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

### HDCPVersionMap

The type of HDCP versions

```typescript
type HDCPVersionMap = {
  hdcp1_4: boolean
  hdcp2_2: boolean
}
```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

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

Types.SemanticVersion

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean
}
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

### Availability

```typescript
type Availability = {
  type: 'channel-lineup' | 'program-lineup'
  id: string
  catalogId?: string
  startTime?: string
  endTime?: string
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

### HDMIPortId

```typescript
type HDMIPortId = string
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

### Entitlement

```typescript
type Entitlement = {
  entitlementId: string
  startTime?: string
  endTime?: string
}
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

### NavigationIntent

A Firebolt compliant representation of a user intention to navigate to a specific place in an app.

```typescript
type NavigationIntent =
  | HomeIntent
  | LaunchIntent
  | EntityIntent
  | PlaybackIntent
  | SearchIntent
  | SectionIntent
  | TuneIntent
  | PlayEntityIntent
  | PlayQueryIntent
```

See also:

Intents.HomeIntent
Intents.LaunchIntent
Intents.EntityIntent
Intents.PlaybackIntent
Intents.SearchIntent
Intents.SectionIntent
Intents.TuneIntent
Intents.PlayEntityIntent
Intents.PlayQueryIntent

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

### SecondScreenEvent

An a message notification from a second screen device

```typescript
type SecondScreenEvent = {
  type: 'dial'
  version?: string
  data?: string
}
```

---

### LifecycleState

The application lifecycle state

```typescript
LifecycleState: {
    INITIALIZING: 'initializing',
    INACTIVE: 'inactive',
    FOREGROUND: 'foreground',
    BACKGROUND: 'background',
    UNLOADING: 'unloading',
    SUSPENDED: 'suspended',
},

```

---
