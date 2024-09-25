---
title: Content

version: pr-feat-native-discovery-test-app
layout: default
sdk: discovery
---

# Content Module

---

Version Content 1.4.1-feat-native-discovery-test-app.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [requestUserInterest](#requestuserinterest)
- [Events](#events)
  - [userInterest](#userinterest)
- [Types](#types)
  - [InterestResult](#interestresult)
  - [InterestEvent](#interestevent)

## Usage

To use the Content module, you can import it into your project from the Firebolt SDK:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'
```

## Overview

undefined

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

| Type     | Description                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Content.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Content.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Content.clear(id)` |

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
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Content.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### requestUserInterest

Provide information about the entity currently displayed or selected on the screen.

```typescript
function requestUserInterest(
  type: InterestType,
  reason: InterestReason,
): Promise<InterestResult>
```

Parameters:

| Param    | Type                                                     | Required | Description                                            |
| -------- | -------------------------------------------------------- | -------- | ------------------------------------------------------ |
| `type`   | [`InterestType`](../Discovery/schemas/#InterestType)     | true     | <br/>values: `'interest' \| 'disinterest'`             |
| `reason` | [`InterestReason`](../Discovery/schemas/#InterestReason) | true     | <br/>values: `'playlist' \| 'reaction' \| 'recording'` |

Promise resolution:

[InterestResult](#interestresult)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let interest = await Content.requestUserInterest('interest', 'playlist')
console.log(interest)
```

Value of `interest`:

```javascript
{
	"appId": "cool-app",
	"entity": {
		"identifiers": {
			"entityId": "345",
			"entityType": "program",
			"programType": "movie"
		},
		"info": {
			"title": "Cool Runnings",
			"synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
			"releaseDate": "1993-01-01T00:00:00.000Z",
			"contentRatings": [
				{
					"scheme": "US-Movie",
					"rating": "PG"
				},
				{
					"scheme": "CA-Movie",
					"rating": "G"
				}
			]
		}
	}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.requestUserInterest",
  "params": {
    "type": "interest",
    "reason": "playlist"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "appId": "cool-app",
    "entity": {
      "identifiers": {
        "entityId": "345",
        "entityType": "program",
        "programType": "movie"
      },
      "info": {
        "title": "Cool Runnings",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1993-01-01T00:00:00.000Z",
        "contentRatings": [
          {
            "scheme": "US-Movie",
            "rating": "PG"
          },
          {
            "scheme": "CA-Movie",
            "rating": "G"
          }
        ]
      }
    }
  }
}
```

</details>

---

## Events

### userInterest

```typescript
function listen('userInterest', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[InterestEvent](#interestevent)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('userInterest', (interest) => {
  console.log(interest)
})
```

Value of `interest`:

```javascript
{
	"appId": "cool-app",
	"type": "interest",
	"reason": "playlist",
	"entity": {
		"identifiers": {
			"entityId": "345",
			"entityType": "program",
			"programType": "movie"
		},
		"info": {
			"title": "Cool Runnings",
			"synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
			"releaseDate": "1993-01-01T00:00:00.000Z",
			"contentRatings": [
				{
					"scheme": "US-Movie",
					"rating": "PG"
				},
				{
					"scheme": "CA-Movie",
					"rating": "G"
				}
			]
		}
	}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.onUserInterest",
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
    "appId": "cool-app",
    "type": "interest",
    "reason": "playlist",
    "entity": {
      "identifiers": {
        "entityId": "345",
        "entityType": "program",
        "programType": "movie"
      },
      "info": {
        "title": "Cool Runnings",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1993-01-01T00:00:00.000Z",
        "contentRatings": [
          {
            "scheme": "US-Movie",
            "rating": "PG"
          },
          {
            "scheme": "CA-Movie",
            "rating": "G"
          }
        ]
      }
    }
  }
}
```

</details>

---

## Types

### InterestResult

```typescript
type InterestResult = {
  appId: string
  entity: EntityDetails
}
```

See also:

[EntityDetails](../Entity/schemas/#EntityDetails)

---

### InterestEvent

```typescript
type InterestEvent = {
  appId: string
  type: InterestType
  reason: InterestReason
  entity: EntityDetails
}
```

See also:

[InterestType](../Discovery/schemas/#InterestType)
[InterestReason](../Discovery/schemas/#InterestReason)
[EntityDetails](../Entity/schemas/#EntityDetails)

---
