---
title: Localization

version: pr-major-lifecycle-improvements
layout: default
sdk: manage
---

# Localization Module

---

Version Localization 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [addAdditionalInfo](#addadditionalinfo)
  - [additionalInfo](#additionalinfo)
  - [countryCode](#countrycode)
  - [language](#language)
  - [locale](#locale)
  - [locality](#locality)
  - [postalCode](#postalcode)
  - [preferredAudioLanguages](#preferredaudiolanguages)
  - [removeAdditionalInfo](#removeadditionalinfo)
  - [timeZone](#timezone)
  - [once](#once)
- [Events](#events)
  - [countryCodeChanged](#countrycodechanged)
  - [languageChanged](#languagechanged)
  - [localeChanged](#localechanged)
  - [localityChanged](#localitychanged)
  - [postalCodeChanged](#postalcodechanged)
  - [preferredAudioLanguagesChanged](#preferredaudiolanguageschanged)
  - [timeZoneChanged](#timezonechanged)
- [Types](#types)

## Usage

To use the Localization module, you can import it into your project from the Firebolt SDK:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for accessessing location and language preferences

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Localization.clear(id)` |

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Localization.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### addAdditionalInfo

Add any platform-specific localization information in key/value pair

```typescript
function addAdditionalInfo(key: string, value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description                        |
| ------- | -------- | -------- | ---------------------------------- |
| `key`   | `string` | true     | Key to add additionalInfo          |
| `value` | `string` | true     | Value to be set for additionalInfo |

Promise resolution:

Capabilities:

| Role    | Capability                                           |
| ------- | ---------------------------------------------------- |
| manages | xrn:firebolt:capability:localization:additional-info |

#### Examples

---

### additionalInfo

Get any platform-specific localization information, in an Map<string, string>

```typescript
function additionalInfo(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:additional-info |

#### Examples

---

### countryCode

Get the ISO 3166-1 alpha-2 code for the country device is located in

To get the value of `countryCode` call the method like this:

```typescript
function countryCode(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:country-code |

#### Examples

---

To set the value of `countryCode` call the method like this:

```typescript
function countryCode(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description             |
| ------- | -------- | -------- | ----------------------- |
| `value` | `string` | true     | the device country code |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function countryCode(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### language

Get the ISO 639 1/2 code for the preferred language

To get the value of `language` call the method like this:

```typescript
function language(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

---

To set the value of `language` call the method like this:

```typescript
function language(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description         |
| ------- | -------- | -------- | ------------------- |
| `value` | `string` | true     | the device language |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locale(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### locale

Get the _full_ BCP 47 code, including script, region, variant, etc., for the preferred langauage/locale

To get the value of `locale` call the method like this:

```typescript
function locale(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locale |

#### Examples

---

To set the value of `locale` call the method like this:

```typescript
function locale(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description       |
| ------- | -------- | -------- | ----------------- |
| `value` | `string` | true     | the device locale |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locale(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### locality

Get the locality/city the device is located in

To get the value of `locality` call the method like this:

```typescript
function locality(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locality |

#### Examples

---

To set the value of `locality` call the method like this:

```typescript
function locality(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description     |
| ------- | -------- | -------- | --------------- |
| `value` | `string` | true     | the device city |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locality(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### postalCode

Get the postal code the device is located in

To get the value of `postalCode` call the method like this:

```typescript
function postalCode(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:localization:postal-code |

#### Examples

---

To set the value of `postalCode` call the method like this:

```typescript
function postalCode(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description            |
| ------- | -------- | -------- | ---------------------- |
| `value` | `string` | true     | the device postal code |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function postalCode(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### preferredAudioLanguages

A prioritized list of ISO 639 1/2 codes for the preferred audio languages on this device.

To get the value of `preferredAudioLanguages` call the method like this:

```typescript
function preferredAudioLanguages(): Promise<string[]>
```

Promise resolution:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

---

To set the value of `preferredAudioLanguages` call the method like this:

```typescript
function preferredAudioLanguages(value: string[]): Promise<void>
```

Parameters:

| Param   | Type       | Required | Description                   |
| ------- | ---------- | -------- | ----------------------------- |
| `value` | `string[]` | true     | the preferred audio languages |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function preferredAudioLanguages(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### removeAdditionalInfo

Remove any platform-specific localization information from map

```typescript
function removeAdditionalInfo(key: string): Promise<void>
```

Parameters:

| Param | Type     | Required | Description                  |
| ----- | -------- | -------- | ---------------------------- |
| `key` | `string` | true     | Key to remove additionalInfo |

Promise resolution:

Capabilities:

| Role    | Capability                                           |
| ------- | ---------------------------------------------------- |
| manages | xrn:firebolt:capability:localization:additional-info |

#### Examples

---

### timeZone

Set the IANA timezone for the device

To get the value of `timeZone` call the method like this:

```typescript
function timeZone(): Promise<string>
```

Promise resolution:

Capabilities:

| Role | Capability                                     |
| ---- | ---------------------------------------------- |
| uses | xrn:firebolt:capability:localization:time-zone |

#### Examples

---

To set the value of `timeZone` call the method like this:

```typescript
function timeZone(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `value` | `string` | true     |             |

Promise resolution:

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function timeZone(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Localization.clear(id)` |

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

| Type     | Description                                                                                          |
| -------- | ---------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Localization.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### countryCodeChanged

```typescript
function listen('countryCodeChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:country-code |

#### Examples

---

### languageChanged

```typescript
function listen('languageChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

---

### localeChanged

```typescript
function listen('localeChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locale |

#### Examples

---

### localityChanged

```typescript
function listen('localityChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locality |

#### Examples

---

### postalCodeChanged

```typescript
function listen('postalCodeChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:localization:postal-code |

#### Examples

---

### preferredAudioLanguagesChanged

```typescript
function listen('preferredAudioLanguagesChanged', (string[]) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

---

### timeZoneChanged

```typescript
function listen('timeZoneChanged', (string) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                     |
| ---- | ---------------------------------------------- |
| uses | xrn:firebolt:capability:localization:time-zone |

#### Examples

---

## Types
