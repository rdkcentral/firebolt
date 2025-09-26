---
title: Accessibility

version: next-major
layout: default
sdk: core
---

# Accessibility

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [FontFamily](#fontfamily)
  - [FontSize](#fontsize)
  - [FontEdge](#fontedge)
  - [Color](#color)
  - [Opacity](#opacity)
  - [HorizontalAlignment](#horizontalalignment)
  - [VerticalAlignment](#verticalalignment)
  - [ClosedCaptionsStyles](#closedcaptionsstyles)
  - [ClosedCaptionsSettings](#closedcaptionssettings)
  - [SpeechRate](#speechrate)
  - [VoiceGuidanceSettings](#voiceguidancesettings)

## Types

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

### Color

```typescript
type Color = string
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
  styles?: ClosedCaptionsStyles // The default styles to use when displaying closed-captions
  preferredLanguages?: string[]
}
```

See also:

[ClosedCaptionsStyles](#closedcaptionsstyles)

---

### SpeechRate

```typescript
type SpeechRate = number
```

---

### VoiceGuidanceSettings

```typescript
type VoiceGuidanceSettings = {
  enabled: boolean // Whether or not voice guidance should be enabled by default
  navigationHints: boolean // Whether or not voice guidance should include additional navigation hints
  rate: SpeechRate // The rate at which voice guidance speech will be read back to the user
  speed?: SpeechRate // **DEPRECATED** Use rate instead. The rate at which voice guidance speech will be read back to the user
}
```

See also:

[SpeechRate](#speechrate)

---
