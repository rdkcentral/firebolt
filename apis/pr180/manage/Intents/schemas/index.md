---
title: Intents

version: pr180
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
     - [HomeIntent](#homeintent)
     - [LaunchIntent](#launchintent)
     - [TVSeriesEntity](#tvseriesentity)
     - [AdditionalEntity](#additionalentity)
     - [TVSeasonEntity](#tvseasonentity)
     - [UntypedEntity](#untypedentity)
     - [MovieEntity](#movieentity)
     - [TVEpisodeEntity](#tvepisodeentity)
     - [TuneIntent](#tuneintent)
     - [PlaybackIntent](#playbackintent)
     - [EntityIntent](#entityintent)
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
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
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
  entityType: "program"
  programType: ProgramType  // In the case of a program `entityType`, specifies the program type.
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
  action: "search"
  data?: {
    query: string
  }
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```



---
### SectionIntent

A Firebolt compliant representation of a user intention to navigate an app to a section not covered by `home`, `entity`, `player`, or `search`, and bring that app to the foreground if needed.

```typescript
type SectionIntent = {
  action: "section"
  data?: {
    sectionName: string
  }
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```



---
### ChannelEntity



```typescript
type ChannelEntity = {
  entityType: "channel"
  channelType: 'streaming' | 'overTheAir'
  entityId: string                         // ID of the channel, in the target App's scope.
  appContentData?: string
}
```



---
### HomeIntent

A Firebolt compliant representation of a user intention to navigate an app to it's home screen, and bring that app to the foreground if needed.

```typescript
type HomeIntent = {
  action: "home"
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```



---
### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: "launch"
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```



---
### TVSeriesEntity



```typescript
type TVSeriesEntity = {
  entityType: "program"
  programType: "series"
  entityId: string
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
  entityType: "program"
  programType: ProgramType  // In the case of a program `entityType`, specifies the program type.
  entityId: string
  assetId?: string
  appContentData?: string
}
```

See also: 

[ProgramEntity](#programentity)

---
### TVSeasonEntity

A Firebolt compliant representation of a TV Season entity.

```typescript
type TVSeasonEntity = {
  entityType: "program"
  programType: "season"
  entityId: string
  seriesId: string
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
### MovieEntity



```typescript
type MovieEntity = {
  entityType: "program"
  programType: "movie"
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
  entityType: "program"
  programType: "episode"
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
### TuneIntent

A Firebolt compliant representation of a user intention to 'tune' to a traditional over-the-air broadcast, or an OTT Stream from an OTT or vMVPD App.

```typescript
type TuneIntent = {
  action: "tune"
  data: {
    entity: ChannelEntity
    options?: {
      assetId?: string                                           // The ID of a specific 'listing', as scoped by the target App's ID-space, which the App should begin playback from.
      restartCurrentProgram?: boolean                            // Denotes that the App should start playback at the most recent program boundary, rather than 'live.'
      time?: string                                              // ISO 8601 Date/Time where the App should begin playback from.
    }
  }
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```

See also: 

[ChannelEntity](#channelentity)

---
### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: "playback"
  data: MovieEntity | TVEpisodeEntity | AdditionalEntity
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```

See also: 

[MovieEntity](#movieentity)
[TVEpisodeEntity](#tvepisodeentity)
[AdditionalEntity](#additionalentity)

---
### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: "entity"
  data: MovieEntity | TVEpisodeEntity | TVSeriesEntity | TVSeasonEntity | AdditionalEntity | UntypedEntity
  context: {
    source: 'voice' | 'channel-lineup' | 'editorial' | 'device'
  }
}
```

See also: 

[MovieEntity](#movieentity)
[TVEpisodeEntity](#tvepisodeentity)
[TVSeriesEntity](#tvseriesentity)
[TVSeasonEntity](#tvseasonentity)
[AdditionalEntity](#additionalentity)
[UntypedEntity](#untypedentity)

---
### NavigationIntent

A Firebolt compliant representation of a user intention to navigate to a specific place in an app.

```typescript
type NavigationIntent = HomeIntent | LaunchIntent | EntityIntent | PlaybackIntent | SearchIntent | SectionIntent | TuneIntent
```

See also: 

[HomeIntent](#homeintent)
[LaunchIntent](#launchintent)
[EntityIntent](#entityintent)
[PlaybackIntent](#playbackintent)
[SearchIntent](#searchintent)
[SectionIntent](#sectionintent)
[TuneIntent](#tuneintent)

---