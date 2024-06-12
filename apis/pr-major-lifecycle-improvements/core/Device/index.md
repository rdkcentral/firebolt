---
title: Device

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Device Module

---

Version Device 0.0.0-unknown.0

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
  - [make](#make)
  - [model](#model)
  - [name](#name)
  - [network](#network)
  - [platform](#platform)
  - [screenResolution](#screenresolution)
  - [sku](#sku)
  - [type](#type)
  - [uid](#uid)
  - [version](#version)
  - [videoResolution](#videoresolution)
  - [listen](#listen)
  - [once](#once)
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
  - [NetworkType](#networktype)
  - [NetworkState](#networkstate)
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
function audio(): Promise<AudioProfiles>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function audio(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

---

### hdcp

Get the supported HDCP profiles

To get the value of `hdcp` call the method like this:

```typescript
function hdcp(): Promise<Types.BooleanMap>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdcp(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### hdr

Get the supported HDR profiles

To get the value of `hdr` call the method like this:

```typescript
function hdr(): Promise<Types.BooleanMap>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function hdr(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

---

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

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function name(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function network(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

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

---

### screenResolution

Get the current screen resolution

To get the value of `screenResolution` call the method like this:

```typescript
function screenResolution(): Promise<
  [
    number, // undefined  item
    number, // undefined  item
  ]
>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function screenResolution(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

---

### videoResolution

Get the current video resolution

To get the value of `videoResolution` call the method like this:

```typescript
function videoResolution(): Promise<
  [
    number, // undefined  item
    number, // undefined  item
  ]
>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function videoResolution(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

## Events

### audioChanged

```typescript
function listen('audioChanged', (AudioProfiles) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

### deviceNameChanged

```typescript
function listen('deviceNameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

---

### hdcpChanged

```typescript
function listen('hdcpChanged', (Types.BooleanMap) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

### hdrChanged

```typescript
function listen('hdrChanged', (Types.BooleanMap) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

### nameChanged

```typescript
function listen('nameChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:name |

#### Examples

---

### networkChanged

```typescript
function listen('networkChanged', (object) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:network:status |

#### Examples

---

### screenResolutionChanged

```typescript
function listen('screenResolutionChanged', ([
    number, // undefined  item
    number // undefined  item
]) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

### videoResolutionChanged

```typescript
function listen('videoResolutionChanged', ([
    number, // undefined  item
    number // undefined  item
]) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:device:info |

#### Examples

---

## Types

### NetworkType

The type of network that is currently active

```typescript
enum NetworkType {
  WIFI = 'wifi',
  ETHERNET = 'ethernet',
  HYBRID = 'hybrid',
}
```

---

### NetworkState

The type of network that is currently active

```typescript
enum NetworkState {
  CONNECTED = 'connected',
  DISCONNECTED = 'disconnected',
}
```

---

### AudioProfiles

```typescript
type AudioProfiles = {}
```

See also:

Types.BooleanMap
Types.AudioProfile

---
