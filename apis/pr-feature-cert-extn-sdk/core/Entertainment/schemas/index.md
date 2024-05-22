---
title: Entertainment

version: pr-feature-cert-extn-sdk
layout: default
sdk: core
---

# Entertainment

---

Version Entertainment 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [OfferingType](#offeringtype)
  - [ProgramType](#programtype)
  - [MusicType](#musictype)
  - [ContentIdentifiers](#contentidentifiers)
  - [Entitlement](#entitlement)
  - [ContentRating](#contentrating)
- [United States](#united-states)
- [Canada](#canada)
  - [WayToWatch](#waytowatch)
  - [EntityInfo](#entityinfo)

## Overview

undefined

## Types

### OfferingType

The offering type of the WayToWatch.

```typescript
OfferingType Enumeration:

| key | value |
|-----|-------|
| FREE | free |
| SUBSCRIBE | subscribe |
| BUY | buy |
| RENT | rent |

```

---

### ProgramType

In the case of a program `entityType`, specifies the program type.

```typescript
ProgramType Enumeration:

| key | value |
|-----|-------|
| MOVIE | movie |
| EPISODE | episode |
| SEASON | season |
| SERIES | series |
| OTHER | other |
| PREVIEW | preview |
| EXTRA | extra |
| CONCERT | concert |
| SPORTING_EVENT | sportingEvent |
| ADVERTISEMENT | advertisement |
| MUSIC_VIDEO | musicVideo |
| MINISODE | minisode |

```

---

### MusicType

In the case of a music `entityType`, specifies the type of music entity.

```typescript
MusicType Enumeration:

| key | value |
|-----|-------|
| SONG | song |
| ALBUM | album |

```

---

### ContentIdentifiers

The ContentIdentifiers object is how the app identifies an entity or asset to
the Firebolt platform. These ids are used to look up metadata and deep link into
the app.

Apps do not need to provide all ids. They only need to provide the minimum
required to target a playable stream or an entity detail screen via a deep link.
If an id isn't needed to get to those pages, it doesn't need to be included.

````typescript
```typescript

````

````



---

### Entitlement



```typescript
```typescript

````

````



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
```typescript

````

````



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
```typescript

````

````

See also:





---

### EntityInfo

An EntityInfo object represents an "entity" on the platform. Currently, only entities of type `program` are supported. `programType` must be supplied to identify the program type.

Additionally, EntityInfo objects must specify a properly formed
ContentIdentifiers object, `entityType`, and `title`.  The app should provide
the `synopsis` property for a good user experience if the content
metadata is not available another way.

The ContentIdentifiers must be sufficient for navigating the user to the
appropriate entity or detail screen via a `detail` intent or deep link.

EntityInfo objects must provide at least one WayToWatch object when returned as
part of an `entityInfo` method and a streamable asset is available to the user.
It is optional for the `purchasedContent` method, but recommended because the UI
may use those data.

```typescript
```typescript

````

```

See also:







---
```
