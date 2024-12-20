---
title: Network

version: pr-feature-networking
layout: default
sdk: core
---

# Network Module

---

Version Network 1.5.0-feature-networking.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [connectionStatus](#connectionstatus)
  - [interfaces](#interfaces)
  - [ipProperties](#ipproperties)
  - [listen](#listen)
  - [once](#once)
  - [wifiStatus](#wifistatus)
- [Events](#events)
  - [connectionStatusChanged](#connectionstatuschanged)
  - [interfaceChanged](#interfacechanged)
  - [ipPropertiesChanged](#ippropertieschanged)
- [Types](#types)
  - [InterfaceType](#interfacetype)
  - [EthernetStandard](#ethernetstandard)
  - [WirelessStandard](#wirelessstandard)
  - [ConnectionState](#connectionstate)
  - [InterfaceDetails](#interfacedetails)
  - [IPProperties](#ipproperties-1)
  - [WifiStatusResult](#wifistatusresult)

## Usage

To use the Network module, you can import it into your project from the Firebolt SDK:

```javascript
import { Network } from '@firebolt-js/sdk'
```

## Overview

A module that surfaces details of the device's network connection, including IP configuration and network capabilities.

## Methods

### connectionStatus

Get the device's current network connection status. The result is based on the current preferred network interface.

To get the value of `connectionStatus` call the method like this:

```typescript
function connectionStatus(): Promise<object>
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
import { Network } from '@firebolt-js/sdk'

let connectionStatus = await Network.connectionStatus()
console.log(connectionStatus)
```

Value of `connectionStatus`:

```javascript
{
	"connected": true,
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
  "method": "Network.connectionStatus",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "connected": true,
    "type": "wifi"
  }
}
```

</details>

Example with no network connection

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let connectionStatus = await Network.connectionStatus()
console.log(connectionStatus)
```

Value of `connectionStatus`:

```javascript
{
	"connected": true,
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
  "method": "Network.connectionStatus",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "connected": false
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function connectionStatus(callback: (value) => object): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let listenerId = await connectionStatus((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `connectionStatus`:

```javascript
{
	"connected": true,
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
  "method": "Network.onConnectionStatusChanged",
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
    "connected": true,
    "type": "wifi"
  }
}
```

</details>

Example with no network connection

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let listenerId = await connectionStatus((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `connectionStatus`:

```javascript
{
	"connected": true,
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
  "method": "Network.onConnectionStatusChanged",
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
    "connected": false
  }
}
```

</details>

---

### interfaces

Get details of the enabled network interfaces on the device.

```typescript
function interfaces(): Promise<InterfaceDetails[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:network:interfaces |

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let interfaces = await Network.interfaces()
console.log(interfaces)
```

Value of `interfaces`:

```javascript
;[
  {
    capability: '802.11ac',
    connectionState: 'disconnected',
    interfaceName: 'wifi0',
    macAddress: '00:00:00:00:00:00',
    preferred: false,
    type: 'wifi',
  },
  {
    capability: 'GE',
    connectionState: 'connected',
    interfaceName: 'eth0',
    macAddress: '00:00:00:00:00:01',
    preferred: true,
    type: 'ethernet',
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
  "method": "Network.interfaces",
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
      "capability": "802.11ac",
      "connectionState": "disconnected",
      "interfaceName": "wifi0",
      "macAddress": "00:00:00:00:00:00",
      "preferred": false,
      "type": "wifi"
    },
    {
      "capability": "GE",
      "connectionState": "connected",
      "interfaceName": "eth0",
      "macAddress": "00:00:00:00:00:01",
      "preferred": true,
      "type": "ethernet"
    }
  ]
}
```

</details>

---

### ipProperties

Get the TCP/IP properties for the provided interface

```typescript
function ipProperties(interfaceName: string): Promise<IPProperties>
```

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `interfaceName` | `string` | true     |             |

Promise resolution:

[IPProperties](#ipproperties-1)

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:network:ipproperties |

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let ipProperties = await Network.ipProperties('eth0')
console.log(ipProperties)
```

Value of `ipProperties`:

```javascript
{
	"interfaceName": "eth0",
	"ipv4Addresses": [
		"192.168.1.100/24"
	],
	"ipv4DNSAddresses": [
		"75.75.75.75"
	],
	"ipv6Addresses": [
		"2001:db8:abcd:0012::0/64"
	],
	"ipv6DNSAddresses": [
		"2001:558:feed::1"
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
  "method": "Network.ipProperties",
  "params": {
    "interfaceName": "eth0"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "interfaceName": "eth0",
    "ipv4Addresses": ["192.168.1.100/24"],
    "ipv4DNSAddresses": ["75.75.75.75"],
    "ipv6Addresses": ["2001:db8:abcd:0012::0/64"],
    "ipv6DNSAddresses": ["2001:558:feed::1"]
  }
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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Network.clear(id)` |

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Network.clear(id)` |

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Network.clear(id)` |

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Network.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### wifiStatus

Get details on the wireless connection for the provided interface

```typescript
function wifiStatus(interfaceName: string): Promise<WifiStatusResult>
```

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `interfaceName` | `string` | true     |             |

Promise resolution:

[WifiStatusResult](#wifistatusresult)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:network:wifistatus |

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let wifiStatus = await Network.wifiStatus('wifi0')
console.log(wifiStatus)
```

Value of `wifiStatus`:

```javascript
{
	"connectionState": "connected",
	"interfaceName": "wifi0",
	"mode": "802.11ac",
	"signalStrength": -60,
	"ssid": "MyNetwork"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Network.wifiStatus",
  "params": {
    "interfaceName": "wifi0"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "connectionState": "connected",
    "interfaceName": "wifi0",
    "mode": "802.11ac",
    "signalStrength": -60,
    "ssid": "MyNetwork"
  }
}
```

</details>

Example with no network connection

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

let wifiStatus = await Network.wifiStatus('wifi0')
console.log(wifiStatus)
```

Value of `wifiStatus`:

```javascript
{
	"connectionState": "connected",
	"interfaceName": "wifi0",
	"mode": "802.11ac",
	"signalStrength": -60,
	"ssid": "MyNetwork"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Network.wifiStatus",
  "params": {
    "interfaceName": "wifi0"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "connectionState": "disconnected",
    "interfaceName": "wifi0"
  }
}
```

</details>

---

## Events

### connectionStatusChanged

See: [connectionStatus](#connectionstatus)

### interfaceChanged

```typescript
function listen('interfaceChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[InterfaceDetails](#interfacedetails)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:network:interfaces |

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

Network.listen('interfaceChanged', (interfaceDetails) => {
  console.log(interfaceDetails)
})
```

Value of `interfaceDetails`:

```javascript
{
	"capability": "802.11ac",
	"connectionState": "connected",
	"interfaceName": "wifi0",
	"macAddress": "00:00:00:00:00:00",
	"preferred": true,
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
  "method": "Network.onInterfaceChanged",
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
    "capability": "802.11ac",
    "connectionState": "connected",
    "interfaceName": "wifi0",
    "macAddress": "00:00:00:00:00:00",
    "preferred": true,
    "type": "wifi"
  }
}
```

</details>

---

### ipPropertiesChanged

```typescript
function listen('ipPropertiesChanged', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[IPProperties](#ipproperties-1)

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:network:ipproperties |

#### Examples

Default Example

JavaScript:

```javascript
import { Network } from '@firebolt-js/sdk'

Network.listen('ipPropertiesChanged', (ipProperties) => {
  console.log(ipProperties)
})
```

Value of `ipProperties`:

```javascript
{
	"interfaceName": "eth0",
	"ipv4Addresses": [
		"192.168.1.100/24"
	],
	"ipv4DNSAddresses": [
		"75.75.75.75"
	],
	"ipv6Addresses": [
		"2001:db8:abcd:0012::0/64"
	],
	"ipv6DNSAddresses": [
		"2001:558:feed::1"
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
  "method": "Network.onIpPropertiesChanged",
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
    "interfaceName": "eth0",
    "ipv4Addresses": ["192.168.1.100/24"],
    "ipv4DNSAddresses": ["75.75.75.75"],
    "ipv6Addresses": ["2001:db8:abcd:0012::0/64"],
    "ipv6DNSAddresses": ["2001:558:feed::1"]
  }
}
```

</details>

---

## Types

### InterfaceType

Network interface type

```typescript
InterfaceType: {
    ETHERNET: 'ethernet',
    WIFI: 'wifi',
    OTHER: 'other',
    UNKNOWN: 'unknown',
},

```

---

### EthernetStandard

Ethernet connection standards

```typescript
EthernetStandard: {
    FE: 'FE',
    GE: 'GE',
    V10GE: '10GE',
},

```

---

### WirelessStandard

Wireless connection standards

```typescript
WirelessStandard: {
    V802_11AC: '802.11ac',
    V802_11AX: '802.11ax',
    V802_11BE: '802.11be',
    V802_11N: '802.11n',
    LEGACY: 'legacy',
    OTHER: 'other',
},

```

---

### ConnectionState

Network connection states

```typescript
ConnectionState: {
    CONNECTED: 'connected',
    DISCONNECTED: 'disconnected',
},

```

---

### InterfaceDetails

Details of a network interface

```typescript
type InterfaceDetails = {
  capability: EthernetStandard | WirelessStandard | 'other' | 'unknown'
  connectionState: ConnectionState // Network connection states
  interfaceName: string // Network interface name
  macAddress: string // Interface MAC address
  preferred: boolean // Whether this is the device's preferred/default interface
  type: InterfaceType // Network interface type
}
```

See also:

[EthernetStandard](#ethernetstandard)
[WirelessStandard](#wirelessstandard)
[ConnectionState](#connectionstate)
[InterfaceType](#interfacetype)

---

### IPProperties

TCP/IP properties of a network interface

```typescript
type IPProperties = {
  interfaceName: string // Network interface name
  ipv4Addresses: string[] // IPv4 addresses in CIDR notation
  ipv4DNSAddresses: string[] // IPv4 DNS addresses
  ipv6Addresses: string[] // IPv6 addresses in CIDR notation
  ipv6DNSAddresses: string[] // IPv6 DNS addresses notation
}
```

---

### WifiStatusResult

Status of a wireless connection

```typescript
type WifiStatusResult = {
  connectionState: ConnectionState // Network connection states
  interfaceName: string // Network interface name
  mode?: WirelessStandard // Wireless connection standards
  signalStrength?: SignalStrength // Relative signal strength indicator (RSSI), in dBm
  ssid?: string // The SSID of the connected wireless network
}
```

See also:

[ConnectionState](#connectionstate)
[WirelessStandard](#wirelessstandard)
[SignalStrength](../Network/schemas/#SignalStrength)

---
