---
title: Discovery

version: pr-feature-user-interest
layout: default
sdk: core
---

# Discovery Module

---

Version Discovery 1.2.0-feature-user-interest.1

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
  - [Localization](#localization)
- [Methods](#methods)
  - [clearContentAccess](#clearcontentaccess)
  - [contentAccess](#contentaccess)
  - [details](#details)
  - [entitlements](#entitlements)
  - [entityInfo](#entityinfo)
  - [launch](#launch)
  - [listen](#listen)
  - [once](#once)
  - [policy](#policy)
  - [provide](#provide)
  - [purchasedContent](#purchasedcontent)
  - [purchases](#purchases)
  - [signIn](#signin)
  - [signOut](#signout)
  - [userInterest](#userinterest)
  - [watched](#watched)
  - [watchNext](#watchnext)
- [Events](#events)
  - [navigateTo](#navigateto)
  - [policyChanged](#policychanged)
  - [requestDetails](#requestdetails)
  - [requestPurchases](#requestpurchases)
  - [requestUserInterest](#requestuserinterest)
- [Provider Interfaces](#provider-interfaces)
  - [DetailsProvider](#detailsprovider)
  - [PurchasesProvider](#purchasesprovider)
  - [UserInterestProvider](#userinterestprovider)
- [Types](#types)
  - [DetailsProviderParameters](#detailsproviderparameters)
  - [PurchasesProviderParameters](#purchasesproviderparameters)
  - [UserInterestProviderParameters](#userinterestproviderparameters)
  - [DiscoveryPolicy](#discoverypolicy)
  - [Availability](#availability)
  - [PurchasedContentParameters](#purchasedcontentparameters)
  - [ContentAccessIdentifiers](#contentaccessidentifiers)
  - [EntityInfoParameters](#entityinfoparameters)
  - [EntityInfoFederatedRequest](#entityinfofederatedrequest)
  - [PurchasedContentFederatedRequest](#purchasedcontentfederatedrequest)

## Usage

To use the Discovery module, you can import it into your project from the Firebolt SDK:

```javascript
import { Discovery } from '@firebolt-js/sdk'
```

## Overview

Your App likely wants to integrate with the Platform's discovery capabilities. For example to add a "Watch Next" tile that links to your app from the platform's home screen.

Getting access to this information requires to connect to lower level APIs made available by the platform. Since implementations differ between operators and platforms, the Firebolt SDK offers a Discovery module, that exposes a generic, agnostic interface to the developer.

Under the hood, an underlaying transport layer will then take care of calling the right APIs for the actual platform implementation that your App is running on.

The Discovery plugin is used to _send_ information to the Platform.

### Localization

Apps should provide all user-facing strings in the device's language, as specified by the Firebolt `Localization.language` property.

Apps should provide prices in the same currency presented in the app. If multiple currencies are supported in the app, the app should provide prices in the user's current default currency.

## Methods

### clearContentAccess

Clear both availabilities and entitlements from the subscriber. This is equivalent of calling `Discovery.contentAccess({ availabilities: [], entitlements: []})`. This is typically called when the user signs out of an account.

```typescript
${method.signature}
```

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

Clear subscriber's availabilities and entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.clearContentAccess()
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
  "method": "Discovery.clearContentAccess",
  "params": {}
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

### contentAccess

Inform the platform of what content the user can access either by discovering it or consuming it. Availabilities determine which content is discoverable to a user, while entitlements determine if the user can currently consume that content. Content can be available but not entitled, this means that user can see the content but when they try to open it they must gain an entitlement either through purchase or subscription upgrade. In case the access changed off-device, this API should be called any time the app comes to the foreground to refresh the access. This API should also be called any time the availabilities or entitlements change within the app for any reason. Typical reasons may include the user signing into an account or upgrading a subscription. Less common cases can cause availabilities to change, such as moving to a new service location. When availabilities or entitlements are removed from the subscriber (such as when the user signs out), then an empty array should be given. To clear both, use the Discovery.clearContentAccess convenience API.

```typescript
${method.signature}
```

Parameters:

| Param | Type | Required | Description                                                                                        |
| ----- | ---- | -------- | -------------------------------------------------------------------------------------------------- |
| `ids` | ``   | true     | A list of identifiers that represent content that is discoverable or consumable for the subscriber |

Promise resolution:

```typescript
void
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

Update subscriber's availabilities

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.contentAccess({
  availabilities: [
    {
      type: 'channel-lineup',
      id: 'partner.com/availability/123',
      startTime: '2021-04-23T18:25:43.511Z',
      endTime: '2021-04-23T18:25:43.511Z',
    },
    {
      type: 'channel-lineup',
      id: 'partner.com/availability/456',
      startTime: '2021-04-23T18:25:43.511Z',
      endTime: '2021-04-23T18:25:43.511Z',
    },
  ],
})
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
  "method": "Discovery.contentAccess",
  "params": {
    "ids": {
      "availabilities": [
        {
          "type": "channel-lineup",
          "id": "partner.com/availability/123",
          "startTime": "2021-04-23T18:25:43.511Z",
          "endTime": "2021-04-23T18:25:43.511Z"
        },
        {
          "type": "channel-lineup",
          "id": "partner.com/availability/456",
          "startTime": "2021-04-23T18:25:43.511Z",
          "endTime": "2021-04-23T18:25:43.511Z"
        }
      ]
    }
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

Update subscriber's availabilities and entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.contentAccess({
  availabilities: [
    {
      type: 'channel-lineup',
      id: 'partner.com/availability/123',
      startTime: '2021-04-23T18:25:43.511Z',
      endTime: '2021-04-23T18:25:43.511Z',
    },
    {
      type: 'channel-lineup',
      id: 'partner.com/availability/456',
      startTime: '2021-04-23T18:25:43.511Z',
      endTime: '2021-04-23T18:25:43.511Z',
    },
  ],
  entitlements: [
    {
      entitlementId: '123',
      startTime: '2025-01-01T00:00:00.000Z',
      endTime: '2025-01-01T00:00:00.000Z',
    },
  ],
})
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
  "method": "Discovery.contentAccess",
  "params": {
    "ids": {
      "availabilities": [
        {
          "type": "channel-lineup",
          "id": "partner.com/availability/123",
          "startTime": "2021-04-23T18:25:43.511Z",
          "endTime": "2021-04-23T18:25:43.511Z"
        },
        {
          "type": "channel-lineup",
          "id": "partner.com/availability/456",
          "startTime": "2021-04-23T18:25:43.511Z",
          "endTime": "2021-04-23T18:25:43.511Z"
        }
      ],
      "entitlements": [
        {
          "entitlementId": "123",
          "startTime": "2025-01-01T00:00:00.000Z",
          "endTime": "2025-01-01T00:00:00.000Z"
        }
      ]
    }
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

Update subscriber's entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.contentAccess({
  entitlements: [
    {
      entitlementId: '123',
      startTime: '2025-01-01T00:00:00.000Z',
      endTime: '2025-01-01T00:00:00.000Z',
    },
  ],
})
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
  "method": "Discovery.contentAccess",
  "params": {
    "ids": {
      "entitlements": [
        {
          "entitlementId": "123",
          "startTime": "2025-01-01T00:00:00.000Z",
          "endTime": "2025-01-01T00:00:00.000Z"
        }
      ]
    }
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

Clear a subscriber's entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.contentAccess({ entitlements: [] })
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
  "method": "Discovery.contentAccess",
  "params": {
    "ids": {
      "entitlements": []
    }
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

Clear a subscriber's availabilities

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.contentAccess({ availabilities: [] })
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
  "method": "Discovery.contentAccess",
  "params": {
    "ids": {
      "availabilities": []
    }
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

### details

Provide information about a program entity and its available watchable assets, such as entitlement status and price, via either a push or pull call flow.

```typescript
${method.signature}
```

Parameters:

| Param      | Type     | Required | Description          |
| ---------- | -------- | -------- | -------------------- |
| `entityId` | `string` | true     |                      |
| `details`  | ``       | true     | The entityInfo data. |

Promise resolution:

```typescript

```

Capabilities:

| Role     | Capability                                    |
| -------- | --------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:entity-info |

#### Examples

Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.details('345', {
  expires: '2025-01-01T00:00:00.000Z',
  details: {
    identifiers: {
      entityId: '345',
      entityType: 'program',
      programType: 'movie',
    },
    info: {
      title: 'Cool Runnings',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1993-01-01T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-Movie',
          rating: 'PG',
        },
        {
          scheme: 'CA-Movie',
          rating: 'G',
        },
      ],
    },
    waysToWatch: [
      {
        identifiers: {
          assetId: '123',
        },
        expires: '2025-01-01T00:00:00.000Z',
        entitled: true,
        entitledExpires: '2025-01-01T00:00:00.000Z',
        offeringType: 'buy',
        price: 2.99,
        videoQuality: ['UHD'],
        audioProfile: ['dolbyAtmos'],
        audioLanguages: ['en'],
        closedCaptions: ['en'],
        subtitles: ['es'],
        audioDescriptions: ['en'],
      },
    ],
  },
})
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
  "method": "Discovery.details",
  "params": {
    "entityId": "345",
    "details": {
      "expires": "2025-01-01T00:00:00.000Z",
      "details": {
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
        },
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

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.details('345', {
  expires: '2025-01-01T00:00:00.000Z',
  details: {
    identifiers: {
      entityId: '345',
      entityType: 'program',
      programType: 'movie',
    },
    info: {
      title: 'Cool Runnings',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1993-01-01T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-Movie',
          rating: 'PG',
        },
        {
          scheme: 'CA-Movie',
          rating: 'G',
        },
      ],
    },
    waysToWatch: [
      {
        identifiers: {
          assetId: '123',
        },
        expires: '2025-01-01T00:00:00.000Z',
        entitled: true,
        entitledExpires: '2025-01-01T00:00:00.000Z',
        offeringType: 'buy',
        price: 2.99,
        videoQuality: ['UHD'],
        audioProfile: ['dolbyAtmos'],
        audioLanguages: ['en'],
        closedCaptions: ['en'],
        subtitles: ['es'],
        audioDescriptions: ['en'],
      },
    ],
  },
})
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
  "method": "Discovery.details",
  "params": {
    "entityId": "345",
    "details": {
      "expires": "2025-01-01T00:00:00.000Z",
      "details": {
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
        },
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

### entitlements

Inform the platform of the users latest entitlements w/in this app.

```typescript
${method.signature}
```

Parameters:

| Param          | Type | Required | Description                  |
| -------------- | ---- | -------- | ---------------------------- |
| `entitlements` | ``   | true     | Array of entitlement objects |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

Update user's entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entitlements([
  {
    entitlementId: 'partner.com/entitlement/123',
    startTime: '2021-04-23T18:25:43.511Z',
    endTime: '2021-04-23T18:25:43.511Z',
  },
  {
    entitlementId: 'partner.com/entitlement/456',
    startTime: '2021-04-23T18:25:43.511Z',
    endTime: '2021-04-23T18:25:43.511Z',
  },
])
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.entitlements",
  "params": {
    "entitlements": [
      {
        "entitlementId": "partner.com/entitlement/123",
        "startTime": "2021-04-23T18:25:43.511Z",
        "endTime": "2021-04-23T18:25:43.511Z"
      },
      {
        "entitlementId": "partner.com/entitlement/456",
        "startTime": "2021-04-23T18:25:43.511Z",
        "endTime": "2021-04-23T18:25:43.511Z"
      }
    ]
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### entityInfo

Provide information about a program entity and its available watchable assets, such as entitlement status and price, via either a push or pull call flow. Includes information about the program entity and its relevant associated entities, such as extras, previews, and, in the case of TV series, seasons and episodes.

See the `EntityInfo` and `WayToWatch` data structures below for more information.

The app only needs to implement Pull support for `entityInfo` at this time.

To allow the platform to pull data, use `entityInfo(callback: Function)`:

```typescript
function entityInfo(
  callback: (parameters: EntityInfoParameters) => Promise<>,
): Promise<boolean>
```

Parameters:

| Param      | Type       | Required | Summary                                     |
| ---------- | ---------- | -------- | ------------------------------------------- |
| `callback` | `Function` | Yes      | A callback for the platform to pull objects |

Callback parameters:

| Param        | Type                   | Required | Summary                                                     |
| ------------ | ---------------------- | -------- | ----------------------------------------------------------- |
| `parameters` | `EntityInfoParameters` | Yes      | An object describing the platform's query for an `` object. |

````typescript
```typescript

````

````

Callback promise resolution:

```typescript
```typescript

````

````



#### Examples


Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo(async parameters => {
  console.log(parameters.entityId)
  console.log(parameters.assetId)
  return {
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
})
console.log(success)
````

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPullEntityInfo",
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
    "correlationId": "xyz",
    "parameters": {
      "entityId": "345"
    }
  }
}
```

Push Request:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": "TBD",
    "result": {
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

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo(async (parameters) => {
  console.log(parameters.entityId)
  console.log(parameters.assetId)
  return {
    expires: '2025-01-01T00:00:00.000Z',
    entity: {
      identifiers: {
        entityId: '345',
      },
      entityType: 'program',
      programType: 'movie',
      title: 'Cool Runnings',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1993-01-01T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-Movie',
          rating: 'PG',
        },
        {
          scheme: 'CA-Movie',
          rating: 'G',
        },
      ],
      waysToWatch: [
        {
          identifiers: {
            assetId: '123',
          },
          expires: '2025-01-01T00:00:00.000Z',
          entitled: true,
          entitledExpires: '2025-01-01T00:00:00.000Z',
          offeringType: 'buy',
          price: 2.99,
          videoQuality: ['UHD'],
          audioProfile: ['dolbyAtmos'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
          subtitles: ['es'],
          audioDescriptions: ['en'],
        },
      ],
    },
    related: [
      {
        identifiers: {
          entityId: '345',
        },
        entityType: 'program',
        programType: 'preview',
        title: 'Cool Runnings Trailer',
        waysToWatch: [
          {
            identifiers: {
              assetId: '123111',
              entityId: '345',
            },
            entitled: true,
            videoQuality: ['HD'],
            audioProfile: ['dolbyAtmos'],
            audioLanguages: ['en'],
            closedCaptions: ['en'],
          },
        ],
      },
    ],
  }
})
console.log(success)
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPullEntityInfo",
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
    "correlationId": "xyz",
    "parameters": {
      "entityId": "345"
    }
  }
}
```

Push Request:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": "TBD",
    "result": {
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
      },
      "related": [
        {
          "identifiers": {
            "entityId": "345"
          },
          "entityType": "program",
          "programType": "preview",
          "title": "Cool Runnings Trailer",
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "123111",
                "entityId": "345"
              },
              "entitled": true,
              "videoQuality": ["HD"],
              "audioProfile": ["dolbyAtmos"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        }
      ]
    }
  }
}
```

</details>

Send entity info for a TV Series with seasons and episodes to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo(async (parameters) => {
  console.log(parameters.entityId)
  console.log(parameters.assetId)
  return {
    expires: '2025-01-01T00:00:00.000Z',
    entity: {
      identifiers: {
        entityId: '98765',
      },
      entityType: 'program',
      programType: 'series',
      title: 'Perfect Strangers',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1986-01-01T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-TV',
          rating: 'TV-PG',
        },
      ],
    },
    related: [
      {
        identifiers: {
          entityId: '111',
          seriesId: '98765',
        },
        entityType: 'program',
        programType: 'season',
        seasonNumber: 1,
        title: 'Perfect Strangers Season 3',
        contentRatings: [
          {
            scheme: 'US-TV',
            rating: 'TV-PG',
          },
        ],
        waysToWatch: [
          {
            identifiers: {
              assetId: '556',
              entityId: '111',
              seriesId: '98765',
            },
            entitled: true,
            offeringType: 'free',
            videoQuality: ['SD'],
            audioProfile: ['stereo'],
            audioLanguages: ['en'],
            closedCaptions: ['en'],
          },
        ],
      },
      {
        identifiers: {
          entityId: '111',
          seriesId: '98765',
        },
        entityType: 'program',
        programType: 'episode',
        seasonNumber: 1,
        episodeNumber: 1,
        title: "Knock Knock, Who's There?",
        synopsis:
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
        releaseDate: '1986-03-25T00:00:00.000Z',
        contentRatings: [
          {
            scheme: 'US-TV',
            rating: 'TV-PG',
          },
        ],
        waysToWatch: [
          {
            identifiers: {
              assetId: '556',
              entityId: '111',
              seriesId: '98765',
            },
            entitled: true,
            offeringType: 'free',
            videoQuality: ['SD'],
            audioProfile: ['stereo'],
            audioLanguages: ['en'],
            closedCaptions: ['en'],
          },
        ],
      },
      {
        identifiers: {
          entityId: '112',
          seriesId: '98765',
        },
        entityType: 'program',
        programType: 'episode',
        seasonNumber: 1,
        episodeNumber: 2,
        title: 'Picture This',
        synopsis:
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
        releaseDate: '1986-04-01T00:00:00.000Z',
        contentRatings: [
          {
            scheme: 'US-TV',
            rating: 'TV-PG',
          },
        ],
        waysToWatch: [
          {
            identifiers: {
              assetId: '557',
              entityId: '112',
              seriesId: '98765',
            },
            entitled: true,
            offeringType: 'free',
            videoQuality: ['SD'],
            audioProfile: ['stereo'],
            audioLanguages: ['en'],
            closedCaptions: ['en'],
          },
        ],
      },
    ],
  }
})
console.log(success)
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPullEntityInfo",
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
    "correlationId": "xyz",
    "parameters": {
      "entityId": "345"
    }
  }
}
```

Push Request:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": "TBD",
    "result": {
      "expires": "2025-01-01T00:00:00.000Z",
      "entity": {
        "identifiers": {
          "entityId": "98765"
        },
        "entityType": "program",
        "programType": "series",
        "title": "Perfect Strangers",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1986-01-01T00:00:00.000Z",
        "contentRatings": [
          {
            "scheme": "US-TV",
            "rating": "TV-PG"
          }
        ]
      },
      "related": [
        {
          "identifiers": {
            "entityId": "111",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "season",
          "seasonNumber": 1,
          "title": "Perfect Strangers Season 3",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "556",
                "entityId": "111",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        },
        {
          "identifiers": {
            "entityId": "111",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "episode",
          "seasonNumber": 1,
          "episodeNumber": 1,
          "title": "Knock Knock, Who's There?",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1986-03-25T00:00:00.000Z",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "556",
                "entityId": "111",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        },
        {
          "identifiers": {
            "entityId": "112",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "episode",
          "seasonNumber": 1,
          "episodeNumber": 2,
          "title": "Picture This",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1986-04-01T00:00:00.000Z",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "557",
                "entityId": "112",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        }
      ]
    }
  }
}
```

</details>

To push data to the platform, e.g. during app launch, use `entityInfo(result: )`:

```typescript
function entityInfo(result: ): Promise<boolean>
```

Parameters:

| Param    | Type | Required | Summary                             |
| -------- | ---- | -------- | ----------------------------------- |
| `result` | ``   | Yes      | The `` data to push to the platform |

````typescript
```typescript

````

````

See also: [EntityInfo](#entityinfo-1)

Promise resolution:

| Type | Summary |
| ---- | ------- |
| `boolean` | Whether or not the push was successful |

#### Examples


Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo({
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
                                          })
console.log(success)
````

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": null,
    "result": {
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

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo({
  expires: '2025-01-01T00:00:00.000Z',
  entity: {
    identifiers: {
      entityId: '345',
    },
    entityType: 'program',
    programType: 'movie',
    title: 'Cool Runnings',
    synopsis:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
    releaseDate: '1993-01-01T00:00:00.000Z',
    contentRatings: [
      {
        scheme: 'US-Movie',
        rating: 'PG',
      },
      {
        scheme: 'CA-Movie',
        rating: 'G',
      },
    ],
    waysToWatch: [
      {
        identifiers: {
          assetId: '123',
        },
        expires: '2025-01-01T00:00:00.000Z',
        entitled: true,
        entitledExpires: '2025-01-01T00:00:00.000Z',
        offeringType: 'buy',
        price: 2.99,
        videoQuality: ['UHD'],
        audioProfile: ['dolbyAtmos'],
        audioLanguages: ['en'],
        closedCaptions: ['en'],
        subtitles: ['es'],
        audioDescriptions: ['en'],
      },
    ],
  },
  related: [
    {
      identifiers: {
        entityId: '345',
      },
      entityType: 'program',
      programType: 'preview',
      title: 'Cool Runnings Trailer',
      waysToWatch: [
        {
          identifiers: {
            assetId: '123111',
            entityId: '345',
          },
          entitled: true,
          videoQuality: ['HD'],
          audioProfile: ['dolbyAtmos'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
        },
      ],
    },
  ],
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": null,
    "result": {
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
      },
      "related": [
        {
          "identifiers": {
            "entityId": "345"
          },
          "entityType": "program",
          "programType": "preview",
          "title": "Cool Runnings Trailer",
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "123111",
                "entityId": "345"
              },
              "entitled": true,
              "videoQuality": ["HD"],
              "audioProfile": ["dolbyAtmos"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        }
      ]
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Send entity info for a TV Series with seasons and episodes to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.entityInfo({
  expires: '2025-01-01T00:00:00.000Z',
  entity: {
    identifiers: {
      entityId: '98765',
    },
    entityType: 'program',
    programType: 'series',
    title: 'Perfect Strangers',
    synopsis:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
    releaseDate: '1986-01-01T00:00:00.000Z',
    contentRatings: [
      {
        scheme: 'US-TV',
        rating: 'TV-PG',
      },
    ],
  },
  related: [
    {
      identifiers: {
        entityId: '111',
        seriesId: '98765',
      },
      entityType: 'program',
      programType: 'season',
      seasonNumber: 1,
      title: 'Perfect Strangers Season 3',
      contentRatings: [
        {
          scheme: 'US-TV',
          rating: 'TV-PG',
        },
      ],
      waysToWatch: [
        {
          identifiers: {
            assetId: '556',
            entityId: '111',
            seriesId: '98765',
          },
          entitled: true,
          offeringType: 'free',
          videoQuality: ['SD'],
          audioProfile: ['stereo'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
        },
      ],
    },
    {
      identifiers: {
        entityId: '111',
        seriesId: '98765',
      },
      entityType: 'program',
      programType: 'episode',
      seasonNumber: 1,
      episodeNumber: 1,
      title: "Knock Knock, Who's There?",
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1986-03-25T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-TV',
          rating: 'TV-PG',
        },
      ],
      waysToWatch: [
        {
          identifiers: {
            assetId: '556',
            entityId: '111',
            seriesId: '98765',
          },
          entitled: true,
          offeringType: 'free',
          videoQuality: ['SD'],
          audioProfile: ['stereo'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
        },
      ],
    },
    {
      identifiers: {
        entityId: '112',
        seriesId: '98765',
      },
      entityType: 'program',
      programType: 'episode',
      seasonNumber: 1,
      episodeNumber: 2,
      title: 'Picture This',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1986-04-01T00:00:00.000Z',
      contentRatings: [
        {
          scheme: 'US-TV',
          rating: 'TV-PG',
        },
      ],
      waysToWatch: [
        {
          identifiers: {
            assetId: '557',
            entityId: '112',
            seriesId: '98765',
          },
          entitled: true,
          offeringType: 'free',
          videoQuality: ['SD'],
          audioProfile: ['stereo'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
        },
      ],
    },
  ],
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.entityInfo",
  "params": {
    "correlationId": null,
    "result": {
      "expires": "2025-01-01T00:00:00.000Z",
      "entity": {
        "identifiers": {
          "entityId": "98765"
        },
        "entityType": "program",
        "programType": "series",
        "title": "Perfect Strangers",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1986-01-01T00:00:00.000Z",
        "contentRatings": [
          {
            "scheme": "US-TV",
            "rating": "TV-PG"
          }
        ]
      },
      "related": [
        {
          "identifiers": {
            "entityId": "111",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "season",
          "seasonNumber": 1,
          "title": "Perfect Strangers Season 3",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "556",
                "entityId": "111",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        },
        {
          "identifiers": {
            "entityId": "111",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "episode",
          "seasonNumber": 1,
          "episodeNumber": 1,
          "title": "Knock Knock, Who's There?",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1986-03-25T00:00:00.000Z",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "556",
                "entityId": "111",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        },
        {
          "identifiers": {
            "entityId": "112",
            "seriesId": "98765"
          },
          "entityType": "program",
          "programType": "episode",
          "seasonNumber": 1,
          "episodeNumber": 2,
          "title": "Picture This",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1986-04-01T00:00:00.000Z",
          "contentRatings": [
            {
              "scheme": "US-TV",
              "rating": "TV-PG"
            }
          ],
          "waysToWatch": [
            {
              "identifiers": {
                "assetId": "557",
                "entityId": "112",
                "seriesId": "98765"
              },
              "entitled": true,
              "offeringType": "free",
              "videoQuality": ["SD"],
              "audioProfile": ["stereo"],
              "audioLanguages": ["en"],
              "closedCaptions": ["en"]
            }
          ]
        }
      ]
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### launch

Launch or foreground the specified app, and optionally instructs it to navigate to the specified user action.
For the Primary Experience, the appId can be any one of:

- xrn:firebolt:application-type:main

- xrn:firebolt:application-type:settings

```typescript
${method.signature}
```

Parameters:

| Param    | Type     | Required | Description                                                                                                                      |
| -------- | -------- | -------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `appId`  | `string` | true     | The durable app Id of the app to launch                                                                                          |
| `intent` | ``       | false    | An optional `NavigationIntent` with details about what part of the app to show first, and context around how/why it was launched |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:launch |

#### Examples

Launch the 'Foo' app to it's home screen.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('foo', {
  action: 'home',
  context: { source: 'voice' },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "foo",
    "intent": {
      "action": "home",
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the 'Foo' app to it's own page for a specific entity.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('foo', {
  action: 'entity',
  data: {
    entityType: 'program',
    programType: 'movie',
    entityId: 'example-movie-id',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "foo",
    "intent": {
      "action": "entity",
      "data": {
        "entityType": "program",
        "programType": "movie",
        "entityId": "example-movie-id"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the 'Foo' app to a fullscreen playback experience for a specific entity.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('foo', {
  action: 'playback',
  data: {
    entityType: 'program',
    programType: 'movie',
    entityId: 'example-movie-id',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "foo",
    "intent": {
      "action": "playback",
      "data": {
        "entityType": "program",
        "programType": "movie",
        "entityId": "example-movie-id"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to a global page for a specific entity.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main', {
  action: 'entity',
  data: {
    entityType: 'program',
    programType: 'movie',
    entityId: 'example-movie-id',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main",
    "intent": {
      "action": "entity",
      "data": {
        "entityType": "program",
        "programType": "movie",
        "entityId": "example-movie-id"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to a global page for the company / partner with the ID 'foo'.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main', {
  action: 'section',
  data: {
    sectionName: 'company:foo',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main",
    "intent": {
      "action": "section",
      "data": {
        "sectionName": "company:foo"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to it's home screen, as if the Home remote button was pressed.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main', {
  action: 'home',
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main",
    "intent": {
      "action": "home",
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to it's search screen.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main', {
  action: 'search',
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main",
    "intent": {
      "action": "search",
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to it's settings screen.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch(
  'xrn:firebolt:application-type:settings ',
  {
    action: 'section',
    data: {
      sectionName: 'settings',
    },
    context: {
      source: 'voice',
    },
  },
)
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:settings ",
    "intent": {
      "action": "section",
      "data": {
        "sectionName": "settings"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to it's linear/epg guide.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main', {
  action: 'section',
  data: {
    sectionName: 'guide',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main",
    "intent": {
      "action": "section",
      "data": {
        "sectionName": "guide"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Launch the Aggregated Experience to the App Store details page for a specific app with the ID 'foo'.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('xrn:firebolt:application-type:main ', {
  action: 'section',
  data: {
    sectionName: 'app:foo',
  },
  context: {
    source: 'voice',
  },
})
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.launch",
  "params": {
    "appId": "xrn:firebolt:application-type:main ",
    "intent": {
      "action": "section",
      "data": {
        "sectionName": "app:foo"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

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

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### policy

get the discovery policy

To get the value of `policy` call the method like this:

```typescript
${method.signature}
```

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:policy |


#### Examples


Getting the discovery policy

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let policy = await Discovery.policy()
console.log(policy)
````

Value of `policy`:

```javascript
{
	"enableRecommendations": true,
	"shareWatchHistory": true,
	"rememberWatchedPrograms": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.policy",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "enableRecommendations": true,
    "shareWatchHistory": true,
    "rememberWatchedPrograms": true
  }
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function policy(callback: (value) => ): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Getting the discovery policy

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await policy((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `policy`:

```javascript
{
	"enableRecommendations": true,
	"shareWatchHistory": true,
	"rememberWatchedPrograms": true
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPolicyChanged",
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
    "enableRecommendations": true,
    "shareWatchHistory": true,
    "rememberWatchedPrograms": true
  }
}
```

</details>

---

### provide

To provide a specific capability to the platform. See [Provider Interfaces](#provider-interfaces) for a list of interfaces available to provide in this module.

```typescript
provide(capability: string, provider: any): void
```

Parameters:

| Param        | Type     | Required | Summary                                      |
| ------------ | -------- | -------- | -------------------------------------------- |
| `capability` | `string` | Yes      | The capability that is being provided.       |
| `provider`   | `any`    | Yes      | An implementation of the required interface. |

See [Provider Interfaces](#provider-interfaces) for each capabilities interface definition.

### purchasedContent

Return content purchased by the user, such as rentals and electronic sell through purchases.

The app should return the user's 100 most recent purchases in `entries`. The total count of purchases must be provided in `count`. If `count` is greater than the total number of `entries`, the UI may provide a link into the app to see the complete purchase list.

The `EntityInfo` object returned is not required to have `waysToWatch` populated, but it is recommended that it do so in case the UI wants to surface additional information on the purchases screen.

The app should implement both Push and Pull methods for `purchasedContent`.

The app should actively push `purchasedContent` when:

- The app becomes Active.
- When the state of the purchasedContent set has changed.
- The app goes into Inactive or Background state, if there is a chance a change event has been missed.

To allow the platform to pull data, use `purchasedContent(callback: Function)`:

```typescript
function purchasedContent(
  callback: (parameters: PurchasedContentParameters) => Promise<>,
): Promise<boolean>
```

Parameters:

| Param      | Type       | Required | Summary                                     |
| ---------- | ---------- | -------- | ------------------------------------------- |
| `callback` | `Function` | Yes      | A callback for the platform to pull objects |

Callback parameters:

| Param        | Type                         | Required | Summary                                                     |
| ------------ | ---------------------------- | -------- | ----------------------------------------------------------- |
| `parameters` | `PurchasedContentParameters` | Yes      | An object describing the platform's query for an `` object. |

````typescript
```typescript

````

````

Callback promise resolution:

```typescript
```typescript

````

````



#### Examples


Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.purchasedContent(async parameters => {
  console.log(parameters.entityId)
  console.log(parameters.assetId)
  return {
          	"totalCount": 10,
          	"expires": "2025-01-01T00:00:00.000Z",
          	"entries": [
          		{
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
          	]
          }
})
console.log(success)
````

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPullPurchasedContent",
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
    "correlationId": "xyz",
    "parameters": {
      "limit": 100
    }
  }
}
```

Push Request:

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "Discovery.purchasedContent",
  "params": {
    "correlationId": "TBD",
    "result": {
      "totalCount": 10,
      "expires": "2025-01-01T00:00:00.000Z",
      "entries": [
        {
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
      ]
    }
  }
}
```

</details>

To push data to the platform, e.g. during app launch, use `purchasedContent(result: )`:

```typescript
function purchasedContent(result: ): Promise<boolean>
```

Parameters:

| Param    | Type | Required | Summary                             |
| -------- | ---- | -------- | ----------------------------------- |
| `result` | ``   | Yes      | The `` data to push to the platform |

````typescript
```typescript

````

````

See also: [PurchasedContent](#purchasedcontent-1)

Promise resolution:

| Type | Summary |
| ---- | ------- |
| `boolean` | Whether or not the push was successful |

#### Examples


Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.purchasedContent({
                                                	"totalCount": 10,
                                                	"expires": "2025-01-01T00:00:00.000Z",
                                                	"entries": [
                                                		{
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
                                                	]
                                                })
console.log(success)
````

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.purchasedContent",
  "params": {
    "correlationId": null,
    "result": {
      "totalCount": 10,
      "expires": "2025-01-01T00:00:00.000Z",
      "entries": [
        {
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
      ]
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### purchases

Provide a list of purchased content for the authenticated account, such as rentals and electronic sell through purchases.

```typescript
${method.signature}
```

Parameters:

| Param       | Type | Required | Description                       |
| ----------- | ---- | -------- | --------------------------------- |
| `purchases` | ``   | true     | The data for the purchasedContent |

Promise resolution:

```typescript

```

Capabilities:

| Role     | Capability                                          |
| -------- | --------------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:purchased-content |

#### Examples

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.purchases({
  totalCount: 10,
  expires: '2025-01-01T00:00:00.000Z',
  entries: [
    {
      identifiers: {
        entityId: '345',
        entityType: 'program',
        programType: 'movie',
      },
      info: {
        title: 'Cool Runnings',
        synopsis:
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
        releaseDate: '1993-01-01T00:00:00.000Z',
        contentRatings: [
          {
            scheme: 'US-Movie',
            rating: 'PG',
          },
          {
            scheme: 'CA-Movie',
            rating: 'G',
          },
        ],
      },
      waysToWatch: [
        {
          identifiers: {
            assetId: '123',
          },
          expires: '2025-01-01T00:00:00.000Z',
          entitled: true,
          entitledExpires: '2025-01-01T00:00:00.000Z',
          offeringType: 'buy',
          price: 2.99,
          videoQuality: ['UHD'],
          audioProfile: ['dolbyAtmos'],
          audioLanguages: ['en'],
          closedCaptions: ['en'],
          subtitles: ['es'],
          audioDescriptions: ['en'],
        },
      ],
    },
  ],
})
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
  "method": "Discovery.purchases",
  "params": {
    "purchases": {
      "totalCount": 10,
      "expires": "2025-01-01T00:00:00.000Z",
      "entries": [
        {
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
          },
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
      ]
    }
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

### signIn

Inform the platform that your user is signed in, for increased visibility in search & discovery. Sign-in state is used separately from what content can be access through entitlements and availabilities. Sign-in state may be used when deciding whether to choose this app to handle a user intent. For instance, if the user tries to launch something generic like playing music from an artist, only a signed-in app will be chosen. If the user wants to tune to a channel, only a signed-in app will be chosen to handle that intent. While signIn can optionally include entitlements as those typically change at signIn time, it is recommended to make a separate call to Discovery.contentAccess for entitlements. signIn is not only for when a user explicitly enters login credentials. If an app does not require any credentials from the user to consume content, such as in a free app, then the app should call signIn immediately on launch.

```typescript
${method.signature}
```

Parameters:

| Param          | Type | Required | Description                                                                                             |
| -------------- | ---- | -------- | ------------------------------------------------------------------------------------------------------- |
| `entitlements` | ``   | false    | Optional array of Entitlements, in case of a different user account, or a long time since last sign-in. |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:sign-in-status |

#### Examples

Send signIn metric

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.signIn(null)
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.signIn",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Send signIn notification with entitlements

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.signIn([
  {
    entitlementId: '123',
    startTime: '2025-01-01T00:00:00.000Z',
    endTime: '2025-01-01T00:00:00.000Z',
  },
])
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.signIn",
  "params": {
    "entitlements": [
      {
        "entitlementId": "123",
        "startTime": "2025-01-01T00:00:00.000Z",
        "endTime": "2025-01-01T00:00:00.000Z"
      }
    ]
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### signOut

Inform the platform that your user has signed out. See `Discovery.signIn` for more details on how the sign-in state is used.signOut will NOT clear entitlements, the app should make a separate call to Discovery.clearContentAccess. Apps should also call signOut when a login token has expired and the user is now in a signed-out state.

```typescript
${method.signature}
```

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:sign-in-status |

#### Examples

Send signOut notification

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.signOut()
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.signOut",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### userInterest

Provide information about the entity currently displayed or selected on the screen.

```typescript
${method.signature}
```

Parameters:

| Param    | Type | Required | Description                                       |
| -------- | ---- | -------- | ------------------------------------------------- |
| `type`   | ``   | true     | values: `'interest' \| 'disinterest'`             |
| `reason` | ``   | true     | values: `'playlist' \| 'reaction' \| 'recording'` |
| `entity` | ``   | true     | The EntityDetails data.                           |

Promise resolution:

```typescript

```

Capabilities:

| Role     | Capability                                      |
| -------- | ----------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:user-interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.userInterest('interest', 'playlist', {
  identifiers: {
    entityId: '345',
    entityType: 'program',
    programType: 'movie',
  },
  info: {
    title: 'Cool Runnings',
    synopsis:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
    releaseDate: '1993-01-01T00:00:00.000Z',
    contentRatings: [
      {
        scheme: 'US-Movie',
        rating: 'PG',
      },
      {
        scheme: 'CA-Movie',
        rating: 'G',
      },
    ],
  },
})
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
  "method": "Discovery.userInterest",
  "params": {
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

### watched

Notify the platform that content was partially or completely watched

```typescript
${method.signature}
```

Parameters:

| Param       | Type      | Required | Description                                                                                                      |
| ----------- | --------- | -------- | ---------------------------------------------------------------------------------------------------------------- |
| `entityId`  | `string`  | true     | The entity Id of the watched content.                                                                            |
| `progress`  | `number`  | false    | How much of the content has been watched (percentage as 0-1 for VOD, number of seconds for live) <br/>minumum: 0 |
| `completed` | `boolean` | false    | Whether or not this viewing is considered "complete," per the app's definition thereof                           |
| `watchedOn` | `string`  | false    | Date/Time the content was watched, ISO 8601 Date/Time <br/>format: date-time                                     |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:discovery:watched |

#### Examples

Notifying the platform of watched content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.watched(
  'partner.com/entity/123',
  0.95,
  true,
  '2021-04-23T18:25:43.511Z',
)
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.watched",
  "params": {
    "entityId": "partner.com/entity/123",
    "progress": 0.95,
    "completed": true,
    "watchedOn": "2021-04-23T18:25:43.511Z"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

### watchNext

Suggest a call-to-action for this app on the platform home screen

```typescript
${method.signature}
```

Parameters:

| Param         | Type                    | Required                                | Description                                                                            |
| ------------- | ----------------------- | --------------------------------------- | -------------------------------------------------------------------------------------- | ----------- |
| `title`       | ``                      | true                                    | The title of this call to action                                                       |
| `identifiers` | ``                      | true                                    | A set of content identifiers for this call to action                                   |
| `expires`     | `string`                | false                                   | When this call to action should no longer be presented to users <br/>format: date-time |
| `images`      | [`                      | Property                                | Type                                                                                   | Description |
| ----------    | ------                  | -------------                           |
| `${property}` | [${type}](${type.link}) | ${description}                          |
| `](#)         | false                   | A set of images for this call to action |

Promise resolution:

```typescript
boolean
```

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:watch-next |

#### Examples

Suggest a watch-next tile for the home screen

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.watchNext(
  'A Cool Show',
  {
    entityId: 'partner.com/entity/123',
  },
  '2021-04-23T18:25:43.511Z',
  {
    '3x4': {
      'en-US': 'https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg',
      es: 'https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg',
    },
    '16x9': {
      en: 'https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg',
    },
  },
)
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.watchNext",
  "params": {
    "title": "A Cool Show",
    "identifiers": {
      "entityId": "partner.com/entity/123"
    },
    "expires": "2021-04-23T18:25:43.511Z",
    "images": {
      "3x4": {
        "en-US": "https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg",
        "es": "https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg"
      },
      "16x9": {
        "en": "https://i.ytimg.com/vi/4r7wHMg5Yjg/maxresdefault.jpg"
      }
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

Suggest a watch-next tile for the home screen

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.watchNext(
  'A Fantastic Show',
  { entityId: 'partner.com/entity/456' },
  null,
  null,
)
console.log(success)
```

Value of `success`:

```javascript
true
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.watchNext",
  "params": {
    "title": "A Fantastic Show",
    "identifiers": {
      "entityId": "partner.com/entity/456"
    }
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": true
}
```

</details>

---

## Events

### navigateTo

```typescript
function listen('navigateTo', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

```typescript

```

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:navigate-to |

#### Examples

Listening for `navigateTo` events

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

Discovery.listen('navigateTo', (value) => {
  console.log(value)
})
```

Value of `value`:

```javascript
{
	"action": "search",
	"data": {
		"query": "a cool show"
	},
	"context": {
		"campaign": "unknown",
		"source": "voice"
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
  "method": "Discovery.onNavigateTo",
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
    "action": "search",
    "data": {
      "query": "a cool show"
    },
    "context": {
      "campaign": "unknown",
      "source": "voice"
    }
  }
}
```

</details>

---

### policyChanged

See: [policy](#policy)

### requestDetails

```typescript
function listen('requestDetails', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

| Property        | Type   | Description |
| --------------- | ------ | ----------- |
| `correlationId` | string |             |
| `parameters`    |        |             |

Capabilities:

| Role     | Capability                                    |
| -------- | --------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:entity-info |

#### Examples

Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

Discovery.listen('requestDetails', (request) => {
  console.log(request)
})
```

Value of `request`:

```javascript
{
	"correlationId": "xyz",
	"parameters": {
		"entityId": "345"
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
  "method": "Discovery.onRequestDetails",
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
    "correlationId": "xyz",
    "parameters": {
      "entityId": "345"
    }
  }
}
```

</details>

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

Discovery.listen('requestDetails', (request) => {
  console.log(request)
})
```

Value of `request`:

```javascript
{
	"correlationId": "xyz",
	"parameters": {
		"entityId": "345"
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
  "method": "Discovery.onRequestDetails",
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
    "correlationId": "xyz",
    "parameters": {
      "entityId": "345"
    }
  }
}
```

</details>

---

### requestPurchases

```typescript
function listen('requestPurchases', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

| Property        | Type   | Description |
| --------------- | ------ | ----------- |
| `correlationId` | string |             |
| `parameters`    |        |             |

Capabilities:

| Role     | Capability                                          |
| -------- | --------------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:purchased-content |

#### Examples

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

Discovery.listen('requestPurchases', (request) => {
  console.log(request)
})
```

Value of `request`:

```javascript
{
	"correlationId": "xyz",
	"parameters": {}
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onRequestPurchases",
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
    "correlationId": "xyz",
    "parameters": {}
  }
}
```

</details>

---

### requestUserInterest

```typescript
function listen('requestUserInterest', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

| Property        | Type   | Description |
| --------------- | ------ | ----------- |
| `correlationId` | string |             |
| `parameters`    |        |             |

Capabilities:

| Role     | Capability                                      |
| -------- | ----------------------------------------------- |
| provides | xrn:firebolt:capability:discovery:user-interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

Discovery.listen('requestUserInterest', (request) => {
  console.log(request)
})
```

Value of `request`:

```javascript
{
	"correlationId": "xyz",
	"parameters": {
		"type": "interest",
		"reason": "playlist"
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
  "method": "Discovery.onRequestUserInterest",
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
    "correlationId": "xyz",
    "parameters": {
      "type": "interest",
      "reason": "playlist"
    }
  }
}
```

</details>

---

## Provider Interfaces

### DetailsProvider

The provider interface for the `xrn:firebolt:capability:discovery:entity-info` capability.

```typescript

```

Usage:

```typescript
Discovery.provide('xrn:firebolt:capability:discovery:entity-info', provider: DetailsProvider | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:discovery:entity-info` capability.**

```javascript
import { Discovery } from '@firebolt-js/sdk'

class MyDetailsProvider {
  async details(parameters, session) {
    return {
      expires: '2025-01-01T00:00:00.000Z',
      details: {
        identifiers: {
          entityId: '345',
          entityType: 'program',
          programType: 'movie',
        },
        info: {
          title: 'Cool Runnings',
          synopsis:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
          releaseDate: '1993-01-01T00:00:00.000Z',
          contentRatings: [
            {
              scheme: 'US-Movie',
              rating: 'PG',
            },
            {
              scheme: 'CA-Movie',
              rating: 'G',
            },
          ],
        },
        waysToWatch: [
          {
            identifiers: {
              assetId: '123',
            },
            expires: '2025-01-01T00:00:00.000Z',
            entitled: true,
            entitledExpires: '2025-01-01T00:00:00.000Z',
            offeringType: 'buy',
            price: 2.99,
            videoQuality: ['UHD'],
            audioProfile: ['dolbyAtmos'],
            audioLanguages: ['en'],
            closedCaptions: ['en'],
            subtitles: ['es'],
            audioDescriptions: ['en'],
          },
        ],
      },
    }
  }
}

Discovery.provide(
  'xrn:firebolt:capability:discovery:entity-info',
  new MyDetailsProvider(),
)
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "Discovery.onRequestDetails",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "id": 1,
  "result": {
    "listening": true,
    "event": "Discovery.onRequestDetails"
  }
}
```

**Asynchronous event to initiate details()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": undefined,
    "parameters": {
      "entityId": "345"
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "Discovery.detailsResponse",
  "params": {
    "correlationId": undefined,
    "result": {
      "expires": "2025-01-01T00:00:00.000Z",
      "details": {
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
        },
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

Response:

```json
{
  "id": 2,
  "result": true
}
```

</details>

### PurchasesProvider

The provider interface for the `xrn:firebolt:capability:discovery:purchased-content` capability.

```typescript

```

Usage:

```typescript
Discovery.provide('xrn:firebolt:capability:discovery:purchased-content', provider: PurchasesProvider | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:discovery:purchased-content` capability.**

```javascript
import { Discovery } from '@firebolt-js/sdk'

class MyPurchasesProvider {
  async purchases(parameters, session) {
    return {
      totalCount: 10,
      expires: '2025-01-01T00:00:00.000Z',
      entries: [
        {
          identifiers: {
            entityId: '345',
            entityType: 'program',
            programType: 'movie',
          },
          info: {
            title: 'Cool Runnings',
            synopsis:
              'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
            releaseDate: '1993-01-01T00:00:00.000Z',
            contentRatings: [
              {
                scheme: 'US-Movie',
                rating: 'PG',
              },
              {
                scheme: 'CA-Movie',
                rating: 'G',
              },
            ],
          },
          waysToWatch: [
            {
              identifiers: {
                assetId: '123',
              },
              expires: '2025-01-01T00:00:00.000Z',
              entitled: true,
              entitledExpires: '2025-01-01T00:00:00.000Z',
              offeringType: 'buy',
              price: 2.99,
              videoQuality: ['UHD'],
              audioProfile: ['dolbyAtmos'],
              audioLanguages: ['en'],
              closedCaptions: ['en'],
              subtitles: ['es'],
              audioDescriptions: ['en'],
            },
          ],
        },
      ],
    }
  }
}

Discovery.provide(
  'xrn:firebolt:capability:discovery:purchased-content',
  new MyPurchasesProvider(),
)
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "Discovery.onRequestPurchases",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "id": 1,
  "result": {
    "listening": true,
    "event": "Discovery.onRequestPurchases"
  }
}
```

**Asynchronous event to initiate purchases()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": undefined,
    "parameters": {}
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "Discovery.purchasesResponse",
  "params": {
    "correlationId": undefined,
    "result": {
      "totalCount": 10,
      "expires": "2025-01-01T00:00:00.000Z",
      "entries": [
        {
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
          },
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
      ]
    }
  }
}
```

Response:

```json
{
  "id": 2,
  "result": true
}
```

</details>

### UserInterestProvider

The provider interface for the `xrn:firebolt:capability:discovery:user-interest` capability.

```typescript

```

Usage:

```typescript
Discovery.provide('xrn:firebolt:capability:discovery:user-interest', provider: UserInterestProvider | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:discovery:user-interest` capability.**

```javascript
import { Discovery } from '@firebolt-js/sdk'

class MyUserInterestProvider {
  async userInterest(parameters, session) {
    return {
      identifiers: {
        entityId: '345',
        entityType: 'program',
        programType: 'movie',
      },
      info: {
        title: 'Cool Runnings',
        synopsis:
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
        releaseDate: '1993-01-01T00:00:00.000Z',
        contentRatings: [
          {
            scheme: 'US-Movie',
            rating: 'PG',
          },
          {
            scheme: 'CA-Movie',
            rating: 'G',
          },
        ],
      },
    }
  }
}

Discovery.provide(
  'xrn:firebolt:capability:discovery:user-interest',
  new MyUserInterestProvider(),
)
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "Discovery.onRequestUserInterest",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "id": 1,
  "result": {
    "listening": true,
    "event": "Discovery.onRequestUserInterest"
  }
}
```

**Asynchronous event to initiate userInterest()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": undefined,
    "parameters": {
      "type": "interest",
      "reason": "playlist"
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "Discovery.userInterestResponse",
  "params": {
    "correlationId": undefined,
    "result": {
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

Response:

```json
{
  "id": 2,
  "result": true
}
```

</details>

## Types

### DetailsProviderParameters

````typescript
```typescript

````

````



---

### PurchasesProviderParameters



```typescript
```typescript

````

````



---

### UserInterestProviderParameters



```typescript
```typescript

````

````

See also:




---

### DiscoveryPolicy



```typescript
```typescript

````

````



---

### Availability



```typescript
```typescript

````

````



---

### PurchasedContentParameters



```typescript
```typescript

````

````

See also:




---

### ContentAccessIdentifiers



```typescript
```typescript

````

````

See also:




---

### EntityInfoParameters



```typescript
```typescript

````

````



---

### EntityInfoFederatedRequest



```typescript
```typescript

````

````

See also:




---

### PurchasedContentFederatedRequest



```typescript
```typescript

````

```

See also:




---
```
