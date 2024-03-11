---
title: Advertising

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Advertising Module

---

Version Advertising 1.1.1-feature-next-major-docs.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [listen](#listen)
  - [once](#once)
  - [resetIdentifier](#resetidentifier)
  - [skipRestriction](#skiprestriction)
- [Events](#events)
  - [skipRestrictionChanged](#skiprestrictionchanged)

## Usage

To use the Advertising module, you can import it into your project from the Firebolt SDK:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'
```

## Overview

A module for platform provided advertising settings and functionality.

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

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

| Type     | Description                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Advertising.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### resetIdentifier

Resets a user's identifier in the ad platform so that the advertising id that apps get will be a new value

```typescript
function resetIdentifier(): Promise<void>
```

Promise resolution:

```typescript
void
```

Capabilities:

| Role    | Capability                                     |
| ------- | ---------------------------------------------- |
| manages | xrn:firebolt:capability:advertising:identifier |

#### Examples

Default Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let result = await Advertising.resetIdentifier()
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
  "method": "Advertising.resetIdentifier",
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

### skipRestriction

Set the value for AdPolicy.skipRestriction

To get the value of `skipRestriction` call the method like this:

```typescript
function skipRestriction(): Promise<SkipRestriction>
```

Promise resolution:

[SkipRestriction](../Advertising/schemas/#SkipRestriction)

Capabilities:

| Role    | Capability                                        |
| ------- | ------------------------------------------------- |
| manages | xrn:firebolt:capability:advertising:configuration |

#### Examples

Default Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let result = await Advertising.skipRestriction()
console.log(result)
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.skipRestriction",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "none"
}
```

</details>

Additional Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let result = await Advertising.skipRestriction()
console.log(result)
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.skipRestriction",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "all"
}
```

</details>

---

To set the value of `skipRestriction` call the method like this:

```typescript
function skipRestriction(value: SkipRestriction): Promise<void>
```

Parameters:

| Param   | Type                                                         | Required | Description                                                  |
| ------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| `value` | [`SkipRestriction`](../Advertising/schemas/#SkipRestriction) | true     | <br/>values: `'none' \| 'adsUnwatched' \| 'adsAll' \| 'all'` |

Promise resolution:

```typescript
null
```

#### Examples

Default Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let result = await Advertising.skipRestriction('none')
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
  "method": "Advertising.setSkipRestriction",
  "params": {
    "value": "none"
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

Additional Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let result = await Advertising.skipRestriction('all')
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
  "method": "Advertising.setSkipRestriction",
  "params": {
    "value": "all"
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
function skipRestriction(callback: (value) => SkipRestriction): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

Default Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let listenerId = await skipRestriction((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.onSkipRestrictionChanged",
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
  "result": "none"
}
```

</details>

Additional Example

JavaScript:

```javascript
import { Advertising } from '@firebolt-js/manage-sdk'

let listenerId = await skipRestriction((value) => {
  console.log(value)
})
console.log(listenerId)
```

Value of `result`:

```javascript
'none'
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "Advertising.onSkipRestrictionChanged",
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
  "result": "all"
}
```

</details>

---

## Events

### skipRestrictionChanged

See: [skipRestriction](#skiprestriction)
