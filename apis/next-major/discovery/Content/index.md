---
title: Content

version: next-major
layout: default
sdk: discovery
---

# Content Module

---

Version Content 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [requestUserInterest](#requestuserinterest)
- [Events](#events)
  - [requestUserInterestChanged](#requestuserinterestchanged)
- [Private Events](#private-events)<details markdown="1"  ontoggle="document.getElementById('private-events-details').open=this.open"><summary>Show</summary>
  </details>
- [Types](#types)

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

To get the value of `requestUserInterest` call the method like this:

```typescript
function requestUserInterest(
  type: Discovery.InterestType,
  reason: Discovery.InterestReason,
): Promise<InterestResult>
```

Parameters:

| Param    | Type                       | Required | Description |
| -------- | -------------------------- | -------- | ----------- |
| `type`   | `Discovery.InterestType`   | true     |             |
| `reason` | `Discovery.InterestReason` | true     |             |

Promise resolution:

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
{"appId":"cool-app","entity":{"identifiers":{"entityId":"345","entityType":"program","programType":"movie"},"info":{"title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}]}}}
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

Example 2

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let interest = await Content.requestUserInterest('interest', 'playlist')
console.log(interest)
```

Value of `interest`:

```javascript
{"appId":"cool-app","entity":{"identifiers":{"entityId":"345","entityType":"program","programType":"movie"},"info":{"title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}]}}}
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
    "appId": "cool-app2",
    "entity": {
      "identifiers": {
        "entityId": "3454",
        "entityType": "program",
        "programType": "movie"
      },
      "info": {
        "title": "Cool Runnings2",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1994-01-01T00:00:00.000Z",
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

To set the value of `requestUserInterest` call the method like this:

```typescript
function requestUserInterest(
  type: Discovery.InterestType,
  reason: Discovery.InterestReason,
  value: Discovery.InterestResult,
): Promise<void>
```

Parameters:

| Param    | Type                       | Required | Description             |
| -------- | -------------------------- | -------- | ----------------------- |
| `type`   | `Discovery.InterestType`   | true     |                         |
| `reason` | `Discovery.InterestReason` | true     |                         |
| `value`  | `Discovery.InterestResult` | true     | The EntityDetails data. |

Promise resolution:

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let result = await Content.requestUserInterest('interest', 'playlist', {
  appId: 'cool-app',
  entity: {
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
  "method": "Content.setRequestUserInterest",
  "params": {
    "type": "interest",
    "reason": "playlist",
    "value": {
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
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

Example 2

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let result = await Content.requestUserInterest('interest', 'playlist', {
  appId: 'cool-app2',
  entity: {
    identifiers: {
      entityId: '3454',
      entityType: 'program',
      programType: 'movie',
    },
    info: {
      title: 'Cool Runnings2',
      synopsis:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.',
      releaseDate: '1994-01-01T00:00:00.000Z',
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
  "method": "Content.setRequestUserInterest",
  "params": {
    "type": "interest",
    "reason": "playlist",
    "value": {
      "appId": "cool-app2",
      "entity": {
        "identifiers": {
          "entityId": "3454",
          "entityType": "program",
          "programType": "movie"
        },
        "info": {
          "title": "Cool Runnings2",
          "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
          "releaseDate": "1994-01-01T00:00:00.000Z",
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
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function ${method.alternative}(${event.signature.params}${if.context}, ${end.if.context}callback: (value) => InterestResult): Promise<number>
```

${event.params}

Promise resolution:

```
number
```

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
{"appId":"cool-app","entity":{"identifiers":{"entityId":"345","entityType":"program","programType":"movie"},"info":{"title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}]}}}
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

Example 2

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

let interest = await Content.requestUserInterest('interest', 'playlist')
console.log(interest)
```

Value of `interest`:

```javascript
{"appId":"cool-app","entity":{"identifiers":{"entityId":"345","entityType":"program","programType":"movie"},"info":{"title":"Cool Runnings","synopsis":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.","releaseDate":"1993-01-01T00:00:00.000Z","contentRatings":[{"scheme":"US-Movie","rating":"PG"},{"scheme":"CA-Movie","rating":"G"}]}}}
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
    "appId": "cool-app2",
    "entity": {
      "identifiers": {
        "entityId": "3454",
        "entityType": "program",
        "programType": "movie"
      },
      "info": {
        "title": "Cool Runnings2",
        "synopsis": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Pulvinar sapien et ligula ullamcorper malesuada proin libero nunc.",
        "releaseDate": "1994-01-01T00:00:00.000Z",
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

### requestUserInterestChanged

```typescript
function listen('requestUserInterestChanged', type: Discovery.InterestType, reason: Discovery.InterestReason, (Discovery.InterestResult) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type                       | Required | Description |
| -------- | -------------------------- | -------- | ----------- |
| `type`   | `Discovery.InterestType`   | true     |             |
| `reason` | `Discovery.InterestReason` | true     |             |

Event value:

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('requestUserInterestChanged', (result) => {
  console.log(result)
})
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
  "method": "Content.onRequestUserInterestChanged",
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
  "result": null
}
```

</details>

Example 2

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('requestUserInterestChanged', (result) => {
  console.log(result)
})
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
  "method": "Content.onRequestUserInterestChanged",
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
  "result": null
}
```

</details>

---

## Private Events

<details markdown="1"  id="private-events-details">
  <summary>View</summary>

### requestUserInterestChanged

```typescript
function listen('requestUserInterestChanged', type: Discovery.InterestType, reason: Discovery.InterestReason, (Discovery.InterestResult) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Parameters:

| Param    | Type                       | Required | Description |
| -------- | -------------------------- | -------- | ----------- |
| `type`   | `Discovery.InterestType`   | true     |             |
| `reason` | `Discovery.InterestReason` | true     |             |

Event value:

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:interest |

#### Examples

Default Example

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('requestUserInterestChanged', (result) => {
  console.log(result)
})
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
  "method": "Content.onRequestUserInterestChanged",
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
  "result": null
}
```

</details>

Example 2

JavaScript:

```javascript
import { Content } from '@firebolt-js/discovery-sdk'

Content.listen('requestUserInterestChanged', (result) => {
  console.log(result)
})
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
  "method": "Content.onRequestUserInterestChanged",
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
  "result": null
}
```

</details>

---

</details>

## Types
