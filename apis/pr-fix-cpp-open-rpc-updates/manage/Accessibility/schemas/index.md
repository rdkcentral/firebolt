---
title: Accessibility

version: pr-fix-cpp-open-rpc-updates
layout: default
sdk: manage
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
  ENABLED: boolean // Whether or not voice guidance should be enabled by default
  SPEED?: VoiceSpeed // The speed at which voice guidance speech will be read back to the user
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
  FONT_FAMILY?: string
  FONT_SIZE?: number
  FONT_COLOR?: string
  FONT_EDGE?: string
  FONT_EDGE_COLOR?: string
  FONT_OPACITY?: number
  BACKGROUND_COLOR?: string
  BACKGROUND_OPACITY?: number
  TEXT_ALIGN?: string
  TEXT_ALIGN_VERTICAL?: string
  WINDOW_COLOR?: string
  WINDOW_OPACITY?: number
}
```

---

### ClosedCaptionsSettings

```typescript
type ClosedCaptionsSettings = {
  ENABLED: boolean // Whether or not closed-captions should be enabled by default
  STYLES?: ClosedCaptionsStyles // The default styles to use when displaying closed-captions
  PREFERRED_LANGUAGES?: string[]
}
```

See also:

[ClosedCaptionsStyles](#closedcaptionsstyles)

---
