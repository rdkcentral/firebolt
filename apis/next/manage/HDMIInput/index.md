---
title: HDMIInput

version: next
layout: default
sdk: manage
---

# HDMIInput Module

---

Version HDMIInput 1.8.0-next.21

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [autoLowLatencyModeCapable](#autolowlatencymodecapable)
  - [close](#close)
  - [edidVersion](#edidversion)
  - [listen](#listen)
  - [lowLatencyMode](#lowlatencymode)
  - [once](#once)
  - [open](#open)
  - [port](#port)
  - [ports](#ports)
- [Events](#events)
  - [autoLowLatencyModeCapableChanged](#autolowlatencymodecapablechanged)
  - [autoLowLatencyModeSignalChanged](#autolowlatencymodesignalchanged)
  - [connectionChanged](#connectionchanged)
  - [edidVersionChanged](#edidversionchanged)
  - [lowLatencyModeChanged](#lowlatencymodechanged)
  - [signalChanged](#signalchanged)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [autoLowLatencyModeSignalChanged](#autolowlatencymodesignalchanged-1)
  - [connectionChanged](#connectionchanged-1)
  - [edidVersionChanged](#edidversionchanged-1)
  - [lowLatencyModeChanged](#lowlatencymodechanged-1)
  - [signalChanged](#signalchanged-1)
  </details>
- [Types](#types)
  - [EDIDVersion](#edidversion-1)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [HDMIPortId](#hdmiportid)
  - [SignalChangedInfo](#signalchangedinfo)
  - [AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)
  - [HDMIInputPort](#hdmiinputport)
  - [AutoLowLatencyModeCapableChangedInfo](#autolowlatencymodecapablechangedinfo)
  - [ConnectionChangedInfo](#connectionchangedinfo)

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
function autoLowLatencyModeCapable(port: HDMIPortId): Promise<boolean>
```

Parameters:

| Param  | Type                        | Required | Description                |
| ------ | --------------------------- | -------- | -------------------------- |
| `port` | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let enabled = await HDMIInput.autoLowLatencyModeCapable('HDMI1')
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
  "method": "HDMIInput.autoLowLatencyModeCapable",
  "params": {
    "port": "HDMI1"
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

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let enabled = await HDMIInput.autoLowLatencyModeCapable('HDMI1')
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
  "method": "HDMIInput.autoLowLatencyModeCapable",
  "params": {
    "port": "HDMI1"
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

To set the value of `autoLowLatencyModeCapable` call the method like this:

```typescript
function autoLowLatencyModeCapable(
  port: HDMIPortId,
  value: boolean,
): Promise<void>
```

Parameters:

| Param   | Type                        | Required | Description                |
| ------- | --------------------------- | -------- | -------------------------- |
| `port`  | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |
| `value` | `boolean`                   | true     |                            |

Promise resolution:

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.autoLowLatencyModeCapable('HDMI1', true)
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
  "method": "HDMIInput.setAutoLowLatencyModeCapable",
  "params": {
    "port": "HDMI1",
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

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.autoLowLatencyModeCapable('HDMI1', false)
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
  "method": "HDMIInput.setAutoLowLatencyModeCapable",
  "params": {
    "port": "HDMI1",
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
function autoLowLatencyModeCapable(
  callback: (value) => AutoLowLatencyModeCapableChangedInfo,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await autoLowLatencyModeCapable((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `data`:

```javascript
{
	"port": "HDMI1",
	"enabled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onAutoLowLatencyModeCapableChanged",
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
    "port": "HDMI1",
    "enabled": true
  }
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await autoLowLatencyModeCapable((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `data`:

```javascript
{
	"port": "HDMI1",
	"enabled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onAutoLowLatencyModeCapableChanged",
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
    "port": "HDMI1",
    "enabled": false
  }
}
```

</details>

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

Default Example for stop

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let port = await HDMIInput.close()
console.log(port)
```

Value of `port`:

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
  "method": "HDMIInput.close",
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

### edidVersion

Property for each port's active EDID version.

To get the value of `edidVersion` call the method like this:

```typescript
function edidVersion(port: HDMIPortId): Promise<EDIDVersion>
```

Parameters:

| Param  | Type                        | Required | Description                |
| ------ | --------------------------- | -------- | -------------------------- |
| `port` | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

[EDIDVersion](#edidversion-1)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let edidVersion = await HDMIInput.edidVersion('HDMI1')
console.log(edidVersion)
```

Value of `edidVersion`:

```javascript
'2.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.edidVersion",
  "params": {
    "port": "HDMI1"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "2.0"
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let edidVersion = await HDMIInput.edidVersion('HDMI1')
console.log(edidVersion)
```

Value of `edidVersion`:

```javascript
'2.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.edidVersion",
  "params": {
    "port": "HDMI1"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "1.4"
}
```

</details>

---

To set the value of `edidVersion` call the method like this:

```typescript
function edidVersion(port: HDMIPortId, value: EDIDVersion): Promise<void>
```

Parameters:

| Param   | Type                            | Required | Description                                |
| ------- | ------------------------------- | -------- | ------------------------------------------ |
| `port`  | [`HDMIPortId`](#hdmiportid)     | true     | <br/>pattern: ^HDMI[0-9]+$                 |
| `value` | [`EDIDVersion`](#edidversion-1) | true     | <br/>values: `'1.4' \| '2.0' \| 'unknown'` |

Promise resolution:

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.edidVersion('HDMI1', '2.0')
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
  "method": "HDMIInput.setEdidVersion",
  "params": {
    "port": "HDMI1",
    "value": "2.0"
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
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.edidVersion('HDMI1', '1.4')
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
  "method": "HDMIInput.setEdidVersion",
  "params": {
    "port": "HDMI1",
    "value": "1.4"
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
function edidVersion(
  port: HDMIPortId,
  callback: (value) => EDIDVersion,
): Promise<number>
```

Parameters:

| Param  | Type                        | Required | Description                |
| ------ | --------------------------- | -------- | -------------------------- |
| `port` | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await edidVersion((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `edidVersion`:

```javascript
'2.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onEdidVersionChanged",
  "params": {
    "port": "HDMI1",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "2.0"
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await edidVersion((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `edidVersion`:

```javascript
'2.0'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onEdidVersionChanged",
  "params": {
    "port": "HDMI1",
    "listen": true
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "1.4"
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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let enabled = await HDMIInput.lowLatencyMode()
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
  "method": "HDMIInput.lowLatencyMode",
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

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let enabled = await HDMIInput.lowLatencyMode()
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
  "method": "HDMIInput.lowLatencyMode",
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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.lowLatencyMode(true)
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
  "method": "HDMIInput.setLowLatencyMode",
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

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let result = await HDMIInput.lowLatencyMode(false)
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
  "method": "HDMIInput.setLowLatencyMode",
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
function lowLatencyMode(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await lowLatencyMode((value) => {
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
  "method": "HDMIInput.onLowLatencyModeChanged",
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

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let listenerId = await lowLatencyMode((value) => {
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
  "method": "HDMIInput.onLowLatencyModeChanged",
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

### open

Opens the HDMI Port allowing it to be the active source device. Incase there is a different HDMI portId already set as the active source, this call would stop the older portId before opening the given portId.

```typescript
function open(portId: HDMIPortId): Promise<void>
```

Parameters:

| Param    | Type                        | Required | Description                |
| -------- | --------------------------- | -------- | -------------------------- |
| `portId` | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

Capabilities:

| Role    | Capability                          |
| ------- | ----------------------------------- |
| manages | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example for open

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let port = await HDMIInput.open('HDMI1')
console.log(port)
```

Value of `port`:

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
  "method": "HDMIInput.open",
  "params": {
    "portId": "HDMI1"
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

### port

Retrieve a specific HDMI input port.

```typescript
function port(portId: HDMIPortId): Promise<HDMIInputPort>
```

Parameters:

| Param    | Type                        | Required | Description                |
| -------- | --------------------------- | -------- | -------------------------- |
| `portId` | [`HDMIPortId`](#hdmiportid) | true     | <br/>pattern: ^HDMI[0-9]+$ |

Promise resolution:

[HDMIInputPort](#hdmiinputport)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let port = await HDMIInput.port('HDMI1')
console.log(port)
```

Value of `port`:

```javascript
{
	"port": "HDMI1",
	"connected": true,
	"signal": "stable",
	"arcCapable": true,
	"arcConnected": true,
	"edidVersion": "2.0",
	"autoLowLatencyModeCapable": true,
	"autoLowLatencyModeSignalled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.port",
  "params": {
    "portId": "HDMI1"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "port": "HDMI1",
    "connected": true,
    "signal": "stable",
    "arcCapable": true,
    "arcConnected": true,
    "edidVersion": "2.0",
    "autoLowLatencyModeCapable": true,
    "autoLowLatencyModeSignalled": true
  }
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

let ports = await HDMIInput.ports()
console.log(ports)
```

Value of `ports`:

```javascript
;[
  {
    port: 'HDMI1',
    connected: true,
    signal: 'stable',
    arcCapable: true,
    arcConnected: true,
    edidVersion: '2.0',
    autoLowLatencyModeCapable: true,
    autoLowLatencyModeSignalled: true,
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.ports",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "port": "HDMI1",
      "connected": true,
      "signal": "stable",
      "arcCapable": true,
      "arcConnected": true,
      "edidVersion": "2.0",
      "autoLowLatencyModeCapable": true,
      "autoLowLatencyModeSignalled": true
    }
  ]
}
```

</details>

---

## Events

### autoLowLatencyModeCapableChanged

See: [autoLowLatencyModeCapable](#autolowlatencymodecapable)

### autoLowLatencyModeSignalChanged

```typescript
function listen('autoLowLatencyModeSignalChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('autoLowLatencyModeSignalChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"autoLowLatencyModeSignalled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onAutoLowLatencyModeSignalChanged",
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
    "port": "HDMI1",
    "autoLowLatencyModeSignalled": true
  }
}
```

</details>

---

### connectionChanged

```typescript
function listen('connectionChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[ConnectionChangedInfo](#connectionchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('connectionChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"connected": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onConnectionChanged",
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
    "port": "HDMI1",
    "connected": true
  }
}
```

</details>

---

### edidVersionChanged

See: [edidVersion](#edidversion)

### lowLatencyModeChanged

See: [lowLatencyMode](#lowlatencymode)

### signalChanged

```typescript
function listen('signalChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[SignalChangedInfo](#signalchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('signalChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"signal": "stable"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onSignalChanged",
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
    "port": "HDMI1",
    "signal": "stable"
  }
}
```

</details>

---

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### autoLowLatencyModeCapableChanged

See: [autoLowLatencyModeCapable](#autolowlatencymodecapable)

### autoLowLatencyModeSignalChanged

```typescript
function listen('autoLowLatencyModeSignalChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('autoLowLatencyModeSignalChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"autoLowLatencyModeSignalled": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onAutoLowLatencyModeSignalChanged",
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
    "port": "HDMI1",
    "autoLowLatencyModeSignalled": true
  }
}
```

</details>

---

### connectionChanged

```typescript
function listen('connectionChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[ConnectionChangedInfo](#connectionchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('connectionChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"connected": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onConnectionChanged",
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
    "port": "HDMI1",
    "connected": true
  }
}
```

</details>

---

### edidVersionChanged

See: [edidVersion](#edidversion)

### lowLatencyModeChanged

See: [lowLatencyMode](#lowlatencymode)

### signalChanged

```typescript
function listen('signalChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[SignalChangedInfo](#signalchangedinfo)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/manage-sdk'

HDMIInput.listen('signalChanged', (info) => {
  console.log(info)
})
```

Value of `info`:

```javascript
{
	"port": "HDMI1",
	"signal": "stable"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "HDMIInput.onSignalChanged",
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
    "port": "HDMI1",
    "signal": "stable"
  }
}
```

</details>

---

</details>

## Types

### EDIDVersion

```typescript
EDIDVersion: {
    V1_4: '1.4',
    V2_0: '2.0',
    UNKNOWN: 'unknown',
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

### HDMIPortId

```typescript
type HDMIPortId = string
```

---

### SignalChangedInfo

```typescript
type SignalChangedInfo = {
  port: HDMIPortId
  signal: HDMISignalStatus
}
```

See also:

[HDMIPortId](#hdmiportid)
[HDMISignalStatus](#hdmisignalstatus)

---

### AutoLowLatencyModeSignalChangedInfo

```typescript
type AutoLowLatencyModeSignalChangedInfo = {
  port?: HDMIPortId
  autoLowLatencyModeSignalled?: boolean
}
```

See also:

[HDMIPortId](#hdmiportid)

---

### HDMIInputPort

```typescript
type HDMIInputPort = {
  port: HDMIPortId
  connected: boolean
  signal: HDMISignalStatus
  arcCapable: boolean
  arcConnected: boolean
  edidVersion: EDIDVersion
  autoLowLatencyModeCapable: boolean
  autoLowLatencyModeSignalled: boolean
}
```

See also:

[HDMIPortId](#hdmiportid)
[HDMISignalStatus](#hdmisignalstatus)
[EDIDVersion](#edidversion-1)

---

### AutoLowLatencyModeCapableChangedInfo

```typescript
type AutoLowLatencyModeCapableChangedInfo = {
  port: HDMIPortId
  enabled: boolean
}
```

See also:

[HDMIPortId](#hdmiportid)

---

### ConnectionChangedInfo

```typescript
type ConnectionChangedInfo = {
  port?: HDMIPortId
  connected?: boolean
}
```

See also:

[HDMIPortId](#hdmiportid)

---
