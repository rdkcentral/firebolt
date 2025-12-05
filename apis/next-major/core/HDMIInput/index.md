---
title: HDMIInput

version: next-major
layout: default
sdk: core
---

# HDMIInput Module

---

Version HDMIInput 1.8.0-next-major.4

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [autoLowLatencyModeCapable](#autolowlatencymodecapable)
  - [edidVersion](#edidversion)
  - [listen](#listen)
  - [lowLatencyMode](#lowlatencymode)
  - [once](#once)
  - [port](#port)
  - [ports](#ports)
- [Events](#events)
  - [onAutoLowLatencyModeCapableChanged](#onautolowlatencymodecapablechanged)
  - [onAutoLowLatencyModeSignalChanged](#onautolowlatencymodesignalchanged)
  - [onConnectionChanged](#onconnectionchanged)
  - [onEdidVersionChanged](#onedidversionchanged)
  - [onLowLatencyModeChanged](#onlowlatencymodechanged)
  - [onSignalChanged](#onsignalchanged)
- [Private Events](#private-events)
- [Types](#types)
  - [EDIDVersion](#edidversion-1)
  - [HDMIPortId](#hdmiportid)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [HDMIInputPort](#hdmiinputport)
  - [SignalChangedInfo](#signalchangedinfo)
  - [ConnectionChangedInfo](#connectionchangedinfo)
  - [AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)

## Usage

To use the HDMIInput module, you can import it into your project from the Firebolt SDK:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'
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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

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
import { HDMIInput } from '@firebolt-js/sdk'

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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function autoLowLatencyModeCapable(
  port: string,
  callback: (enabled) => boolean,
): Promise<number>
```

| Param     | Type      | Required | Description                |
| --------- | --------- | -------- | -------------------------- |
| `port`    | `string`  | true     | <br/>pattern: ^HDMI[0-9]+$ |
| `enabled` | `boolean` | false    |                            |

Promise resolution:

```
number
```

#### Examples

Default Example

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await autoLowLatencyModeCapable((result) => {
  console.log(result)
})
```

Value of `result`:

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
    "port": "HDMI1",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default Example #2

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await autoLowLatencyModeCapable((result) => {
  console.log(result)
})
```

Value of `result`:

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
    "port": "HDMI1",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

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

[EDIDVersion](#edidversion-1)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

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
import { HDMIInput } from '@firebolt-js/sdk'

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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function edidVersion(
  port: string,
  callback: (edidVersion) => EDIDVersion,
): Promise<number>
```

| Param         | Type                            | Required | Description                                |
| ------------- | ------------------------------- | -------- | ------------------------------------------ |
| `port`        | `string`                        | true     | <br/>pattern: ^HDMI[0-9]+$                 |
| `edidVersion` | [`EDIDVersion`](#edidversion-1) | false    | <br/>values: `'1.4' \| '2.0' \| 'unknown'` |

Promise resolution:

```
number
```

#### Examples

Default Example

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await edidVersion((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"port": "HDMI1",
	"edidVersion": "2.0"
}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default Example #2

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await edidVersion((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"port": "HDMI1",
	"edidVersion": "2.0"
}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
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
import { HDMIInput } from '@firebolt-js/sdk'

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
import { HDMIInput } from '@firebolt-js/sdk'

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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function lowLatencyMode(callback: (enabled) => boolean): Promise<number>
```

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Promise resolution:

```
number
```

#### Examples

Default Example

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await lowLatencyMode((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default Example #2

```typescript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await lowLatencyMode((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
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

[HDMIInputPort](#hdmiinputport)

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let port = await HDMIInput.port('HDMI1')
console.log(port)
```

Value of `port`:

```javascript
{"port":"HDMI1","connected":true,"signal":"stable","arcCapable":true,"arcConnected":true,"edidVersion":"2.0","autoLowLatencyModeCapable":true,"autoLowLatencyModeSignalled":true}
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
import { HDMIInput } from '@firebolt-js/sdk'

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

### onAutoLowLatencyModeCapableChanged

See: [autoLowLatencyModeCapable](#autolowlatencymodecapable)

### onAutoLowLatencyModeSignalChanged

```typescript
function listen('onAutoLowLatencyModeSignalChanged', (AutoLowLatencyModeSignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                                                          | Required | Description |
| ------ | ----------------------------------------------------------------------------- | -------- | ----------- |
| `info` | [`AutoLowLatencyModeSignalChangedInfo`](#autolowlatencymodesignalchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen(
  'onAutoLowLatencyModeSignalChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"autoLowLatencyModeSignalled": true
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onConnectionChanged

```typescript
function listen('onConnectionChanged', (ConnectionChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                              | Required | Description |
| ------ | ------------------------------------------------- | -------- | ----------- |
| `info` | [`ConnectionChangedInfo`](#connectionchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen('onConnectionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"connected": true
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onEdidVersionChanged

See: [edidVersion](#edidversion)

### onLowLatencyModeChanged

See: [lowLatencyMode](#lowlatencymode)

### onSignalChanged

```typescript
function listen('onSignalChanged', (SignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                      | Required | Description |
| ------ | ----------------------------------------- | -------- | ----------- |
| `info` | [`SignalChangedInfo`](#signalchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen('onSignalChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"signal": "stable"
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

## Private Events

### onAutoLowLatencyModeCapableChanged

See: [autoLowLatencyModeCapable](#autolowlatencymodecapable)

### onAutoLowLatencyModeSignalChanged

```typescript
function listen('onAutoLowLatencyModeSignalChanged', (AutoLowLatencyModeSignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                                                          | Required | Description |
| ------ | ----------------------------------------------------------------------------- | -------- | ----------- |
| `info` | [`AutoLowLatencyModeSignalChangedInfo`](#autolowlatencymodesignalchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen(
  'onAutoLowLatencyModeSignalChanged',
  (result) => {
    console.log(result)
  },
)
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"autoLowLatencyModeSignalled": true
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onConnectionChanged

```typescript
function listen('onConnectionChanged', (ConnectionChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                              | Required | Description |
| ------ | ------------------------------------------------- | -------- | ----------- |
| `info` | [`ConnectionChangedInfo`](#connectionchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen('onConnectionChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"connected": true
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onEdidVersionChanged

See: [edidVersion](#edidversion)

### onLowLatencyModeChanged

See: [lowLatencyMode](#lowlatencymode)

### onSignalChanged

```typescript
function listen('onSignalChanged', (SignalChangedInfo) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param  | Type                                      | Required | Description |
| ------ | ----------------------------------------- | -------- | ----------- |
| `info` | [`SignalChangedInfo`](#signalchangedinfo) | true     |             |

Capabilities:

| Role | Capability                          |
| ---- | ----------------------------------- |
| uses | xrn:firebolt:capability:inputs:hdmi |

#### Examples

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

let listenerId = await HDMIInput.listen('onSignalChanged', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"info": {
		"port": "HDMI1",
		"signal": "stable"
	}
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

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

### HDMIPortId

```typescript
type HDMIPortId = string
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

[EDIDVersion](#edidversion-1)

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
