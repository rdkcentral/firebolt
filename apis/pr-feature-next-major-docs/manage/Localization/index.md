---
title: Localization

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Localization Module

---

Version Localization 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [addAdditionalInfo](#addadditionalinfo)
  - [additionalInfo](#additionalinfo)
  - [countryCode](#countrycode)
  - [language](#language)
  - [listen](#listen)
  - [locale](#locale)
  - [locality](#locality)
  - [once](#once)
  - [postalCode](#postalcode)
  - [preferredAudioLanguages](#preferredaudiolanguages)
  - [removeAdditionalInfo](#removeadditionalinfo)
  - [timeZone](#timezone)
- [Events](#events)
  - [countryCodeChanged](#countrycodechanged)
  - [languageChanged](#languagechanged)
  - [localeChanged](#localechanged)
  - [localityChanged](#localitychanged)
  - [postalCodeChanged](#postalcodechanged)
  - [preferredAudioLanguagesChanged](#preferredaudiolanguageschanged)
  - [timeZoneChanged](#timezonechanged)

## Usage

To use the Localization module, you can import it into your project from the Firebolt SDK:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'
```

## Overview

Methods for accessessing location and language preferences

## Methods

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

```typescript
void
```

Capabilities:

| Role    | Capability                                           |
| ------- | ---------------------------------------------------- |
| manages | xrn:firebolt:capability:localization:additional-info |

#### Examples

Add an additionalInfo for localization

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.addAdditionalInfo('defaultKey', 'defaultValue=')
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
  "method": "Localization.addAdditionalInfo",
  "params": {
    "key": "defaultKey",
    "value": "defaultValue="
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

### additionalInfo

Get any platform-specific localization information, in an Map<string, string>

```typescript
function additionalInfo(): Promise<object>
```

Promise resolution:

```typescript
object
```

Capabilities:

| Role | Capability                                           |
| ---- | ---------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:additional-info |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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

```typescript
type CountryCode = string
```

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:country-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `countryCode` call the method like this:

```typescript
function countryCode(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description                                      |
| ------- | -------- | -------- | ------------------------------------------------ |
| `value` | `string` | true     | the device country code <br/>pattern: ^[A-Z]{2}$ |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.countryCode('US')
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
  "method": "Localization.setCountryCode",
  "params": {
    "value": "US"
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
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.countryCode('UK')
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
  "method": "Localization.setCountryCode",
  "params": {
    "value": "UK"
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
function countryCode(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await countryCode((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onCountryCodeChanged",
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
  "result": "US"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await countryCode((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onCountryCodeChanged",
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
  "result": "UK"
}
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

```typescript
type Language = string
```

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `language` call the method like this:

```typescript
function language(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description                                     |
| ------- | -------- | -------- | ----------------------------------------------- |
| `value` | `string` | true     | the device language <br/>pattern: ^[A-Za-z]{2}$ |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.language('en')
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
  "method": "Localization.setLanguage",
  "params": {
    "value": "en"
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
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.language('es')
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
  "method": "Localization.setLanguage",
  "params": {
    "value": "es"
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
function language(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await language((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLanguageChanged",
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
  "result": "en"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await language((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLanguageChanged",
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
  "result": "es"
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

```typescript
type Locale = string
```

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locale |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `locale` call the method like this:

```typescript
function locale(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description                                                  |
| ------- | -------- | -------- | ------------------------------------------------------------ |
| `value` | `string` | true     | the device locale <br/>pattern: ^[a-zA-Z]+([a-zA-Z0-9\-]\*)$ |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.locale('en-US')
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
  "method": "Localization.setLocale",
  "params": {
    "value": "en-US"
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
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.locale('es-US')
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
  "method": "Localization.setLocale",
  "params": {
    "value": "es-US"
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
function locale(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await locale((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLocaleChanged",
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
  "result": "en-US"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await locale((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLocaleChanged",
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
  "result": "es-US"
}
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

```typescript
type Locality = string
```

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locality |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `locality` call the method like this:

```typescript
function locality(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description     |
| ------- | -------- | -------- | --------------- |
| `value` | `string` | true     | the device city |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.locality('Philadelphia')
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
  "method": "Localization.setLocality",
  "params": {
    "value": "Philadelphia"
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
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.locality('Rockville')
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
  "method": "Localization.setLocality",
  "params": {
    "value": "Rockville"
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
function locality(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await locality((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLocalityChanged",
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
  "result": "Philadelphia"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await locality((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onLocalityChanged",
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
  "result": "Rockville"
}
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

```typescript
string
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:localization:postal-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `postalCode` call the method like this:

```typescript
function postalCode(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description            |
| ------- | -------- | -------- | ---------------------- |
| `value` | `string` | true     | the device postal code |

Promise resolution:

```typescript
null
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.postalCode('19103')
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
  "method": "Localization.setPostalCode",
  "params": {
    "value": "19103"
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
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.postalCode('20850')
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
  "method": "Localization.setPostalCode",
  "params": {
    "value": "20850"
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
function postalCode(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await postalCode((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onPostalCodeChanged",
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
  "result": "19103"
}
```

</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await postalCode((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onPostalCodeChanged",
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
  "result": "20850"
}
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

```typescript
string[]
```

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

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
import { Localization } from '@firebolt-js/manage-sdk'

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

To set the value of `preferredAudioLanguages` call the method like this:

```typescript
function preferredAudioLanguages(value: string[]): Promise<void>
```

Parameters:

| Param   | Type       | Required | Description                                            |
| ------- | ---------- | -------- | ------------------------------------------------------ |
| `value` | `string[]` | true     | the preferred audio languages <br/>pattern: ^[a-z]{3}$ |

Promise resolution:

```typescript
null
```

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.preferredAudioLanguages(['spa', 'eng'])
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
  "method": "Localization.setPreferredAudioLanguages",
  "params": {
    "value": ["spa", "eng"]
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

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.preferredAudioLanguages(['eng', 'spa'])
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
  "method": "Localization.setPreferredAudioLanguages",
  "params": {
    "value": ["eng", "spa"]
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
function preferredAudioLanguages(callback: (value) => string[]): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await preferredAudioLanguages((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onPreferredAudioLanguagesChanged",
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
  "result": ["spa", "eng"]
}
```

</details>

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await preferredAudioLanguages((value) => {
  console.log(value)
})
console.log(listenerId)
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
  "method": "Localization.onPreferredAudioLanguagesChanged",
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
  "result": ["eng", "spa"]
}
```

</details>

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

```typescript
void
```

Capabilities:

| Role    | Capability                                           |
| ------- | ---------------------------------------------------- |
| manages | xrn:firebolt:capability:localization:additional-info |

#### Examples

Remove an additionalInfo for localization

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.removeAdditionalInfo('defaultKey')
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
  "method": "Localization.removeAdditionalInfo",
  "params": {
    "key": "defaultKey"
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

### timeZone

Set the IANA timezone for the device

To get the value of `timeZone` call the method like this:

```typescript
function timeZone(): Promise<string>
```

Promise resolution:

```typescript
type TimeZone = string
```

Capabilities:

| Role | Capability                                     |
| ---- | ---------------------------------------------- |
| uses | xrn:firebolt:capability:localization:time-zone |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.timeZone()
console.log(result)
```

Value of `result`:

```javascript
'America/New_York'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.timeZone",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "America/New_York"
}
```

</details>

Additional Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.timeZone()
console.log(result)
```

Value of `result`:

```javascript
'America/New_York'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.timeZone",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "America/Los_Angeles"
}
```

</details>

---

To set the value of `timeZone` call the method like this:

```typescript
function timeZone(value: string): Promise<void>
```

Parameters:

| Param   | Type     | Required | Description                         |
| ------- | -------- | -------- | ----------------------------------- |
| `value` | `string` | true     | <br/>pattern: ^[-+_/ A-Za-z 0-9]\*$ |

Promise resolution:

```typescript
null
```

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.timeZone('America/New_York')
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
  "method": "Localization.setTimeZone",
  "params": {
    "value": "America/New_York"
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

Additional Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let result = await Localization.timeZone('America/Los_Angeles')
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
  "method": "Localization.setTimeZone",
  "params": {
    "value": "America/Los_Angeles"
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
function timeZone(callback: (value) => string): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await timeZone((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `result`:

```javascript
'America/New_York'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onTimeZoneChanged",
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
  "result": "America/New_York"
}
```

</details>

Additional Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/manage-sdk'

let listenerId = await timeZone((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `result`:

```javascript
'America/New_York'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Localization.onTimeZoneChanged",
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
  "result": "America/Los_Angeles"
}
```

</details>

---

## Events

### countryCodeChanged

See: [countryCode](#countrycode)

### languageChanged

See: [language](#language)

### localeChanged

See: [locale](#locale)

### localityChanged

See: [locality](#locality)

### postalCodeChanged

See: [postalCode](#postalcode)

### preferredAudioLanguagesChanged

See: [preferredAudioLanguages](#preferredaudiolanguages)

### timeZoneChanged

See: [timeZone](#timezone)
