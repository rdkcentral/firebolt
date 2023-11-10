---
title: StreamingPlayer

version: pr206
layout: default
sdk: manage
---

# StreamingPlayer Module
---
Version StreamingPlayer 1.0.0-player

## Table of Contents
   - [Table of Contents](#table-of-contents)
   - [Usage](#usage)
   - [Overview](#overview)
   - [Methods](#methods)
     - [create](#create)
   - [Types](#types)
     - [StreamingPlayerCreateRequest](#streamingplayercreaterequest)
     - [StreamingPlayerInstance](#streamingplayerinstance)



## Usage
To use the StreamingPlayer module, you can import it into your project from the Firebolt SDK:

```javascript
import { StreamingPlayer } from '@firebolt-js/manage-sdk'
```


## Overview
 A module for controlling and accessing media over streaming

## Methods

### create

Creates an instance of a player that can be used to play media over streaming. Player instance that is created should also provide firebolt capability 'xrn:firebolt:capability:player:base'. If there is no provider running but there is a provider in the catalog, it will be launched.

```typescript
function create(request: StreamingPlayerCreateRequest): Promise<StreamingPlayerInstance>
```

Parameters:

| Param                  | Type                 | Required                 | Description                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `request` | [`StreamingPlayerCreateRequest`](#streamingplayercreaterequest) | true | The create request  |


Promise resolution:

[StreamingPlayerInstance](#streamingplayerinstance)

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:player:streaming |


#### Examples


Default example #1

JavaScript:

```javascript
import { StreamingPlayer } from '@firebolt-js/manage-sdk'

StreamingPlayer.create({})
    .then(playerInstance => {
        console.log(playerInstance)
    })
```

Value of `playerInstance`:

```javascript
{
	"playerId": "123",
	"windowId": "456"
}
```
<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "StreamingPlayer.create",
	"params": {
		"request": {}
	}
}
```

Response:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"playerId": "123",
		"windowId": "456"
	}
}
```
</details>


---



## Types

### StreamingPlayerCreateRequest



```typescript
type StreamingPlayerCreateRequest = {
}
```



---
### StreamingPlayerInstance



```typescript
type StreamingPlayerInstance = {
  playerId: string                // The id of player which can be used to load media or control the player
  windowId: string                // The id of window which will render the media in, can be used to control on screen where the media is shown
}
```



---