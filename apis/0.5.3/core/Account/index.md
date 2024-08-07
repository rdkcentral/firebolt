---
title: Account
---

# Account Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [account.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/account.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)

 - [Methods](#methods)
    - [id](#id)
    - [uid](#uid)
 - [Schemas](#schemas)
<span></span>

## Usage
To use the Account module, you can import it into your project from the Firebolt SDK:

```javascript
import { Account } from '@firebolt-js/sdk'
```
## Overview
A module for querying about the device account.

## Events


## Methods
### id
Get the platform back-office account identifier

```typescript
function id(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the id |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Account } from '@firebolt-js/sdk'

Account.id()
    .then(id => {
        console.log(id)
    })
```
Value of `id`

```javascript
"123"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "account.id",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "123"
}
```

</details>




---

### uid
Gets a unique id for the current app & account

```typescript
function uid(): Promise<string>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | a unique ID |


---

#### Examples

##### Getting the unique ID
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Account } from '@firebolt-js/sdk'

Account.uid()
    .then(uniqueId => {
        console.log(uniqueId)
    })
```
Value of `uniqueId`

```javascript
"ee6723b8-7ab3-462c-8d93-dbf61227998e"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "account.uid",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "ee6723b8-7ab3-462c-8d93-dbf61227998e"
}
```

</details>




---



