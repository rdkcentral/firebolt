---
title: Privacy

version: chore-pr-channel
layout: default
sdk: manage
---

# Privacy Module
---
Version Privacy 1.0.1-chore-pr-channel.2

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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowACRCollection()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowACRCollection()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowACRCollection(true)
    .then(result => {
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

Privacy.allowACRCollection(false)
    .then(result => {
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

allowACRCollection(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowACRCollection(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowAppContentAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowAppContentAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowAppContentAdTargeting(true)
    .then(result => {
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

Privacy.allowAppContentAdTargeting(false)
    .then(result => {
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
function allowAppContentAdTargeting(callback: (value) => boolean): Promise<number>
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

allowAppContentAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowAppContentAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowCameraAnalytics()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowCameraAnalytics()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowCameraAnalytics(true)
    .then(result => {
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

Privacy.allowCameraAnalytics(false)
    .then(result => {
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

allowCameraAnalytics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowCameraAnalytics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPersonalization()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowPersonalization()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPersonalization(true)
    .then(result => {
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

Privacy.allowPersonalization(false)
    .then(result => {
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

allowPersonalization(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowPersonalization(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPrimaryBrowseAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowPrimaryBrowseAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPrimaryBrowseAdTargeting(true)
    .then(result => {
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

Privacy.allowPrimaryBrowseAdTargeting(false)
    .then(result => {
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
function allowPrimaryBrowseAdTargeting(callback: (value) => boolean): Promise<number>
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

allowPrimaryBrowseAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowPrimaryBrowseAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPrimaryContentAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowPrimaryContentAdTargeting()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowPrimaryContentAdTargeting(true)
    .then(result => {
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

Privacy.allowPrimaryContentAdTargeting(false)
    .then(result => {
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
function allowPrimaryContentAdTargeting(callback: (value) => boolean): Promise<number>
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

allowPrimaryContentAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowPrimaryContentAdTargeting(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowProductAnalytics()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowProductAnalytics()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowProductAnalytics(true)
    .then(result => {
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

Privacy.allowProductAnalytics(false)
    .then(result => {
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

allowProductAnalytics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowProductAnalytics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowRemoteDiagnostics()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowRemoteDiagnostics()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowRemoteDiagnostics(true)
    .then(result => {
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

Privacy.allowRemoteDiagnostics(false)
    .then(result => {
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

allowRemoteDiagnostics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowRemoteDiagnostics(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowResumePoints()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowResumePoints()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowResumePoints(true)
    .then(result => {
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

Privacy.allowResumePoints(false)
    .then(result => {
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

allowResumePoints(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowResumePoints(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowUnentitledPersonalization()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowUnentitledPersonalization()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowUnentitledPersonalization(true)
    .then(result => {
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

Privacy.allowUnentitledPersonalization(false)
    .then(result => {
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
function allowUnentitledPersonalization(callback: (value) => boolean): Promise<number>
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

allowUnentitledPersonalization(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowUnentitledPersonalization(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowUnentitledResumePoints()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowUnentitledResumePoints()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowUnentitledResumePoints(true)
    .then(result => {
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

Privacy.allowUnentitledResumePoints(false)
    .then(result => {
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
function allowUnentitledResumePoints(callback: (value) => boolean): Promise<number>
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

allowUnentitledResumePoints(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowUnentitledResumePoints(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowWatchHistory()
    .then(allow => {
        console.log(allow)
    })
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

Privacy.allowWatchHistory()
    .then(allow => {
        console.log(allow)
    })
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

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `value` | `boolean` | true |   |


Promise resolution:

```typescript
null
```

#### Examples


Default example #1

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.allowWatchHistory(true)
    .then(result => {
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

Privacy.allowWatchHistory(false)
    .then(result => {
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

allowWatchHistory(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

allowWatchHistory(value => {
  console.log(value)
}).then(listenerId => {
  console.log(listenerId)
})
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

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module  pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
```

The `once` method will only pass the next instance of this event, and then dicard the listener you provided.

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event to listen for, see [Events](#events). |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. |

Promise resolution:

| Type | Description |
|------|-------------|
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Privacy.clear(id)` |

Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| *callback* | `function` | Yes | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |


Callback parameters:

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `event` | `string` | Yes | The event that has occured listen for, see [Events](#events). |
| `data` | `any` | Yes | The event data, which depends on which event is firing, see [Events](#events). |


Promise resolution:

| Type | Description |
|------|-------------|
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

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |


#### Examples


Default Example

JavaScript:

```javascript
import { Privacy } from '@firebolt-js/manage-sdk'

Privacy.settings()
    .then(settings => {
        console.log(settings)
    })
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