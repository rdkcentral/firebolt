---
title: Discovery

version: next-major
layout: default
sdk: core
---

# Discovery Module

---

Version Discovery 1.8.0-next-major.3

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
  - [Localization](#localization)
- [Methods](#methods)
  - [clearContentAccess](#clearcontentaccess)
  - [contentAccess](#contentaccess)
  - [entitlements](#entitlements)
  - [entityInfo](#entityinfo)
  - [launch](#launch)
  - [listen](#listen)
  - [once](#once)
  - [policy](#policy)
  - [provide](#provide)
  - [purchasedContent](#purchasedcontent)
  - [signIn](#signin)
  - [signOut](#signout)
  - [userInterest](#userinterest)
  - [watched](#watched)
  - [watchNext](#watchnext)
- [Events](#events)
  - [onEntityInfoChanged](#onentityinfochanged)
  - [onNavigateTo](#onnavigateto)
  - [onPolicyChanged](#onpolicychanged)
  - [onPurchasedContentChanged](#onpurchasedcontentchanged)
- [Private Events](#private-events)
- [Provider Interfaces](#provider-interfaces)
  - [Discovery](#discovery)
- [Types](#types)
  - [DiscoveryPolicy](#discoverypolicy)
  - [EntityInfoResult](#entityinforesult)
  - [PurchasedContentResult](#purchasedcontentresult)
  - [Availability](#availability)
  - [ContentAccessIdentifiers](#contentaccessidentifiers)

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
function clearContentAccess(): Promise<void>
```

Promise resolution:

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
function contentAccess(ids: ContentAccessIdentifiers): Promise<void>
```

Parameters:

| Param | Type                                                    | Required | Description                                                                                        |
| ----- | ------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------- |
| `ids` | [`ContentAccessIdentifiers`](#contentaccessidentifiers) | true     | A list of identifiers that represent content that is discoverable or consumable for the subscriber |

Promise resolution:

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

### entitlements

[Deprecated] This method is deprecated as of since version 0.10.0. Please use `contentAccess` as a replacement.

```typescript
function entitlements(
  entitlements: Entertainment.Entitlement[],
): Promise<boolean>
```

---

### entityInfo

Provide information about a program entity and its available watchable assets, such as entitlement status and price, via either a push or pull call flow. Includes information about the program entity and its relevant associated entities, such as extras, previews, and, in the case of TV series, seasons and episodes.

See the `EntityInfo` and `WayToWatch` data structures below for more information.

The app only needs to implement Pull support for `entityInfo` at this time.

To get the value of `entityInfo` call the method like this:

```typescript
function entityInfo(
  entityId: string,
  assedId: string,
): Promise<EntityInfoResult>
```

Parameters:

| Param      | Type     | Required | Description |
| ---------- | -------- | -------- | ----------- |
| `entityId` | `string` | true     |             |
| `assedId`  | `string` | true     |             |

Promise resolution:

[EntityInfoResult](#entityinforesult)

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:entity-info |

#### Examples

Entity info for a movie.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.entityInfo('id-123', 'asseId-123')
console.log(result)
```

Value of `result`:

```javascript
{"expires":"2025-01-01T00:00:00.000Z","entity":{"identifiers":{"entityId":"345"},"entityType":"program","programType":"movie","title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}],"waysToWatch":[{"identifiers":{"assetId":"123"},"expires":"2025-01-01T00:00:00.000Z","entitled":true,"entitledExpires":"2025-01-01T00:00:00.000Z","offeringType":"buy","price":2.99,"videoQuality":["UHD"],"audioProfile":["dolbyAtmos"],"audioLanguages":["en"],"closedCaptions":["en"],"subtitles":["es"],"audioDescriptions":["en"]}]}}
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
    "entityId": "id-123",
    "assedId": "asseId-123"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
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
```

</details>

Entity info for a movie with a trailer.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.entityInfo('id-1234', 'asseId-1234')
console.log(result)
```

Value of `result`:

```javascript
{"expires":"2025-01-01T00:00:00.000Z","entity":{"identifiers":{"entityId":"345"},"entityType":"program","programType":"movie","title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}],"waysToWatch":[{"identifiers":{"assetId":"123"},"expires":"2025-01-01T00:00:00.000Z","entitled":true,"entitledExpires":"2025-01-01T00:00:00.000Z","offeringType":"buy","price":2.99,"videoQuality":["UHD"],"audioProfile":["dolbyAtmos"],"audioLanguages":["en"],"closedCaptions":["en"],"subtitles":["es"],"audioDescriptions":["en"]}]}}
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
    "entityId": "id-1234",
    "assedId": "asseId-1234"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
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
```

</details>

---

To set the value of `entityInfo` call the method like this:

```typescript
function entityInfo(
  entityId: string,
  assedId: string,
  value: EntityInfoResult,
): Promise<void>
```

Parameters:

| Param      | Type                                    | Required | Description         |
| ---------- | --------------------------------------- | -------- | ------------------- |
| `entityId` | `string`                                | true     |                     |
| `assedId`  | `string`                                | true     |                     |
| `value`    | [`EntityInfoResult`](#entityinforesult) | true     | The entityInfo data |

Promise resolution:

#### Examples

Entity info for a movie.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.entityInfo('id-123', 'asseId-123', {
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
  "method": "Discovery.setEntityInfo",
  "params": {
    "entityId": "id-123",
    "assedId": "asseId-123",
    "value": {
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
  "result": null
}
```

</details>

Entity info for a movie with a trailer.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.entityInfo('id-1234', 'asseId-1234', {
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
  "method": "Discovery.setEntityInfo",
  "params": {
    "entityId": "id-1234",
    "assedId": "asseId-1234",
    "value": {
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
  "result": null
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function entityInfo(
  entityId: string,
  assedId: string,
  callback: (result) => EntityInfoResult,
): Promise<number>
```

| Param      | Type                                    | Required | Description         |
| ---------- | --------------------------------------- | -------- | ------------------- |
| `entityId` | `string`                                | true     |                     |
| `assedId`  | `string`                                | true     |                     |
| `result`   | [`EntityInfoResult`](#entityinforesult) | false    | The entityInfo data |

Promise resolution:

```
number
```

#### Examples

Entity info for a movie.

```typescript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await entityInfo((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"entityId": "id-123",
	"assedId": "asseId-123",
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
  "method": "Discovery.onEntityInfoChanged",
  "params": {
    "entityId": "id-123",
    "assedId": "asseId-123",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Entity info for a movie with a trailer.

```typescript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await entityInfo((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"entityId": "id-123",
	"assedId": "asseId-123",
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
  "method": "Discovery.onEntityInfoChanged",
  "params": {
    "entityId": "id-1234",
    "assedId": "asseId-1234",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### launch

Launch or foreground the specified app, and optionally instructs it to navigate to the specified user action.
For the Primary Experience, the appId can be any one of:

- xrn:firebolt:application-type:main

- xrn:firebolt:application-type:settings

```typescript
function launch(
  appId: string,
  intent: Intents.NavigationIntent,
): Promise<boolean>
```

Parameters:

| Param    | Type                                                               | Required | Description                                                                                                                      |
| -------- | ------------------------------------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `appId`  | `string`                                                           | true     | The durable app Id of the app to launch                                                                                          |
| `intent` | [`Intents.NavigationIntent`](../Intents/schemas/#NavigationIntent) | false    | An optional `NavigationIntent` with details about what part of the app to show first, and context around how/why it was launched |

Promise resolution:

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

Launch the 'Foo' app to it's home screen where the launch intent came from a child-directed browse menu.

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.launch('foo', {
  action: 'home',
  context: { source: 'browse' },
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
        "source": "browse"
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

let success = await Discovery.launch('xrn:firebolt:application-type:settings', {
  action: 'section',
  data: {
    sectionName: 'settings',
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
    "appId": "xrn:firebolt:application-type:settings",
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

Get the discovery policy

To get the value of `policy` call the method like this:

```typescript
function policy(): Promise<DiscoveryPolicy>
```

Promise resolution:

[DiscoveryPolicy](#discoverypolicy)

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:discovery:policy |

#### Examples

Getting the discovery policy

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let policy = await Discovery.policy()
console.log(policy)
```

Value of `policy`:

```javascript
{"enableRecommendations":true,"shareWatchHistory":true,"rememberWatchedPrograms":true}
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
function policy(callback: (policy) => DiscoveryPolicy): Promise<number>
```

| Param    | Type                                  | Required | Description                  |
| -------- | ------------------------------------- | -------- | ---------------------------- |
| `policy` | [`DiscoveryPolicy`](#discoverypolicy) | false    | discovery policy opt-in/outs |

Promise resolution:

```
number
```

#### Examples

Getting the discovery policy

```typescript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await policy((result) => {
  console.log(result)
})
```

Value of `result`:

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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### provide

undefined

```typescript
function provide(enabled: boolean): Promise<null>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | false    |             |

Promise resolution:

Capabilities:

| Role     | Capability                                 |
| -------- | ------------------------------------------ |
| provides | xrn:firebolt:capability:discovery:interest |

#### Examples

Default example

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.provide(true)
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
  "method": "Discovery.provide",
  "params": {
    "enabled": true
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

### purchasedContent

Return content purchased by the user, such as rentals and electronic sell through purchases.

The app should return the user's 100 most recent purchases in `entries`. The total count of purchases must be provided in `count`. If `count` is greater than the total number of `entries`, the UI may provide a link into the app to see the complete purchase list.

The `EntityInfo` object returned is not required to have `waysToWatch` populated, but it is recommended that it do so in case the UI wants to surface additional information on the purchases screen.

The app should implement both Push and Pull methods for `purchasedContent`.

The app should actively push `purchasedContent` when:

- The app becomes Active.
- When the state of the purchasedContent set has changed.
- The app goes into Inactive or Background state, if there is a chance a change event has been missed.

To get the value of `purchasedContent` call the method like this:

```typescript
function purchasedContent(
  offeringType: Entertainment.OfferingType,
  programType: Entertainment.ProgramType,
): Promise<PurchasedContentResult>
```

Parameters:

| Param          | Type                                                                   | Required | Description                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `offeringType` | [`Entertainment.OfferingType`](../Entertainment/schemas/#OfferingType) | true     | <br/>values: `'free' \| 'subscribe' \| 'buy' \| 'rent'`                                                                                                                         |
| `programType`  | [`Entertainment.ProgramType`](../Entertainment/schemas/#ProgramType)   | true     | <br/>values: `'movie' \| 'episode' \| 'season' \| 'series' \| 'other' \| 'preview' \| 'extra' \| 'concert' \| 'sportingEvent' \| 'advertisement' \| 'musicVideo' \| 'minisode'` |

Promise resolution:

[PurchasedContentResult](#purchasedcontentresult)

Capabilities:

| Role | Capability                                          |
| ---- | --------------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:purchased-content |

#### Examples

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.purchasedContent('buy', 'movie')
console.log(result)
```

Value of `result`:

```javascript
{"totalCount":10,"expires":"2025-01-01T00:00:00.000Z","entries":[{"identifiers":{"entityId":"345"},"entityType":"program","programType":"movie","title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}],"waysToWatch":[{"identifiers":{"assetId":"123"},"expires":"2025-01-01T00:00:00.000Z","entitled":true,"entitledExpires":"2025-01-01T00:00:00.000Z","offeringType":"buy","price":2.99,"videoQuality":["UHD"],"audioProfile":["dolbyAtmos"],"audioLanguages":["en"],"closedCaptions":["en"],"subtitles":["es"],"audioDescriptions":["en"]}]}]}
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
    "offeringType": "buy",
    "programType": "movie"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
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
```

</details>

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.purchasedContent('buy', 'movie')
console.log(result)
```

Value of `result`:

```javascript
{"totalCount":10,"expires":"2025-01-01T00:00:00.000Z","entries":[{"identifiers":{"entityId":"345"},"entityType":"program","programType":"movie","title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}],"waysToWatch":[{"identifiers":{"assetId":"123"},"expires":"2025-01-01T00:00:00.000Z","entitled":true,"entitledExpires":"2025-01-01T00:00:00.000Z","offeringType":"buy","price":2.99,"videoQuality":["UHD"],"audioProfile":["dolbyAtmos"],"audioLanguages":["en"],"closedCaptions":["en"],"subtitles":["es"],"audioDescriptions":["en"]}]}]}
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
    "offeringType": "buy",
    "programType": "movie"
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "totalCount": 10,
    "expires": "2025-03-03T00:00:00.000Z",
    "entries": [
      {
        "identifiers": {
          "entityId": "789"
        },
        "entityType": "program",
        "programType": "movie",
        "title": "Cool Runnings",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1995-01-01T00:00:00.000Z",
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
              "assetId": "12345"
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
```

</details>

---

To set the value of `purchasedContent` call the method like this:

```typescript
function purchasedContent(
  offeringType: OfferingType,
  programType: ProgramType,
  value: PurchasedContentResult,
): Promise<void>
```

Parameters:

| Param          | Type                                                                   | Required | Description                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `offeringType` | [`Entertainment.OfferingType`](../Entertainment/schemas/#OfferingType) | true     | <br/>values: `'free' \| 'subscribe' \| 'buy' \| 'rent'`                                                                                                                         |
| `programType`  | [`Entertainment.ProgramType`](../Entertainment/schemas/#ProgramType)   | true     | <br/>values: `'movie' \| 'episode' \| 'season' \| 'series' \| 'other' \| 'preview' \| 'extra' \| 'concert' \| 'sportingEvent' \| 'advertisement' \| 'musicVideo' \| 'minisode'` |
| `value`        | [`PurchasedContentResult`](#purchasedcontentresult)                    | true     | The data for the purchasedContent                                                                                                                                               |

Promise resolution:

#### Examples

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.purchasedContent('buy', 'movie', {
  totalCount: 10,
  expires: '2025-01-01T00:00:00.000Z',
  entries: [
    {
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
  "method": "Discovery.setPurchasedContent",
  "params": {
    "offeringType": "buy",
    "programType": "movie",
    "value": {
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
  "result": null
}
```

</details>

Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let result = await Discovery.purchasedContent('buy', 'movie', {
  totalCount: 10,
  expires: '2025-03-03T00:00:00.000Z',
  entries: [
    {
      identifiers: {
        entityId: '789',
      },
      entityType: 'program',
      programType: 'movie',
      title: 'Cool Runnings',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1995-01-01T00:00:00.000Z',
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
            assetId: '12345',
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
  "method": "Discovery.setPurchasedContent",
  "params": {
    "offeringType": "buy",
    "programType": "movie",
    "value": {
      "totalCount": 10,
      "expires": "2025-03-03T00:00:00.000Z",
      "entries": [
        {
          "identifiers": {
            "entityId": "789"
          },
          "entityType": "program",
          "programType": "movie",
          "title": "Cool Runnings",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1995-01-01T00:00:00.000Z",
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
                "assetId": "12345"
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

To subscribe to notifications when the value changes, call the method like this:

```typescript
function purchasedContent(
  offeringType: OfferingType,
  programType: ProgramType,
  callback: (result) => PurchasedContentResult,
): Promise<number>
```

| Param          | Type                                                                   | Required | Description                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `offeringType` | [`Entertainment.OfferingType`](../Entertainment/schemas/#OfferingType) | true     | <br/>values: `'free' \| 'subscribe' \| 'buy' \| 'rent'`                                                                                                                         |
| `programType`  | [`Entertainment.ProgramType`](../Entertainment/schemas/#ProgramType)   | true     | <br/>values: `'movie' \| 'episode' \| 'season' \| 'series' \| 'other' \| 'preview' \| 'extra' \| 'concert' \| 'sportingEvent' \| 'advertisement' \| 'musicVideo' \| 'minisode'` |
| `result`       | [`PurchasedContentResult`](#purchasedcontentresult)                    | true     | The data for the purchasedContent                                                                                                                                               |

Promise resolution:

```
number
```

#### Examples

Inform the platform of the user's purchased content

```typescript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await purchasedContent((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"offeringType": "buy",
	"programType": "movie",
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
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPurchasedContentChanged",
  "params": {
    "offeringType": "buy",
    "programType": "movie",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

Inform the platform of the user's purchased content

```typescript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await purchasedContent((result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"offeringType": "buy",
	"programType": "movie",
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
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Discovery.onPurchasedContentChanged",
  "params": {
    "offeringType": "buy",
    "programType": "movie",
    "listen": true
  }
}
```

Response:

```json
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### signIn

Inform the platform that your user is signed in, for increased visibility in search & discovery. Sign-in state is used separately from what content can be access through entitlements and availabilities. Sign-in state may be used when deciding whether to choose this app to handle a user intent. For instance, if the user tries to launch something generic like playing music from an artist, only a signed-in app will be chosen. If the user wants to tune to a channel, only a signed-in app will be chosen to handle that intent. While signIn can optionally include entitlements as those typically change at signIn time, it is recommended to make a separate call to Discovery.contentAccess for entitlements. signIn is not only for when a user explicitly enters login credentials. If an app does not require any credentials from the user to consume content, such as in a free app, then the app should call signIn immediately on launch.

```typescript
function signIn(entitlements: Entertainment.Entitlement[]): Promise<boolean>
```

Parameters:

| Param          | Type                          | Required | Description                                                                                             |
| -------------- | ----------------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `entitlements` | `Entertainment.Entitlement[]` | false    | Optional array of Entitlements, in case of a different user account, or a long time since last sign-in. |

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:sign-in-status |

#### Examples

Send signIn metric

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.signIn()
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
function signOut(): Promise<boolean>
```

Promise resolution:

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

Send an entity that the user has expressed interest in to the platform.

```typescript
function userInterest(
  type: InterestType,
  reason: InterestReason,
  entity: Entity.EntityDetails,
): Promise<null>
```

Parameters:

| Param    | Type                                                       | Required | Description                                            |
| -------- | ---------------------------------------------------------- | -------- | ------------------------------------------------------ |
| `type`   | [`InterestType`](../Discovery/schemas/#InterestType)       | true     | <br/>values: `'interest' \| 'disinterest'`             |
| `reason` | [`InterestReason`](../Discovery/schemas/#InterestReason)   | true     | <br/>values: `'playlist' \| 'reaction' \| 'recording'` |
| `entity` | [`Entity.EntityDetails`](../Entity/schemas/#EntityDetails) | true     |                                                        |

Promise resolution:

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

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
function watched(
  entityId: string,
  progress: number,
  completed: boolean,
  watchedOn: string,
  agePolicy: Policies.AgePolicy,
): Promise<boolean>
```

Parameters:

| Param       | Type                                                   | Required | Description                                                                                                            |
| ----------- | ------------------------------------------------------ | -------- | ---------------------------------------------------------------------------------------------------------------------- |
| `entityId`  | `string`                                               | true     | The entity Id of the watched content.                                                                                  |
| `progress`  | `number`                                               | false    | How much of the content has been watched (percentage as (0-0.999) for VOD, number of seconds for live) <br/>minumum: 0 |
| `completed` | `boolean`                                              | false    | Whether or not this viewing is considered "complete," per the app's definition thereof                                 |
| `watchedOn` | `string`                                               | false    | Date/Time the content was watched, ISO 8601 Date/Time <br/>format: date-time                                           |
| `agePolicy` | [`Policies.AgePolicy`](../Policies/schemas/#AgePolicy) | false    |                                                                                                                        |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:discovery:watched |

#### Examples

Notify the platform of watched content

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

Notify the platform that child-directed content was watched

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let success = await Discovery.watched(
  'partner.com/entity/123',
  0.95,
  true,
  '2021-04-23T18:25:43.511Z',
  'app:child',
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
    "watchedOn": "2021-04-23T18:25:43.511Z",
    "agePolicy": "app:child"
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
function watchNext(
  title: Types.LocalizedString,
  identifiers: Entertainment.ContentIdentifiers,
  expires: string,
  images: object,
): Promise<boolean>
```

Parameters:

| Param         | Type                                                                               | Required | Description                                                                            |
| ------------- | ---------------------------------------------------------------------------------- | -------- | -------------------------------------------------------------------------------------- |
| `title`       | [`Types.LocalizedString`](../Types/schemas/#LocalizedString)                       | true     | The title of this call to action                                                       |
| `identifiers` | [`Entertainment.ContentIdentifiers`](../Entertainment/schemas/#ContentIdentifiers) | true     | A set of content identifiers for this call to action                                   |
| `expires`     | `string`                                                                           | false    | When this call to action should no longer be presented to users <br/>format: date-time |
| `images`      | `object`                                                                           | false    | A set of images for this call to action                                                |

Promise resolution:

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
  undefined,
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

### onEntityInfoChanged

See: [entityInfo](#entityinfo)

### onNavigateTo

```typescript
function listen('onNavigateTo', (NavigationIntent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                                               | Required | Description                                                           |
| ------- | ------------------------------------------------------------------ | -------- | --------------------------------------------------------------------- |
| `value` | [`Intents.NavigationIntent`](../Intents/schemas/#NavigationIntent) | false    | An object describing where in the app the user intends to navigate to |

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:navigate-to |

#### Examples

Listening for `navigateTo` events

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await Discovery.listen('onNavigateTo', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"event": {
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onPolicyChanged

See: [policy](#policy)

### onPurchasedContentChanged

See: [purchasedContent](#purchasedcontent)

## Private Events

### onEntityInfoChanged

See: [entityInfo](#entityinfo)

### onNavigateTo

```typescript
function listen('onNavigateTo', (NavigationIntent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

| Param   | Type                                                               | Required | Description                                                           |
| ------- | ------------------------------------------------------------------ | -------- | --------------------------------------------------------------------- |
| `value` | [`Intents.NavigationIntent`](../Intents/schemas/#NavigationIntent) | false    | An object describing where in the app the user intends to navigate to |

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:navigate-to |

#### Examples

Listening for `navigateTo` events

JavaScript:

```javascript
import { Discovery } from '@firebolt-js/sdk'

let listenerId = await Discovery.listen('onNavigateTo', (result) => {
  console.log(result)
})
```

Value of `result`:

```javascript
{
	"event": {
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
{ "jsonrpc": "2.0", "id": 1, "result": null }
```

</details>

---

### onPolicyChanged

See: [policy](#policy)

### onPurchasedContentChanged

See: [purchasedContent](#purchasedcontent)

## Provider Interfaces

### Discovery

The provider interface for the `xrn:firebolt:capability:discovery:interest` capability.

```typescript
interface Discovery {
  requestUserInterest(
    type: InterestType,
    reason: InterestReason,
    session: ProviderSession,
  ): Promise<InterestResult>
  entityInfo(
    entityId: string,
    assedId: string,
    session: ProviderSession,
  ): Promise<EntityInfoResult>
  purchasedContent(
    offeringType: OfferingType,
    programType: ProgramType,
    session: ProviderSession,
  ): Promise<PurchasedContentResult>
  userInterest(
    type: InterestType,
    reason: InterestReason,
    entity: EntityDetails,
    session: ProviderSession,
  ): Promise<null>
}
```

Usage:

```typescript
Discovery.provide('xrn:firebolt:capability:discovery:interest', provider: Discovery | object)
```

#### Examples

**Register your app to provide the `xrn:firebolt:capability:discovery:interest` capability.**

```javascript
import { Discovery } from '@firebolt-js/sdk'

class MyDiscovery {

    async Discovery.requestUserInterest(parameters, session) {
        ${if.provider.interface.example.result}return {
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
        }${end.if.provider.interface.example.result}
    }

    async Discovery.entityInfo(parameters, session) {
        ${if.provider.interface.example.result}return {
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
        }${end.if.provider.interface.example.result}
    }

    async Discovery.purchasedContent(parameters, session) {
        ${if.provider.interface.example.result}return {
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
        }${end.if.provider.interface.example.result}
    }

    async Discovery.userInterest(parameters, session) {
        ${if.provider.interface.example.result}return null${end.if.provider.interface.example.result}
    }

}

Discovery.provide('xrn:firebolt:capability:discovery:interest', new MyDiscovery())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Discovery.onRequestDiscovery.requestUserInterest",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Discovery.onRequestDiscovery.entityInfo",
    "params": {
        "listen": true
    }
}

{
    "id": 3,
    "method": "Discovery.onRequestDiscovery.purchasedContent",
    "params": {
        "listen": true
    }
}

{
    "id": 4,
    "method": "Discovery.onRequestDiscovery.userInterest",
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
        "event": "Discovery.onRequestDiscovery.requestUserInterest"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Discovery.onRequestDiscovery.entityInfo"
    }

}

{
    "id": 3,
    "result": {
        "listening": true,
        "event": "Discovery.onRequestDiscovery.purchasedContent"
    }

}

{
    "id": 4,
    "result": {
        "listening": true,
        "event": "Discovery.onRequestDiscovery.userInterest"
    }

}

```

**Asynchronous event to initiate Discovery.requestUserInterest()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": "interest"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 5,
  "method": "Discovery.Discovery.requestUserInterestResponse",
  "params": {
    "correlationId": "",
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
}
```

Response:

```json
{
  "id": 5,
  "result": true
}
```

**Asynchronous event to initiate Discovery.entityInfo()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "",
    "parameters": "id-123"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 6,
  "method": "Discovery.Discovery.entityInfoResponse",
  "params": {
    "correlationId": "",
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
  "id": 6,
  "result": true
}
```

**Asynchronous event to initiate Discovery.purchasedContent()**

Event Response:

```json
{
  "id": 3,
  "result": {
    "correlationId": "",
    "parameters": "buy"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 7,
  "method": "Discovery.Discovery.purchasedContentResponse",
  "params": {
    "correlationId": "",
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
  "id": 7,
  "result": true
}
```

**Asynchronous event to initiate Discovery.userInterest()**

Event Response:

```json
{
  "id": 4,
  "result": {
    "correlationId": "",
    "parameters": "interest"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 8,
  "method": "Discovery.Discovery.userInterestResponse",
  "params": {
    "correlationId": "",
    "result": null
  }
}
```

Response:

```json
{
  "id": 8,
  "result": true
}
```

</details>

## Types

### DiscoveryPolicy

```typescript
type DiscoveryPolicy = {
  enableRecommendations: boolean // Whether or not to the user has enabled history-based recommendations
  shareWatchHistory: boolean // Whether or not the user has enabled app watch history data to be shared with the platform
  rememberWatchedPrograms: boolean // Whether or not the user has enabled watch history
}
```

---

### EntityInfoResult

The result for an `entityInfo()` push or pull.

```typescript
type EntityInfoResult = {
  expires: string
  entity: EntityInfo // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
  related?: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[Entertainment.EntityInfo](../Entertainment/schemas/#EntityInfo)

---

### PurchasedContentResult

```typescript
type PurchasedContentResult = {
  expires: string
  totalCount: number
  entries: EntityInfo[] // An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.
}
```

See also:

[Entertainment.EntityInfo](../Entertainment/schemas/#EntityInfo)

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

### ContentAccessIdentifiers

```typescript
type ContentAccessIdentifiers = {
  availabilities?: Availability[] // A list of identifiers that represent what content is discoverable for the subscriber. Excluding availabilities will cause no change to the availabilities that are stored for this subscriber. Providing an empty array will clear the subscriber's availabilities
  entitlements?: Entitlement[] // A list of identifiers that represent what content is consumable for the subscriber. Excluding entitlements will cause no change to the entitlements that are stored for this subscriber. Providing an empty array will clear the subscriber's entitlements
}
```

See also:

[Availability](#availability)
[Entertainment.Entitlement](../Entertainment/schemas/#Entitlement)

---
