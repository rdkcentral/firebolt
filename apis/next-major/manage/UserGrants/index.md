---
title: UserGrants

version: next-major
layout: default
sdk: manage
---

# UserGrants Module

---

Version UserGrants 1.8.0-next-major.2

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [app](#app)
  - [capability](#capability)
  - [clear](#clear)
  - [deny](#deny)
  - [device](#device)
  - [grant](#grant)
  - [request](#request)
- [Types](#types)
  - [EDIDVersion](#edidversion)
  - [WifiSecurityMode](#wifisecuritymode)
  - [AudioProfile](#audioprofile)
  - [Role](#role)
  - [DenyReason](#denyreason)
  - [OfferingType](#offeringtype)
  - [MusicType](#musictype)
  - [ProgramType](#programtype)
  - [GrantModificationOptions](#grantmodificationoptions)
  - [RequestOptions](#requestoptions)
  - [HDMIPortId](#hdmiportid)
  - [WifiSignalStrength](#wifisignalstrength)
  - [WifiFrequency](#wififrequency)
  - [AccessPoint](#accesspoint)
  - [HDMISignalStatus](#hdmisignalstatus)
  - [SpeechRate](#speechrate)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [FontFamily](#fontfamily)
  - [FontSize](#fontsize)
  - [Color](#color)
  - [FontEdge](#fontedge)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ISO639_2Language](#isolanguage)
  - [Capability](#capability-1)
  - [Permission](#permission)
  - [EventObjectPrimitives](#eventobjectprimitives)
  - [CapPermissionStatus](#cappermissionstatus)
  - [EventObject](#eventobject)
  - [EntityDetails](#entitydetails)
  - [Entity](#entity)
  - [Metadata](#metadata)
  - [ProgramEntity](#programentity)
  - [MusicEntity](#musicentity)
  - [ChannelEntity](#channelentity)
  - [UntypedEntity](#untypedentity)
  - [PlaylistEntity](#playlistentity)
  - [MovieEntity](#movieentity)
  - [TVEpisodeEntity](#tvepisodeentity)
  - [TVSeasonEntity](#tvseasonentity)
  - [TVSeriesEntity](#tvseriesentity)
  - [AdditionalEntity](#additionalentity)
  - [PlayableEntity](#playableentity)
  - [WayToWatch](#waytowatch)
  - [GrantState](#grantstate)
  - [ContentIdentifiers](#contentidentifiers)
  - [ContentRating](#contentrating)
- [United States](#united-states)
- [Canada](#canada)
  - [AppInfo](#appinfo)
  - [GrantInfo](#grantinfo)
  - [EntityInfo](#entityinfo)
  - [AgePolicy](#agepolicy)
  - [HomeIntent](#homeintent)
  - [LaunchIntent](#launchintent)
  - [EntityIntent](#entityintent)
  - [PlaybackIntent](#playbackintent)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [TuneIntent](#tuneintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlayQueryIntent](#playqueryintent)
  - [Intent](#intent)
  - [IntentProperties](#intentproperties)
  - [ResultReason](#resultreason)

## Usage

To use the UserGrants module, you can import it into your project from the Firebolt SDK:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'
```

## Overview

A module for managing grants given by the user

## Methods

### app

Get all granted and denied user grants for the given app

```typescript
function app(appId: string): Promise<object[]>
```

Parameters:

| Param   | Type     | Required | Description |
| ------- | -------- | -------- | ----------- |
| `appId` | `string` | true     |             |

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.app('certapp')
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: { id: 'certapp', title: 'Firebolt Certification' },
    state: 'granted',
    capability: 'xrn:firebolt:capability:data:app-usage',
    role: 'use',
    lifespan: 'seconds',
    expires: '2022-12-14T20:20:39+00:00',
  },
  {
    app: { id: 'certapp', title: 'Firebolt Certification' },
    state: 'denied',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'appActive',
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
  "method": "UserGrants.app",
  "params": {
    "appId": "certapp"
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
      "app": {
        "id": "certapp",
        "title": "Firebolt Certification"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:data:app-usage",
      "role": "use",
      "lifespan": "seconds",
      "expires": "2022-12-14T20:20:39+00:00"
    },
    {
      "app": {
        "id": "certapp",
        "title": "Firebolt Certification"
      },
      "state": "denied",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "appActive"
    }
  ]
}
```

</details>

---

### capability

Get all granted and denied user grants for the given capability

```typescript
function capability(capability: Capabilities.Capability): Promise<object[]>
```

Parameters:

| Param        | Type                      | Required | Description                                                            |
| ------------ | ------------------------- | -------- | ---------------------------------------------------------------------- |
| `capability` | `Capabilities.Capability` | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.capability(
  'xrn:firebolt:capability:localization:postal-code',
)
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
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
  "method": "UserGrants.capability",
  "params": {
    "capability": "xrn:firebolt:capability:localization:postal-code"
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
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

### clear

Clears the grant for a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function clear(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description                                                            |
| ------------ | ------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | `Capabilities.Role`       | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | `Capabilities.Capability` | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                  | false    |                                                                        |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.clear(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
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
  "method": "UserGrants.clear",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### deny

Denies a given capability, to a specific app if appropriate. Calling this results in a persisted Denied Grant that lasts for the duration of the Grant Policy lifespan.

```typescript
function deny(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description                                                            |
| ------------ | ------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | `Capabilities.Role`       | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | `Capabilities.Capability` | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                  | false    |                                                                        |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.deny(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
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
  "method": "UserGrants.deny",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### device

Get all granted and denied user grants for the device

```typescript
function device(): Promise<object[]>
```

Promise resolution:

Capabilities:

| Role | Capability                           |
| ---- | ------------------------------------ |
| uses | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.device()
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
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
  "method": "UserGrants.device",
  "params": {}
}
```

Response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": [
    {
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

### grant

Grants a given capability to a specific app, if appropriate. Calling this results in a persisted active grant that lasts for the duration of the grant policy lifespan.

```typescript
function grant(
  role: Capabilities.Role,
  capability: Capabilities.Capability,
  options: object,
): Promise<void>
```

Parameters:

| Param        | Type                      | Required | Description                                                            |
| ------------ | ------------------------- | -------- | ---------------------------------------------------------------------- |
| `role`       | `Capabilities.Role`       | true     | <br/>values: `'use' \| 'manage' \| 'provide'`                          |
| `capability` | `Capabilities.Capability` | true     | <br/>pattern: ^xrn:firebolt:capability:([a-z0-9\-]+)((:[a-z0-9\-]+)?)$ |
| `options`    | `object`                  | false    |                                                                        |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default Example

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let result = await UserGrants.grant(
  'use',
  'xrn:firebolt:capability:localization:postal-code',
  { appId: 'certapp' },
)
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
  "method": "UserGrants.grant",
  "params": {
    "role": "use",
    "capability": "xrn:firebolt:capability:localization:postal-code",
    "options": {
      "appId": "certapp"
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

### request

Requests Firebolt to carry out a set of user grants for a given application such that the user grant provider is notified or an existing user grant is reused.

```typescript
function request(
  appId: string,
  permissions: Capabilities.Permission[],
  options: RequestOptions,
): Promise<object[]>
```

Parameters:

| Param         | Type                                | Required | Description     |
| ------------- | ----------------------------------- | -------- | --------------- |
| `appId`       | `string`                            | true     |                 |
| `permissions` | `Capabilities.Permission[]`         | true     |                 |
| `options`     | [`RequestOptions`](#requestoptions) | false    | Request options |

Promise resolution:

Capabilities:

| Role    | Capability                           |
| ------- | ------------------------------------ |
| manages | xrn:firebolt:capability:grants:state |

#### Examples

Default result #1

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.request('certapp', [
  {
    role: 'use',
    capability: 'xrn:firebolt:capability:localization:postal-code',
  },
])
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: { id: 'certapp', title: 'Certification App' },
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
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
  "method": "UserGrants.request",
  "params": {
    "appId": "certapp",
    "permissions": [
      {
        "role": "use",
        "capability": "xrn:firebolt:capability:localization:postal-code"
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
  "result": [
    {
      "app": {
        "id": "certapp",
        "title": "Certification App"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

Default result #2

JavaScript:

```javascript
import { UserGrants } from '@firebolt-js/manage-sdk'

let info = await UserGrants.request(
  'certapp',
  [
    {
      role: 'use',
      capability: 'xrn:firebolt:capability:localization:postal-code',
    },
  ],
  {
    force: true,
  },
)
console.log(info)
```

Value of `info`:

```javascript
;[
  {
    app: { id: 'certapp', title: 'Certification App' },
    state: 'granted',
    capability: 'xrn:firebolt:capability:localization:postal-code',
    role: 'use',
    lifespan: 'powerActive',
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
  "method": "UserGrants.request",
  "params": {
    "appId": "certapp",
    "permissions": [
      {
        "role": "use",
        "capability": "xrn:firebolt:capability:localization:postal-code"
      }
    ],
    "options": {
      "force": true
    }
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
      "app": {
        "id": "certapp",
        "title": "Certification App"
      },
      "state": "granted",
      "capability": "xrn:firebolt:capability:localization:postal-code",
      "role": "use",
      "lifespan": "powerActive"
    }
  ]
}
```

</details>

---

## Types

### EDIDVersion

```typescript
EDIDVersion: {
    V1_4: '1.4',
    V2_0: '2.0',
    UNKNOWN: 'unknown',
},

```

---

### WifiSecurityMode

Security Mode supported for Wifi

```typescript
WifiSecurityMode: {
    NONE: 'none',
    WEP_64: 'wep64',
    WEP_128: 'wep128',
    WPA_PSK_TKIP: 'wpaPskTkip',
    WPA_PSK_AES: 'wpaPskAes',
    WPA_2PSK_TKIP: 'wpa2PskTkip',
    WPA_2PSK_AES: 'wpa2PskAes',
    WPA_ENTERPRISE_TKIP: 'wpaEnterpriseTkip',
    WPA_ENTERPRISE_AES: 'wpaEnterpriseAes',
    WPA_2ENTERPRISE_TKIP: 'wpa2EnterpriseTkip',
    WPA_2ENTERPRISE_AES: 'wpa2EnterpriseAes',
    WPA_2PSK: 'wpa2Psk',
    WPA_2ENTERPRISE: 'wpa2Enterprise',
    WPA_3PSK_AES: 'wpa3PskAes',
    WPA_3SAE: 'wpa3Sae',
},

```

---

### AudioProfile

```typescript
AudioProfile: {
    STEREO: 'stereo',
    DOLBY_DIGITAL_5_1: 'dolbyDigital5.1',
    DOLBY_DIGITAL_5_1_PLUS: 'dolbyDigital5.1+',
    DOLBY_ATMOS: 'dolbyAtmos',
},

```

---

### Role

Role provides access level for the app for a given capability.

```typescript
Role: {
    USE: 'use',
    MANAGE: 'manage',
    PROVIDE: 'provide',
},

```

---

### DenyReason

Reasons why a Capability might not be invokable

```typescript
DenyReason: {
    UNPERMITTED: 'unpermitted',
    UNSUPPORTED: 'unsupported',
    DISABLED: 'disabled',
    UNAVAILABLE: 'unavailable',
    GRANT_DENIED: 'grantDenied',
    UNGRANTED: 'ungranted',
},

```

---

### OfferingType

The offering type of the WayToWatch.

```typescript
OfferingType: {
    FREE: 'free',
    SUBSCRIBE: 'subscribe',
    BUY: 'buy',
    RENT: 'rent',
},

```

---

### MusicType

In the case of a music `entityType`, specifies the type of music entity.

```typescript
MusicType: {
    SONG: 'song',
    ALBUM: 'album',
},

```

---

### ProgramType

In the case of a program `entityType`, specifies the program type.

```typescript
ProgramType: {
    MOVIE: 'movie',
    EPISODE: 'episode',
    SEASON: 'season',
    SERIES: 'series',
    OTHER: 'other',
    PREVIEW: 'preview',
    EXTRA: 'extra',
    CONCERT: 'concert',
    SPORTING_EVENT: 'sportingEvent',
    ADVERTISEMENT: 'advertisement',
    MUSIC_VIDEO: 'musicVideo',
    MINISODE: 'minisode',
},

```

---

### GrantModificationOptions

Options when modifying any grant

```typescript
type GrantModificationOptions = {
  appId?: string
}
```

---

### RequestOptions

```typescript
type RequestOptions = {
  force?: boolean // Whether to force for user grant even if the previous decision stored
}
```

---

### HDMIPortId

```typescript
type HDMIPortId = string
```

---

### WifiSignalStrength

Strength of Wifi signal, value is negative based on RSSI specification.

```typescript
type WifiSignalStrength = number
```

---

### WifiFrequency

Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.

```typescript
type WifiFrequency = number
```

---

### AccessPoint

Properties of a scanned wifi list item.

```typescript
type AccessPoint = {
  ssid?: string // Name of the wifi.
  securityMode?: WifiSecurityMode // Security Mode supported for Wifi
  signalStrength?: WifiSignalStrength // Strength of Wifi signal, value is negative based on RSSI specification.
  frequency?: WifiFrequency // Wifi Frequency in Ghz, example 2.4Ghz and 5Ghz.
}
```

See also:

[WifiSecurityMode](#wifisecuritymode)
[WifiSignalStrength](#wifisignalstrength)
[WifiFrequency](#wififrequency)

---

### HDMISignalStatus

```typescript
HDMISignalStatus: {
    NONE: 'none',
    STABLE: 'stable',
    UNSTABLE: 'unstable',
    UNSUPPORTED: 'unsupported',
    UNKNOWN: 'unknown',
},

```

---

### SpeechRate

```typescript
type SpeechRate = number
```

---

### ClosedCaptionsStyles

The default styles to use when displaying closed-captions

```typescript
type ClosedCaptionsStyles = {
  fontFamily?: string
  fontSize?: number
  fontColor?: string
  fontEdge?: string
  fontEdgeColor?: string
  fontOpacity?: number
  backgroundColor?: string
  backgroundOpacity?: number
  textAlign?: string
  textAlignVertical?: string
  windowColor?: string
  windowOpacity?: number
}
```

---

### FontFamily

```typescript
FontFamily: {
    MONOSPACED_SERIF: 'monospaced_serif',
    PROPORTIONAL_SERIF: 'proportional_serif',
    MONOSPACED_SANSERIF: 'monospaced_sanserif',
    PROPORTIONAL_SANSERIF: 'proportional_sanserif',
    SMALLCAPS: 'smallcaps',
    CURSIVE: 'cursive',
    CASUAL: 'casual',
},

```

---

### FontSize

```typescript
type FontSize = number
```

---

### Color

```typescript
type Color = string
```

---

### FontEdge

```typescript
FontEdge: {
    NONE: 'none',
    RAISED: 'raised',
    DEPRESSED: 'depressed',
    UNIFORM: 'uniform',
    DROP_SHADOW_LEFT: 'drop_shadow_left',
    DROP_SHADOW_RIGHT: 'drop_shadow_right',
},

```

---

### Opacity

```typescript
type Opacity = number
```

---

### HorizontalAlignment

```typescript
type HorizontalAlignment = string
```

---

### VerticalAlignment

```typescript
type VerticalAlignment = string
```

---

### ISO639_2Language

```typescript
type ISO639_2Language = string
```

---

### Capability

A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.

```typescript
type Capability = string
```

---

### Permission

A capability combined with a Role, which an app may be permitted (by a distributor) or granted (by an end user).

```typescript
type Permission = {
  role?: Role // Role provides access level for the app for a given capability.
  capability: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
}
```

See also:

Capabilities.Role
Capabilities.Capability

---

### EventObjectPrimitives

```typescript
type EventObjectPrimitives = string | number | number | boolean | null
```

---

### CapPermissionStatus

```typescript
type CapPermissionStatus = {
  permitted?: boolean // Provides info whether the capability is permitted
  granted?: boolean
}
```

---

### EventObject

```typescript
type EventObject = [property: string]: EventObjectPrimitives | EventObjectPrimitives | EventObject[] | EventObject
```

See also:

[EventObjectPrimitives](#eventobjectprimitives)
[EventObject](#eventobject-1)

---

### EntityDetails

```typescript
type EntityDetails = {
  identifiers:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  info?: Metadata
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entity.Metadata
Entertainment.WayToWatch

---

### Entity

```typescript
type Entity =
  | ProgramEntity
  | MusicEntity
  | ChannelEntity
  | UntypedEntity
  | PlaylistEntity
```

See also:

Entity.ProgramEntity
Entity.MusicEntity
Entity.ChannelEntity
Entity.UntypedEntity
Entity.PlaylistEntity

---

### Metadata

```typescript
type Metadata = {
  title?: string // Title of the entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
}
```

See also:

Entertainment.ContentRating

---

### ProgramEntity

```typescript
type ProgramEntity =
  | MovieEntity
  | TVEpisodeEntity
  | TVSeasonEntity
  | TVSeriesEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.TVSeasonEntity
Entity.TVSeriesEntity
Entity.AdditionalEntity

---

### MusicEntity

```typescript
type MusicEntity = {
  entityType: 'music'
  musicType: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  entityId: string
}
```

See also:

Entertainment.MusicType

---

### ChannelEntity

```typescript
type ChannelEntity = {
  entityType: 'channel'
  channelType: 'streaming' | 'overTheAir'
  entityId: string // ID of the channel, in the target App's scope.
  appContentData?: string
}
```

---

### UntypedEntity

```typescript
type UntypedEntity = {
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlaylistEntity

A Firebolt compliant representation of a Playlist entity.

```typescript
type PlaylistEntity = {
  entityType: 'playlist'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### MovieEntity

A Firebolt compliant representation of a Movie entity.

```typescript
type MovieEntity = {
  entityType: 'program'
  programType: 'movie'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVEpisodeEntity

A Firebolt compliant representation of a TV Episode entity.

```typescript
type TVEpisodeEntity = {
  entityType: 'program'
  programType: 'episode'
  entityId: string
  seriesId: string
  seasonId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeasonEntity

A Firebolt compliant representation of a TV Season entity.

```typescript
type TVSeasonEntity = {
  entityType: 'program'
  programType: 'season'
  entityId: string
  seriesId: string
  assetId?: string
  appContentData?: string
}
```

---

### TVSeriesEntity

A Firebolt compliant representation of a TV Series entity.

```typescript
type TVSeriesEntity = {
  entityType: 'program'
  programType: 'series'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### AdditionalEntity

A Firebolt compliant representation of the remaining program entity types.

```typescript
type AdditionalEntity = {
  entityType: 'program'
  programType:
    | 'concert'
    | 'sportingEvent'
    | 'preview'
    | 'other'
    | 'advertisement'
    | 'musicVideo'
    | 'minisode'
    | 'extra'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

---

### PlayableEntity

```typescript
type PlayableEntity =
  | MovieEntity
  | TVEpisodeEntity
  | PlaylistEntity
  | MusicEntity
  | AdditionalEntity
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.PlaylistEntity
Entity.MusicEntity
Entity.AdditionalEntity

---

### WayToWatch

A WayToWatch describes a way to watch a video program. It may describe a single
streamable asset or a set of streamable assets. For example, an app provider may
describe HD, SD, and UHD assets as individual WayToWatch objects or rolled into
a single WayToWatch.

If the WayToWatch represents a single streamable asset, the provided
ContentIdentifiers must be sufficient to play back the specific asset when sent
via a playback intent or deep link. If the WayToWatch represents multiple
streamable assets, the provided ContentIdentifiers must be sufficient to
playback one of the assets represented with no user action. In this scenario,
the app SHOULD choose the best asset for the user based on their device and
settings. The ContentIdentifiers MUST also be sufficient for navigating the user
to the appropriate entity or detail screen via an entity intent.

The app should set the `entitled` property to indicate if the user can watch, or
not watch, the asset without making a purchase. If the entitlement is known to
expire at a certain time (e.g., a rental), the app should also provide the
`entitledExpires` property. If the entitlement is not expired, the UI will use
the `entitled` property to display watchable assets to the user, adjust how
assets are presented to the user, and how intents into the app are generated.
For example, the the Aggregated Experience could render a "Watch" button for an
entitled asset versus a "Subscribe" button for an non-entitled asset.

The app should set the `offeringType` to define how the content may be
authorized. The UI will use this to adjust how content is presented to the user.

A single WayToWatch cannot represent streamable assets available via multiple
purchase paths. If, for example, an asset has both Buy, Rent and Subscription
availability, the three different entitlement paths MUST be represented as
multiple WayToWatch objects.

`price` should be populated for WayToWatch objects with `buy` or `rent`
`offeringType`. If the WayToWatch represents a set of assets with various price
points, the `price` provided must be the lowest available price.

```typescript
type WayToWatch = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  expires?: string // Time when the WayToWatch is no longer available.
  entitled?: boolean // Specify if the user is entitled to watch the entity.
  entitledExpires?: string // Time when the entity is no longer entitled.
  offeringType?: OfferingType // The offering type of the WayToWatch.
  hasAds?: boolean // True if the streamable asset contains ads.
  price?: number // For "buy" and "rent" WayToWatch, the price to buy or rent in the user's preferred currency.
  videoQuality?: 'SD' | 'HD' | 'UHD'[] // List of the video qualities available via the WayToWatch.
  audioProfile: AudioProfile[] // List of the audio types available via the WayToWatch.
  audioLanguages?: string[] // List of audio track languages available on the WayToWatch. The first is considered the primary language. Languages are expressed as ISO 639 1/2 codes.
  closedCaptions?: string[] // List of languages for which closed captions are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  subtitles?: string[] // List of languages for which subtitles are available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
  audioDescriptions?: string[] // List of languages for which audio descriptions (DVD) as available on the WayToWatch. Languages are expressed as ISO 639 1/2 codes.
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.OfferingType
Types.AudioProfile

---

### GrantState

The state the grant is in

```typescript
GrantState: {
    GRANTED: 'granted',
    DENIED: 'denied',
},

```

---

### ContentIdentifiers

The ContentIdentifiers object is how the app identifies an entity or asset to
the Firebolt platform. These ids are used to look up metadata and deep link into
the app.

Apps do not need to provide all ids. They only need to provide the minimum
required to target a playable stream or an entity detail screen via a deep link.
If an id isn't needed to get to those pages, it doesn't need to be included.

```typescript
type ContentIdentifiers = {
  assetId?: string // Identifies a particular playable asset. For example, the HD version of a particular movie separate from the UHD version.
  entityId?: string // Identifies an entity, such as a Movie, TV Series or TV Episode.
  seasonId?: string // The TV Season for a TV Episode.
  seriesId?: string // The TV Series for a TV Episode or TV Season.
  appContentData?: string // App-specific content identifiers.
}
```

---

### ContentRating

A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.

## United States

`US-Movie` (MPAA):

Ratings: `NR`, `G`, `PG`, `PG13`, `R`, `NC17`

Advisories: `AT`, `BN`, `SL`, `SS`, `N`, `V`

`US-TV` (Vchip):

Ratings: `TVY`, `TVY7`, `TVG`, `TVPG`, `TV14`, `TVMA`

Advisories: `FV`, `D`, `L`, `S`, `V`

## Canada

`CA-Movie` (OFRB):

Ratings: `G`, `PG`, `14A`, `18A`, `R`, `E`

`CA-TV` (AGVOT)

Ratings: `E`, `C`, `C8`, `G`, `PG`, `14+`, `18+`

Advisories: `C`, `C8`, `G`, `PG`, `14+`, `18+`

`CA-Movie-Fr` (Canadian French language movies):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

`CA-TV-Fr` (Canadian French language TV):

Ratings: `G`, `8+`, `13+`, `16+`, `18+`

```typescript
type ContentRating = {
  scheme:
    | 'CA-Movie'
    | 'CA-TV'
    | 'CA-Movie-Fr'
    | 'CA-TV-Fr'
    | 'US-Movie'
    | 'US-TV' // The rating scheme.
  rating: string // The content rating.
  advisories?: string[] // Optional list of subratings or content advisories.
}
```

---

### AppInfo

Information about an app that a grant was for

```typescript
type AppInfo = {
  id: string
  title?: string
}
```

---

### GrantInfo

Information about a grant given by a user

```typescript
type GrantInfo = {
  app?: object // Information about an app that a grant was for
  state: 'granted' | 'denied' // The state the grant is in
  capability: Capability // A Capability is a discrete unit of functionality that a Firebolt device might be able to perform.
  role: Role // Role provides access level for the app for a given capability.
  lifespan: 'once' | 'forever' | 'appActive' | 'powerActive' | 'seconds'
  expires?: string
}
```

See also:

Capabilities.Capability
Capabilities.Role

---

### EntityInfo

An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.

Additionally, EntityInfo objects must specify a properly formed
ContentIdentifiers object, `entityType`, and `title`. The app should provide
the `synopsis` property for a good user experience if the content
metadata is not available another way.

The ContentIdentifiers must be sufficient for navigating the user to the
appropriate entity or detail screen via a `detail` intent or deep link.

EntityInfo objects must provide at least one WayToWatch object when returned as
part of an `entityInfo` method and a streamable asset is available to the user.
It is optional for the `purchasedContent` method, but recommended because the UI
may use those data.

```typescript
type EntityInfo = {
  identifiers: ContentIdentifiers // The ContentIdentifiers object is how the app identifies an entity or asset to
  title: string // Title of the entity.
  entityType: 'program' | 'music' // The type of the entity, e.g. `program` or `music`.
  programType?: ProgramType // In the case of a program `entityType`, specifies the program type.
  musicType?: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
  waysToWatch?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

Entertainment.ContentIdentifiers
Entertainment.ProgramType
Entertainment.MusicType
Entertainment.ContentRating
Entertainment.WayToWatch

---

### AgePolicy

The policy that describes various age groups to which content is directed. See distributor documentation for further details.

```typescript
type AgePolicy = string | 'app:adult' | 'app:child' | 'app:teen'
```

---

### HomeIntent

A Firebolt compliant representation of a user intention to navigate an app to it's home screen, and bring that app to the foreground if needed.

```typescript
type HomeIntent = {
  action: 'home'
  context: object
}
```

---

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: 'launch'
  context: object
}
```

---

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: 'entity'
  data:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  context: object
}
```

---

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: 'playback'
  data: PlayableEntity
  context: object
}
```

See also:

Entity.PlayableEntity

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  action: 'search'
  data?: object
  context: object
}
```

---

### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  action: 'section'
  data: object
  context: object
}
```

---

### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  action: 'tune'
  data: object
  context: object
}
```

See also:

Entity.ChannelEntity

---

### PlayEntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlayEntityIntent = {
  action: 'play-entity'
  data: object
  context: object
}
```

See also:

Entity.PlayableEntity

---

### PlayQueryIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for an abstract query to be searched for and played by the app.

```typescript
type PlayQueryIntent = {
  action: 'play-query'
  data: object
  context: object
}
```

See also:

Entertainment.ProgramType
Entertainment.MusicType

---

### Intent

A Firebolt compliant representation of a user intention.

```typescript
type Intent = {
  action: string
  context: object
}
```

See also:

Policies.AgePolicy

---

### IntentProperties

```typescript
type IntentProperties = {}
```

---

### ResultReason

The reason for the result of challenging the user

```typescript
ResultReason: {
    NO_PIN_REQUIRED: 'noPinRequired',
    NO_PIN_REQUIRED_WINDOW: 'noPinRequiredWindow',
    EXCEEDED_PIN_FAILURES: 'exceededPinFailures',
    CORRECT_PIN: 'correctPin',
    CANCELLED: 'cancelled',
},

```

---
