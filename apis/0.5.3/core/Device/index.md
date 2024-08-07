---
title: Device
---

# Device Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [device.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/device.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)
    - [deviceNameChanged](#evicenamechanged)
 - [Methods](#methods)
    - [id](#id)
    - [distributor](#distributor)
    - [platform](#platform)
    - [uid](#uid)
    - [type](#type)
    - [model](#model)
    - [sku](#sku)
    - [make](#make)
    - [version](#version)
    - [hdcp](#hdcp)
    - [hdr](#hdr)
    - [audio](#audio)
    - [screenResolution](#screenresolution)
    - [videoResolution](#videoresolution)
    - [name](#name)
    - [network](#network)
 - [Schemas](#schemas)
    - [Resolution](#resolution)
    - [NetworkType](#networktype)
    - [NetworkState](#networkstate)
    - [AudioProfiles](#audioprofiles)
    - [AudioProfile](#audioprofile)

<span></span>

## Usage
To use the Device module, you can import it into your project from the Firebolt SDK:

```javascript
import { Device } from '@firebolt-js/sdk'
```
## Overview
A module for querying about the device and it's capabilities.

## Events
### deviceNameChanged
Get the human readable name of the device

```typescript
// listen to deviceNameChanged
Device.listen('deviceNameChanged', (data: string) => void): Promise<bigint>

// listen to deviceNameChanged once
Device.once('deviceNameChanged', (data: string) => void): Promise<bigint>

// clear a listener
Device.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| `string` | the device friendly-name |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Device.clear(id)` |

#### Examples

##### Getting the device name
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.listen('deviceNameChanged', value => {
  console.log(value)
})
```
Value of `value`

```javascript
"Living Room"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

<h6>Request</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.onDeviceNameChanged",
  "params": {}
}
```

<h6>Response</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Device.listen('deviceNameChanged', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Device.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Device.once('deviceNameChanged', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Device.clear('deviceNameChanged')
```
</details>

---



## Methods
### id
Get the platform back-office device identifier

```typescript
function id(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the id |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.id()
    .then(id => {
        console.log(id)
    })
```
Value of `id`

```javascript
"123"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.id",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "123"
}
```

</details>




---

### distributor
Get the distributor ID for this device

```typescript
function distributor(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the distributor ID |


---

#### Examples

##### Getting the distributor ID
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.distributor()
    .then(distributorId => {
        console.log(distributorId)
    })
```
Value of `distributorId`

```javascript
"Company"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.distributor",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Company"
}
```

</details>




---

### platform
Get the platform ID for this device

```typescript
function platform(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the platform ID |


---

#### Examples

##### Getting the platform ID
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.platform()
    .then(platformId => {
        console.log(platformId)
    })
```
Value of `platformId`

```javascript
"WPE"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.platform",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "WPE"
}
```

</details>




---

### uid
Gets a unique id for the current app & device

```typescript
function uid(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | a unique ID |


---

#### Examples

##### Getting the unique ID
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.uid()
    .then(uniqueId => {
        console.log(uniqueId)
    })
```
Value of `uniqueId`

```javascript
"ee6723b8-7ab3-462c-8d93-dbf61227998e"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.uid",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "ee6723b8-7ab3-462c-8d93-dbf61227998e"
}
```

</details>




---

### type
Get the device type

```typescript
function type(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device type |


---

#### Examples

##### Getting the device type
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.type()
    .then(deviceType => {
        console.log(deviceType)
    })
```
Value of `deviceType`

```javascript
"STB"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.type",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "STB"
}
```

</details>




---

### model
Get the device model

```typescript
function model(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device model |


---

#### Examples

##### Getting the device model
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.model()
    .then(model => {
        console.log(model)
    })
```
Value of `model`

```javascript
"xi6"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.model",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "xi6"
}
```

</details>




---

### sku
Get the device sku

```typescript
function sku(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device sku |


---

#### Examples

##### Getting the device sku
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.sku()
    .then(sku => {
        console.log(sku)
    })
```
Value of `sku`

```javascript
"AX061AEI"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.sku",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "AX061AEI"
}
```

</details>




---

### make
Get the device make

```typescript
function make(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device make |


---

#### Examples

##### Getting the device make
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.make()
    .then(make => {
        console.log(make)
    })
```
Value of `make`

```javascript
"Arris"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.make",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Arris"
}
```

</details>




---

### version
Get the SDK, OS and other version info

```typescript
function version(): Promise<object>
```
#### Promise Resolution

the versions

| Field | Type | Description |
| ----- | ---- | ----------- |
| `sdk` | [`SemanticVersion`](../schemas/types#/definitions/semanticversion) | The Firebolt SDK version |
| `os` | [`SemanticVersion`](../schemas/types#/definitions/semanticversion) | The Firebolt OS version |
| `debug` | `string` | Detail version as a string, for debugging purposes |


---

#### Examples

##### Getting the os and sdk versions
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.version()
    .then(versions => {
        console.log(versions)
    })
```
Value of `versions`

```javascript
{
  "sdk": {
    "major": 0,
    "minor": 5,
    "patch": 0,
    "readable": "Firebolt JS SDK v0.5.0"
  },
  "os": {
    "major": 0,
    "minor": 1,
    "patch": 0,
    "readable": "Firebolt OS v0.1.0"
  },
  "debug": ""
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
  "method": "device.version",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "sdk": {
      "major": 0,
      "minor": 5,
      "patch": 0,
      "readable": "Firebolt JS SDK v0.5.0"
    },
    "os": {
      "major": 0,
      "minor": 1,
      "patch": 0,
      "readable": "Firebolt OS v0.1.0"
    },
    "debug": ""
  }
}
```

</details>




---

### hdcp
Get the supported HDCP profiles

```typescript
function hdcp(): Promise<BooleanMap>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`BooleanMap`](../schemas/types#/definitions/booleanmap) | the supported HDCP profiles |


---

#### Examples

##### Getting the supported HDCP profiles
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.hdcp()
    .then(supportedHdcpProfiles => {
        console.log(supportedHdcpProfiles)
    })
```
Value of `supportedHdcpProfiles`

```javascript
{
  "hdcp1.4": true,
  "hdcp2.2": true
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
  "method": "device.hdcp",
  "params": {}
}
```

###### Response

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
Get the supported HDR profiles

```typescript
function hdr(): Promise<BooleanMap>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`BooleanMap`](../schemas/types#/definitions/booleanmap) | the supported HDR profiles |


---

#### Examples

##### Getting the supported HDR profiles
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.hdr()
    .then(supportedHdrProfiles => {
        console.log(supportedHdrProfiles)
    })
```
Value of `supportedHdrProfiles`

```javascript
{
  "hdr10": true,
  "hdr10Plus": true,
  "dolbyVision": true,
  "hlg": true
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
  "method": "device.hdr",
  "params": {}
}
```

###### Response

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

### audio
Get the supported audio profiles

```typescript
function audio(): Promise<AudioProfiles>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`AudioProfiles`](#audioprofiles) | the supported audio profiles |


---

#### Examples

##### Getting the supported audio profiles
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.audio()
    .then(supportedAudioProfiles => {
        console.log(supportedAudioProfiles)
    })
```
Value of `supportedAudioProfiles`

```javascript
{
  "stereo": true,
  "dolbyDigital5.1": true,
  "dolbyDigital5.1+": true,
  "dolbyAtmos": true
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
  "method": "device.audio",
  "params": {}
}
```

###### Response

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

### screenResolution
Get the current screen resolution

```typescript
function screenResolution(): Promise<[bigint, bigint]>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `[bigint, bigint]` | the resolution |


---

#### Examples

##### Getting the screen resolution
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.screenResolution()
    .then(screenResolution => {
        console.log(screenResolution)
    })
```
Value of `screenResolution`

```javascript
[
  1920,
  1080
]
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.screenResolution",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    1920,
    1080
  ]
}
```

</details>




---

### videoResolution
Get the current video resolution

```typescript
function videoResolution(): Promise<[bigint, bigint]>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `[bigint, bigint]` | the resolution |


---

#### Examples

##### Getting the video resolution
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.videoResolution()
    .then(videoResolution => {
        console.log(videoResolution)
    })
```
Value of `videoResolution`

```javascript
[
  1920,
  1080
]
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.videoResolution",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    1920,
    1080
  ]
}
```

</details>




---

### name
Get the human readable name of the device

```typescript
function name(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device friendly-name |


---

#### Examples

##### Getting the device name
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.name()
    .then(deviceName => {
        console.log(deviceName)
    })
```
Value of `deviceName`

```javascript
"Living Room"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "device.name",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>




---

### network
Get the current network status and type

```typescript
function network(): Promise<object>
```
#### Promise Resolution

the status and type

| Field | Type | Description |
| ----- | ---- | ----------- |
| `state` | [`NetworkState`](#networkstate) |  |
| `type` | [`NetworkType`](#networktype) |  |


---

#### Examples

##### Getting the network info
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Device } from '@firebolt-js/sdk'

Device.network()
    .then(networkInfo => {
        console.log(networkInfo)
    })
```
Value of `networkInfo`

```javascript
{
  "state": "connected",
  "type": "wifi"
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
  "method": "device.network",
  "params": {}
}
```

###### Response

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



## Schemas

### Resolution

```typescript
type Resolution = [bigint, bigint]
```





---

### NetworkType

```typescript
type NetworkType = 'wifi' | 'ethernet' | 'hybrid'
```



#### Details

The type of network that is currently active

---

### NetworkState

```typescript
type NetworkState = 'connected' | 'disconnected'
```



#### Details

The type of network that is currently active

---

### AudioProfiles

```typescript
type AudioProfiles = {
}
```

See also: 

 - [BooleanMap](../schemas/types#/definitions/booleanmap)
 - [AudioProfile](../schemas/types#/definitions/audioprofile)



---

### AudioProfile

```typescript
type AudioProfile;
```

See also: 

 - [AudioProfile](../schemas/types#/definitions/audioprofile)



---


