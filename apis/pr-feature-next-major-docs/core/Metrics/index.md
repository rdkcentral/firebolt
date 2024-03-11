---
title: Metrics

version: pr-feature-next-major-docs
layout: default
sdk: core
---

# Metrics Module

---

Version Metrics 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [action](#action)
  - [error](#error)
  - [mediaEnded](#mediaended)
  - [mediaLoadStart](#medialoadstart)
  - [mediaPause](#mediapause)
  - [mediaPlay](#mediaplay)
  - [mediaPlaying](#mediaplaying)
  - [mediaProgress](#mediaprogress)
  - [mediaRateChange](#mediaratechange)
  - [mediaRenditionChange](#mediarenditionchange)
  - [mediaSeeked](#mediaseeked)
  - [mediaSeeking](#mediaseeking)
  - [mediaWaiting](#mediawaiting)
  - [page](#page)
  - [ready](#ready)
  - [signIn](#signin)
  - [signOut](#signout)
  - [startContent](#startcontent)
  - [stopContent](#stopcontent)
- [Types](#types)
  - [ErrorType](#errortype)
  - [MediaPosition](#mediaposition)

## Usage

To use the Metrics module, you can import it into your project from the Firebolt SDK:

```javascript
import { Metrics } from '@firebolt-js/sdk'
```

## Overview

Methods for sending metrics

## Methods

### action

Inform the platform of something not covered by other Metrics APIs.

```typescript
function action(
  category: 'user' | 'app',
  type: string,
  parameters?: object,
): Promise<boolean>
```

Parameters:

| Param        | Type     | Required | Description                                                                                                                                 |
| ------------ | -------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `category`   | `string` | true     | The category of action being logged. Must be 'user' for user-initated actions or 'app' for all other actions <br/>values: `'user' \| 'app'` |
| `type`       | `string` | true     | A short, indexible identifier for the action, e.g. 'SignIn Prompt Displayed' <br/>maxLength: 256                                            |
| `parameters` | `object` | false    |                                                                                                                                             |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send foo action

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.action('user', 'The user did foo', null)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.action",
  "params": {
    "category": "user",
    "type": "The user did foo"
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

---

### error

Inform the platform of an error that has occured in your app.

```typescript
function error(
  type: ErrorType,
  code: string,
  description: string,
  visible: boolean,
  parameters?: object,
): Promise<boolean>
```

Parameters:

| Param         | Type                      | Required | Description                                                                                        |
| ------------- | ------------------------- | -------- | -------------------------------------------------------------------------------------------------- |
| `type`        | [`ErrorType`](#errortype) | true     | The type of error <br/>values: `'network' \| 'media' \| 'restriction' \| 'entitlement' \| 'other'` |
| `code`        | `string`                  | true     | an app-specific error code                                                                         |
| `description` | `string`                  | true     | A short description of the error                                                                   |
| `visible`     | `boolean`                 | true     | Whether or not this error was visible to the user.                                                 |
| `parameters`  | `object`                  | false    | Optional additional parameters to be logged with the error                                         |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send error metric

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.error(
  'media',
  'MEDIA-STALLED',
  'playback stalled',
  true,
  null,
)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.error",
  "params": {
    "type": "media",
    "code": "MEDIA-STALLED",
    "description": "playback stalled",
    "visible": true
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

---

### mediaEnded

Called when playback has stopped because the end of the media was reached.

```typescript
function mediaEnded(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send ended metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaEnded('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaEnded",
  "params": {
    "entityId": "345"
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

---

### mediaLoadStart

Called when setting the URL of a media asset to play, in order to infer load time.

```typescript
function mediaLoadStart(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send loadstart metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaLoadStart('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaLoadStart",
  "params": {
    "entityId": "345"
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

---

### mediaPause

Called when media playback will pause due to an intentional pause operation.

```typescript
function mediaPause(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send pause metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaPause('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaPause",
  "params": {
    "entityId": "345"
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

---

### mediaPlay

Called when media playback should start due to autoplay, user-initiated play, or unpausing.

```typescript
function mediaPlay(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send play metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaPlay('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaPlay",
  "params": {
    "entityId": "345"
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

---

### mediaPlaying

Called when media playback actually starts due to autoplay, user-initiated play, unpausing, or recovering from a buffering interuption.

```typescript
function mediaPlaying(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send playing metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaPlaying('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaPlaying",
  "params": {
    "entityId": "345"
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

---

### mediaProgress

Called every 60 seconds as media playback progresses.

```typescript
function mediaProgress(
  entityId: string,
  progress: MediaPosition,
): Promise<boolean>
```

Parameters:

| Param      | Type                              | Required | Description                                                                                                                                                                |
| ---------- | --------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entityId` | `string`                          | true     | The entityId of the media.                                                                                                                                                 |
| `progress` | [`MediaPosition`](#mediaposition) | true     | Progress of playback, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send progress metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaProgress('345', 0.75)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaProgress",
  "params": {
    "entityId": "345",
    "progress": 0.75
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

---

### mediaRateChange

Called when the playback rate of media is changed.

```typescript
function mediaRateChange(entityId: string, rate: number): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |
| `rate`     | `number` | true     | The new playback rate.     |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send ratechange metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaRateChange('345', 2)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaRateChange",
  "params": {
    "entityId": "345",
    "rate": 2
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

---

### mediaRenditionChange

Called when the playback rendition (e.g. bitrate, dimensions, profile, etc) is changed.

```typescript
function mediaRenditionChange(
  entityId: string,
  bitrate: number,
  width: number,
  height: number,
  profile?: string,
): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                                       |
| ---------- | -------- | -------- | ------------------------------------------------- |
| `entityId` | `string` | true     | The entityId of the media.                        |
| `bitrate`  | `number` | true     | The new bitrate in kbps.                          |
| `width`    | `number` | true     | The new resolution width.                         |
| `height`   | `number` | true     | The new resolution height.                        |
| `profile`  | `string` | false    | A description of the new profile, e.g. 'HDR' etc. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send renditionchange metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaRenditionChange(
  '345',
  5000,
  1920,
  1080,
  'HDR+',
)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaRenditionChange",
  "params": {
    "entityId": "345",
    "bitrate": 5000,
    "width": 1920,
    "height": 1080,
    "profile": "HDR+"
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

---

### mediaSeeked

Called when a seek is completed during media playback.

```typescript
function mediaSeeked(
  entityId: string,
  position: MediaPosition,
): Promise<boolean>
```

Parameters:

| Param      | Type                              | Required | Description                                                                                                                                                                                    |
| ---------- | --------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entityId` | `string`                          | true     | The entityId of the media.                                                                                                                                                                     |
| `position` | [`MediaPosition`](#mediaposition) | true     | Resulting position of the seek operation, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send seeked metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaSeeked('345', 0.51)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaSeeked",
  "params": {
    "entityId": "345",
    "position": 0.51
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

---

### mediaSeeking

Called when a seek is initiated during media playback.

```typescript
function mediaSeeking(entityId: string, target: MediaPosition): Promise<boolean>
```

Parameters:

| Param      | Type                              | Required | Description                                                                                                                                                                          |
| ---------- | --------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `entityId` | `string`                          | true     | The entityId of the media.                                                                                                                                                           |
| `target`   | [`MediaPosition`](#mediaposition) | true     | Target destination of the seek, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send seeking metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaSeeking('345', 0.5)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaSeeking",
  "params": {
    "entityId": "345",
    "target": 0.5
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

---

### mediaWaiting

Called when media playback will halt due to a network, buffer, or other unintentional constraint.

```typescript
function mediaWaiting(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                |
| ---------- | -------- | -------- | -------------------------- |
| `entityId` | `string` | true     | The entityId of the media. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

Send waiting metric.

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.mediaWaiting('345')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.mediaWaiting",
  "params": {
    "entityId": "345"
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

---

### page

Inform the platform that your user has navigated to a page or view.

```typescript
function page(pageId: string): Promise<boolean>
```

Parameters:

| Param    | Type     | Required | Description             |
| -------- | -------- | -------- | ----------------------- |
| `pageId` | `string` | true     | Page ID of the content. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send page metric

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.page('xyz')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.page",
  "params": {
    "pageId": "xyz"
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

Send startContent metric w/ entity

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.page('home')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.page",
  "params": {
    "pageId": "home"
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

---

### ready

_This is an private RPC method._

Inform the platform that your app is minimally usable. This method is called automatically by `Lifecycle.ready()`

Result:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send ready metric

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Metrics.ready",
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

---

### signIn

_This is an private RPC method._

Log a sign in event, called by Discovery.signIn().

Result:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send signIn metric

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Metrics.signIn",
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

Send signIn metric with entitlements

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Metrics.signIn",
  "params": {
    "entitlements": [
      {
        "entitlementId": "123",
        "startTime": "2025-01-01T00:00:00.000Z",
        "endTime": "2025-01-01T00:00:00.000Z"
      }
    ]
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

---

### signOut

_This is an private RPC method._

Log a sign out event, called by Discovery.signOut().

Result:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send signOut metric

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Metrics.signOut",
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

---

### startContent

Inform the platform that your user has started content.

```typescript
function startContent(entityId?: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                        |
| ---------- | -------- | -------- | ---------------------------------- |
| `entityId` | `string` | false    | Optional entity ID of the content. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send startContent metric

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.startContent(null)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.startContent",
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

Send startContent metric w/ entity

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.startContent('abc')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.startContent",
  "params": {
    "entityId": "abc"
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

---

### stopContent

Inform the platform that your user has stopped content.

```typescript
function stopContent(entityId?: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                        |
| ---------- | -------- | -------- | ---------------------------------- |
| `entityId` | `string` | false    | Optional entity ID of the content. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

Send stopContent metric

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.stopContent(null)
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.stopContent",
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

Send stopContent metric w/ entity

JavaScript:

```javascript
import { Metrics } from '@firebolt-js/sdk'

let success = await Metrics.stopContent('abc')
console.log(success)
```

Value of `success`:

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
  "method": "Metrics.stopContent",
  "params": {
    "entityId": "abc"
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

---

## Types

### ErrorType

```typescript
enum ErrorType {
  NETWORK = 'network',
  MEDIA = 'media',
  RESTRICTION = 'restriction',
  ENTITLEMENT = 'entitlement',
  OTHER = 'other',
}
```

---

### MediaPosition

Represents a position inside playback content, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration.

```typescript
type MediaPosition = void | number | number
```

---
