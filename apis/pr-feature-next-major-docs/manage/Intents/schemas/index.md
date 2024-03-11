---
title: Intents

version: pr-feature-next-major-docs
layout: default
sdk: manage
---

# Intents

---

Version Intents 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [Intent](#intent)
  - [IntentProperties](#intentproperties)
  - [ProgramEntity](#programentity)
  - [Identifier](#identifier)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [ChannelEntity](#channelentity)
  - [MusicEntity](#musicentity)
  - [PlayQueryIntent](#playqueryintent)
  - [HomeIntent](#homeintent)
  - [LaunchIntent](#launchintent)
  - [TVSeriesEntity](#tvseriesentity)
  - [PlaylistEntity](#playlistentity)
  - [TVSeasonEntity](#tvseasonentity)
  - [AdditionalEntity](#additionalentity)
  - [MovieEntity](#movieentity)
  - [TVEpisodeEntity](#tvepisodeentity)
  - [UntypedEntity](#untypedentity)
  - [EntityIntent](#entityintent)
  - [PlayableEntity](#playableentity)
  - [TuneIntent](#tuneintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlaybackIntent](#playbackintent)
  - [NavigationIntent](#navigationintent)

## Overview

undefined

## Types

### Intent

A Firebolt compliant representation of a user intention.

```typescript
type Intent = {
  action: string
  context: {
    source: string
  }
}
```

---

### IntentProperties

```typescript
type IntentProperties = {
  action: any
  data: any
  context: any
}
```

---

### ProgramEntity

```typescript
type ProgramEntity = {
  entityType: 'program'
  programType: ProgramType // In the case of a program `entityType`, specifies the program type.
  entityId: string
}
```

See also:

'movie' | 'episode' | 'season' | 'series' | 'other' | 'preview' | 'extra' | 'concert' | 'sportingEvent' | 'advertisement' | 'musicVideo' | 'minisode'

---

### Identifier

```typescript
type Identifier = string
```

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  action: 'search'
  data?: {
    query: string
  }
  context: {
    source: string
  }
}
```

---

### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  action: 'section'
  data?: {
    sectionName: string
  }
  context: {
    source: string
  }
}
```

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

### MusicEntity

```typescript
type MusicEntity = {
  entityType: 'music'
  musicType: MusicType // In the case of a music `entityType`, specifies the type of music entity.
  entityId: string
}
```

See also:

'song' | 'album'

---

### PlayQueryIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for an abstract query to be searched for and played by the app.

```typescript
type PlayQueryIntent = {
  action: 'play-query'
  data: {
    query: string
    options?: {
      programTypes?: ProgramType[]
      musicTypes?: MusicType[]
    }
  }
  context: {
    source: string
  }
}
```

See also:

'movie' | 'episode' | 'season' | 'series' | 'other' | 'preview' | 'extra' | 'concert' | 'sportingEvent' | 'advertisement' | 'musicVideo' | 'minisode'
'song' | 'album'

---

### HomeIntent

A Firebolt compliant representation of a user intention to navigate an app to it's home screen, and bring that app to the foreground if needed.

```typescript
type HomeIntent = {
  action: 'home'
  context: {
    source: string
  }
}
```

---

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: 'launch'
  context: {
    source: string
  }
}
```

---

### TVSeriesEntity

```typescript
type TVSeriesEntity = {
  entityType: 'program'
  programType: 'series'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

See also:

[ProgramEntity](#programentity)

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

See also:

[ProgramEntity](#programentity)

---

### AdditionalEntity

```typescript
type AdditionalEntity = {
  entityType: 'program'
  programType: ProgramType // In the case of a program `entityType`, specifies the program type.
  entityId: string
  assetId?: string
  appContentData?: string
}
```

See also:

[ProgramEntity](#programentity)

---

### MovieEntity

```typescript
type MovieEntity = {
  entityType: 'program'
  programType: 'movie'
  entityId: string
  assetId?: string
  appContentData?: string
}
```

See also:

[ProgramEntity](#programentity)

---

### TVEpisodeEntity

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

See also:

[ProgramEntity](#programentity)

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

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: 'entity'
  data:
    | MovieEntity
    | TVEpisodeEntity
    | TVSeriesEntity
    | TVSeasonEntity
    | MusicEntity
    | PlaylistEntity
    | AdditionalEntity
    | UntypedEntity
  context: {
    source: string
  }
}
```

See also:

[MovieEntity](#movieentity)
[TVEpisodeEntity](#tvepisodeentity)
[TVSeriesEntity](#tvseriesentity)
[TVSeasonEntity](#tvseasonentity)
[MusicEntity](#musicentity)
[PlaylistEntity](#playlistentity)
[AdditionalEntity](#additionalentity)
[UntypedEntity](#untypedentity)

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

### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  action: 'tune'
  data: {
    entity: ChannelEntity
    options?: {
      assetId?: string // The ID of a specific 'listing', as scoped by the target App's ID-space, which the App should begin playback from.
      restartCurrentProgram?: boolean // Denotes that the App should start playback at the most recent program boundary, rather than 'live.'
      time?: string // ISO 8601 Date/Time where the App should begin playback from.
    }
  }
  context: {
    source: string
  }
}
```

See also:

[ChannelEntity](#channelentity)

---

### PlayEntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlayEntityIntent = {
  action: 'play-entity'
  data: {
    entity: PlayableEntity
    options?: {
      playFirstId?: string
      playFirstTrack?: number
    }
  }
  context: {
    source: string
  }
}
```

See also:

MovieEntity | TVEpisodeEntity | PlaylistEntity | MusicEntity | AdditionalEntity

---

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: 'playback'
  data: PlayableEntity
  context: {
    source: string
  }
}
```

See also:

MovieEntity | TVEpisodeEntity | PlaylistEntity | MusicEntity | AdditionalEntity

---

### NavigationIntent

A Firebolt compliant representation of a user intention to navigate to a specific place in an app.

```typescript
type NavigationIntent =
  | HomeIntent
  | LaunchIntent
  | EntityIntent
  | PlaybackIntent
  | SearchIntent
  | SectionIntent
  | TuneIntent
  | PlayEntityIntent
  | PlayQueryIntent
```

See also:

[HomeIntent](#homeintent)
[LaunchIntent](#launchintent)
[EntityIntent](#entityintent)
[PlaybackIntent](#playbackintent)
[SearchIntent](#searchintent)
[SectionIntent](#sectionintent)
[TuneIntent](#tuneintent)
[PlayEntityIntent](#playentityintent)
[PlayQueryIntent](#playqueryintent)

---
