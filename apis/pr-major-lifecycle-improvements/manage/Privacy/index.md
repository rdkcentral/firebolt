---
title: Privacy

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# Privacy Module

---

Version Privacy 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
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

### allowACRCollection

Whether the user allows their automatic content recognition data to be collected

To get the value of `allowACRCollection` call the method like this:

```typescript
function allowACRCollection(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowACRCollection(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowAppContentAdTargeting

Whether the user allows ads to be targeted to the user while watching content in apps

To get the value of `allowAppContentAdTargeting` call the method like this:

```typescript
function allowAppContentAdTargeting(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowAppContentAdTargeting(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowCameraAnalytics

Whether the user allows data from their camera to be used for Product Analytics

To get the value of `allowCameraAnalytics` call the method like this:

```typescript
function allowCameraAnalytics(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowCameraAnalytics(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowPersonalization

Whether the user allows their usage data to be used for personalization and recommendations

To get the value of `allowPersonalization` call the method like this:

```typescript
function allowPersonalization(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowPersonalization(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowPrimaryBrowseAdTargeting

Whether the user allows ads to be targeted to the user while browsing in the primary experience

To get the value of `allowPrimaryBrowseAdTargeting` call the method like this:

```typescript
function allowPrimaryBrowseAdTargeting(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowPrimaryBrowseAdTargeting(
  callback: (value) => null,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowPrimaryContentAdTargeting

Whether the user allows ads to be targeted to the user while watching content in the primary experience

To get the value of `allowPrimaryContentAdTargeting` call the method like this:

```typescript
function allowPrimaryContentAdTargeting(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowPrimaryContentAdTargeting(
  callback: (value) => null,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowProductAnalytics

Whether the user allows their usage data can be used for analytics about the product

To get the value of `allowProductAnalytics` call the method like this:

```typescript
function allowProductAnalytics(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowProductAnalytics(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowRemoteDiagnostics

Whether the user allows their personal data to be included in diagnostic telemetry. This also allows whether device logs can be remotely accessed from the client device

To get the value of `allowRemoteDiagnostics` call the method like this:

```typescript
function allowRemoteDiagnostics(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowRemoteDiagnostics(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowResumePoints

Whether the user allows resume points for content to show in the main experience

To get the value of `allowResumePoints` call the method like this:

```typescript
function allowResumePoints(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowResumePoints(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowUnentitledPersonalization

Whether the user allows their usage data to be used for personalization and recommendations for unentitled content

To get the value of `allowUnentitledPersonalization` call the method like this:

```typescript
function allowUnentitledPersonalization(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowUnentitledPersonalization(
  callback: (value) => null,
): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowUnentitledResumePoints

Whether the user allows resume points for content from unentitled providers to show in the main experience

To get the value of `allowUnentitledResumePoints` call the method like this:

```typescript
function allowUnentitledResumePoints(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowUnentitledResumePoints(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### allowWatchHistory

Whether the user allows their watch history from all sources to show in the main experience

To get the value of `allowWatchHistory` call the method like this:

```typescript
function allowWatchHistory(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

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

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function allowWatchHistory(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### settings

Gets the allowed value for all privacy settings

```typescript
function settings(): Promise<PrivacySettings>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

## Events

### allowACRCollectionChanged

```typescript
function listen('allowACRCollectionChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowAppContentAdTargetingChanged

```typescript
function listen('allowAppContentAdTargetingChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowCameraAnalyticsChanged

```typescript
function listen('allowCameraAnalyticsChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowPersonalizationChanged

```typescript
function listen('allowPersonalizationChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowPrimaryBrowseAdTargetingChanged

```typescript
function listen('allowPrimaryBrowseAdTargetingChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowPrimaryContentAdTargetingChanged

```typescript
function listen('allowPrimaryContentAdTargetingChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowProductAnalyticsChanged

```typescript
function listen('allowProductAnalyticsChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowRemoteDiagnosticsChanged

```typescript
function listen('allowRemoteDiagnosticsChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowResumePointsChanged

```typescript
function listen('allowResumePointsChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowUnentitledPersonalizationChanged

```typescript
function listen('allowUnentitledPersonalizationChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowUnentitledResumePointsChanged

```typescript
function listen('allowUnentitledResumePointsChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

### allowWatchHistoryChanged

```typescript
function listen('allowWatchHistoryChanged', (boolean) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:privacy:settings |

#### Examples

---

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
