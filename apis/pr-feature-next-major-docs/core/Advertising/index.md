---
title: Advertising

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Advertising Module

---

Version Advertising 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [advertisingId](#advertisingid)
  - [appBundleId](#appbundleid)
  - [config](#config)
  - [deviceAttributes](#deviceattributes)
  - [listen](#listen)
  - [once](#once)
  - [policy](#policy)
- [Events](#events)
  - [policyChanged](#policychanged)
- [Types](#types)
  - [AdConfigurationOptions](#adconfigurationoptions)
  - [AdPolicy](#adpolicy)
  - [AdvertisingIdOptions](#advertisingidoptions)

## Usage

To use the Advertising module, you can import it into your project from the Firebolt SDK:

```javascript
import { Advertising } from '@firebolt-js/sdk'
```

## Overview

A module for platform provided advertising settings and functionality.

## Methods

### advertisingId

Get the advertising ID

```typescript
function advertisingId(options?: AdvertisingIdOptions): Promise<object>
```

Parameters:

| Param     | Type                                            | Required | Description           |
| --------- | ----------------------------------------------- | -------- | --------------------- |
| `options` | [`AdvertisingIdOptions`](#advertisingidoptions) | false    | AdvertisingId options |

Promise resolution:

| Property   | Type   | Description |
| ---------- | ------ | ----------- |
| `ifa`      | string |             |
| `ifa_type` | string |             |
| `lmt`      | string |             |

Capabilities:

| Role | Capability                                     |
| ---- | ---------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:identifier |

#### Examples

Getting the advertising ID

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let advertisingId = await Advertising.advertisingId(null)
console.log(advertisingId)
```

Value of `advertisingId`:

```javascript
{
	"ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
	"ifa_type": "idfa",
	"lmt": "0"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.advertisingId",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
    "ifa_type": "idfa",
    "lmt": "0"
  }
}
```

</details>

Getting the advertising ID with scope browse

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let advertisingId = await Advertising.advertisingId({
  scope: { type: 'browse', id: 'paidPlacement' },
})
console.log(advertisingId)
```

Value of `advertisingId`:

```javascript
{
	"ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
	"ifa_type": "idfa",
	"lmt": "0"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.advertisingId",
  "params": {
    "options": {
      "scope": {
        "type": "browse",
        "id": "paidPlacement"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
    "ifa_type": "idfa",
    "lmt": "0"
  }
}
```

</details>

Getting the advertising ID with scope content

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let advertisingId = await Advertising.advertisingId({
  scope: { type: 'content', id: 'metadata:linear:station:123' },
})
console.log(advertisingId)
```

Value of `advertisingId`:

```javascript
{
	"ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
	"ifa_type": "idfa",
	"lmt": "0"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.advertisingId",
  "params": {
    "options": {
      "scope": {
        "type": "content",
        "id": "metadata:linear:station:123"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
    "ifa_type": "idfa",
    "lmt": "0"
  }
}
```

</details>

---

### appBundleId

Get the App's Bundle ID

```typescript
function appBundleId(): Promise<string>
```

Promise resolution:

```typescript
string
```

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

Default Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let appBundleId = await Advertising.appBundleId()
console.log(appBundleId)
```

Value of `appBundleId`:

```javascript
'operator.app'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.appBundleId",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "operator.app"
}
```

</details>

---

### config

Build configuration object for Ad Framework initialization

```typescript
function config(options: AdConfigurationOptions): Promise<object>
```

Parameters:

| Param     | Type                                                | Required | Description           |
| --------- | --------------------------------------------------- | -------- | --------------------- |
| `options` | [`AdConfigurationOptions`](#adconfigurationoptions) | true     | Configuration options |

Promise resolution:

```typescript
object
```

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

Initializing the Ad Framework

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let adFrameworkConfig = await Advertising.config({
  environment: 'prod',
  authenticationEntity: 'MVPD',
})
console.log(adFrameworkConfig)
```

Value of `adFrameworkConfig`:

```javascript
{
	"adServerUrl": "https://demo.v.fwmrm.net/ad/p/1",
	"adServerUrlTemplate": "https://demo.v.fwmrm.net/ad/p/1?flag=+sltp+exvt+slcb+emcr+amcb+aeti&prof=12345:caf_allinone_profile &nw=12345&mode=live&vdur=123&caid=a110523018&asnw=372464&csid=gmott_ios_tablet_watch_live_ESPNU&ssnw=372464&vip=198.205.92.1&resp=vmap1&metr=1031&pvrn=12345&vprn=12345&vcid=1X0Ce7L3xRWlTeNhc7br8Q%3D%3D",
	"adNetworkId": "519178",
	"adProfileId": "12345:caf_allinone_profile",
	"adSiteSectionId": "caf_allinone_profile_section",
	"adOptOut": true,
	"privacyData": "ew0KICAicGR0IjogImdkcDp2MSIsDQogICJ1c19wcml2YWN5IjogIjEtTi0iLA0KICAibG10IjogIjEiIA0KfQ0K",
	"ifaValue": "01234567-89AB-CDEF-GH01-23456789ABCD",
	"ifa": "ewogICJ2YWx1ZSI6ICIwMTIzNDU2Ny04OUFCLUNERUYtR0gwMS0yMzQ1Njc4OUFCQ0QiLAogICJpZmFfdHlwZSI6ICJzc3BpZCIsCiAgImxtdCI6ICIwIgp9Cg==",
	"appName": "FutureToday",
	"appBundleId": "FutureToday.comcast",
	"distributorAppId": "1001",
	"deviceAdAttributes": "ewogICJib0F0dHJpYnV0ZXNGb3JSZXZTaGFyZUlkIjogIjEyMzQiCn0=",
	"coppa": 0,
	"authenticationEntity": "60f72475281cfba3852413bd53e957f6"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.config",
  "params": {
    "options": {
      "environment": "prod",
      "authenticationEntity": "MVPD"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "adServerUrl": "https://demo.v.fwmrm.net/ad/p/1",
    "adServerUrlTemplate": "https://demo.v.fwmrm.net/ad/p/1?flag=+sltp+exvt+slcb+emcr+amcb+aeti&prof=12345:caf_allinone_profile &nw=12345&mode=live&vdur=123&caid=a110523018&asnw=372464&csid=gmott_ios_tablet_watch_live_ESPNU&ssnw=372464&vip=198.205.92.1&resp=vmap1&metr=1031&pvrn=12345&vprn=12345&vcid=1X0Ce7L3xRWlTeNhc7br8Q%3D%3D",
    "adNetworkId": "519178",
    "adProfileId": "12345:caf_allinone_profile",
    "adSiteSectionId": "caf_allinone_profile_section",
    "adOptOut": true,
    "privacyData": "ew0KICAicGR0IjogImdkcDp2MSIsDQogICJ1c19wcml2YWN5IjogIjEtTi0iLA0KICAibG10IjogIjEiIA0KfQ0K",
    "ifaValue": "01234567-89AB-CDEF-GH01-23456789ABCD",
    "ifa": "ewogICJ2YWx1ZSI6ICIwMTIzNDU2Ny04OUFCLUNERUYtR0gwMS0yMzQ1Njc4OUFCQ0QiLAogICJpZmFfdHlwZSI6ICJzc3BpZCIsCiAgImxtdCI6ICIwIgp9Cg==",
    "appName": "FutureToday",
    "appBundleId": "FutureToday.comcast",
    "distributorAppId": "1001",
    "deviceAdAttributes": "ewogICJib0F0dHJpYnV0ZXNGb3JSZXZTaGFyZUlkIjogIjEyMzQiCn0=",
    "coppa": 0,
    "authenticationEntity": "60f72475281cfba3852413bd53e957f6"
  }
}
```

</details>

---

### deviceAttributes

Get the device advertising device attributes

```typescript
function deviceAttributes(): Promise<object>
```

Promise resolution:

```typescript
object
```

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

Getting the device attributes

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let deviceAttributes = await Advertising.deviceAttributes()
console.log(deviceAttributes)
```

Value of `deviceAttributes`:

```javascript
{
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.deviceAttributes",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {}
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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### policy

Get the advertising privacy and playback policy

To get the value of `policy` call the method like this:

```typescript
function policy(): Promise<AdPolicy>
```

Promise resolution:

[AdPolicy](#adpolicy)

Capabilities:

| Role | Capability                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------- |
| uses | xrn:firebolt:capability:privacy:advertising<br/>xrn:firebolt:capability:advertising:configuration |

#### Examples

Getting the advertising policy settings

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let adPolicy = await Advertising.policy()
console.log(adPolicy)
```

Value of `adPolicy`:

```javascript
{
	"skipRestriction": "adsUnwatched",
	"limitAdTracking": false
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.policy",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "skipRestriction": "adsUnwatched",
    "limitAdTracking": false
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function policy(callback: (value) => AdPolicy): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the advertising policy settings

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/sdk'

let listenerId = await policy((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `adPolicy`:

```javascript
{
	"skipRestriction": "adsUnwatched",
	"limitAdTracking": false
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.onPolicyChanged",
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
    "skipRestriction": "adsUnwatched",
    "limitAdTracking": false
  }
}
```

</details>

---

## Events

### policyChanged

See: [policy](#policy)

## Types

### AdConfigurationOptions

```typescript
type AdConfigurationOptions = {
  coppa?: boolean // Whether or not the app requires US COPPA compliance.
  environment?: 'prod' | 'test' // Whether the app is running in a production or test mode.
  authenticationEntity?: string // The authentication provider, when it is separate entity than the app provider, e.g. an MVPD.
}
```

---

### AdPolicy

Describes various ad playback enforcement rules that the app should follow.

```typescript
type AdPolicy = {
  skipRestriction?: SkipRestriction // The advertisement skip restriction.
  limitAdTracking?: boolean
}
```

See also:

'none' | 'adsUnwatched' | 'adsAll' | 'all'

---

### AdvertisingIdOptions

```typescript
type AdvertisingIdOptions = {
  scope?: {
    type: 'browse' | 'content' // The scope type, which will determine where to show advertisement
    id: string // A value that identifies a specific scope within the scope type
  }
}
```

---
