---
title: Intents

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Intents

---

Version 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [AppIntentMessage](#appintentmessage)
  - [PlatformIntentMessage](#platformintentmessage)
  - [NavigationIntent](#navigationintent)
  - [LaunchIntent](#launchintent)
  - [HomeIntent](#homeintent)
  - [EntityIntent](#entityintent)
  - [ChannelIntent](#channelintent)
  - [TuneIntent](#tuneintent)
  - [PlaybackIntent](#playbackintent)
  - [SearchIntent](#searchintent)
  - [SectionIntent](#sectionintent)
  - [PlayEntityIntent](#playentityintent)
  - [PlayQueryIntent](#playqueryintent)
  - [ContentDiscoveryIntent](#contentdiscoveryintent)
  - [EntityAppSelectionIntent](#entityappselectionintent)
  - [FocusIntent](#focusintent)
  - [SelectIntent](#selectintent)
  - [BackIntent](#backintent)
  - [ExitIntent](#exitintent)
  - [ScrollIntent](#scrollintent)
  - [ButtonIntent](#buttonintent)
  - [VolumeIntent](#volumeintent)
  - [MuteIntent](#muteintent)
  - [PowerIntent](#powerintent)
  - [MicrophoneIntent](#microphoneintent)
  - [InputIntent](#inputintent)
  - [PauseIntent](#pauseintent)
  - [PlayIntent](#playintent)
  - [ReplayIntent](#replayintent)
  - [StopIntent](#stopintent)
  - [PlaybackSpeedIntent](#playbackspeedintent)
  - [FastForwardIntent](#fastforwardintent)
  - [RewindIntent](#rewindintent)
  - [SeekIntent](#seekintent)
  - [SkipIntent](#skipintent)
  - [ClosedCaptionsIntent](#closedcaptionsintent)
  - [VoiceGuidanceIntent](#voiceguidanceintent)
  - [AudioDescriptionsIntent](#audiodescriptionsintent)
  - [HighContrastIntent](#highcontrastintent)
  - [ScreenMagnificationIntent](#screenmagnificationintent)
  - [MessageIntent](#messageintent)

## Overview

undefined

## Types

### AppIntentMessage

A message sent to a Firebolt app.

```typescript
type AppIntentMessage = {
  appId: string
  intent: NavigationIntent // A Firebolt compliant representation of a user intention to navigate to a specific place in an app.
  metadata?: object
  type: string
}
```

See also:

[NavigationIntent](#navigationintent)

---

### PlatformIntentMessage

A message sent to the Firebolt platform.

```typescript
type PlatformIntentMessage = {
  intent:
    | ContentDiscoveryIntent
    | EntityAppSelectionIntent
    | PlayIntent
    | PauseIntent
    | ReplayIntent
    | StopIntent
    | PlaybackSpeedIntent
    | SeekIntent
    | SkipIntent
    | FastForwardIntent
    | RewindIntent
    | ClosedCaptionsIntent
    | AudioDescriptionsIntent
    | ButtonIntent
    | FocusIntent
    | SelectIntent
    | BackIntent
    | ExitIntent
    | ChannelIntent
    | ScrollIntent
    | PowerIntent
    | VolumeIntent
    | MuteIntent
    | MicrophoneIntent
    | InputIntent
    | TuneIntent
    | VoiceGuidanceIntent
    | HighContrastIntent
    | ScreenMagnificationIntent
    | MessageIntent
  metadata?: object
  type: string
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

### LaunchIntent

A Firebolt compliant representation of a user intention to launch an app.

```typescript
type LaunchIntent = {
  action: 'launch'
  context: object
}
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

### EntityIntent

A Firebolt compliant representation of a user intention to navigate an app to a specific entity page, and bring that app to the foreground if needed.

```typescript
type EntityIntent = {
  action: 'entity'
  data:
    | Entity.ProgramEntity
    | Entity.MusicEntity
    | Entity.ChannelEntity
    | Entity.UntypedEntity
    | Entity.PlaylistEntity
  context: object
}
```

---

### ChannelIntent

A Firebolt compliant representation of a user intent to 'surf' to the next or previous channel.

```typescript
type ChannelIntent = {
  action: 'channel'
  data: 'next' | 'previous'
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

### PlaybackIntent

A Firebolt compliant representation of a user intention to navigate an app to a the video player for a specific, playable entity, and bring that app to the foreground if needed.

```typescript
type PlaybackIntent = {
  action: 'playback'
  data: Entity.PlayableEntity
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

### ContentDiscoveryIntent

A Firebolt compliant representation of a user intention to discover content with out a clear specific entity match.

```typescript
type ContentDiscoveryIntent = {
  action: 'discovery'
  data: object
  context: object
}
```

---

### EntityAppSelectionIntent

A Firebolt compliant representation of a user intention to navigate to a specific entity that could be served by more than one app.

```typescript
type EntityAppSelectionIntent = {
  action: 'entityAppSelection'
  data: object
  context: object
}
```

See also:

Entity.MovieEntity
Entity.TVEpisodeEntity
Entity.TVSeriesEntity
Entity.TVSeasonEntity
Entity.AdditionalEntity

---

### FocusIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing remote directional pad buttons.

```typescript
type FocusIntent = {
  action: 'focus'
  data: object
  context: object
}
```

---

### SelectIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing the remote 'select' button.

```typescript
type SelectIntent = {
  action: 'select'
  context: object
}
```

---

### BackIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing the remote 'back' button.

```typescript
type BackIntent = {
  action: 'back'
  context: object
}
```

---

### ExitIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing the remote 'back' button.

```typescript
type ExitIntent = {
  action: 'exit'
  context: object
}
```

---

### ScrollIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing remote directional pad buttons.

```typescript
type ScrollIntent = {
  action: 'scroll'
  data: object
  context: object
}
```

---

### ButtonIntent

A Firebolt compliant representation of a user intention to interact with their device in a way analogous to pressing one of the remote buttons.

```typescript
type ButtonIntent = {
  action: 'button'
  data?: object
  context: object
}
```

---

### VolumeIntent

A Firebolt compliant representation of a user intention to change the device volume.

```typescript
type VolumeIntent = {
  action: 'volume'
  data?: object
  context: object
}
```

---

### MuteIntent

A Firebolt compliant representation of a user intention to mute or unmute the device.

```typescript
type MuteIntent = {
  action: 'mute'
  data?: object
  context: object
}
```

---

### PowerIntent

A Firebolt compliant representation of a user intention to turn their device on or off.

```typescript
type PowerIntent = {
  action: 'power'
  data?: object
  context: object
}
```

---

### MicrophoneIntent

A Firebolt compliant representation of a user intention to turn their microphone on or off.

```typescript
type MicrophoneIntent = {
  action: 'microphone'
  data?: object
  context: object
}
```

---

### InputIntent

A Firebolt compliant representation of a user intention to change which video input is active.

```typescript
type InputIntent = {
  action: 'input'
  data?: object
  context: object
}
```

---

### PauseIntent

A Firebolt compliant representation of a user intention to pause in-progress playback.

```typescript
type PauseIntent = {
  action: 'pause'
  context: object
}
```

---

### PlayIntent

A Firebolt compliant representation of a user intention to play/resume content.

```typescript
type PlayIntent = {
  action: 'play'
  context: object
}
```

---

### ReplayIntent

A Firebolt compliant representation of a user intention to replay content.

```typescript
type ReplayIntent = {
  action: 'replay'
  context: object
}
```

---

### StopIntent

A Firebolt compliant representation of a user intention to stop content.

```typescript
type StopIntent = {
  action: 'stop'
  context: object
}
```

---

### PlaybackSpeedIntent

A Firebolt compliant representation of a user intention to change the speed of in-progress playback.

```typescript
type PlaybackSpeedIntent = {
  action: 'speed'
  data?: object
  context: object
}
```

---

### FastForwardIntent

A Firebolt compliant representation of a user intention to fast-forward in-progress playback.

```typescript
type FastForwardIntent = {
  action: 'fast-forward'
  data?: object
  context: object
}
```

---

### RewindIntent

A Firebolt compliant representation of a user intention to rewind in-progress playback.

```typescript
type RewindIntent = {
  action: 'rewind'
  data?: object
  context: object
}
```

---

### SeekIntent

A Firebolt compliant representation of a user intention to seek to a different time for in-progress playback.

```typescript
type SeekIntent = {
  action: 'seek'
  data?: object
  context: object
}
```

---

### SkipIntent

A Firebolt compliant representation of a user intention to skip a scene/chapter/ad during in-progress playback.

```typescript
type SkipIntent = {
  action: 'skip'
  data?: object
  context: object
}
```

---

### ClosedCaptionsIntent

A Firebolt compliant representation of a user intention to enable/disable closed captions.

```typescript
type ClosedCaptionsIntent = {
  action: 'closed-captions'
  data?: object
  context: object
}
```

---

### VoiceGuidanceIntent

A Firebolt compliant representation of a user intention to enable/disable voice guidance.

```typescript
type VoiceGuidanceIntent = {
  action: 'voice-guidance'
  data?: object
  context: object
}
```

---

### AudioDescriptionsIntent

A Firebolt compliant representation of a user intention to enable/disable audio descriptions.

```typescript
type AudioDescriptionsIntent = {
  action: 'audio-descriptions'
  data?: object
  context: object
}
```

---

### HighContrastIntent

A Firebolt compliant representation of a user intention to enable or disable high contrast mode.

```typescript
type HighContrastIntent = {
  action: 'high-contrast'
  data?: object
  context: object
}
```

---

### ScreenMagnificationIntent

A Firebolt compliant representation of a user intention to turn screen magnification on or off.

```typescript
type ScreenMagnificationIntent = {
  action: 'screen-magnification'
  data?: object
  context: object
}
```

---

### MessageIntent

A Firebolt compliant representation of a platform intention to display a message on the device.

```typescript
type MessageIntent = {
  action: 'message'
  data?: object
  context: object
}
```

---
