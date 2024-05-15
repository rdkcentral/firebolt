---
title: Content

version: pr-feature-user-interest
layout: default
sdk: discovery
---

# Content Module

---

Version Content 1.2.0-feature-user-interest.1

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [requestDetails](#requestdetails)
  - [requestPurchases](#requestpurchases)
  - [requestUserInterest](#requestuserinterest)
- [Events](#events)
  - [details](#details)
  - [purchases](#purchases)
  - [userInterest](#userinterest)
- [Types](#types)
  - [DetailsInfo](#detailsinfo)

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

### requestDetails

Provide information about a program entity and its available watchable assets, such as entitlement status and price, via either a push or pull call flow.

```typescript
${method.signature}
```

Parameters:

| Param      | Type     | Required | Description |
| ---------- | -------- | -------- | ----------- |
| `entityId` | `string` | true     |             |

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:entity-info |


#### Examples


Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let details = await Content.requestDetails("345")
console.log(details)
````

Value of `details`:

```javascript
{
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
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.requestDetails",
  "params": {
    "entityId": "345"
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
```

</details>

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let details = await Content.requestDetails('345')
console.log(details)
```

Value of `details`:

```javascript
{
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
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.requestDetails",
  "params": {
    "entityId": "345"
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
```

</details>

---

### requestPurchases

Provide a list of purchased content for the authenticated account, such as rentals and electronic sell through purchases.

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
| uses | xrn:firebolt:capability:discovery:purchased-content |


#### Examples


Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let purchases = await Content.requestPurchases()
console.log(purchases)
````

Value of `purchases`:

```javascript
{
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
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.requestPurchases",
  "params": {}
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
```

</details>

---

### requestUserInterest

Provide information about the entity currently displayed or selected on the screen.

```typescript
${method.signature}
```

Parameters:

| Param    | Type | Required | Description                                       |
| -------- | ---- | -------- | ------------------------------------------------- |
| `type`   | ``   | true     | values: `'interest' \| 'disinterest'`             |
| `reason` | ``   | true     | values: `'playlist' \| 'reaction' \| 'recording'` |

Promise resolution:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:user-interest |


#### Examples


Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let entity = await Content.requestUserInterest("interest", "playlist")
console.log(entity)
````

Value of `entity`:

```javascript
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

</details>

---

## Events

### details

```typescript
function listen('details', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:entity-info |


#### Examples


Send entity info for a movie to the platform.

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('details', data => {
  console.log(data)
})
````

Value of `data`:

```javascript
{
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
  "method": "Content.onDetails",
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

</details>

Send entity info for a movie with a trailer to the platform.

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('details', (data) => {
  console.log(data)
})
```

Value of `data`:

```javascript
{
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
  "method": "Content.onDetails",
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

</details>

---

### purchases

```typescript
function listen('purchases', () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:purchased-content |


#### Examples


Inform the platform of the user's purchased content

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('purchases', purchases => {
  console.log(purchases)
})
````

Value of `purchases`:

```javascript
{
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
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Content.onPurchases",
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
```

</details>

---

### userInterest

```typescript
function listen('userInterest', | `type` | [``](${method.param.link}) | ${method.param.required} | ${method.param.summary} ${method.param.constraints} |
, | `reason` | [``](${method.param.link}) | ${method.param.required} | ${method.param.summary} ${method.param.constraints} |
, () => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type | Required | Description                                       |
| -------- | ---- | -------- | ------------------------------------------------- |
| `type`   | ``   | true     | values: `'interest' \| 'disinterest'`             |
| `reason` | ``   | true     | values: `'playlist' \| 'reaction' \| 'recording'` |

Event value:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:discovery:user-interest |


#### Examples


Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('userInterest', entity => {
  console.log(entity)
})
````

Value of `entity`:

```javascript
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
    "type": "interest",
    "reason": "playlist",
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

</details>

---

## Types

### DetailsInfo

````typescript
```typescript

````

```

See also:



---
```
