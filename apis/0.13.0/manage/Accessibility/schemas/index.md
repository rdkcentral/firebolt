---
title: Accessibility

version: 0.13.0
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
     - [ClosedCaptionsStyles](#closedcaptionsstyles)
     - [FontFamily](#fontfamily)
     - [FontSize](#fontsize)
     - [Color](#color)
     - [FontEdge](#fontedge)
     - [Opacity](#opacity)
     - [HorizontalAlignment](#horizontalalignment)
     - [VerticalAlignment](#verticalalignment)
     - [VoiceSpeed](#voicespeed)


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

### VoiceSpeed



```typescript
type VoiceSpeed = number
```



---
