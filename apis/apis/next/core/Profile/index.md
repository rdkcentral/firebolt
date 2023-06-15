---
title: Profile

version: next
layout: default
sdk: core
---

# Profile Module
---
Version Profile 0.13.1-next.1

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [approveContentRating](#approvecontentrating)
     - [approvePurchase](#approvepurchase)
     - [flags](#flags)



## Usage
To use the Profile module, you can import it into your project from the Firebolt SDK:

```javascript
import { Profile } from '@firebolt-js/sdk'
```


## Overview
 Methods for getting information about the current user/account profile

## Methods

### approveContentRating

Verifies that the current profile should have access to mature/adult content.

```typescript
function approveContentRating(): Promise<boolean>
```



Promise resolution:

```typescript
boolean
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:approve:content |


#### Examples


Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.approveContentRating()
    .then(allow => {
        console.log(allow)
    })
```

Value of `allow`:

```javascript
false
```
<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Profile.approveContentRating",
	"params": {}
}
```

Response:

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



Promise resolution:

```typescript
boolean
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:approve:purchase |


#### Examples


Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.approvePurchase()
    .then(allow => {
        console.log(allow)
    })
```

Value of `allow`:

```javascript
false
```
<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Profile.approvePurchase",
	"params": {}
}
```

Response:

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
function flags(): Promise<object>
```



Promise resolution:

```typescript
type FlatMap = {
  [property: string]: string | number | boolean
}
```

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:profile:flags |


#### Examples


Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

Profile.flags()
    .then(flags => {
        console.log(flags)
    })
```

Value of `flags`:

```javascript
{
	"userExperience": "1000"
}
```
<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "Profile.flags",
	"params": {}
}
```

Response:

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



