---
title: Lifecycle

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Lifecycle Module

---

Version Lifecycle 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [close](#close)
  - [finished](#finished)
  - [provideActivatable](#provideactivatable)
  - [provideApplication](#provideapplication)
  - [provideSleepable](#providesleepable)
- [Provider Interfaces](#provider-interfaces)
  - [Application](#application)
  - [Activatable](#activatable)
  - [Sleepable](#sleepable)
- [Types](#types)

## Usage

To use the Lifecycle module, you can import it into your project from the Firebolt SDK:

```javascript
import { Lifecycle } from '@firebolt-js/sdk'
```

## Overview

Methods and events for responding to lifecycle changes in your app

## Methods

### close

Request that the platform move your app out of focus

```typescript
function close(reason: CloseReason): Promise<void>
```

Parameters:

| Param    | Type          | Required | Description                                   |
| -------- | ------------- | -------- | --------------------------------------------- |
| `reason` | `CloseReason` | true     | The reason the app is requesting to be closed |

Promise resolution:

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:state |

#### Examples

---

### finished

Notify the platform that the app is done unloading

```typescript
function finished(): Promise<void>
```

Promise resolution:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:application |

#### Examples

---

### provideActivatable

Register an app's Activatable interface.

```typescript
function provideActivatable(enabled: boolean): Promise<void>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | true     |             |

Promise resolution:

Capabilities:

| Role     | Capability                                    |
| -------- | --------------------------------------------- |
| provides | xrn:firebolt:capability:lifecycle:activatable |

#### Examples

---

### provideApplication

Register an app's Application interface.

```typescript
function provideApplication(enabled: boolean): Promise<void>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | true     |             |

Promise resolution:

Capabilities:

| Role     | Capability                                    |
| -------- | --------------------------------------------- |
| provides | xrn:firebolt:capability:lifecycle:application |

#### Examples

---

### provideSleepable

Register an app's Sleepable interface.

```typescript
function provideSleepable(enabled: boolean): Promise<void>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | true     |             |

Promise resolution:

Capabilities:

| Role     | Capability                                  |
| -------- | ------------------------------------------- |
| provides | xrn:firebolt:capability:lifecycle:sleepable |

#### Examples

---

## Provider Interfaces

### Application

The provider interface for the `Application` capability.

```typescript
interface Application {
    create(params: CreateParameters, session: ProviderSession): Promise<void>
    resume(, session: ProviderSession): Promise<void>
    suspend(, session: ProviderSession): Promise<void>
    destroy(, session: ProviderSession): Promise<void>

}
```

Usage:

```typescript
Lifecycle.provide('Application', provider: Application | object)
```

#### Examples

**Register your app to provide the `Application` capability.**

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

class MyApplication {

    async Application.create(parameters, session) {
        return null
    }

    async Application.resume(parameters, session) {
        return null
    }

    async Application.suspend(parameters, session) {
        return null
    }

    async Application.destroy(parameters, session) {
        return null
    }

}

Lifecycle.provide('Application', new MyApplication())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Lifecycle.onRequestApplication.create",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Lifecycle.onRequestApplication.resume",
    "params": {
        "listen": true
    }
}

{
    "id": 3,
    "method": "Lifecycle.onRequestApplication.suspend",
    "params": {
        "listen": true
    }
}

{
    "id": 4,
    "method": "Lifecycle.onRequestApplication.destroy",
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
        "event": "Lifecycle.onRequestApplication.create"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Lifecycle.onRequestApplication.resume"
    }

}

{
    "id": 3,
    "result": {
        "listening": true,
        "event": "Lifecycle.onRequestApplication.suspend"
    }

}

{
    "id": 4,
    "result": {
        "listening": true,
        "event": "Lifecycle.onRequestApplication.destroy"
    }

}

```

**Asynchronous event to initiate Application.create()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": {
      "preload": false
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 5,
  "method": "Lifecycle.Application.createResponse",
  "params": {
    "correlationId": "",
    "result": null
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

**Asynchronous event to initiate Application.resume()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 6,
  "method": "Lifecycle.Application.resumeResponse",
  "params": {
    "correlationId": "",
    "result": null
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

**Asynchronous event to initiate Application.suspend()**

Event Response:

```json
{
  "id": 3,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 7,
  "method": "Lifecycle.Application.suspendResponse",
  "params": {
    "correlationId": "",
    "result": null
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

**Asynchronous event to initiate Application.destroy()**

Event Response:

```json
{
  "id": 4,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 8,
  "method": "Lifecycle.Application.destroyResponse",
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

### Activatable

The provider interface for the `Activatable` capability.

```typescript
interface Activatable {
    activate(intent: Intents.NavigationIntent, session: ProviderSession): Promise<void>
    deactivate(, session: ProviderSession): Promise<void>

}
```

Usage:

```typescript
Lifecycle.provide('Activatable', provider: Activatable | object)
```

#### Examples

**Register your app to provide the `Activatable` capability.**

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

class MyActivatable {

    async Activatable.activate(parameters, session) {
        return null
    }

    async Activatable.deactivate(parameters, session) {
        return null
    }

}

Lifecycle.provide('Activatable', new MyActivatable())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Lifecycle.onRequestActivatable.activate",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Lifecycle.onRequestActivatable.deactivate",
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
        "event": "Lifecycle.onRequestActivatable.activate"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Lifecycle.onRequestActivatable.deactivate"
    }

}

```

**Asynchronous event to initiate Activatable.activate()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": {
      "action": "search",
      "data": {
        "query": "cats"
      },
      "context": {
        "source": "voice"
      }
    }
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 3,
  "method": "Lifecycle.Activatable.activateResponse",
  "params": {
    "correlationId": "",
    "result": null
  }
}
```

Response:

```json
{
  "id": 3,
  "result": true
}
```

**Asynchronous event to initiate Activatable.deactivate()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 4,
  "method": "Lifecycle.Activatable.deactivateResponse",
  "params": {
    "correlationId": "",
    "result": null
  }
}
```

Response:

```json
{
  "id": 4,
  "result": true
}
```

</details>

### Sleepable

The provider interface for the `Sleepable` capability.

```typescript
interface Sleepable {
    sleep(, session: ProviderSession): Promise<void>
    wake(, session: ProviderSession): Promise<void>

}
```

Usage:

```typescript
Lifecycle.provide('Sleepable', provider: Sleepable | object)
```

#### Examples

**Register your app to provide the `Sleepable` capability.**

```javascript
import { Lifecycle } from '@firebolt-js/sdk'

class MySleepable {

    async Sleepable.sleep(parameters, session) {
        return null
    }

    async Sleepable.wake(parameters, session) {
        return null
    }

}

Lifecycle.provide('Sleepable', new MySleepable())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json

{
    "id": 1,
    "method": "Lifecycle.onRequestSleepable.sleep",
    "params": {
        "listen": true
    }
}

{
    "id": 2,
    "method": "Lifecycle.onRequestSleepable.wake",
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
        "event": "Lifecycle.onRequestSleepable.sleep"
    }

}

{
    "id": 2,
    "result": {
        "listening": true,
        "event": "Lifecycle.onRequestSleepable.wake"
    }

}

```

**Asynchronous event to initiate Sleepable.sleep()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 3,
  "method": "Lifecycle.Sleepable.sleepResponse",
  "params": {
    "correlationId": "",
    "result": null
  }
}
```

Response:

```json
{
  "id": 3,
  "result": true
}
```

**Asynchronous event to initiate Sleepable.wake()**

Event Response:

```json
{
  "id": 2,
  "result": {
    "correlationId": "",
    "parameters": ""
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 4,
  "method": "Lifecycle.Sleepable.wakeResponse",
  "params": {
    "correlationId": "",
    "result": null
  }
}
```

Response:

```json
{
  "id": 4,
  "result": true
}
```

</details>

## Types
