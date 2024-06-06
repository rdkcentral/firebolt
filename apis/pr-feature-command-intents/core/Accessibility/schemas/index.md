---
title: Accessibility

version: pr-feature-command-intents
layout: default
sdk: core
---

# Accessibility

---

Version Accessibility 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [FontFamily](#fontfamily)
  - [VoiceSpeed](#voicespeed)
  - [VoiceGuidanceSettings](#voiceguidancesettings)
  - [FontSize](#fontsize)
  - [Color](#color)
  - [FontEdge](#fontedge)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [ClosedCaptionsSettings](#closedcaptionssettings)

## Overview

undefined

## Types

### FontFamily

```typescript

```

---

### VoiceSpeed

```typescript

```

---

### VoiceGuidanceSettings

```typescript
type VoiceGuidanceSettings = {
  enabled: boolean // Whether or not voice guidance should be enabled by default
  speed: VoiceSpeed // The speed at which voice guidance speech will be read back to the user
}
```

See also:

[VoiceSpeed](#voicespeed)

---

### FontSize

```typescript

```

---

### Color

```typescript

```

---

### FontEdge

```typescript

```

---

### Opacity

```typescript

```

---

### HorizontalAlignment

```typescript

```

---

### VerticalAlignment

```typescript

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

### ClosedCaptionsSettings

```typescript
type ClosedCaptionsSettings = {
  enabled: boolean // Whether or not closed-captions should be enabled by default
  styles: ClosedCaptionsStyles // The default styles to use when displaying closed-captions
  preferredLanguages?: string[]
}
```

See also:

[ClosedCaptionsStyles](#closedcaptionsstyles)

---
