---
title: Metrics

version: next-major
layout: default
sdk: core
---

# Metrics Module

---

Version Metrics 0.0.0-unknown.0

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
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [EventObject](#eventobject)

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
  category: string,
  type: string,
  parameters: object,
): Promise<boolean>
```

Parameters:

| Param        | Type     | Required | Description                                                                                                                                 |
| ------------ | -------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `category`   | `string` | true     | The category of action being logged. Must be 'user' for user-initated actions or 'app' for all other actions <br/>values: `'user' \| 'app'` |
| `type`       | `string` | true     | A short, indexible identifier for the action, e.g. 'SignIn Prompt Displayed' <br/>maxLength: 256                                            |
| `parameters` | `object` | false    |                                                                                                                                             |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### error

Inform the platform of an error that has occured in your app.

```typescript
function error(
  type: ErrorType,
  code: string,
  description: string,
  visible: boolean,
  parameters: object,
): Promise<boolean>
```

Parameters:

| Param         | Type        | Required | Description                                                                                        |
| ------------- | ----------- | -------- | -------------------------------------------------------------------------------------------------- |
| `type`        | `ErrorType` | true     | The type of error <br/>values: `'network' \| 'media' \| 'restriction' \| 'entitlement' \| 'other'` |
| `code`        | `string`    | true     | an app-specific error code                                                                         |
| `description` | `string`    | true     | A short description of the error                                                                   |
| `visible`     | `boolean`   | true     | Whether or not this error was visible to the user.                                                 |
| `parameters`  | `object`    | false    | Optional additional parameters to be logged with the error                                         |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

| Param      | Type            | Required | Description                                                                                                                                                                |
| ---------- | --------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entityId` | `string`        | true     | The entityId of the media.                                                                                                                                                 |
| `progress` | `MediaPosition` | true     | Progress of playback, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

---

### mediaRenditionChange

Called when the playback rendition (e.g. bitrate, dimensions, profile, etc) is changed.

```typescript
function mediaRenditionChange(
  entityId: string,
  bitrate: number,
  width: number,
  height: number,
  profile: string,
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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

| Param      | Type            | Required | Description                                                                                                                                                                                    |
| ---------- | --------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `entityId` | `string`        | true     | The entityId of the media.                                                                                                                                                                     |
| `position` | `MediaPosition` | true     | Resulting position of the seek operation, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

---

### mediaSeeking

Called when a seek is initiated during media playback.

```typescript
function mediaSeeking(entityId: string, target: MediaPosition): Promise<boolean>
```

Parameters:

| Param      | Type            | Required | Description                                                                                                                                                                          |
| ---------- | --------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `entityId` | `string`        | true     | The entityId of the media.                                                                                                                                                           |
| `target`   | `MediaPosition` | true     | Target destination of the seek, as a decimal percentage (0-0.999) for content with a known duration, or an integer number of seconds (0-86400) for content with an unknown duration. |

Promise resolution:

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:metrics:media |

#### Examples

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

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### ready

_This is an private RPC method._

Inform the platform that your app is minimally usable. This method is called automatically by `Lifecycle.ready()`

Result:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### signIn

_This is an private RPC method._

Log a sign in event, called by Discovery.signIn().

Result:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### signOut

_This is an private RPC method._

Log a sign out event, called by Discovery.signOut().

Result:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### startContent

Inform the platform that your user has started content.

```typescript
function startContent(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                        |
| ---------- | -------- | -------- | ---------------------------------- |
| `entityId` | `string` | false    | Optional entity ID of the content. |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

---

### stopContent

Inform the platform that your user has stopped content.

```typescript
function stopContent(entityId: string): Promise<boolean>
```

Parameters:

| Param      | Type     | Required | Description                        |
| ---------- | -------- | -------- | ---------------------------------- |
| `entityId` | `string` | false    | Optional entity ID of the content. |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:metrics:general |

#### Examples

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

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### EventObject

```typescript
type EventObject = {}
```

See also:

EventObjectPrimitives
EventObject

---
