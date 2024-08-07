---
title: Localization
---

# Localization Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [localization.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/localization.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)

 - [Methods](#methods)
    - [locality](#locality)
    - [postalCode](#postalcode)
    - [countryCode](#countrycode)
    - [language](#language)
    - [locale](#locale)
    - [latlon](#latlon)
    - [additionalInfo](#additionalinfo)
 - [Schemas](#schemas)
    - [LatLon](#latlon)

<span></span>

## Usage
To use the Localization module, you can import it into your project from the Firebolt SDK:

```javascript
import { Localization } from '@firebolt-js/sdk'
```
## Overview
Methods for accessessing location and language preferences

## Events


## Methods
### locality
Get the locality/city the device is located in

```typescript
function locality(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device city |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.locality()
    .then(locality => {
        console.log(locality)
    })
```
Value of `locality`

```javascript
"Philadelphia"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.locality",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Philadelphia"
}
```

</details>




---

### postalCode
Get the postal code the device is located in

```typescript
function postalCode(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device postal code |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.postalCode()
    .then(postalCode => {
        console.log(postalCode)
    })
```
Value of `postalCode`

```javascript
"19103"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.postalCode",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "19103"
}
```

</details>




---

### countryCode
Get the ISO 3166 code for the counrty device is located in

```typescript
function countryCode(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device country code |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.countryCode()
    .then(code => {
        console.log(code)
    })
```
Value of `code`

```javascript
"US"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.countryCode",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "US"
}
```

</details>




---

### language
Get the ISO 639 1/2 code for the preferred language

```typescript
function language(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device language |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.language()
    .then(lang => {
        console.log(lang)
    })
```
Value of `lang`

```javascript
"en"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.language",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "en"
}
```

</details>




---

### locale
Get the *full* BCP 47 code, including script, region, variant, etc., for the preferred langauage/locale

```typescript
function locale(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device locale |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.locale()
    .then(locale => {
        console.log(locale)
    })
```
Value of `locale`

```javascript
"en-US"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.locale",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "en-US"
}
```

</details>




---

### latlon
Get the approximate latitude and longitude coordinates of the device location

```typescript
function latlon(): Promise<[number, number]>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `[number, number]` | lat/long tuple |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.latlon()
    .then(latlong => {
        console.log(latlong)
    })
```
Value of `latlong`

```javascript
[
  39.9549,
  75.1699
]
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.latlon",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    39.9549,
    75.1699
  ]
}
```

</details>




---

### additionalInfo
Get any platform-specific localization information, in an Map<string, string>

```typescript
function additionalInfo(): Promise<object>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `object` | the additional info |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Localization } from '@firebolt-js/sdk'

Localization.additionalInfo()
    .then(info => {
        console.log(info)
    })
```
Value of `info`

```javascript
{}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "localization.additionalInfo",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {}
}
```

</details>




---



## Schemas

### LatLon

```typescript
type LatLon = [number, number]
```





---


