---
title: Entity

version: pr-trigger-build
layout: default
sdk: manage
---

# Entity

---

Version Entity 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [MovieEntity](#movieentity)
  - [Metadata](#metadata)
  - [MusicEntity](#musicentity)
  - [ChannelEntity](#channelentity)
  - [UntypedEntity](#untypedentity)
  - [PlaylistEntity](#playlistentity)
  - [TVEpisodeEntity](#tvepisodeentity)
  - [TVSeasonEntity](#tvseasonentity)
  - [TVSeriesEntity](#tvseriesentity)
  - [AdditionalEntity](#additionalentity)
  - [ProgramEntity](#programentity)
  - [Entity](#entity)
  - [EntityDetails](#entitydetails)
  - [PlayableEntity](#playableentity)

## Overview

undefined

## Types

### MovieEntity

A Firebolt compliant representation of a Movie entity.

```typescript
type MovieEntity = {
  ENTITY_TYPE: 'program'
  PROGRAM_TYPE: 'movie'
  ENTITY_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### Metadata

```typescript
type Metadata = {
  TITLE?: string // Title of the entity.
  SYNOPSIS?: string // Short description of the entity.
  SEASON_NUMBER?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  SEASON_COUNT?: number // For TV series, seasons, and episodes, the total number of seasons.
  EPISODE_NUMBER?: number // For TV episodes, the episode number.
  EPISODE_COUNT?: number // For TV seasons and episodes, the total number of episodes in the current season.
  RELEASE_DATE?: string // The date that the program or entity was released or first aired.
  CONTENT_RATINGS?: ContentRating[] // A ContentRating represents an age or content based of an entity. Supported rating schemes and associated types are below.
}
```

See also:

[ContentRating](../Entertainment/schemas/#ContentRating)

---

### MusicEntity

```typescript
type MusicEntity = {
  ENTITY_TYPE: 'music'
  MUSIC_TYPE: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  ENTITY_ID: string
}
```

See also:

[MusicType](../Entertainment/schemas/#MusicType)

---

### ChannelEntity

```typescript
type ChannelEntity = {
  ENTITY_TYPE: 'channel'
  CHANNEL_TYPE: 'streaming' | 'overTheAir'
  ENTITY_ID: string // ID of the channel, in the target App's scope.
  APP_CONTENT_DATA?: string
}
```

---

### UntypedEntity

```typescript
type UntypedEntity = {
  ENTITY_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### PlaylistEntity

A Firebolt compliant representation of a Playlist entity.

```typescript
type PlaylistEntity = {
  ENTITY_TYPE: 'playlist'
  ENTITY_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### TVEpisodeEntity

A Firebolt compliant representation of a TV Episode entity.

```typescript
type TVEpisodeEntity = {
  ENTITY_TYPE: 'program'
  PROGRAM_TYPE: 'episode'
  ENTITY_ID: string
  SERIES_ID: string
  SEASON_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### TVSeasonEntity

A Firebolt compliant representation of a TV Season entity.

```typescript
type TVSeasonEntity = {
  ENTITY_TYPE: 'program'
  PROGRAM_TYPE: 'season'
  ENTITY_ID: string
  SERIES_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### TVSeriesEntity

A Firebolt compliant representation of a TV Series entity.

```typescript
type TVSeriesEntity = {
  ENTITY_TYPE: 'program'
  PROGRAM_TYPE: 'series'
  ENTITY_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

---

### AdditionalEntity

A Firebolt compliant representation of the remaining program entity types.

```typescript
type AdditionalEntity = {
  ENTITY_TYPE: 'program'
  PROGRAM_TYPE:
    | 'concert'
    | 'sportingEvent'
    | 'preview'
    | 'other'
    | 'advertisement'
    | 'musicVideo'
    | 'minisode'
    | 'extra'
  ENTITY_ID: string
  ASSET_ID?: string
  APP_CONTENT_DATA?: string
}
```

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

[MovieEntity](#movieentity)
[TVEpisodeEntity](#tvepisodeentity)
[TVSeasonEntity](#tvseasonentity)
[TVSeriesEntity](#tvseriesentity)
[AdditionalEntity](#additionalentity)

---

### Entity

```typescript

```

See also:

[ProgramEntity](#programentity)
[MusicEntity](#musicentity)
[ChannelEntity](#channelentity)
[UntypedEntity](#untypedentity)
[PlaylistEntity](#playlistentity)

---

### EntityDetails

```typescript
type EntityDetails = {
  IDENTIFIERS:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  INFO?: Metadata
  WAYS_TO_WATCH?: WayToWatch[] // A WayToWatch describes a way to watch a video program. It may describe a single
}
```

See also:

[Metadata](#metadata)
[WayToWatch](../Entertainment/schemas/#WayToWatch)

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

[MovieEntity](#movieentity)
[TVEpisodeEntity](#tvepisodeentity)
[PlaylistEntity](#playlistentity)
[MusicEntity](#musicentity)
[AdditionalEntity](#additionalentity)

---
