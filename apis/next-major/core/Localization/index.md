---
title: Localization

version: next-major
layout: default
sdk: core
---

# Localization Module

---

Version Localization 1.8.0-next-major.3

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [additionalInfo](#additionalinfo)
  - [countryCode](#countrycode)
  - [language](#language)
  - [latlon](#latlon)
  - [listen](#listen)
  - [locale](#locale)
  - [locality](#locality)
  - [once](#once)
  - [postalCode](#postalcode)
  - [preferredAudioLanguages](#preferredaudiolanguages)
- [Events](#events)
  - [onCountryCodeChanged](#oncountrycodechanged)
  - [onLanguageChanged](#onlanguagechanged)
  - [onLocaleChanged](#onlocalechanged)
  - [onLocalityChanged](#onlocalitychanged)
  - [onPostalCodeChanged](#onpostalcodechanged)
  - [onPreferredAudioLanguagesChanged](#onpreferredaudiolanguageschanged)
- [Private Events](#private-events)
- [Types](#types)
  - [LatLon](#latlon-1)

## Usage

To use the Localization module, you can import it into your project from the Firebolt SDK:

```javascript
import { Localization } from '@firebolt-js/sdk'
```

## Overview

Methods for accessessing location and language preferences

## Methods

### additionalInfo

Get any platform-specific localization information

```typescript
function additionalInfo(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:additional-info |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let info = await Localization.additionalInfo()
console.log(info)
```

Value of `info`:

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
  "method": "Localization.additionalInfo",
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

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let code = await Localization.countryCode()
console.log(code)
```

Value of `code`:

```javascript
'US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.countryCode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "US"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let code = await Localization.countryCode()
console.log(code)
```

Value of `code`:

```javascript
'US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.countryCode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "UK"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function countryCode(callback: (code) => string): Promise<number>
```

| Param  | Type     | Required | Description                                      |
| ------ | -------- | -------- | ------------------------------------------------ |
| `code` | `string` | false    | the device country code <br/>pattern: ^[A-Z]{2}$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await countryCode((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onCountryCodeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await countryCode((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onCountryCodeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

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

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let lang = await Localization.language()
console.log(lang)
```

Value of `lang`:

```javascript
'en'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.language",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "en"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let lang = await Localization.language()
console.log(lang)
```

Value of `lang`:

```javascript
'en'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.language",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "es"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locale(callback: (lang) => string): Promise<number>
```

| Param  | Type     | Required | Description                                     |
| ------ | -------- | -------- | ----------------------------------------------- |
| `lang` | `string` | false    | the device language <br/>pattern: ^[A-Za-z]{2}$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locale((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'en'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLanguageChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locale((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'en'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLanguageChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### latlon

Get the approximate latitude and longitude coordinates of the device location

```typescript
function latlon(): Promise<
  [
    number, // undefined  item
    number, // undefined  item
  ]
>
```

Promise resolution:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:location |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let latlong = await Localization.latlon()
console.log(latlong)
```

Value of `latlong`:

```javascript
;[39.9549, 75.1699]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.latlon",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [39.9549, 75.1699]
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

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let locale = await Localization.locale()
console.log(locale)
```

Value of `locale`:

```javascript
'en-US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.locale",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "en-US"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let locale = await Localization.locale()
console.log(locale)
```

Value of `locale`:

```javascript
'en-US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.locale",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "es-US"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locale(callback: (locale) => string): Promise<number>
```

| Param    | Type     | Required | Description                                                  |
| -------- | -------- | -------- | ------------------------------------------------------------ |
| `locale` | `string` | false    | the device locale <br/>pattern: ^[a-zA-Z]+([a-zA-Z0-9\-]\*)$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locale((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'en-US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLocaleChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locale((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'en-US'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLocaleChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

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

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let locality = await Localization.locality()
console.log(locality)
```

Value of `locality`:

```javascript
'Philadelphia'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.locality",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Philadelphia"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let locality = await Localization.locality()
console.log(locality)
```

Value of `locality`:

```javascript
'Philadelphia'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.locality",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Rockville"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function locality(callback: (locality) => string): Promise<number>
```

| Param      | Type     | Required | Description     |
| ---------- | -------- | -------- | --------------- |
| `locality` | `string` | false    | the device city |

Promise resolution:

```
number
```

#### Examples

Default example #1

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locality((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'Philadelphia'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLocalityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await locality((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'Philadelphia'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onLocalityChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

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

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let postalCode = await Localization.postalCode()
console.log(postalCode)
```

Value of `postalCode`:

```javascript
'19103'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.postalCode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "19103"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let postalCode = await Localization.postalCode()
console.log(postalCode)
```

Value of `postalCode`:

```javascript
'19103'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.postalCode",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "20850"
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function postalCode(callback: (postalCode) => string): Promise<number>
```

| Param        | Type     | Required | Description            |
| ------------ | -------- | -------- | ---------------------- |
| `postalCode` | `string` | false    | the device postal code |

Promise resolution:

```
number
```

#### Examples

Default example #1

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await postalCode((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'19103'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onPostalCodeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await postalCode((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
'19103'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onPostalCodeChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

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

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let languages = await Localization.preferredAudioLanguages()
console.log(languages)
```

Value of `languages`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.preferredAudioLanguages",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["spa", "eng"]
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let languages = await Localization.preferredAudioLanguages()
console.log(languages)
```

Value of `languages`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.preferredAudioLanguages",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": ["eng", "spa"]
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function preferredAudioLanguages(
  callback: (languages) => string[],
): Promise<number>
```

| Param       | Type       | Required | Description                                            |
| ----------- | ---------- | -------- | ------------------------------------------------------ |
| `languages` | `string[]` | false    | the preferred audio languages <br/>pattern: ^[a-z]{3}$ |

Promise resolution:

```
number
```

#### Examples

Default Example

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await preferredAudioLanguages((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onPreferredAudioLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Default Example #2

```typescript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await preferredAudioLanguages((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
;['spa', 'eng']
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onPreferredAudioLanguagesChanged",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

## Events

### onCountryCodeChanged

See: [countryCode](#countrycode)

### onLanguageChanged

See: [locale](#locale)

### onLocaleChanged

See: [locale](#locale)

### onLocalityChanged

See: [locality](#locality)

### onPostalCodeChanged

See: [postalCode](#postalcode)

### onPreferredAudioLanguagesChanged

See: [preferredAudioLanguages](#preferredaudiolanguages)

## Private Events

### onCountryCodeChanged

See: [countryCode](#countrycode)

### onLanguageChanged

See: [locale](#locale)

### onLocaleChanged

See: [locale](#locale)

### onLocalityChanged

See: [locality](#locality)

### onPostalCodeChanged

See: [postalCode](#postalcode)

### onPreferredAudioLanguagesChanged

See: [preferredAudioLanguages](#preferredaudiolanguages)

## Types

### LatLon

```typescript
type LatLon = [
  number, // undefined  item
  number, // undefined  item
]
```

---
