---
title: Intents

version: pr-feature-and-fixes-1-4-0
layout: default
sdk: discovery
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

## Overview

undefined

## Types

### Intent

A Firebolt compliant representation of a user intention.

```typescript

```

---

### IntentProperties

```typescript

```

---

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  ACTION: 'entity'
  DATA:
    | ProgramEntity
    | MusicEntity
    | ChannelEntity
    | UntypedEntity
    | PlaylistEntity
  CONTEXT: object
}
```

---

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  ACTION: 'playback'
  DATA: PlayableEntity
  CONTEXT: object
}
```

See also:

[PlayableEntity](../Entity/schemas/#PlayableEntity)

---

### SearchIntent

A Firebolt compliant representation of a user intention to navigate an app to it's search UI with a search term populated, and bring that app to the foreground if needed.

```typescript
type SearchIntent = {
  ACTION: 'search'
  DATA?: object
  CONTEXT: object
}
```

---

### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  ACTION: 'section'
  DATA: object
  CONTEXT: object
}
```

---

### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  ACTION: 'tune'
  DATA: object
  CONTEXT: object
}
```

See also:

[ChannelEntity](../Entity/schemas/#ChannelEntity)

---

### PlayEntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlayEntityIntent = {
  ACTION: 'play-entity'
  DATA: object
  CONTEXT: object
}
```

See also:

[PlayableEntity](../Entity/schemas/#PlayableEntity)

---

### PlayQueryIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for an abstract query to be searched for and played by the app.

```typescript
type PlayQueryIntent = {
  ACTION: 'play-query'
  DATA: object
  CONTEXT: object
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
  ACTION: 'home'
  CONTEXT: object
}
```

---

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  ACTION: 'launch'
  CONTEXT: object
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
