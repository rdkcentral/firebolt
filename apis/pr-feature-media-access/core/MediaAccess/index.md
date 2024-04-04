---
title: MediaAccess

version: pr-feature-media-access
layout: default
sdk: core
---

# MediaAccess Module

---

Version MediaAccess 1.2.0-feature-media-access.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [audio](#audio)
  - [files](#files)
  - [images](#images)
  - [media](#media)
  - [stopVolumes](#stopvolumes)
  - [video](#video)
  - [volumes](#volumes)
- [Events](#events)
  - [onVolumeAvailable](#onvolumeavailable)
  - [onVolumeUnavailable](#onvolumeunavailable)
- [Types](#types)
  - [VolumeType](#volumetype)
  - [Volume](#volume)
  - [MediaFile](#mediafile)

## Usage

To use the MediaAccess module, you can import it into your project from the Firebolt SDK:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'
```

## Overview

A module for access user-cultivated media files, e.g. photos on a USB drive.

## Methods

### audio

Access available audio MediaFiles.

```typescript
${method.signature}
```

Parameters:

| Param     | Type | Required | Description                                                   |
| --------- | ---- | -------- | ------------------------------------------------------------- |
| `volumes` | ``   | false    | A set of queries used to match which volumes will be matched. |
| `files`   | ``   | false    | A set of queries used to match which files will be matched.   |

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:media-access:audio |

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

let files = await MediaAccess.audio({}, null)
console.log(files)
```

Value of `files`:

```javascript
;[
  {
    uri: '/usb/my-usb-drive/song1.mp3',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'audio/mpeg',
  },
  {
    uri: '/local/music/song2.mp3',
    volume: {
      uri: '/local/music',
      name: 'music',
      type: 'local',
    },
    type: 'audio/mpeg',
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
  "method": "MediaAccess.audio",
  "params": {
    "volumes": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "uri": "/usb/my-usb-drive/song1.mp3",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "audio/mpeg"
    },
    {
      "uri": "/local/music/song2.mp3",
      "volume": {
        "uri": "/local/music",
        "name": "music",
        "type": "local"
      },
      "type": "audio/mpeg"
    }
  ]
}
```

</details>

---

### files

Access all available MediaFiles.

```typescript
${method.signature}
```

Parameters:

| Param     | Type | Required | Description                                                   |
| --------- | ---- | -------- | ------------------------------------------------------------- |
| `volumes` | ``   | false    | A set of queries used to match which volumes will be matched. |
| `files`   | ``   | false    | A set of queries used to match which files will be matched.   |

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:media-access:files |

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

let files = await MediaAccess.files({}, null)
console.log(files)
```

Value of `files`:

```javascript
;[
  {
    uri: '/usb/my-usb-drive/notes.txt',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'text/plain',
  },
  {
    uri: '/usb/my-usb-drive/song1.mp3',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'audio/mpeg',
  },
  {
    uri: '/local/music/song2.mp3',
    volume: {
      uri: '/local/music',
      name: 'music',
      type: 'local',
    },
    type: 'audio/mpeg',
  },
  {
    uri: '/usb/my-usb-drive/photo1.jpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'image/jpg',
  },
  {
    uri: '/local/photos/photo1.jpg',
    volume: {
      uri: '/local/photos',
      name: 'photos',
      type: 'local',
    },
    type: 'image/jpg',
  },
  {
    uri: '/usb/my-usb-drive/video1.mpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'video/mp4',
  },
  {
    uri: '/local/videos/video2.mpg',
    volume: {
      uri: '/local/videos',
      name: 'videos',
      type: 'local',
    },
    type: 'video/mp4',
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
  "method": "MediaAccess.files",
  "params": {
    "volumes": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "uri": "/usb/my-usb-drive/notes.txt",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "text/plain"
    },
    {
      "uri": "/usb/my-usb-drive/song1.mp3",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "audio/mpeg"
    },
    {
      "uri": "/local/music/song2.mp3",
      "volume": {
        "uri": "/local/music",
        "name": "music",
        "type": "local"
      },
      "type": "audio/mpeg"
    },
    {
      "uri": "/usb/my-usb-drive/photo1.jpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "image/jpg"
    },
    {
      "uri": "/local/photos/photo1.jpg",
      "volume": {
        "uri": "/local/photos",
        "name": "photos",
        "type": "local"
      },
      "type": "image/jpg"
    },
    {
      "uri": "/usb/my-usb-drive/video1.mpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "video/mp4"
    },
    {
      "uri": "/local/videos/video2.mpg",
      "volume": {
        "uri": "/local/videos",
        "name": "videos",
        "type": "local"
      },
      "type": "video/mp4"
    }
  ]
}
```

</details>

---

### images

Access available image MediaFiles.

```typescript
${method.signature}
```

Parameters:

| Param     | Type | Required | Description                                                   |
| --------- | ---- | -------- | ------------------------------------------------------------- |
| `volumes` | ``   | false    | A set of queries used to match which volumes will be matched. |
| `files`   | ``   | false    | A set of queries used to match which files will be matched.   |

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                                  |
| ---- | ------------------------------------------- |
| uses | xrn:firebolt:capability:media-access:images |

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

let files = await MediaAccess.images({}, null)
console.log(files)
```

Value of `files`:

```javascript
;[
  {
    uri: '/usb/my-usb-drive/photo1.jpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'image/jpg',
  },
  {
    uri: '/local/photos/photo1.jpg',
    volume: {
      uri: '/local/photos',
      name: 'photos',
      type: 'local',
    },
    type: 'image/jpg',
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
  "method": "MediaAccess.images",
  "params": {
    "volumes": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "uri": "/usb/my-usb-drive/photo1.jpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "image/jpg"
    },
    {
      "uri": "/local/photos/photo1.jpg",
      "volume": {
        "uri": "/local/photos",
        "name": "photos",
        "type": "local"
      },
      "type": "image/jpg"
    }
  ]
}
```

</details>

---

### media

Access all available MediaFiles of either audio, video, or image types.

```typescript
${method.signature}
```

Parameters:

| Param     | Type | Required | Description                                                   |
| --------- | ---- | -------- | ------------------------------------------------------------- |
| `volumes` | ``   | false    | A set of queries used to match which volumes will be matched. |
| `files`   | ``   | false    | A set of queries used to match which files will be matched.   |

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                              |
| ---- | --------------------------------------- |
| uses | xrn:firebolt:capability:media-access:\* |

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

let files = await MediaAccess.media({}, null)
console.log(files)
```

Value of `files`:

```javascript
;[
  {
    uri: '/usb/my-usb-drive/song1.mp3',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'audio/mpeg',
  },
  {
    uri: '/local/music/song2.mp3',
    volume: {
      uri: '/local/music',
      name: 'music',
      type: 'local',
    },
    type: 'audio/mpeg',
  },
  {
    uri: '/usb/my-usb-drive/photo1.jpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'image/jpg',
  },
  {
    uri: '/local/photos/photo1.jpg',
    volume: {
      uri: '/local/photos',
      name: 'photos',
      type: 'local',
    },
    type: 'image/jpg',
  },
  {
    uri: '/usb/my-usb-drive/video1.mpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'video/mp4',
  },
  {
    uri: '/local/videos/video2.mpg',
    volume: {
      uri: '/local/videos',
      name: 'videos',
      type: 'local',
    },
    type: 'video/mp4',
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
  "method": "MediaAccess.media",
  "params": {
    "volumes": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "uri": "/usb/my-usb-drive/song1.mp3",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "audio/mpeg"
    },
    {
      "uri": "/local/music/song2.mp3",
      "volume": {
        "uri": "/local/music",
        "name": "music",
        "type": "local"
      },
      "type": "audio/mpeg"
    },
    {
      "uri": "/usb/my-usb-drive/photo1.jpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "image/jpg"
    },
    {
      "uri": "/local/photos/photo1.jpg",
      "volume": {
        "uri": "/local/photos",
        "name": "photos",
        "type": "local"
      },
      "type": "image/jpg"
    },
    {
      "uri": "/usb/my-usb-drive/video1.mpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "video/mp4"
    },
    {
      "uri": "/local/videos/video2.mpg",
      "volume": {
        "uri": "/local/videos",
        "name": "videos",
        "type": "local"
      },
      "type": "video/mp4"
    }
  ]
}
```

</details>

---

### stopVolumes

_This is an private RPC method._

Access available Volumes with MediaFiles.

Parameters:

| Param           | Type     | Required | Description |
| --------------- | -------- | -------- | ----------- |
| `correlationId` | `string` | true     |             |

Result:

```typescript

```

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:media-access:volumes |

#### Examples

Default example #1

JSON-RPC:

Request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "MediaAccess.stopVolumes",
  "params": {
    "correlationId": "xyz"
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

---

### video

Access available video MediaFiles.

```typescript
${method.signature}
```

Parameters:

| Param     | Type | Required | Description                                                   |
| --------- | ---- | -------- | ------------------------------------------------------------- |
| `volumes` | ``   | false    | A set of queries used to match which volumes will be matched. |
| `files`   | ``   | false    | A set of queries used to match which files will be matched.   |

Promise resolution:

```typescript

```

Capabilities:

| Role | Capability                                 |
| ---- | ------------------------------------------ |
| uses | xrn:firebolt:capability:media-access:video |

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

let files = await MediaAccess.video({}, null)
console.log(files)
```

Value of `files`:

```javascript
;[
  {
    uri: '/usb/my-usb-drive/video1.mpg',
    volume: {
      uri: '/usb/my-usb-drive',
      name: 'My USB Drive',
      type: 'usb',
    },
    type: 'video/mp4',
  },
  {
    uri: '/local/videos/video2.mpg',
    volume: {
      uri: '/local/videos',
      name: 'videos',
      type: 'local',
    },
    type: 'video/mp4',
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
  "method": "MediaAccess.video",
  "params": {
    "volumes": {}
  }
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "uri": "/usb/my-usb-drive/video1.mpg",
      "volume": {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      "type": "video/mp4"
    },
    {
      "uri": "/local/videos/video2.mpg",
      "volume": {
        "uri": "/local/videos",
        "name": "videos",
        "type": "local"
      },
      "type": "video/mp4"
    }
  ]
}
```

</details>

---

### volumes

Access available Volumes with MediaFiles.

```typescript
function volumes(| `query` | [``](${method.param.link}) | ${method.param.required} | ${method.param.summary} ${method.param.constraints} |
add: (volume: ) => void, remove?: (volume: ) => void ): Process
```

Parameters:

| Param   | Type       | Required | Summary                                                        |
| ------- | ---------- | -------- | -------------------------------------------------------------- |
| `query` | ``         | true     |                                                                |
| add     | `function` | true     | Callback to pass any `` objects to, as they become available   |
| remove  | `function` | false    | Callback to pass any `` objects to, as they become unavailable |

Returns:

```typescript
interface Process {
  stop(): void // Stops updating this temporal set with  objects
}
```

Additionally, the `volumes` method may be called witha `timeout` parameter to find the first match and automatically stop scanning:

```typescript
function volumes(| `query` | [``](${method.param.link}) | ${method.param.required} | ${method.param.summary} ${method.param.constraints} |
timeout: number): Promise<>
```

Parameters:

| Param   | Type     | Required | Summary                               |
| ------- | -------- | -------- | ------------------------------------- |
| `query` | ``       | true     |                                       |
| timeout | `number` | true     | How long to wait, in ms, for a match. |

Promise resolution:

```typescript

```

#### Examples

Default example #1

JavaScript:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

const process = MediaAccess.volumes(
  {},
  (volume) => {
    console.log('Added to temporal set:')
    console.dir(volume)
  },
  (volume) => {
    console.log('Removed from temporal set:')
    console.dir(volume)
  },
)

setTimeout(() => process.stop(), 10000)
```

Request only the first match:

```javascript
import { MediaAccess } from '@firebolt-js/sdk'

const volume = await MediaAccess.volumes({}, 1000)
```

Value of `volume`:

```javascript
{
	"uri": "/usb/my-usb-drive",
	"name": "My USB Drive",
	"type": "usb"
}
```

<details markdown="1" >
<summary>JSON-RPC:</summary>
Request:

```json
[
  {
    "jsonrpc": "2.0",
    "id": 1,
    "method": "MediaAccess.volumes",
    "params": {
      "TBD": "TBD"
    }
  },
  {
    "jsonrpc": "2.0",
    "id": 2,
    "method": "MediaAccess.onvolumeAvailable",
    "params": {
      "listen": true
    }
  },
  {
    "jsonrpc": "2.0",
    "id": 3,
    "method": "MediaAccess.onvolumeUnavailable",
    "params": {
      "listen": true
    }
  }
]
```

Response:

```json
[
  {
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
      {
        "uri": "/usb/my-usb-drive",
        "name": "My USB Drive",
        "type": "usb"
      },
      {
        "uri": "/local/photos",
        "name": "photos",
        "type": "local"
      }
    ]
  },
  {
    "jsonrpc": "2.0",
    "id": 2,
    "result": {
      "listening": true
    }
  },
  {
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
      "listening": true
    }
  },
  {
    "jsonrpc": "2.0",
    "id": 2,
    "result": {
      "uri": "/usb/my-usb-drive",
      "name": "My USB Drive",
      "type": "usb"
    }
  }
]
```

</details>

---

## Events

### onVolumeAvailable

_This is an private RPC method._

Access available Volumes with MediaFiles.

Parameters:

| Param           | Type      | Required | Description |
| --------------- | --------- | -------- | ----------- |
| `correlationId` | `string`  | true     |             |
| `query`         | ``        | true     |             |
| `listen`        | `boolean` | true     |             |

Result:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:media-access:volumes |


#### Examples


Default example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "MediaAccess.onVolumeAvailable",
	"params": {
		"correlationId": "xyz",
		"query": {},
		"listen": true
	}
}
````

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "uri": "/usb/my-usb-drive",
    "name": "My USB Drive",
    "type": "usb"
  }
}
```

---

### onVolumeUnavailable

_This is an private RPC method._

Access available Volumes with MediaFiles.

Parameters:

| Param           | Type      | Required | Description |
| --------------- | --------- | -------- | ----------- |
| `correlationId` | `string`  | true     |             |
| `query`         | ``        | true     |             |
| `listen`        | `boolean` | true     |             |

Result:

````typescript
```typescript

````

````

Capabilities:

| Role                  | Capability                 |
| --------------------- | -------------------------- |
| uses | xrn:firebolt:capability:media-access:volumes |


#### Examples


Default example #1

JSON-RPC:

Request:

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"method": "MediaAccess.onVolumeUnavailable",
	"params": {
		"correlationId": "xyz",
		"query": {},
		"listen": true
	}
}
````

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "uri": "/usb/my-usb-drive",
    "name": "My USB Drive",
    "type": "usb"
  }
}
```

---

## Types

### VolumeType

```typescript
VolumeType Enumeration:

| key | value |
|-----|-------|
| USB | usb |
| LOCAL | local |

```

---

### Volume

````typescript
```typescript

````

````

See also:



---

### MediaFile



```typescript
```typescript

````

```

See also:



---
```
