---
title: HDMIInput

version: next-major
layout: default
sdk: manage
---

# HDMIInput Module

---

Version HDMIInput 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [autoLowLatencyModeCapable](#autolowlatencymodecapable)
  - [close](#close)
  - [edidVersion](#edidversion)
  - [lowLatencyMode](#lowlatencymode)
  - [open](#open)
  - [port](#port)
  - [ports](#ports)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [autoLowLatencyModeCapableChanged](#autolowlatencymodecapablechanged)
  - [autoLowLatencyModeSignalChanged](#autolowlatencymodesignalchanged)
  - [connectionChanged](#connectionchanged)
  - [edidVersionChanged](#edidversionchanged)
  - [lowLatencyModeChanged](#lowlatencymodechanged)
  - [signalChanged](#signalchanged)
- [Types](#types)
  - [EDIDVersion](#edidversion-1)
  - [HDMIInputPort](#hdmiinputport)
  - [SignalChangedInfo](#signalchangedinfo)
  - [ConnectionChangedInfo](#connectionchangedinfo)
  - [AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)
  - [AutoLowLatencyModeCapableChangedInfo](#autolowlatencymodecapablechangedinfo)

## Usage

To use the HDMIInput module, you can import it into your project from the Firebolt SDK:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for managing HDMI inputs on an HDMI sink device.

## Methods

### autoLowLatencyModeCapable

Property for each port auto low latency mode setting.

To get the value of `autoLowLatencyModeCapable` call the method like this:

```typescript
function autoLowLatencyModeCapable(port: string): Promise<boolean>
```

Parameters:

| Param  | Type     | Required | Description                |
| ------ | -------- | -------- | -------------------------- |
| `port` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

To set the value of `autoLowLatencyModeCapable` call the method like this:

```typescript
function autoLowLatencyModeCapable(port: string, value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description                |
| ------- | --------- | -------- | -------------------------- |
| `port`  | `string`  | true     | <br/>pattern: ^HDMI[0-9]+$ |
| `value` | `boolean` | true     |                            |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function autoLowLatencyModeCapable(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### close

Closes the given HDMI Port if it is the current active source for HDMI Input. If there was no active source, then there would no action taken on the device.

```typescript
function close(): Promise<void>
```

Promise resolution:

Capabilities:

| Role    | Capability                          |
| ------- | ----------------------------------- |
| manages | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### edidVersion

Property for each port's active EDID version.

To get the value of `edidVersion` call the method like this:

```typescript
function edidVersion(port: string): Promise<EDIDVersion>
```

Parameters:

| Param  | Type     | Required | Description                |
| ------ | -------- | -------- | -------------------------- |
| `port` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

To set the value of `edidVersion` call the method like this:

```typescript
function edidVersion(port: string, value: EDIDVersion): Promise<void>
```

Parameters:

| Param   | Type          | Required | Description                                |
| ------- | ------------- | -------- | ------------------------------------------ |
| `port`  | `string`      | true     | <br/>pattern: ^HDMI[0-9]+$                 |
| `value` | `EDIDVersion` | true     | <br/>values: `'1.4' \| '2.0' \| 'unknown'` |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function edidVersion(port: string, callback: (value) => null): Promise<number>
```

Parameters:

| Param  | Type     | Required | Description                |
| ------ | -------- | -------- | -------------------------- |
| `port` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

```
number
```

#### Examples

---

### lowLatencyMode

Property for the low latency mode setting.

To get the value of `lowLatencyMode` call the method like this:

```typescript
function lowLatencyMode(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

To set the value of `lowLatencyMode` call the method like this:

```typescript
function lowLatencyMode(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function lowLatencyMode(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### open

Opens the HDMI Port allowing it to be the active source device. Incase there is a different HDMI portId already set as the active source, this call would stop the older portId before opening the given portId.

```typescript
function open(portId: string): Promise<void>
```

Parameters:

| Param    | Type     | Required | Description                |
| -------- | -------- | -------- | -------------------------- |
| `portId` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role    | Capability                          |
| ------- | ----------------------------------- |
| manages | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### port

Retrieve a specific HDMI input port.

```typescript
function port(portId: string): Promise<HDMIInputPort>
```

Parameters:

| Param    | Type     | Required | Description                |
| -------- | -------- | -------- | -------------------------- |
| `portId` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### ports

Retrieve a list of HDMI input ports.

```typescript
function ports(): Promise<HDMIInputPort[]>
```

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `HDMIInput.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `HDMIInput.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `HDMIInput.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `HDMIInput.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### autoLowLatencyModeCapableChanged

```typescript
function listen('autoLowLatencyModeCapableChanged', (AutoLowLatencyModeCapableChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### autoLowLatencyModeSignalChanged

```typescript
function listen('autoLowLatencyModeSignalChanged', (AutoLowLatencyModeSignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### connectionChanged

```typescript
function listen('connectionChanged', (ConnectionChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### edidVersionChanged

```typescript
function listen('edidVersionChanged', port: string, (EDIDVersion) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description                |
| ------ | -------- | -------- | -------------------------- |
| `port` | `string` | true     | <br/>pattern: ^HDMI[0-9]+$ |

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### lowLatencyModeChanged

```typescript
function listen('lowLatencyModeChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

### signalChanged

```typescript
function listen('signalChanged', (SignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

---

## Types

### EDIDVersion

```typescript
enum EDIDVersion {
  V1_4 = '1.4',
  V2_0 = '2.0',
  UNKNOWN = 'unknown',
}
```

---

### HDMIInputPort

```typescript
type HDMIInputPort = {
  port: string
  connected: boolean
  signal: 'none' | 'stable' | 'unstable' | 'unsupported' | 'unknown'
  arcCapable: boolean
  arcConnected: boolean
  edidVersion: EDIDVersion
  autoLowLatencyModeCapable: boolean
  autoLowLatencyModeSignalled: boolean
}
```

See also:

EDIDVersion

---

### SignalChangedInfo

```typescript
type SignalChangedInfo = {
  port: string
  signal: 'none' | 'stable' | 'unstable' | 'unsupported' | 'unknown'
}
```

---

### ConnectionChangedInfo

```typescript
type ConnectionChangedInfo = {
  port?: string
  connected?: boolean
}
```

---

### AutoLowLatencyModeSignalChangedInfo

```typescript
type AutoLowLatencyModeSignalChangedInfo = {
  port?: string
  autoLowLatencyModeSignalled?: boolean
}
```

---

### AutoLowLatencyModeCapableChangedInfo

```typescript
type AutoLowLatencyModeCapableChangedInfo = {
  port: string
  enabled: boolean
}
```

---
