---
title: Privacy

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Privacy Module

---

Version Privacy 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [allowACRCollection](#allowacrcollection)
  - [allowAppContentAdTargeting](#allowappcontentadtargeting)
  - [allowCameraAnalytics](#allowcameraanalytics)
  - [allowPersonalization](#allowpersonalization)
  - [allowPrimaryBrowseAdTargeting](#allowprimarybrowseadtargeting)
  - [allowPrimaryContentAdTargeting](#allowprimarycontentadtargeting)
  - [allowProductAnalytics](#allowproductanalytics)
  - [allowRemoteDiagnostics](#allowremotediagnostics)
  - [allowResumePoints](#allowresumepoints)
  - [allowUnentitledPersonalization](#allowunentitledpersonalization)
  - [allowUnentitledResumePoints](#allowunentitledresumepoints)
  - [allowWatchHistory](#allowwatchhistory)
  - [listen](#listen)
  - [once](#once)
  - [settings](#settings)
- [Events](#events)
  - [allowACRCollectionChanged](#allowacrcollectionchanged)
  - [allowAppContentAdTargetingChanged](#allowappcontentadtargetingchanged)
  - [allowCameraAnalyticsChanged](#allowcameraanalyticschanged)
  - [allowPersonalizationChanged](#allowpersonalizationchanged)
  - [allowPrimaryBrowseAdTargetingChanged](#allowprimarybrowseadtargetingchanged)
  - [allowPrimaryContentAdTargetingChanged](#allowprimarycontentadtargetingchanged)
  - [allowProductAnalyticsChanged](#allowproductanalyticschanged)
  - [allowRemoteDiagnosticsChanged](#allowremotediagnosticschanged)
  - [allowResumePointsChanged](#allowresumepointschanged)
  - [allowUnentitledPersonalizationChanged](#allowunentitledpersonalizationchanged)
  - [allowUnentitledResumePointsChanged](#allowunentitledresumepointschanged)
  - [allowWatchHistoryChanged](#allowwatchhistorychanged)
- [Types](#types)
  - [PrivacySettings](#privacysettings)

## Usage

To use the Privacy module, you can import it into your project from the Firebolt SDK:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing device settings.

## Methods

### allowACRCollection

Whether the user allows their automatic content recognition data to be collected

To get the value of `allowACRCollection` call the method like this:

```typescript
function allowACRCollection(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowACRCollection()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowACRCollection",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowACRCollection()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowACRCollection",
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

To set the value of `allowACRCollection` call the method like this:

```typescript
function allowACRCollection(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowACRCollection(true)
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
  "method": "Privacy.setAllowACRCollection",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowACRCollection(false)
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
  "method": "Privacy.setAllowACRCollection",
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
function allowACRCollection(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowACRCollection((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowACRCollectionChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowACRCollection((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowACRCollectionChanged",
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

### allowAppContentAdTargeting

Whether the user allows ads to be targeted to the user while watching content in apps

To get the value of `allowAppContentAdTargeting` call the method like this:

```typescript
function allowAppContentAdTargeting(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowAppContentAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowAppContentAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowAppContentAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowAppContentAdTargeting",
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

To set the value of `allowAppContentAdTargeting` call the method like this:

```typescript
function allowAppContentAdTargeting(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowAppContentAdTargeting(true)
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
  "method": "Privacy.setAllowAppContentAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowAppContentAdTargeting(false)
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
  "method": "Privacy.setAllowAppContentAdTargeting",
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
function allowAppContentAdTargeting(
  callback: (value) => boolean,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowAppContentAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowAppContentAdTargetingChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowAppContentAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowAppContentAdTargetingChanged",
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

### allowCameraAnalytics

Whether the user allows data from their camera to be used for Product Analytics

To get the value of `allowCameraAnalytics` call the method like this:

```typescript
function allowCameraAnalytics(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowCameraAnalytics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowCameraAnalytics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowCameraAnalytics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowCameraAnalytics",
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

To set the value of `allowCameraAnalytics` call the method like this:

```typescript
function allowCameraAnalytics(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowCameraAnalytics(true)
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
  "method": "Privacy.setAllowCameraAnalytics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowCameraAnalytics(false)
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
  "method": "Privacy.setAllowCameraAnalytics",
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
function allowCameraAnalytics(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowCameraAnalytics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowCameraAnalyticsChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowCameraAnalytics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowCameraAnalyticsChanged",
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

### allowPersonalization

Whether the user allows their usage data to be used for personalization and recommendations

To get the value of `allowPersonalization` call the method like this:

```typescript
function allowPersonalization(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPersonalization()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPersonalization",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPersonalization()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPersonalization",
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

To set the value of `allowPersonalization` call the method like this:

```typescript
function allowPersonalization(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPersonalization(true)
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
  "method": "Privacy.setAllowPersonalization",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPersonalization(false)
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
  "method": "Privacy.setAllowPersonalization",
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
function allowPersonalization(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPersonalization((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPersonalizationChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPersonalization((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPersonalizationChanged",
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

### allowPrimaryBrowseAdTargeting

Whether the user allows ads to be targeted to the user while browsing in the primary experience

To get the value of `allowPrimaryBrowseAdTargeting` call the method like this:

```typescript
function allowPrimaryBrowseAdTargeting(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPrimaryBrowseAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPrimaryBrowseAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPrimaryBrowseAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPrimaryBrowseAdTargeting",
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

To set the value of `allowPrimaryBrowseAdTargeting` call the method like this:

```typescript
function allowPrimaryBrowseAdTargeting(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPrimaryBrowseAdTargeting(true)
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
  "method": "Privacy.setAllowPrimaryBrowseAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPrimaryBrowseAdTargeting(false)
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
  "method": "Privacy.setAllowPrimaryBrowseAdTargeting",
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
function allowPrimaryBrowseAdTargeting(
  callback: (value) => boolean,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPrimaryBrowseAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPrimaryBrowseAdTargetingChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPrimaryBrowseAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPrimaryBrowseAdTargetingChanged",
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

### allowPrimaryContentAdTargeting

Whether the user allows ads to be targeted to the user while watching content in the primary experience

To get the value of `allowPrimaryContentAdTargeting` call the method like this:

```typescript
function allowPrimaryContentAdTargeting(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPrimaryContentAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPrimaryContentAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowPrimaryContentAdTargeting()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowPrimaryContentAdTargeting",
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

To set the value of `allowPrimaryContentAdTargeting` call the method like this:

```typescript
function allowPrimaryContentAdTargeting(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPrimaryContentAdTargeting(true)
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
  "method": "Privacy.setAllowPrimaryContentAdTargeting",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowPrimaryContentAdTargeting(false)
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
  "method": "Privacy.setAllowPrimaryContentAdTargeting",
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
function allowPrimaryContentAdTargeting(
  callback: (value) => boolean,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPrimaryContentAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPrimaryContentAdTargetingChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowPrimaryContentAdTargeting((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowPrimaryContentAdTargetingChanged",
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

### allowProductAnalytics

Whether the user allows their usage data can be used for analytics about the product

To get the value of `allowProductAnalytics` call the method like this:

```typescript
function allowProductAnalytics(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowProductAnalytics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowProductAnalytics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowProductAnalytics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowProductAnalytics",
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

To set the value of `allowProductAnalytics` call the method like this:

```typescript
function allowProductAnalytics(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowProductAnalytics(true)
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
  "method": "Privacy.setAllowProductAnalytics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowProductAnalytics(false)
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
  "method": "Privacy.setAllowProductAnalytics",
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
function allowProductAnalytics(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowProductAnalytics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowProductAnalyticsChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowProductAnalytics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowProductAnalyticsChanged",
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

### allowRemoteDiagnostics

Whether the user allows their personal data to be included in diagnostic telemetry. This also allows whether device logs can be remotely accessed from the client device

To get the value of `allowRemoteDiagnostics` call the method like this:

```typescript
function allowRemoteDiagnostics(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowRemoteDiagnostics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowRemoteDiagnostics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowRemoteDiagnostics()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowRemoteDiagnostics",
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

To set the value of `allowRemoteDiagnostics` call the method like this:

```typescript
function allowRemoteDiagnostics(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowRemoteDiagnostics(true)
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
  "method": "Privacy.setAllowRemoteDiagnostics",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowRemoteDiagnostics(false)
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
  "method": "Privacy.setAllowRemoteDiagnostics",
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
function allowRemoteDiagnostics(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowRemoteDiagnostics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowRemoteDiagnosticsChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowRemoteDiagnostics((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowRemoteDiagnosticsChanged",
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

### allowResumePoints

Whether the user allows resume points for content to show in the main experience

To get the value of `allowResumePoints` call the method like this:

```typescript
function allowResumePoints(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowResumePoints()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowResumePoints",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowResumePoints()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowResumePoints",
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

To set the value of `allowResumePoints` call the method like this:

```typescript
function allowResumePoints(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowResumePoints(true)
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
  "method": "Privacy.setAllowResumePoints",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowResumePoints(false)
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
  "method": "Privacy.setAllowResumePoints",
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
function allowResumePoints(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowResumePoints((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowResumePointsChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowResumePoints((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowResumePointsChanged",
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

### allowUnentitledPersonalization

Whether the user allows their usage data to be used for personalization and recommendations for unentitled content

To get the value of `allowUnentitledPersonalization` call the method like this:

```typescript
function allowUnentitledPersonalization(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowUnentitledPersonalization()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowUnentitledPersonalization",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowUnentitledPersonalization()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowUnentitledPersonalization",
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

To set the value of `allowUnentitledPersonalization` call the method like this:

```typescript
function allowUnentitledPersonalization(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowUnentitledPersonalization(true)
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
  "method": "Privacy.setAllowUnentitledPersonalization",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowUnentitledPersonalization(false)
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
  "method": "Privacy.setAllowUnentitledPersonalization",
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
function allowUnentitledPersonalization(
  callback: (value) => boolean,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowUnentitledPersonalization((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowUnentitledPersonalizationChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowUnentitledPersonalization((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowUnentitledPersonalizationChanged",
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

### allowUnentitledResumePoints

Whether the user allows resume points for content from unentitled providers to show in the main experience

To get the value of `allowUnentitledResumePoints` call the method like this:

```typescript
function allowUnentitledResumePoints(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowUnentitledResumePoints()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowUnentitledResumePoints",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowUnentitledResumePoints()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowUnentitledResumePoints",
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

To set the value of `allowUnentitledResumePoints` call the method like this:

```typescript
function allowUnentitledResumePoints(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowUnentitledResumePoints(true)
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
  "method": "Privacy.setAllowUnentitledResumePoints",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowUnentitledResumePoints(false)
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
  "method": "Privacy.setAllowUnentitledResumePoints",
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
function allowUnentitledResumePoints(
  callback: (value) => boolean,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowUnentitledResumePoints((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowUnentitledResumePointsChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowUnentitledResumePoints((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowUnentitledResumePointsChanged",
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

### allowWatchHistory

Whether the user allows their watch history from all sources to show in the main experience

To get the value of `allowWatchHistory` call the method like this:

```typescript
function allowWatchHistory(): Promise<boolean>
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowWatchHistory()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowWatchHistory",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let allow = await Privacy.allowWatchHistory()
console.log(allow)
```

Value of `allow`:

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
  "method": "Privacy.allowWatchHistory",
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

To set the value of `allowWatchHistory` call the method like this:

```typescript
function allowWatchHistory(value: boolean): Promise<void>
```

Parameters:

| Param   | Type      | Required | Description |
| ------- | --------- | -------- | ----------- |
| `value` | `boolean` | true     |             |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowWatchHistory(true)
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
  "method": "Privacy.setAllowWatchHistory",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let result = await Privacy.allowWatchHistory(false)
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
  "method": "Privacy.setAllowWatchHistory",
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
function allowWatchHistory(callback: (value) => boolean): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowWatchHistory((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowWatchHistoryChanged",
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

Default example #2

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let listenerId = await allowWatchHistory((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `allow`:

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
  "method": "Privacy.onAllowWatchHistoryChanged",
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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### settings

Gets the allowed value for all privacy settings

```typescript
function settings(): Promise<PrivacySettings>
```

Promise resolution:

[PrivacySettings](#privacysettings)

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

Default Example

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

let settings = await Privacy.settings()
console.log(settings)
```

Value of `settings`:

```javascript
{
	"allowACRCollection": true,
	"allowResumePoints": false,
	"allowAppContentAdTargeting": false,
	"allowCameraAnalytics": true,
	"allowPersonalization": true,
	"allowPrimaryBrowseAdTargeting": false,
	"allowPrimaryContentAdTargeting": false,
	"allowProductAnalytics": true,
	"allowRemoteDiagnostics": true,
	"allowUnentitledPersonalization": true,
	"allowUnentitledResumePoints": false,
	"allowWatchHistory": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Privacy.settings",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "allowACRCollection": true,
    "allowResumePoints": false,
    "allowAppContentAdTargeting": false,
    "allowCameraAnalytics": true,
    "allowPersonalization": true,
    "allowPrimaryBrowseAdTargeting": false,
    "allowPrimaryContentAdTargeting": false,
    "allowProductAnalytics": true,
    "allowRemoteDiagnostics": true,
    "allowUnentitledPersonalization": true,
    "allowUnentitledResumePoints": false,
    "allowWatchHistory": true
  }
}
```

</details>

---

## Events

### allowACRCollectionChanged

See: [allowACRCollection](#allowacrcollection)

### allowAppContentAdTargetingChanged

See: [allowAppContentAdTargeting](#allowappcontentadtargeting)

### allowCameraAnalyticsChanged

See: [allowCameraAnalytics](#allowcameraanalytics)

### allowPersonalizationChanged

See: [allowPersonalization](#allowpersonalization)

### allowPrimaryBrowseAdTargetingChanged

See: [allowPrimaryBrowseAdTargeting](#allowprimarybrowseadtargeting)

### allowPrimaryContentAdTargetingChanged

See: [allowPrimaryContentAdTargeting](#allowprimarycontentadtargeting)

### allowProductAnalyticsChanged

See: [allowProductAnalytics](#allowproductanalytics)

### allowRemoteDiagnosticsChanged

See: [allowRemoteDiagnostics](#allowremotediagnostics)

### allowResumePointsChanged

See: [allowResumePoints](#allowresumepoints)

### allowUnentitledPersonalizationChanged

See: [allowUnentitledPersonalization](#allowunentitledpersonalization)

### allowUnentitledResumePointsChanged

See: [allowUnentitledResumePoints](#allowunentitledresumepoints)

### allowWatchHistoryChanged

See: [allowWatchHistory](#allowwatchhistory)

## Types

### PrivacySettings

```typescript
type PrivacySettings = {
  allowACRCollection: boolean
  allowResumePoints: boolean
  allowAppContentAdTargeting: boolean
  allowCameraAnalytics: boolean
  allowPersonalization: boolean
  allowPrimaryBrowseAdTargeting: boolean
  allowPrimaryContentAdTargeting: boolean
  allowProductAnalytics: boolean
  allowRemoteDiagnostics: boolean
  allowUnentitledPersonalization: boolean
  allowUnentitledResumePoints: boolean
  allowWatchHistory: boolean
}
```

---
