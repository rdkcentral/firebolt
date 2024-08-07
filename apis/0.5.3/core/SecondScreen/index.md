---
title: SecondScreen
---

# SecondScreen Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [secondscreen.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/secondscreen.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)
    - [launchRequest](#aunchrequest)
    - [closeRequest](#loserequest)
 - [Methods](#methods)
    - [protocols](#protocols)
    - [device](#device)
    - [friendlyName](#friendlyname)
 - [Schemas](#schemas)
<span></span>

## Usage
To use the SecondScreen module, you can import it into your project from the Firebolt SDK:

```javascript
import { SecondScreen } from '@firebolt-js/sdk'
```
## Overview
Methods for communicating with second screen devices

## Events
### launchRequest
Listen to the launchRequest event

```typescript
// listen to launchRequest
SecondScreen.listen('launchRequest', (data: SecondScreenEvent) => void): Promise<bigint>

// listen to launchRequest once
SecondScreen.once('launchRequest', (data: SecondScreenEvent) => void): Promise<bigint>

// clear a listener
SecondScreen.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`SecondScreenEvent`](../schemas/secondscreen#/definitions/secondscreenevent) | An a message notification from a second screen device |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('launchRequest', launchRequestEvent => {
  console.log(launchRequestEvent)
})
```
Value of `launchRequestEvent`

```javascript
{
  "type": "dial",
  "version": "1.7",
  "data": "{\"code\":\"AQDPQZiQcb3KQ7gY7yy5tHTMbbkGHR9Zjp-KL53H3eKBZIeAt7O9UKYPu6B21l2UZVmIqkFXDXBmXvK4g2e3EgZtjMNmKPsTltgnRl95DImtOXjSpWtTjSaOkW4w1kZKUTwLKdwVWTzBVH8ERHorvLU6vCGOVHxXt65LNwdl5HKRweShVC1V9QsyvRnQS61ov0UclmrH_xZML2Bt-Q-rZFjey5MjwupIb4x4f53XUJMhjHpDHoIUKrjpdPDQvK2a\",\"friendlyName\":\"Operator_TX061AEI\",\"UDN\":\"608fef11-2800-482a-962b-23a6690c93c1\"}"
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

<h6>Request</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "secondscreen.onLaunchRequest",
  "params": {
    "listen": true
  }
}
```

<h6>Response</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "type": "dial",
    "version": "1.7",
    "data": "{\"code\":\"AQDPQZiQcb3KQ7gY7yy5tHTMbbkGHR9Zjp-KL53H3eKBZIeAt7O9UKYPu6B21l2UZVmIqkFXDXBmXvK4g2e3EgZtjMNmKPsTltgnRl95DImtOXjSpWtTjSaOkW4w1kZKUTwLKdwVWTzBVH8ERHorvLU6vCGOVHxXt65LNwdl5HKRweShVC1V9QsyvRnQS61ov0UclmrH_xZML2Bt-Q-rZFjey5MjwupIb4x4f53XUJMhjHpDHoIUKrjpdPDQvK2a\",\"friendlyName\":\"Operator_TX061AEI\",\"UDN\":\"608fef11-2800-482a-962b-23a6690c93c1\"}"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
SecondScreen.listen('launchRequest', (value) => {
  console.log(value)
}).then( (listenerId) => {
  SecondScreen.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
SecondScreen.once('launchRequest', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
SecondScreen.clear('launchRequest')
```
</details>

---

### closeRequest
Listen to the closeRequest event

```typescript
// listen to closeRequest
SecondScreen.listen('closeRequest', (data: SecondScreenEvent) => void): Promise<bigint>

// listen to closeRequest once
SecondScreen.once('closeRequest', (data: SecondScreenEvent) => void): Promise<bigint>

// clear a listener
SecondScreen.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`SecondScreenEvent`](../schemas/secondscreen#/definitions/secondscreenevent) | An a message notification from a second screen device |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `SecondScreen.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.listen('closeRequest', closeRequestEvent => {
  console.log(closeRequestEvent)
})
```
Value of `closeRequestEvent`

```javascript
{
  "type": "dial",
  "version": "1.7"
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

<h6>Request</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "secondscreen.onCloseRequest",
  "params": {
    "listen": true
  }
}
```

<h6>Response</h6>

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "type": "dial",
    "version": "1.7"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
SecondScreen.listen('closeRequest', (value) => {
  console.log(value)
}).then( (listenerId) => {
  SecondScreen.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
SecondScreen.once('closeRequest', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
SecondScreen.clear('closeRequest')
```
</details>

---



## Methods
### protocols
Get the supported second screen discovery protocols

```typescript
function protocols(): Promise<BooleanMap>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`BooleanMap`](../schemas/types#/definitions/booleanmap) | the supported protocols |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.protocols()
    .then(protocols => {
        console.log(protocols)
    })
```
Value of `protocols`

```javascript
{
  "dial1.7": true
}
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "secondscreen.protocols",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "dial1.7": true
  }
}
```

</details>




---

### device
Get the broadcasted id for the device

```typescript
function device(type?: string): Promise<string>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `type` | `string` | false | The type of second screen protocol, e.g. "dial"  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device id |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.device(null)
    .then(deviceId => {
        console.log(deviceId)
    })
```
Value of `deviceId`

```javascript
"device-id"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "secondscreen.device",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "device-id"
}
```

</details>




---

### friendlyName
Get the broadcasted friendly name for the device

```typescript
function friendlyName(type?: string): Promise<string>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `type` | `string` | false | The type of second screen protocol, e.g. "dial"  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the device friendly-name |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { SecondScreen } from '@firebolt-js/sdk'

SecondScreen.friendlyName(null)
    .then(friendlyName => {
        console.log(friendlyName)
    })
```
Value of `friendlyName`

```javascript
"Living Room"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "secondscreen.friendlyName",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>




---



