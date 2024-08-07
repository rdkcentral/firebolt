---
title: Lifecycle
---

# Lifecycle Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [lifecycle.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/lifecycle.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)
    - [inactive](#nactive)
    - [foreground](#oreground)
    - [background](#ackground)
    - [suspended](#uspended)
    - [unloading](#nloading)
 - [Methods](#methods)
    - [ready](#ready)
    - [close](#close)
    - [finished](#finished)
    - [state](#state)
 - [Schemas](#schemas)
    - [LifecycleEvent](#lifecycleevent)
    - [LifecycleState](#lifecyclestate)
    - [CloseReason](#closereason)

<span></span>

## Usage
To use the Lifecycle module, you can import it into your project from the Firebolt SDK:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'
```
## Overview
Methods and events for responding to lifecycle changes in your app

## Events
### inactive
Listen to the inactive event

```typescript
// listen to inactive
Lifecycle.listen('inactive', (data: LifecycleEvent) => void): Promise<bigint>

// listen to inactive once
Lifecycle.once('inactive', (data: LifecycleEvent) => void): Promise<bigint>

// clear a listener
Lifecycle.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`LifecycleEvent`](#lifecycleevent) | A an object describing the previous and current states |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('inactive', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "inactive",
  "previous": "initializing"
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
  "method": "lifecycle.onInactive",
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
    "state": "inactive",
    "previous": "initializing"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.listen('inactive', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Lifecycle.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Lifecycle.once('inactive', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.clear('inactive')
```
</details>

---

### foreground
Listen to the foreground event

```typescript
// listen to foreground
Lifecycle.listen('foreground', (data: LifecycleEvent) => void): Promise<bigint>

// listen to foreground once
Lifecycle.once('foreground', (data: LifecycleEvent) => void): Promise<bigint>

// clear a listener
Lifecycle.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`LifecycleEvent`](#lifecycleevent) | A an object describing the previous and current states |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('foreground', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "foreground",
  "previous": "inactive"
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
  "method": "lifecycle.onForeground",
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
    "state": "foreground",
    "previous": "inactive"
  }
}
```

</details>

##### Move to foreground via remote branded buton
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('foreground', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "foreground",
  "previous": "inactive",
  "source": "remote"
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
  "method": "lifecycle.onForeground",
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
    "state": "foreground",
    "previous": "inactive",
    "source": "remote"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.listen('foreground', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Lifecycle.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Lifecycle.once('foreground', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.clear('foreground')
```
</details>

---

### background
Listen to the background event

```typescript
// listen to background
Lifecycle.listen('background', (data: LifecycleEvent) => void): Promise<bigint>

// listen to background once
Lifecycle.once('background', (data: LifecycleEvent) => void): Promise<bigint>

// clear a listener
Lifecycle.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`LifecycleEvent`](#lifecycleevent) | A an object describing the previous and current states |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('background', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "background",
  "previous": "foreground"
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
  "method": "lifecycle.onBackground",
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
    "state": "background",
    "previous": "foreground"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.listen('background', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Lifecycle.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Lifecycle.once('background', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.clear('background')
```
</details>

---

### suspended
Listen to the suspended event

```typescript
// listen to suspended
Lifecycle.listen('suspended', (data: LifecycleEvent) => void): Promise<bigint>

// listen to suspended once
Lifecycle.once('suspended', (data: LifecycleEvent) => void): Promise<bigint>

// clear a listener
Lifecycle.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`LifecycleEvent`](#lifecycleevent) | A an object describing the previous and current states |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('suspended', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "suspended",
  "previous": "inactive"
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
  "method": "lifecycle.onSuspended",
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
    "state": "suspended",
    "previous": "inactive"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.listen('suspended', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Lifecycle.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Lifecycle.once('suspended', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.clear('suspended')
```
</details>

---

### unloading
Listen to the unloading event

```typescript
// listen to unloading
Lifecycle.listen('unloading', (data: LifecycleEvent) => void): Promise<bigint>

// listen to unloading once
Lifecycle.once('unloading', (data: LifecycleEvent) => void): Promise<bigint>

// clear a listener
Lifecycle.clear(listenerId?: bigint): void

```
#### Event value

| Type | Description |
| ---- | ----------- |
| [`LifecycleEvent`](#lifecycleevent) | A an object describing the previous and current states |


#### Promise Resolution

| Type | Description |
|------|-------------|
| `bigint` | Listener ID to clear() the callback method and stop receiving the event, e.g. `Lifecycle.clear(id)` |

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.listen('unloading', value => {
  console.log(value)
})
```
Value of `value`

```javascript
{
  "state": "unloading",
  "previous": "inactive"
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
  "method": "lifecycle.onUnloading",
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
    "state": "unloading",
    "previous": "inactive"
  }
}
```

</details>



##### Listen to an event only once
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.listen('unloading', (value) => {
  console.log(value)
}).then( (listenerId) => {
  Lifecycle.clear(listenerId)
})
```

Alternately, simply call `once()`:

```javascript
Lifecycle.once('unloading', (value) => {
  console.log(value)
})
```
</details>

##### Clear all listeners for an event
<details>
  <summary><b>JavaScript</b></summary>

```javascript
Lifecycle.clear('unloading')
```
</details>

---



## Methods
### ready
Notify the platform that the app is ready

```typescript
function ready(): Promise<void>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `void` |  |


---

#### Examples

##### Let the platform know that your app is ready
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.ready()
    .then(result => {
        console.log(result)
    })
```
Value of `result`

```javascript
null
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "lifecycle.ready",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>




---

### close
Request that the platform move your app out of focus

```typescript
function close(reason: CloseReason): Promise<void>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `reason` | [`CloseReason`](#closereason) | true | The reason the app is requesting to be closed  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `void` |  |


---

#### Examples

##### Close the app when the user presses back on the app home screen
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.close("remoteButton")
    .then(success => {
        console.log(success)
    })
```
Value of `success`

```javascript
null
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "lifecycle.close",
  "params": {
    "reason": "remoteButton"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>

##### Close the app when the user selects an exit menu item
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.close("userExit")
    .then(success => {
        console.log(success)
    })
```
Value of `success`

```javascript
null
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "lifecycle.close",
  "params": {
    "reason": "userExit"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>




---

### finished
Notify the platform that the app is done unloading

```typescript
function finished(): Promise<void>
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `void` |  |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.finished()
    .then(results => {
        console.log(results)
    })
```
Value of `results`

```javascript
null
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "lifecycle.finished",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": null
}
```

</details>




---

### state
Get the current state of the app. This function is **synchronous**.

```typescript
function state(): LifecycleState
```
#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| [`LifecycleState`](#lifecyclestate) | Valid states in the `Lifecycle` API |


---

#### Examples

##### Default Example
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

Lifecycle.state()
    .then(state => {
        console.log(state)
    })
```
Value of `state`

```javascript
"foreground"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "lifecycle.state",
  "params": {}
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "foreground"
}
```

</details>




---



## Schemas

### LifecycleEvent

```typescript
type LifecycleEvent = {
  state: LifecycleState        // The current lifcycle state
  previous: LifecycleState     // The previous lifcycle state
  source?: 'voice' | 'remote'  // The source of the lifecycle change.
}
```



#### Details

A an object describing the previous and current states

---

### LifecycleState

```typescript
type LifecycleState = 'initializing' | 'inactive' | 'background' | 'foreground' | 'suspended' | 'unloading'
```



#### Details

Valid states in the `Lifecycle` API

---

### CloseReason

```typescript
type CloseReason = 'remoteButton' | 'userExit' | 'error'
```



#### Details

Reasons for calling the `close` method

---


