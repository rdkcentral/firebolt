---
title: Content

version: pr-feature-user-interest
layout: default
sdk: discovery
---

# Content Module

---

Version Content 1.0.1-feature-user-interest.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [entity](#entity)
  - [listen](#listen)
  - [once](#once)
  - [providers](#providers)
  - [purchases](#purchases)
  - [requestUserInterest](#requestuserinterest)
- [Events](#events)
  - [userInterestedIn](#userinterestedin)
- [Types](#types)
  - [ContentProvider](#contentprovider)
  - [PurchasedContentParameters](#purchasedcontentparameters)
  - [FederationOptions](#federationoptions)
  - [ProvidedPurchasedContentResult](#providedpurchasedcontentresult)
  - [EntityInfoParameters](#entityinfoparameters)
  - [ProvidedEntityInfoResult](#providedentityinforesult)

## Usage

To use the Content module, you can import it into your project from the Firebolt SDK:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'
```

## Overview

undefined

## Methods

### entity

Gets information about a program entity from a provider and its available watchable assets, such as entitlement status and price. Includes information about the program entity and its relevant associated entities, such as extras, previews, and, in the case of TV series, seasons and episodes.

```typescript
function entity(
  provider: string,
  parameters: EntityInfoParameters,
  options?: FederationOptions,
): Promise<ProvidedEntityInfoResult>
```

Parameters:

| Param        | Type                                            | Required | Description                                     |
| ------------ | ----------------------------------------------- | -------- | ----------------------------------------------- |
| `provider`   | `string`                                        | true     | The id of the provider that has the entity info |
| `parameters` | [`EntityInfoParameters`](#entityinfoparameters) | true     | The content parameters                          |
| `options`    | [`FederationOptions`](#federationoptions)       | false    | Any options with making the request to provider |

Promise resolution:

[ProvidedEntityInfoResult](#providedentityinforesult)

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:entity-info |

#### Examples

Get info about specific content from a provider

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let content = await Content.entity(
  'Vudu',
  { entityId: '111' },
  { timeout: 10000 },
)
console.log(content)
```

Value of `content`:

```javascript
{
	"provider": "Vudu",
	"data": {
		"expires": "2025-01-01T00:00:00.000Z",
		"entity": {
			"identifiers": {
				"entityId": "345"
			},
			"entityType": "program",
			"programType": "movie",
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
			],
			"waysToWatch": [
				{
					"identifiers": {
						"assetId": "123"
					},
					"expires": "2025-01-01T00:00:00.000Z",
					"entitled": true,
					"entitledExpires": "2025-01-01T00:00:00.000Z",
					"offeringType": "buy",
					"price": 2.99,
					"videoQuality": [
						"UHD"
					],
					"audioProfile": [
						"dolbyAtmos"
					],
					"audioLanguages": [
						"en"
					],
					"closedCaptions": [
						"en"
					],
					"subtitles": [
						"es"
					],
					"audioDescriptions": [
						"en"
					]
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
  "method": "Content.entity",
  "params": {
    "provider": "Vudu",
    "parameters": {
      "entityId": "111"
    },
    "options": {
      "timeout": 10000
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "provider": "Vudu",
    "data": {
      "expires": "2025-01-01T00:00:00.000Z",
      "entity": {
        "identifiers": {
          "entityId": "345"
        },
        "entityType": "program",
        "programType": "movie",
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
        ],
        "waysToWatch": [
          {
            "identifiers": {
              "assetId": "123"
            },
            "expires": "2025-01-01T00:00:00.000Z",
            "entitled": true,
            "entitledExpires": "2025-01-01T00:00:00.000Z",
            "offeringType": "buy",
            "price": 2.99,
            "videoQuality": ["UHD"],
            "audioProfile": ["dolbyAtmos"],
            "audioLanguages": ["en"],
            "closedCaptions": ["en"],
            "subtitles": ["es"],
            "audioDescriptions": ["en"]
          }
        ]
      }
    }
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

### providers

Returns a list of providers and the discovery apis they support

```typescript
function providers(): Promise<ContentProvider[]>
```

Promise resolution:

```typescript
ContentProvider[]
```

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:providers |

#### Examples

Getting the list of providers and the discovery apis they support

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let providers = await Content.providers()
console.log(providers)
```

Value of `providers`:

```javascript
;[
  {
    id: 'Vudu',
    apis: ['purchases', 'entity'],
  },
  {
    id: 'NetflixApp',
    apis: ['search'],
  },
]
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.providers",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "id": "Vudu",
      "apis": ["purchases", "entity"]
    },
    {
      "id": "NetflixApp",
      "apis": ["search"]
    }
  ]
}
```

</details>

---

### purchases

Gets a list of entities that the user has purchased

```typescript
function purchases(
  provider: string,
  parameters: PurchasedContentParameters,
  options?: FederationOptions,
): Promise<ProvidedPurchasedContentResult>
```

Parameters:

| Param        | Type                                                        | Required | Description                                              |
| ------------ | ----------------------------------------------------------- | -------- | -------------------------------------------------------- |
| `provider`   | `string`                                                    | true     | The id of the provider to request purchased content from |
| `parameters` | [`PurchasedContentParameters`](#purchasedcontentparameters) | true     | Any parameters to control what purchases are returned    |
| `options`    | [`FederationOptions`](#federationoptions)                   | false    | Any options with making the request to provider          |

Promise resolution:

[ProvidedPurchasedContentResult](#providedpurchasedcontentresult)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:purchased-content |

#### Examples

Gets a list of entities that the user has purchased

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let ProvidedPurchasedContentResult = await Content.purchases(
  'Vudu',
  { limit: 10 },
  { timeout: 10000 },
)
console.log(ProvidedPurchasedContentResult)
```

Value of `ProvidedPurchasedContentResult`:

```javascript
{
	"provider": "Vudu",
	"data": {
		"totalCount": 1,
		"expires": "2025-01-01T00:00:00.000Z",
		"entries": [
			{
				"identifiers": {
					"entityId": "345"
				},
				"entityType": "program",
				"programType": "movie",
				"title": "Cool Runnings",
				"synopsis": "When a Jamaican sprinter is disqualified from the Olympic Games, he enlists the help of a dishonored coach to start the first Jamaican Bobsled Team.",
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
		]
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
  "method": "Content.purchases",
  "params": {
    "provider": "Vudu",
    "parameters": {
      "limit": 10
    },
    "options": {
      "timeout": 10000
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "provider": "Vudu",
    "data": {
      "totalCount": 1,
      "expires": "2025-01-01T00:00:00.000Z",
      "entries": [
        {
          "identifiers": {
            "entityId": "345"
          },
          "entityType": "program",
          "programType": "movie",
          "title": "Cool Runnings",
          "synopsis": "When a Jamaican sprinter is disqualified from the Olympic Games, he enlists the help of a dishonored coach to start the first Jamaican Bobsled Team.",
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
      ]
    }
  }
}
```

</details>

---

### requestUserInterest

undefined

```typescript
function requestUserInterest(type?: InterestType): Promise<EntityInfo>
```

Parameters:

| Param  | Type           | Required | Description                                |
| ------ | -------------- | -------- | ------------------------------------------ |
| `type` | `InterestType` | false    | <br/>values: `'interest' \| 'disinterest'` |

Promise resolution:

[EntityInfo](../Entertainment/schemas/#EntityInfo)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let entity = await Content.requestUserInterest('interest')
console.log(entity)
```

Value of `entity`:

```javascript
{
	"identifiers": {
		"entityId": "xyz"
	},
	"entityType": "program",
	"programType": "movie",
	"title": "Interesting Movie Title"
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
    "type": "interest"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "identifiers": {
      "entityId": "xyz"
    },
    "entityType": "program",
    "programType": "movie",
    "title": "Interesting Movie Title"
  }
}
```

</details>

---

## Events

### userInterestedIn

```typescript
function listen('userInterestedIn', (InterestedInIntent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

[InterestedInIntent](../Intents/schemas/#InterestedInIntent)

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('userInterestedIn', (intent) => {
  console.log(intent)
})
```

Value of `intent`:

```javascript
{
	"action": "interestedIn",
	"data": {
		"appId": "cool-app",
		"type": "interest",
		"entity": {
			"identifiers": {
				"entityId": "xyz"
			},
			"entityType": "program",
			"programType": "movie",
			"title": "Interesting Movie Title"
		}
	},
	"context": {
		"source": "api"
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
  "method": "Content.onUserInterestedIn",
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
    "action": "interestedIn",
    "data": {
      "appId": "cool-app",
      "type": "interest",
      "entity": {
        "identifiers": {
          "entityId": "xyz"
        },
        "entityType": "program",
        "programType": "movie",
        "title": "Interesting Movie Title"
      }
    },
    "context": {
      "source": "api"
    }
  }
}
```

</details>

---

## Types

### ContentProvider

```typescript
type ContentProvider = {
  id: string
  apis: string[]
}
```

---

### PurchasedContentParameters

```typescript
type PurchasedContentParameters = {
  limit: number
  offeringType?: OfferingType // The offering type of the WayToWatch.
  programType?: ProgramType // In the case of a program `entityType`, specifies the program type.
}
```

See also:

'free' | 'subscribe' | 'buy' | 'rent'
'movie' | 'episode' | 'season' | 'series' | 'other' | 'preview' | 'extra' | 'concert' | 'sportingEvent' | 'advertisement' | 'musicVideo' | 'minisode'

---

### FederationOptions

```typescript
type FederationOptions = {
  timeout?: number
}
```

---

### ProvidedPurchasedContentResult

```typescript
type ProvidedPurchasedContentResult = {
  provider: string
  data: PurchasedContentResult
}
```

See also:

[PurchasedContentResult](../Discovery/schemas/#PurchasedContentResult)

---

### EntityInfoParameters

```typescript
type EntityInfoParameters = {
  entityId: string
  assetId?: string
}
```

---

### ProvidedEntityInfoResult

```typescript
type ProvidedEntityInfoResult = {
  provider: string
  data: EntityInfoResult // The result for an `entityInfo()` push or pull.
}
```

See also:

[EntityInfoResult](../Discovery/schemas/#EntityInfoResult)

---
