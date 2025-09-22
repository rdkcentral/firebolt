---
title: HDMIInput

version: next-major
layout: default
sdk: core
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
  - [edidVersion](#edidversion)
  - [listen](#listen)
  - [lowLatencyMode](#lowlatencymode)
  - [once](#once)
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
  - [HDMIInput.HDMIPortId](#hdmiinputhdmiportid)
  - [HDMIInput.HDMISignalStatus](#hdmiinputhdmisignalstatus)
  - [HDMIInputPort](#hdmiinputport)
  - [AutoLowLatencyModeSignalChangedInfo](#autolowlatencymodesignalchangedinfo)
  - [AutoLowLatencyModeCapableChangedInfo](#autolowlatencymodecapablechangedinfo)
  - [ConnectionChangedInfo](#connectionchangedinfo)
  - [SignalChangedInfo](#signalchangedinfo)

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
function ${method.alternative}(${event.signature.params}${if.context}, ${end.if.context}callback: (value) => boolean): Promise<number>
```

${event.params}

Promise resolution:

```
number
```

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
function ${method.alternative}(${event.signature.params}${if.context}, ${end.if.context}callback: (value) => EDIDVersion): Promise<number>
```

${event.params}

Promise resolution:

```
number
```

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
function ${method.alternative}(${event.signature.params}${if.context}, ${end.if.context}callback: (value) => boolean): Promise<number>
```

${event.params}

Promise resolution:

```
number
```

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeCapableChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeCapableChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeSignalChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('connectionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('edidVersionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('edidVersionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('lowLatencyModeChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('lowLatencyModeChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('signalChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

---

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeCapableChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeCapableChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('autoLowLatencyModeSignalChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('connectionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('edidVersionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('edidVersionChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('lowLatencyModeChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('lowLatencyModeChanged', (result) => {
  console.log(result)
})
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
  "result": null
}
```

</details>

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

Default Example

JavaScript:

```javascript
import { HDMIInput } from '@firebolt-js/sdk'

HDMIInput.listen('signalChanged', (result) => {
  console.log(result)
})
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
  "result": null
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

### HDMIInput.HDMIPortId

```typescript
type HDMIPortId = string
```

---

### HDMIInput.HDMISignalStatus

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

EDIDVersion

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

### ConnectionChangedInfo

```typescript
type ConnectionChangedInfo = {
  port?: string
  connected?: boolean
}
```

---

### SignalChangedInfo

```typescript
type SignalChangedInfo = {
  port: string
  signal: 'none' | 'stable' | 'unstable' | 'unsupported' | 'unknown'
}
```

---
