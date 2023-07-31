---
title: Accessibility

version: test
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
     - [ClosedCaptionsSettings](#closedcaptionssettings)
     - [VoiceGuidanceSettings](#voiceguidancesettings)
     - [VoiceSpeed](#voicespeed)
     - [ClosedCaptionsStyles](#closedcaptionsstyles)
     - [FontFamily](#fontfamily)
     - [FontSize](#fontsize)
     - [Color](#color)
     - [FontEdge](#fontedge)
     - [Opacity](#opacity)
     - [HorizontalAlignment](#horizontalalignment)
     - [VerticalAlignment](#verticalalignment)


## Overview
 undefined

## Types

### ClosedCaptionsSettings



```typescript
type ClosedCaptionsSettings = {
  enabled: boolean               // Whether or not closed-captions should be enabled by default
  styles: ClosedCaptionsStyles   // The default styles to use when displaying closed-captions
}
```

See also: 

[ClosedCaptionsStyles](#closedcaptionsstyles)

---

### VoiceGuidanceSettings



```typescript
type VoiceGuidanceSettings = {
  enabled: boolean              // Whether or not voice guidance should be enabled by default
  speed: VoiceSpeed
}
```

See also: 

number

---

### VoiceSpeed



```typescript
type VoiceSpeed = number
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
}
```



---

### FontFamily



```typescript
type FontFamily = string
```



---

### FontSize



```typescript
type FontSize = number
```



---

### Color



```typescript
type Color = string
```



---

### FontEdge



```typescript
type FontEdge = string
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
