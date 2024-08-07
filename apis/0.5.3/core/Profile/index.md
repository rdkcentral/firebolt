---
title: Profile
---

# Profile Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [profile.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/profile.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)

 - [Methods](#methods)
    - [approveContentRating](#approvecontentrating)
    - [approvePurchase](#approvepurchase)
    - [flags](#flags)
 - [Schemas](#schemas)
<span></span>

## Usage
To use the Profile module, you can import it into your project from the Firebolt SDK:

```javascript
import { Profile } from '@firebolt-js/sdk'
```
## Overview
Methods for getting information about the current user/account profile

## Events


## Methods
### approveContentRating
Verifies that the current profile should have access to mature/adult content.

```typescript
function approveContentRating(): Promise<boolean>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `boolean` | Whether or not to allow access |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.approveContentRating()
    .then(allow => {
        console.log(allow)
    })
```
Value of `allow`

```javascript
false
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "profile.approveContentRating",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>




---

### approvePurchase
Verifies that the current profile should have access to making purchases.

```typescript
function approvePurchase(): Promise<boolean>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `boolean` | Whether or not to allow access |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.approvePurchase()
    .then(allow => {
        console.log(allow)
    })
```
Value of `allow`

```javascript
false
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "profile.approvePurchase",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": false
}
```

</details>




---

### flags
Get a map of profile flags for the current session.

```typescript
function flags(): Promise<FlatMap>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`FlatMap`](../schemas/types#/definitions/flatmap) | The profile flags. |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.flags()
    .then(flags => {
        console.log(flags)
    })
```
Value of `flags`

```javascript
{
  "userExperience": "1000"
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "profile.flags",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "userExperience": "1000"
  }
}
```

</details>




---



