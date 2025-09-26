---
title: Profile

version: pr-docs-gen-pr-test
layout: default
sdk: core
---

# Profile Module

---

Version Profile 1.5.0-docs-gen-pr-test.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [approveContentRating](#approvecontentrating)
  - [approvePurchase](#approvepurchase)
  - [flags](#flags)
  - [listen](#listen)
  - [once](#once)
  - [viewingRestrictions](#viewingrestrictions)
- [Events](#events)
  - [viewingRestrictionsChanged](#viewingrestrictionschanged)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  </details>
- [Types](#types)
  - [ContentRating](#contentrating)
  - [ViewingRestriction](#viewingrestriction)

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

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:approve:content |

#### Examples

Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

let allow = await Profile.approveContentRating()
console.log(allow)
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

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:approve:purchase |

#### Examples

Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

let allow = await Profile.approvePurchase()
console.log(allow)
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
function flags(): Promise<FlatMap>
```

Promise resolution:

[FlatMap](../Types/schemas/#FlatMap)

Capabilities:

| Role | Capability                            |
| ---- | ------------------------------------- |
| uses | xrn:firebolt:capability:profile:flags |

#### Examples

Default Example

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

let flags = await Profile.flags()
console.log(flags)
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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Profile.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Profile.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Profile.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Profile.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### viewingRestrictions

The profile's preferred viewing restrictions.

To get the value of `viewingRestrictions` call the method like this:

```typescript
function viewingRestrictions(): Promise<object>
```

Promise resolution:

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:profile:viewingrestrictions |

#### Examples

Viewing restrictions that disallow content with an MPAA R or US TV-14-V rating

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

let viewingRestrictions = await Profile.viewingRestrictions()
console.log(viewingRestrictions)
```

Value of `viewingRestrictions`:

```javascript
{
	"enabled": true,
	"restrictions": [
		{
			"scheme": "MPAA",
			"ratings": [
				{
					"rating": "R"
				}
			]
		},
		{
			"scheme": "US_TV",
			"ratings": [
				{
					"rating": "TV-14",
					"subRatings": [
						"V"
					]
				}
			]
		}
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Profile.viewingRestrictions",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enabled": true,
    "restrictions": [
      {
        "scheme": "MPAA",
        "ratings": [
          {
            "rating": "R"
          }
        ]
      },
      {
        "scheme": "US_TV",
        "ratings": [
          {
            "rating": "TV-14",
            "subRatings": ["V"]
          }
        ]
      }
    ]
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function viewingRestrictions(callback: (value) => object): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Viewing restrictions that disallow content with an MPAA R or US TV-14-V rating

JavaScript:

```javascript
import { Profile } from '@firebolt-js/sdk'

let listenerId = await viewingRestrictions((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `viewingRestrictions`:

```javascript
{
	"enabled": true,
	"restrictions": [
		{
			"scheme": "MPAA",
			"ratings": [
				{
					"rating": "R"
				}
			]
		},
		{
			"scheme": "US_TV",
			"ratings": [
				{
					"rating": "TV-14",
					"subRatings": [
						"V"
					]
				}
			]
		}
	]
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Profile.onViewingRestrictionsChanged",
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
  "result": {
    "enabled": true,
    "restrictions": [
      {
        "scheme": "MPAA",
        "ratings": [
          {
            "rating": "R"
          }
        ]
      },
      {
        "scheme": "US_TV",
        "ratings": [
          {
            "rating": "TV-14",
            "subRatings": ["V"]
          }
        ]
      }
    ]
  }
}
```

</details>

---

## Events

### viewingRestrictionsChanged

See: [viewingRestrictions](#viewingrestrictions)

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### viewingRestrictionsChanged

See: [viewingRestrictions](#viewingrestrictions)

</details>

## Types

### ContentRating

The rating and subrating for content.

```typescript
type ContentRating = {
  rating?: string // The rating to be restricted. Refer to operator documentation for supported values.
  subRatings?: string[] // A list of sub-ratings to be restricted. Refer to operator documentation for supported values.
}
```

---

### ViewingRestriction

The content viewing restriction.

```typescript
type ViewingRestriction = {
  scheme?: string // The scheme for the restriction (e.g. MPAA for US movies). Scheme values may be region or operator dependant; refer to operator documentation for the scheme values supported on your targeted platform.
  ratings?: ContentRating[] // The rating and subrating for content.
}
```

See also:

[ContentRating](#contentrating)

---
