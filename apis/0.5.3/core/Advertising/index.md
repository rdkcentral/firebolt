---
title: Advertising
---

# Advertising Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [advertising.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/advertising.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)

 - [Methods](#methods)
    - [config](#config)
    - [policy](#policy)
    - [advertisingId](#advertisingid)
    - [deviceAttributes](#deviceattributes)
    - [appBundleId](#appbundleid)
 - [Schemas](#schemas)
    - [AdPolicy](#adpolicy)
    - [SkipRestriction](#skiprestriction)
    - [AdConfigurationOptions](#adconfigurationoptions)

<span></span>

## Usage
To use the Advertising module, you can import it into your project from the Firebolt SDK:

```javascript
import { Advertising } from '@firebolt-js/sdk'
```
## Overview
A module for platform provided advertising settings and functionality.

## Events


## Methods
### config
Build configuration object for Ad Framework initialization

```typescript
function config(options: AdConfigurationOptions): Promise<AdConfiguration>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `options` | [`AdConfigurationOptions`](#adconfigurationoptions) | true | Configuration options  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`AdConfiguration`](#adconfiguration) | An opaque object represneting the AdConfiguration |


---

#### Examples

##### Initializing the Ad Framework
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Advertising } from '@firebolt-js/sdk'

Advertising.config({"environment":"prod","authenticationEntity":"MVPD"})
    .then(adFrameworkConfig => {
        console.log(adFrameworkConfig)
    })
```
Value of `adFrameworkConfig`

```javascript
{
  "adServerUrl": "http://demo.v.fwmrm.net/ad/p/1",
  "adServerUrlTemplate": "http://demo.v.fwmrm.net/ad/p/1?flag=+sltp+exvt+slcb+emcr+amcb+aeti&prof=12345:caf_allinone_profile &nw=12345&mode=live&vdur=123&caid=a110523018&asnw=372464&csid=gmott_ios_tablet_watch_live_ESPNU&ssnw=372464&vip=198.205.92.1&resp=vmap1&metr=1031&pvrn=12345&vprn=12345&vcid=1X0Ce7L3xRWlTeNhc7br8Q%3D%3D",
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

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "advertising.config",
  "params": {
    "options": {
      "environment": "prod",
      "authenticationEntity": "MVPD"
    }
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "adServerUrl": "http://demo.v.fwmrm.net/ad/p/1",
    "adServerUrlTemplate": "http://demo.v.fwmrm.net/ad/p/1?flag=+sltp+exvt+slcb+emcr+amcb+aeti&prof=12345:caf_allinone_profile &nw=12345&mode=live&vdur=123&caid=a110523018&asnw=372464&csid=gmott_ios_tablet_watch_live_ESPNU&ssnw=372464&vip=198.205.92.1&resp=vmap1&metr=1031&pvrn=12345&vprn=12345&vcid=1X0Ce7L3xRWlTeNhc7br8Q%3D%3D",
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

### policy
Get the advertising privacy and playback policy

```typescript
function policy(): Promise<AdPolicy>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`AdPolicy`](#adpolicy) | Describes various ad playback enforcement rules that the app should follow. |


---

#### Examples

##### Getting the advertising policy settings
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Advertising } from '@firebolt-js/sdk'

Advertising.policy()
    .then(adPolicy => {
        console.log(adPolicy)
    })
```
Value of `adPolicy`

```javascript
{
  "skipRestriction": "adsUnwatched",
  "limitAdTracking": false
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
  "method": "advertising.policy",
  "params": {}
}
```

###### Response

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

### advertisingId
Get the advertising ID

```typescript
function advertisingId(): Promise<object>
```
#### Promise Resolution

the advertising ID

| Field | Type | Description |
| ----- | ---- | ----------- |
| `ifa` | `string` |  |
| `ifa_type` | `string` |  |
| `lmt` | `string` |  |


---

#### Examples

##### Getting the advertising ID
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Advertising } from '@firebolt-js/sdk'

Advertising.advertisingId()
    .then(advertisingId => {
        console.log(advertisingId)
    })
```
Value of `advertisingId`

```javascript
{
  "ifa": "01234567-89AB-CDEF-GH01-23456789ABCD",
  "ifa_type": "idfa",
  "lmt": "0"
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
  "method": "advertising.advertisingId",
  "params": {}
}
```

###### Response

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

### deviceAttributes
Get the device advertising device attributes

```typescript
function deviceAttributes(): Promise<object>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `object` | the device attributes |


---

#### Examples

##### Getting the device attributes
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Advertising } from '@firebolt-js/sdk'

Advertising.deviceAttributes()
    .then(deviceAttributes => {
        console.log(deviceAttributes)
    })
```
Value of `deviceAttributes`

```javascript
{}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "advertising.deviceAttributes",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {}
}
```

</details>




---

### appBundleId
Get the App's Bundle ID

```typescript
function appBundleId(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the app bundle ID |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Advertising } from '@firebolt-js/sdk'

Advertising.appBundleId()
    .then(appBundleId => {
        console.log(appBundleId)
    })
```
Value of `appBundleId`

```javascript
"operator.app"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "advertising.appBundleId",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "operator.app"
}
```

</details>




---



## Schemas

### AdPolicy

```typescript
type AdPolicy = {
  skipRestriction?: SkipRestriction  // The advertisement skip restriction.
  limitAdTracking?: boolean
}
```



#### Details

Describes various ad playback enforcement rules that the app should follow.

---

### SkipRestriction

```typescript
type SkipRestriction = 'none' | 'adsUnwatched' | 'adsAll' | 'all'
```



#### Details

The advertisement skip restriction.

Applies to fast-forward/rewind (e.g. trick mode), seeking over an entire opportunity (e.g. jump), seeking out of what's currently playing, and "Skip this ad..." features. Seeking over multiple ad opportunities only requires playback of the _last_ opportunity, not all opportunities, preceding the seek destination.

| Value        | Description                                                                    |
|--------------|--------------------------------------------------------------------------------|
| none         |No fast-forward, jump, or skip restrictions                                    |
| adsUnwatched | Restrict fast-forward, jump, and skip for unwatched ad opportunities only.     |
| adsAll       | Restrict fast-forward, jump, and skip for all ad opportunities                 |
| all          | Restrict fast-forward, jump, and skip for all ad opportunities and all content |

Namespace: `xrn:advertising:policy:skipRestriction:`



---

### AdConfigurationOptions

```typescript
type AdConfigurationOptions = {
  coppa?: boolean                // Whether or not the app requires US COPPA compliance.
  environment?: 'prod' | 'test'  // Whether the app is running in a production or test mode.
  authenticationEntity?: string  // The authentication provider, when it is separate entity than the app provider, e.g. an MVPD.
}
```





---


