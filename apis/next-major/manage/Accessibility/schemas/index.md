---
title: Accessibility

version: next-major
layout: default
sdk: manage
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
  - [SpeechRate](#speechrate)

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

### SpeechRate

```typescript
type SpeechRate = number
```

---
