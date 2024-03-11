---
title: Wifi

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Wifi Module

---

Version Wifi 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [connect](#connect)
  - [disconnect](#disconnect)
  - [scan](#scan)
  - [wps](#wps)
- [Types](#types)
  - [WifiSecurityMode](#wifisecuritymode)
  - [WPSSecurityPin](#wpssecuritypin)
  - [WifiSignalStrength](#wifisignalstrength)
  - [WifiFrequency](#wififrequency)
  - [AccessPoint](#accesspoint)
  - [AccessPointList](#accesspointlist)

## Usage

To use the Wifi module, you can import it into your project from the Firebolt SDK:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'
```

## Overview

A module for providing support for Wifi.

## Methods

### connect

Connect the device to the specified SSID.

```typescript
function connect(
  ssid?: string,
  passphrase?: string,
  security?: WifiSecurityMode,
): Promise<AccessPoint>
```

Parameters:

| Param        | Type                                    | Required | Description                                                                                                                                                                                                                                                            |
| ------------ | --------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ssid`       | `string`                                | false    |                                                                                                                                                                                                                                                                        |
| `passphrase` | `string`                                | false    |                                                                                                                                                                                                                                                                        |
| `security`   | [`WifiSecurityMode`](#wifisecuritymode) | false    | <br/>values: `'none' \| 'wep64' \| 'wep128' \| 'wpaPskTkip' \| 'wpaPskAes' \| 'wpa2PskTkip' \| 'wpa2PskAes' \| 'wpaEnterpriseTkip' \| 'wpaEnterpriseAes' \| 'wpa2EnterpriseTkip' \| 'wpa2EnterpriseAes' \| 'wpa2Psk' \| 'wpa2Enterprise' \| 'wpa3PskAes' \| 'wpa3Sae'` |

Promise resolution:

[AccessPoint](#accesspoint)

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

Connect to a wpa2Psk Wifi with password

JavaScript:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'

let connectedWifi = await Wifi.connect('DND', 'gargoyle', 'wpa2Psk')
console.log(connectedWifi)
```

Value of `connectedWifi`:

```javascript
{
	"ssid": "DND",
	"security": "wpa2Psk",
	"signalStrength": -70,
	"frequency": 2.4
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Wifi.connect",
  "params": {
    "ssid": "DND",
    "passphrase": "gargoyle",
    "security": "wpa2Psk"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ssid": "DND",
    "security": "wpa2Psk",
    "signalStrength": -70,
    "frequency": 2.4
  }
}
```

</details>

Connect to a WPA2 PSK Wifi with password

JavaScript:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'

let connectedWifi = await Wifi.connect('Guardian WIFI', '', 'none')
console.log(connectedWifi)
```

Value of `connectedWifi`:

```javascript
{
	"ssid": "DND",
	"security": "wpa2Psk",
	"signalStrength": -70,
	"frequency": 2.4
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Wifi.connect",
  "params": {
    "ssid": "Guardian WIFI",
    "passphrase": "",
    "security": "none"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ssid": "Guardian WIFI",
    "security": "none",
    "signalStrength": -70,
    "frequency": 2.4
  }
}
```

</details>

---

### disconnect

Disconnect the device if connected via WIFI.

```typescript
function disconnect(): Promise<void>
```

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

Disconnect

JavaScript:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'

let result = await Wifi.disconnect()
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
  "method": "Wifi.disconnect",
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

### scan

Scan available wifi networks in the location.

```typescript
function scan(timeout?: Timeout): Promise<AccessPointList>
```

Parameters:

| Param         | Type                                   | Required | Description     |
| ------------- | -------------------------------------- | -------- | --------------- |
| `timeout`     | [`Timeout`](../Types/schemas/#Timeout) | false    | <br/>minumum: 0 |
| maximum: 9999 |

Promise resolution:

[AccessPointList](#accesspointlist)

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

Successful Wifi List

JavaScript:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'

let list = await Wifi.scan(30)
console.log(list)
```

Value of `list`:

```javascript
{
	"list": [
		{
			"ssid": "DND",
			"security": "wpa2Psk",
			"signalStrength": -70,
			"frequency": 2.4
		},
		{
			"ssid": "Fortnite",
			"security": "WPA2_ENTERPRISE_AES",
			"signalStrength": -70,
			"frequency": 5
		},
		{
			"ssid": "Guardian",
			"security": "none",
			"signalStrength": -70,
			"frequency": 2.4
		}
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
  "method": "Wifi.scan",
  "params": {
    "timeout": 30
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "list": [
      {
        "ssid": "DND",
        "security": "wpa2Psk",
        "signalStrength": -70,
        "frequency": 2.4
      },
      {
        "ssid": "Fortnite",
        "security": "WPA2_ENTERPRISE_AES",
        "signalStrength": -70,
        "frequency": 5
      },
      {
        "ssid": "Guardian",
        "security": "none",
        "signalStrength": -70,
        "frequency": 2.4
      }
    ]
  }
}
```

</details>

---

### wps

Connect to WPS

```typescript
function wps(security?: WPSSecurityPin): Promise<AccessPoint>
```

Parameters:

| Param      | Type                                | Required | Description                                               |
| ---------- | ----------------------------------- | -------- | --------------------------------------------------------- |
| `security` | [`WPSSecurityPin`](#wpssecuritypin) | false    | <br/>values: `'pushButton' \| 'pin' \| 'manufacturerPin'` |

Promise resolution:

[AccessPoint](#accesspoint)

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

Connect to a WPS Wifi router

JavaScript:

```javascript
import { Wifi } from '@firebolt-js/manage-sdk'

let connectedWifi = await Wifi.wps('pushButton')
console.log(connectedWifi)
```

Value of `connectedWifi`:

```javascript
{
	"ssid": "DND",
	"security": "wpa2Psk",
	"signalStrength": -70,
	"frequency": 2.4
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Wifi.wps",
  "params": {
    "security": "pushButton"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ssid": "DND",
    "security": "wpa2Psk",
    "signalStrength": -70,
    "frequency": 2.4
  }
}
```

</details>

---

## Types

### WifiSecurityMode

Security Mode supported for Wifi

```typescript
enum WifiSecurityMode {
  NONE = 'none',
  WEP_64 = 'wep64',
  WEP_128 = 'wep128',
  WPA_PSK_TKIP = 'wpaPskTkip',
  WPA_PSK_AES = 'wpaPskAes',
  WPA_2PSK_TKIP = 'wpa2PskTkip',
  WPA_2PSK_AES = 'wpa2PskAes',
  WPA_ENTERPRISE_TKIP = 'wpaEnterpriseTkip',
  WPA_ENTERPRISE_AES = 'wpaEnterpriseAes',
  WPA_2ENTERPRISE_TKIP = 'wpa2EnterpriseTkip',
  WPA_2ENTERPRISE_AES = 'wpa2EnterpriseAes',
  WPA_2PSK = 'wpa2Psk',
  WPA_2ENTERPRISE = 'wpa2Enterprise',
  WPA_3PSK_AES = 'wpa3PskAes',
  WPA_3SAE = 'wpa3Sae',
}
```

---

### WPSSecurityPin

Security pin type for WPS(Wifi Protected Setup).

```typescript
enum WPSSecurityPin {
  PUSH_BUTTON = 'pushButton',
  PIN = 'pin',
  MANUFACTURER_PIN = 'manufacturerPin',
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

### AccessPoint

Properties of a scanned wifi list item.

```typescript
type AccessPoint = {
  ssid?: string // Name of the wifi.
  securityMode?: WifiSecurityMode // Security Mode supported for Wifi
  signalStrength?: WifiSignalStrength // Strength of Wifi signal, value is negative based on RSSI specification.
  frequency?: WifiFrequency // Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.
}
```

See also:

'none' | 'wep64' | 'wep128' | 'wpaPskTkip' | 'wpaPskAes' | 'wpa2PskTkip' | 'wpa2PskAes' | 'wpaEnterpriseTkip' | 'wpaEnterpriseAes' | 'wpa2EnterpriseTkip' | 'wpa2EnterpriseAes' | 'wpa2Psk' | 'wpa2Enterprise' | 'wpa3PskAes' | 'wpa3Sae'
number
number

---

### AccessPointList

List of scanned Wifi networks available near the device.

```typescript
type AccessPointList = {
  list?: AccessPoint[]
}
```

See also:

[AccessPoint](#accesspoint)

---
