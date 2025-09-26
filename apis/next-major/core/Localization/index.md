---
title: Localization

version: next-major
layout: default
sdk: core
---

# Localization Module

---

Version Localization 1.8.0-next-major.2

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
  - [countryCodeChanged](#countrycodechanged)
  - [languageChanged](#languagechanged)
  - [localeChanged](#localechanged)
  - [localityChanged](#localitychanged)
  - [postalCodeChanged](#postalcodechanged)
  - [preferredAudioLanguagesChanged](#preferredaudiolanguageschanged)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  - [languageChanged](#languagechanged-1)
  - [localeChanged](#localechanged-1)
  - [localityChanged](#localitychanged-1)
  - [postalCodeChanged](#postalcodechanged-1)
  - [preferredAudioLanguagesChanged](#preferredaudiolanguageschanged-1)
  </details>
- [Types](#types)
  - [NetworkType](#networktype)
  - [NetworkState](#networkstate)
  - [EDIDVersion](#edidversion)
  - [WifiSecurityMode](#wifisecuritymode)
  - [AudioProfile](#audioprofile)
  - [SkipRestriction](#skiprestriction)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [OfferingType](#offeringtype)
  - [MusicType](#musictype)
  - [ProgramType](#programtype)
  - [WifiFrequency](#wififrequency)
  - [SemanticVersion](#semanticversion)
  - [Availability](#availability)
  - [SpeechRate](#speechrate)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [FontFamily](#fontfamily)
  - [FontSize](#fontsize)
  - [Color](#color)
  - [FontEdge](#fontedge)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ISO639_2Language](#isolanguage)
  - [Locality](#locality-1)
  - [CountryCode](#countrycode-1)
  - [Language](#language-1)
  - [Locale](#locale-1)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [Capability](#capability)
  - [LatLon](#latlon-1)
  - [CapPermissionStatus](#cappermissionstatus)
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [EntityDetails](#entitydetails)
  - [Entity](#entity)
  - [Metadata](#metadata)
  - [ProgramEntity](#programentity)
  - [MusicEntity](#musicentity)
  - [ChannelEntity](#channelentity)
  - [UntypedEntity](#untypedentity)
  - [PlaylistEntity](#playlistentity)
  - [MovieEntity](#movieentity)
  - [TVEpisodeEntity](#tvepisodeentity)
  - [TVSeasonEntity](#tvseasonentity)
  - [TVSeriesEntity](#tvseriesentity)
  - [AdditionalEntity](#additionalentity)
  - [PlayableEntity](#playableentity)
  - [WayToWatch](#waytowatch)
  - [EventObject](#eventobject)
  - [ContentIdentifiers](#contentidentifiers)
  - [ContentRating](#contentrating)
- [United States](#united-states)
- [Canada](#canada)
  - [HDMIPortId](#hdmiportid)
  - [WifiSignalStrength](#wifisignalstrength)
  - [Entitlement](#entitlement)
  - [EntityInfo](#entityinfo)
  - [AgePolicy](#agepolicy)
  - [NavigationIntent](#navigationintent)
  - [HomeIntent](#homeintent)
  - [LaunchIntent](#launchintent)
  - [EntityIntent](#entityintent)
  - [PlaybackIntent](#playbackintent)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [TuneIntent](#tuneintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlayQueryIntent](#playqueryintent)
  - [Intent](#intent)
  - [IntentProperties](#intentproperties)
  - [SecondScreenEvent](#secondscreenevent)
  - [LifecycleState](#lifecyclestate)

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
function countryCode(callback: (value) => string): Promise<number>
```

Parameters:

| Param  | Type     | Required | Description                                      |
| ------ | -------- | -------- | ------------------------------------------------ |
| `code` | `string` | false    | the device country code <br/>pattern: ^[A-Z]{2}$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### language
Get the ISO 639 1/2 code for the preferred language

To get the value of `language` call the method like this:

```typescript
function language(): Promise<string>
````

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
function locale(callback: (value) => string): Promise<number>
```

Parameters:

| Param  | Type     | Required | Description                                     |
| ------ | -------- | -------- | ----------------------------------------------- |
| `lang` | `string` | false    | the device language <br/>pattern: ^[A-Za-z]{2}$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('languageChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('languageChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### latlon


Get the approximate latitude and longitude coordinates of the device location

```typescript
function latlon(): Promise<[
    number, // undefined  item
    number // undefined  item
]>
````

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
function locale(callback: (value) => string): Promise<number>
```

Parameters:

| Param    | Type     | Required | Description                                                  |
| -------- | -------- | -------- | ------------------------------------------------------------ |
| `locale` | `string` | false    | the device locale <br/>pattern: ^[a-zA-Z]+([a-zA-Z0-9\-]\*)$ |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### locality
Get the locality/city the device is located in

To get the value of `locality` call the method like this:

```typescript
function locality(): Promise<string>
````

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
function locality(callback: (value) => string): Promise<number>
```

Parameters:

| Param      | Type     | Required | Description     |
| ---------- | -------- | -------- | --------------- |
| `locality` | `string` | false    | the device city |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
````

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
function postalCode(callback: (value) => string): Promise<number>
```

Parameters:

| Param        | Type     | Required | Description            |
| ------------ | -------- | -------- | ---------------------- |
| `postalCode` | `string` | false    | the device postal code |

Promise resolution:

```
number
```

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


### preferredAudioLanguages
A prioritized list of ISO 639 1/2 codes for the preferred audio languages on this device.

To get the value of `preferredAudioLanguages` call the method like this:

```typescript
function preferredAudioLanguages(): Promise<string[]>
````

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
function preferredAudioLanguages(callback: (value) => string[]): Promise<number>
```

Parameters:

| Param       | Type       | Required | Description                                            |
| ----------- | ---------- | -------- | ------------------------------------------------------ |
| `languages` | `string[]` | false    | the preferred audio languages <br/>pattern: ^[a-z]{3}$ |

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen(
  'preferredAudioLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('preferredAudioLanguagesChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---



## Events

### countryCodeChanged





```typescript
function listen('countryCodeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description                                      |
| ------ | -------- | -------- | ------------------------------------------------ |
| `code` | `string` | false    | the device country code <br/>pattern: ^[A-Z]{2}$ |

Event value:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:country-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### languageChanged


[Deprecated] This method is deprecated as of since version 0.17.0. Please use `locale` as a replacement.



---

### localeChanged





```typescript
function listen('localeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type     | Required | Description                                                  |
| -------- | -------- | -------- | ------------------------------------------------------------ |
| `locale` | `string` | false    | the device locale <br/>pattern: ^[a-zA-Z]+([a-zA-Z0-9\-]\*)$ |

Event value:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locale |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### localityChanged





```typescript
function listen('localityChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param      | Type     | Required | Description     |
| ---------- | -------- | -------- | --------------- |
| `locality` | `string` | false    | the device city |

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locality |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### postalCodeChanged





```typescript
function listen('postalCodeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type     | Required | Description            |
| ------------ | -------- | -------- | ---------------------- |
| `postalCode` | `string` | false    | the device postal code |

Event value:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:localization:postal-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### preferredAudioLanguagesChanged





```typescript
function listen('preferredAudioLanguagesChanged', (string[]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type       | Required | Description                                            |
| ----------- | ---------- | -------- | ------------------------------------------------------ |
| `languages` | `string[]` | false    | the preferred audio languages <br/>pattern: ^[a-z]{3}$ |

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen(
  'preferredAudioLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('preferredAudioLanguagesChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---


## Private Events
<details markdown="1"  id="private-events-details">
  <summary>View</summary>

  ### countryCodeChanged





```typescript
function listen('countryCodeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param  | Type     | Required | Description                                      |
| ------ | -------- | -------- | ------------------------------------------------ |
| `code` | `string` | false    | the device country code <br/>pattern: ^[A-Z]{2}$ |

Event value:

Capabilities:

| Role | Capability                                        |
| ---- | ------------------------------------------------- |
| uses | xrn:firebolt:capability:localization:country-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('countryCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### languageChanged


[Deprecated] This method is deprecated as of since version 0.17.0. Please use `locale` as a replacement.



---

### localeChanged





```typescript
function listen('localeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type     | Required | Description                                                  |
| -------- | -------- | -------- | ------------------------------------------------------------ |
| `locale` | `string` | false    | the device locale <br/>pattern: ^[a-zA-Z]+([a-zA-Z0-9\-]\*)$ |

Event value:

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locale |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### localityChanged





```typescript
function listen('localityChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param      | Type     | Required | Description     |
| ---------- | -------- | -------- | --------------- |
| `locality` | `string` | false    | the device city |

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:locality |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('localityChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### postalCodeChanged





```typescript
function listen('postalCodeChanged', (string) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param        | Type     | Required | Description            |
| ------------ | -------- | -------- | ---------------------- |
| `postalCode` | `string` | false    | the device postal code |

Event value:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:localization:postal-code |

#### Examples

Default example #1

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', (result) => {
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('postalCodeChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

### preferredAudioLanguagesChanged





```typescript
function listen('preferredAudioLanguagesChanged', (string[]) => void): Promise<number>
````

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param       | Type       | Required | Description                                            |
| ----------- | ---------- | -------- | ------------------------------------------------------ |
| `languages` | `string[]` | false    | the preferred audio languages <br/>pattern: ^[a-z]{3}$ |

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:localization:language |

#### Examples

Default Example

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen(
  'preferredAudioLanguagesChanged',
  (result) => {
    console.log(result)
  },
)
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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>

Default Example #2

JavaScript:

```javascript
import { Localization } from '@firebolt-js/sdk'

let listenerId = await Localization.listen('preferredAudioLanguagesChanged', result => {
  console.log(result)
})
````

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

````json
{"jsonrpc":"2.0","id":1,"result":null}
```</details>


---

</details>


## Types

### NetworkType

The type of network that is currently active

```typescript
NetworkType: {
    WIFI: 'wifi',
    ETHERNET: 'ethernet',
    HYBRID: 'hybrid',
},

````

---

### NetworkState

The type of network that is currently active

```typescript
NetworkState: {
    CONNECTED: 'connected',
    DISCONNECTED: 'disconnected',
},

```

---

### EDIDVersion

```typescript
EDIDVersion: {
    V1_4: '1.4',
    V2_0: '2.0',
    UNKNOWN: 'unknown',
},

```

---

### WifiSecurityMode

Security Mode supported for Wifi

```typescript
WifiSecurityMode: {
    NONE: 'none',
    WEP_64: 'wep64',
    WEP_128: 'wep128',
    WPA_PSK_TKIP: 'wpaPskTkip',
    WPA_PSK_AES: 'wpaPskAes',
    WPA_2PSK_TKIP: 'wpa2PskTkip',
    WPA_2PSK_AES: 'wpa2PskAes',
    WPA_ENTERPRISE_TKIP: 'wpaEnterpriseTkip',
    WPA_ENTERPRISE_AES: 'wpaEnterpriseAes',
    WPA_2ENTERPRISE_TKIP: 'wpa2EnterpriseTkip',
    WPA_2ENTERPRISE_AES: 'wpa2EnterpriseAes',
    WPA_2PSK: 'wpa2Psk',
    WPA_2ENTERPRISE: 'wpa2Enterprise',
    WPA_3PSK_AES: 'wpa3PskAes',
    WPA_3SAE: 'wpa3Sae',
},

```

---

### AudioProfile

```typescript
AudioProfile: {
    STEREO: 'stereo',
    DOLBY_DIGITAL_5_1: 'dolbyDigital5.1',
    DOLBY_DIGITAL_5_1_PLUS: 'dolbyDigital5.1+',
    DOLBY_ATMOS: 'dolbyAtmos',
},

```

---

### SkipRestriction

The advertisement skip restriction.

Applies to fast-forward/rewind (e.g. trick mode), seeking over an entire opportunity (e.g. jump), seeking out of what's currently playing, and "Skip this ad..." features. Seeking over multiple ad opportunities only requires playback of the _last_ opportunity, not all opportunities, preceding the seek destination.

| Value        | Description                                                                    |
| ------------ | ------------------------------------------------------------------------------ |
| none         | No fast-forward, jump, or skip restrictions                                    |
| adsUnwatched | Restrict fast-forward, jump, and skip for unwatched ad opportunities only.     |
| adsAll       | Restrict fast-forward, jump, and skip for all ad opportunities                 |
| all          | Restrict fast-forward, jump, and skip for all ad opportunities and all content |

Namespace: `xrn:advertising:policy:skipRestriction:`

```typescript
SkipRestriction: {
    NONE: 'none',
    ADS_UNWATCHED: 'adsUnwatched',
    ADS_ALL: 'adsAll',
    ALL: 'all',
},

```

---

### Role

Role provides access level for the app for a given capability.

```typescript
Role: {
    USE: 'use',
    MANAGE: 'manage',
    PROVIDE: 'provide',
},

```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
DenyReason: {
    UNPERMITTED: 'unpermitted',
    UNSUPPORTED: 'unsupported',
    DISABLED: 'disabled',
    UNAVAILABLE: 'unavailable',
    GRANT_DENIED: 'grantDenied',
    UNGRANTED: 'ungranted',
},

```

---

### OfferingType

The offering type of the WayToWatch.

```typescript
OfferingType: {
    FREE: 'free',
    SUBSCRIBE: 'subscribe',
    BUY: 'buy',
    RENT: 'rent',
},

```

---

### MusicType

In the case of a music `entityType`, specifies the type of music entity.

```typescript
MusicType: {
    SONG: 'song',
    ALBUM: 'album',
},

```

---

### ProgramType

In the case of a program `entityType`, specifies the program type.

```typescript
ProgramType: {
    MOVIE: 'movie',
    EPISODE: 'episode',
    SEASON: 'season',
    SERIES: 'series',
    OTHER: 'other',
    PREVIEW: 'preview',
    EXTRA: 'extra',
    CONCERT: 'concert',
    SPORTING_EVENT: 'sportingEvent',
    ADVERTISEMENT: 'advertisement',
    MUSIC_VIDEO: 'musicVideo',
    MINISODE: 'minisode',
},

```

---

### WifiFrequency

Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.

```typescript
type WifiFrequency = number
```

---

### SemanticVersion

```typescript
type SemanticVersion = {
  major: number
  minor: number
  patch: number
  readable: string
}
```

---

### Availability

```typescript
type Availability = {
  type: 'channel-lineup' | 'program-lineup'
  id: string
  catalogId?: string
  startTime?: string
  endTime?: string
}
```

---

### SpeechRate

```typescript
type SpeechRate = number
```

---

### ClosedCaptionsStyles

The default styles to use when displaying closed-captions

```typescript
type ClosedCaptionsStyles = {
  fontFamily?: string
  fontSize?: number
  fontColor?: string
  fontEdge?: string
  fontEdgeColor?: string
  fontOpacity?: number
  backgroundColor?: string
  backgroundOpacity?: number
  textAlign?: string
  textAlignVertical?: string
  windowColor?: string
  windowOpacity?: number
}
```

---

### FontFamily

```typescript
FontFamily: {
    MONOSPACED_SERIF: 'monospaced_serif',
    PROPORTIONAL_SERIF: 'proportional_serif',
    MONOSPACED_SANSERIF: 'monospaced_sanserif',
    PROPORTIONAL_SANSERIF: 'proportional_sanserif',
    SMALLCAPS: 'smallcaps',
    CURSIVE: 'cursive',
    CASUAL: 'casual',
},

```

---

### FontSize

```typescript
type FontSize = number
```

---

### Color

```typescript
type Color = string
```

---

### FontEdge

```typescript
FontEdge: {
    NONE: 'none',
    RAISED: 'raised',
    DEPRESSED: 'depressed',
    UNIFORM: 'uniform',
    DROP_SHADOW_LEFT: 'drop_shadow_left',
    DROP_SHADOW_RIGHT: 'drop_shadow_right',
},

```

---

### Opacity

```typescript
type Opacity = number
```

---

### HorizontalAlignment

```typescript
type HorizontalAlignment = string
```

---

### VerticalAlignment

```typescript
type VerticalAlignment = string
```

---

### ISO639_2Language

```typescript
type ISO639_2Language = string
```

---

### Locality

```typescript
type Locality = string
```

---

### CountryCode

```typescript
type CountryCode = string
```

---

### Language

```typescript
type Language = string
```

---

### Locale

```typescript
type Locale = string
```

---

### HDMISignalStatus

```typescript
HDMISignalStatus: {
    NONE: 'none',
    STABLE: 'stable',
    UNSTABLE: 'unstable',
    UNSUPPORTED: 'unsupported',
    UNKNOWN: 'unknown',
},

```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

---

### LatLon

```typescript
type LatLon = [
  number, // undefined  item
  number, // undefined  item
]
```

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean
}
```

---

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### EntityDetails

```typescript
type EntityDetails = {
  identifiers:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  info?: Metadata
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entity.Metadata
Entertainment.WayToWatch

---

### Entity

```typescript
type Entity =
  | ProgramEntity
  | MusicEntity
  | ChannelEntity
  | UntypedEntity
  | PlaylistEntity
```

See also:

Entity.ProgramEntity
Entity.MusicEntity
Entity.ChannelEntity
Entity.UntypedEntity
Entity.PlaylistEntity

---

### Metadata

```typescript
type Metadata = {
  title?: string // Title of the entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
}
```

See also:

Entertainment.ContentRating

---

### ProgramEntity

```typescript
type ProgramEntity =
  | MovieEntity
  | TVEpisodeEntity
  | TVSeasonEntity
  | TVSeriesEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.TVSeasonEntity
Entity.TVSeriesEntity
Entity.AdditionalEntity

---

### MusicEntity

```typescript
type MusicEntity = {
  entityType: 'music'
  musicType: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  entityId: string
}
```

See also:

Entertainment.MusicType

---

### ChannelEntity

```typescript
type ChannelEntity = {
  entityType: 'channel'
  channelType: 'streaming' | 'overTheAir'
  entityId: string // ID of the channel, in the target App's scope.
  appContentData?: string
}
```

---

### UntypedEntity

```typescript
type UntypedEntity = {
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlaylistEntity

A Firebolt compliant representation of a Playlist entity.

```typescript
type PlaylistEntity = {
  entityType: 'playlist'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### MovieEntity

A Firebolt compliant representation of a Movie entity.

```typescript
type MovieEntity = {
  entityType: 'program'
  programType: 'movie'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVEpisodeEntity

A Firebolt compliant representation of a TV Episode entity.

```typescript
type TVEpisodeEntity = {
  entityType: 'program'
  programType: 'episode'
  entityId: string
  seriesId: string
  seasonId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeasonEntity

A Firebolt compliant representation of a TV Season entity.

```typescript
type TVSeasonEntity = {
  entityType: 'program'
  programType: 'season'
  entityId: string
  seriesId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeriesEntity

A Firebolt compliant representation of a TV Series entity.

```typescript
type TVSeriesEntity = {
  entityType: 'program'
  programType: 'series'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### AdditionalEntity

A Firebolt compliant representation of the remaining program entity types.

```typescript
type AdditionalEntity = {
  entityType: 'program'
  programType:
    | 'concert'
    | 'sportingEvent'
    | 'preview'
    | 'other'
    | 'advertisement'
    | 'musicVideo'
    | 'minisode'
    | 'extra'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlayableEntity

```typescript
type PlayableEntity =
  | MovieEntity
  | TVEpisodeEntity
  | PlaylistEntity
  | MusicEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.PlaylistEntity
Entity.MusicEntity
Entity.AdditionalEntity

---

### WayToWatch

A WayToWatch describes a way to watch a video program. It may describe a single
streamable asset or a set of streamable assets. For example, an app provider may
describe HD, SD, and UHD assets as individual WayToWatch objects or rolled into
a single WayToWatch.

If the WayToWatch represents a single streamable asset, the provided
ContentIdentifiers must be sufficient to play back the specific asset when sent
via a playback intent or deep link. If the WayToWatch represents multiple
streamable assets, the provided ContentIdentifiers must be sufficient to
playback one of the assets represented with no user action. In this scenario,
the app SHOULD choose the best asset for the user based on their device and
settings. The ContentIdentifiers MUST also be sufficient for navigating the user
to the appropriate entity or detail screen via an entity intent.

The app should set the `entitled` property to indicate if the user can watch, or
not watch, the asset without making a purchase. If the entitlement is known to
expire at a certain time (e.g., a rental), the app should also provide the
`entitledExpires` property. If the entitlement is not expired, the UI will use
the `entitled` property to display watchable assets to the user, adjust how
assets are presented to the user, and how intents into the app are generated.
For example, the the Aggregated Experience could render a "Watch" button for an
entitled asset versus a "Subscribe" button for an non-entitled asset.

The app should set the `offeringType` to define how the content may be
authorized. The UI will use this to adjust how content is presented to the user.

A single WayToWatch cannot represent streamable assets available via multiple
purchase paths. If, for example, an asset has both Buy, Rent and Subscription
availability, the three different entitlement paths MUST be represented as
multiple WayToWatch objects.

`price` should be populated for WayToWatch objects with `buy` or `rent`
`offeringType`. If the WayToWatch represents a set of assets with various price
points, the `price` provided must be the lowest available price.

```typescript
type WayToWatch = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  expires?: string // Time when the WayToWatch is no longer available.
  entitled?: boolean // Specify if the user is entitled to watch the entity.
  entitledExpires?: string // Time when the entity is no longer entitled.
  offeringType?: OfferingType // The offering type of the WayToWatch.
  hasAds?: boolean // True if the streamable asset contains ads.
  price?: number // For "buy" and "rent" WayToWatch, the price to buy or rent in the user's preferred currency.
  videoQuality?: 'SD' | 'HD' | 'UHD'[] // List of the video qualities available via the WayToWatch.
  audioProfile: AudioProfile[] // List of the audio types available via the WayToWatch.
  audioLanguages?: string[] // List of audio track languages available on the WayToWatch. The first is considered the primary language. Languages are expressed as ISO 639 1/2 codes.
  closedCaptions?: string[] // List of languages for which closed captions are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  subtitles?: string[] // List of languages for which subtitles are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  audioDescriptions?: string[] // List of languages for which audio descriptions (DVD) as available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.OfferingType
Types.AudioProfile

---

### EventObject

```typescript
type EventObject = [property: string]: EventObjectPrimitives | EventObjectPrimitives | EventObject[] | EventObject
```

See also:

[EventObjectPrimitives](#eventobjectprimitives)
[EventObject](#eventobject-1)

---

### ContentIdentifiers

The ContentIdentifiers object is how the app identifies an entity or asset to
the Firebolt platform. These ids are used to look up metadata and deep link into
the app.

Apps do not need to provide all ids. They only need to provide the minimum
required to target a playable stream or an entity detail screen via a deep link.
If an id isn't needed to get to those pages, it doesn't need to be included.

```typescript
type ContentIdentifiers = {
  assetId?: string // Identifies a particular playable asset. For example, the HD version of a particular movie separate from the UHD version.
  entityId?: string // Identifies an entity, such as a Movie, TV Series or TV Episode.
  seasonId?: string // The TV Season for a TV Episode.
  seriesId?: string // The TV Series for a TV Episode or TV Season.
  appContentData?: string // App-specific content identifiers.
}
```

---

### ContentRating

A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.

## United States

`US-Movie` (MPAA):

Ratings: `NR`, `G`, `PG`, `PG13`, `R`, `NC17`

Advisories: `AT`, `BN`, `SL`, `SS`, `N`, `V`

`US-TV` (Vchip):

Ratings: `TVY`, `TVY7`, `TVG`, `TVPG`, `TV14`, `TVMA`

Advisories: `FV`, `D`, `L`, `S`, `V`

## Canada

`CA-Movie` (OFRB):

Ratings: `G`, `PG`, `14A`, `18A`, `R`, `E`

`CA-TV` (AGVOT)

Ratings: `E`, `C`, `C8`, `G`, `PG`, `14+`, `18+`

Advisories: `C`, `C8`, `G`, `PG`, `14+`, `18+`

`CA-Movie-Fr` (Canadian French language movies):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

`CA-TV-Fr` (Canadian French language TV):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

```typescript
type ContentRating = {
  scheme:
    | 'CA-Movie'
    | 'CA-TV'
    | 'CA-Movie-Fr'
    | 'CA-TV-Fr'
    | 'US-Movie'
    | 'US-TV' // The rating scheme.
  rating: string // The content rating.
  advisories?: string[] // Optional list of subratings or content advisories.
}
```

---

### HDMIPortId

```typescript
type HDMIPortId = string
```

---

### WifiSignalStrength

Strength of Wifi signal, value is negative based on RSSI specification.

```typescript
type WifiSignalStrength = number
```

---

### Entitlement

```typescript
type Entitlement = {
  entitlementId: string
  startTime?: string
  endTime?: string
}
```

---

### EntityInfo

An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.

Additionally, EntityInfo objects must specify a properly formed
ContentIdentifiers object, `entityType`, and `title`. The app should provide
the `synopsis` property for a good user experience if the content
metadata is not available another way.

The ContentIdentifiers must be sufficient for navigating the user to the
appropriate entity or detail screen via a `detail` intent or deep link.

EntityInfo objects must provide at least one WayToWatch object when returned as
part of an `entityInfo` method and a streamable asset is available to the user.
It is optional for the `purchasedContent` method, but recommended because the UI
may use those data.

```typescript
type EntityInfo = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  title: string // Title of the entity.
  entityType: 'program' | 'music' // The type of the entity, e.g. `program` or `music`.
  programType?: ProgramType // In the case of a program `entityType`, specifies the program type.
  musicType?: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.ProgramType
Entertainment.MusicType
Entertainment.ContentRating
Entertainment.WayToWatch

---

### AgePolicy

The policy that describes various age groups to which content is directed. See distributor documentation for further details.

```typescript
type AgePolicy = string | 'app:adult' | 'app:child' | 'app:teen'
```

---

### NavigationIntent

A Firebolt compliant representation of a user intention to navigate to a specific place in an app.

```typescript
type NavigationIntent =
  | HomeIntent
  | LaunchIntent
  | EntityIntent
  | PlaybackIntent
  | SearchIntent
  | SectionIntent
  | TuneIntent
  | PlayEntityIntent
  | PlayQueryIntent
```

See also:

Intents.HomeIntent
Intents.LaunchIntent
Intents.EntityIntent
Intents.PlaybackIntent
Intents.SearchIntent
Intents.SectionIntent
Intents.TuneIntent
Intents.PlayEntityIntent
Intents.PlayQueryIntent

---

### HomeIntent

A Firebolt compliant representation of a user intention to navigate an app to it's home screen, and bring that app to the foreground if needed.

```typescript
type HomeIntent = {
  action: 'home'
  context: object
}
```

---

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: 'launch'
  context: object
}
```

---

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: 'entity'
  data:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  context: object
}
```

---

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: 'playback'
  data: PlayableEntity
  context: object
}
```

See also:

Entity.PlayableEntity

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  action: 'search'
  data?: object
  context: object
}
```

---

### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  action: 'section'
  data: object
  context: object
}
```

---

### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  action: 'tune'
  data: object
  context: object
}
```

See also:

Entity.ChannelEntity

---

### PlayEntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlayEntityIntent = {
  action: 'play-entity'
  data: object
  context: object
}
```

See also:

Entity.PlayableEntity

---

### PlayQueryIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for an abstract query to be searched for and played by the app.

```typescript
type PlayQueryIntent = {
  action: 'play-query'
  data: object
  context: object
}
```

See also:

Entertainment.ProgramType
Entertainment.MusicType

---

### Intent

A Firebolt compliant representation of a user intention.

```typescript
type Intent = {
  action: string
  context: object
}
```

See also:

Policies.AgePolicy

---

### IntentProperties

```typescript
type IntentProperties = {}
```

---

### SecondScreenEvent

An a message notification from a second screen device

```typescript
type SecondScreenEvent = {
  type: 'dial'
  version?: string
  data?: string
}
```

---

### LifecycleState

The application lifecycle state

```typescript
LifecycleState: {
    INITIALIZING: 'initializing',
    INACTIVE: 'inactive',
    FOREGROUND: 'foreground',
    BACKGROUND: 'background',
    UNLOADING: 'unloading',
    SUSPENDED: 'suspended',
},

```

---
