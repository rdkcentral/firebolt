---
title: Wifi

version: next-major
layout: default
sdk: manage
---

# Wifi Module

---

Version Wifi 0.0.0-unknown.0

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
  - [WifiFrequency](#wififrequency)
  - [WifiSignalStrength](#wifisignalstrength)
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
  ssid: string,
  passphrase: string,
  security: WifiSecurityMode,
): Promise<AccessPoint>
```

Parameters:

| Param        | Type               | Required | Description                                                                                                                                                                                                                                                            |
| ------------ | ------------------ | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ssid`       | `string`           | false    |                                                                                                                                                                                                                                                                        |
| `passphrase` | `string`           | false    |                                                                                                                                                                                                                                                                        |
| `security`   | `WifiSecurityMode` | false    | <br/>values: `'none' \| 'wep64' \| 'wep128' \| 'wpaPskTkip' \| 'wpaPskAes' \| 'wpa2PskTkip' \| 'wpa2PskAes' \| 'wpaEnterpriseTkip' \| 'wpaEnterpriseAes' \| 'wpa2EnterpriseTkip' \| 'wpa2EnterpriseAes' \| 'wpa2Psk' \| 'wpa2Enterprise' \| 'wpa3PskAes' \| 'wpa3Sae'` |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

---

### disconnect

Disconnect the device if connected via WIFI.

```typescript
function disconnect(): Promise<void>
```

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

---

### scan

Scan available wifi networks in the location.

```typescript
function scan(timeout: Types.Timeout): Promise<AccessPointList>
```

Parameters:

| Param     | Type            | Required | Description |
| --------- | --------------- | -------- | ----------- |
| `timeout` | `Types.Timeout` | false    |             |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

---

### wps

Connect to WPS

```typescript
function wps(security: WPSSecurityPin): Promise<AccessPoint>
```

Parameters:

| Param      | Type             | Required | Description                                               |
| ---------- | ---------------- | -------- | --------------------------------------------------------- |
| `security` | `WPSSecurityPin` | false    | <br/>values: `'pushButton' \| 'pin' \| 'manufacturerPin'` |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:protocol:wifi |

#### Examples

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

### WifiFrequency

Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.

```typescript

```

---

### WifiSignalStrength

Strength of Wifi signal, value is negative based on RSSI specification.

```typescript

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

WifiSecurityMode
WifiSignalStrength
WifiFrequency

---

### AccessPointList

List of scanned Wifi networks available near the device.

```typescript
type AccessPointList = {
  list?: AccessPoint[] // Properties of a scanned wifi list item.
}
```

See also:

AccessPoint

---
