---
title: Advertising

version: next-major
layout: default
sdk: core
---

# Advertising Module

---

Version Advertising 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [advertisingId](#advertisingid)
  - [appBundleId](#appbundleid)
  - [config](#config)
  - [deviceAttributes](#deviceattributes)
  - [policy](#policy)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [policyChanged](#policychanged)
- [Types](#types)
  - [AdPolicy](#adpolicy)
  - [AdConfigurationOptions](#adconfigurationoptions)
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
function advertisingId(options: AdvertisingIdOptions): Promise<object>
```

Parameters:

| Param     | Type                   | Required | Description           |
| --------- | ---------------------- | -------- | --------------------- |
| `options` | `AdvertisingIdOptions` | false    | AdvertisingId options |

Promise resolution:

Capabilities:

| Role | Capability                                     |
| ---- | ---------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:identifier |

#### Examples

---

### appBundleId

Get the App's Bundle ID

```typescript
function appBundleId(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

---

### config

Build configuration object for Ad Framework initialization

```typescript
function config(options: AdConfigurationOptions): Promise<object>
```

Parameters:

| Param     | Type                     | Required | Description           |
| --------- | ------------------------ | -------- | --------------------- |
| `options` | `AdConfigurationOptions` | true     | Configuration options |

Promise resolution:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

---

### deviceAttributes

Get the device advertising device attributes

```typescript
function deviceAttributes(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:advertising:configuration |

#### Examples

---

### policy

Get the advertising privacy and playback policy

To get the value of `policy` call the method like this:

```typescript
function policy(): Promise<AdPolicy>
```

Promise resolution:

Capabilities:

| Role | Capability                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------- |
| uses | xrn:firebolt:capability:privacy:advertising<br/>xrn:firebolt:capability:advertising:configuration |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function policy(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

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

## Events

### policyChanged

```typescript
function listen('policyChanged', (AdPolicy) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                                                                        |
| ---- | ------------------------------------------------------------------------------------------------- |
| uses | xrn:firebolt:capability:privacy:advertising<br/>xrn:firebolt:capability:advertising:configuration |

#### Examples

---

## Types

### AdPolicy

Describes various ad playback enforcement rules that the app should follow.

```typescript
type AdPolicy = {
  skipRestriction?: SkipRestriction // The advertisement skip restriction.
  limitAdTracking?: boolean
}
```

See also:

SkipRestriction

---

### AdConfigurationOptions

```typescript
type AdConfigurationOptions = {
  coppa?: boolean // Whether or not the app requires US COPPA compliance.
  environment?: 'prod' | 'test' // Whether the app is running in a production or test mode.
  authenticationEntity?: string // The authentication provider, when it is separate entity than the app provider, e.g. an MVPD.
}
```

---

### AdvertisingIdOptions

```typescript
type AdvertisingIdOptions = {
  scope?: object // Provides the options to send scope type and id to select desired advertising id
}
```

---
