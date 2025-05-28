---
title: Intents

version: pr-fix-force-viewingrestrictions-build
layout: default
sdk: manage
---

# Intents

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [Intent](#intent)
  - [IntentProperties](#intentproperties)
  - [EntityIntent](#entityintent)
  - [PlaybackIntent](#playbackintent)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [TuneIntent](#tuneintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlayQueryIntent](#playqueryintent)
  - [HomeIntent](#homeintent)
  - [LaunchIntent](#launchintent)
  - [NavigationIntent](#navigationintent)

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
type IntentProperties = {}
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
  context: {
    source: string
  }
}
```

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

[PlayableEntity](../Entity/schemas/#PlayableEntity)

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  action: 'search'
  data?: {
    query: string
    suggestions?:
      | ProgramEntity
      | MusicEntity
      | ChannelEntity
      | UntypedEntity
      | PlaylistEntity[]
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
  data: {
    sectionName: string
  }
  context: {
    source: string
  }
}
```

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
    // The options property of the data property MUST have only one of the following fields.
  }
  context: {
    source: string
  }
}
```

See also:

[ChannelEntity](../Entity/schemas/#ChannelEntity)

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

[PlayableEntity](../Entity/schemas/#PlayableEntity)

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

[ProgramType](../Entertainment/schemas/#ProgramType)
[MusicType](../Entertainment/schemas/#MusicType)

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
