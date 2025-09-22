---
title: Entity

version: next-major
layout: default
sdk: discovery
---

# Entity

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Types](#types)
  - [Metadata](#metadata)
  - [EntityDetails](#entitydetails)

## Types

### Metadata

```typescript
type Metadata = {
  title?: string // Title of the entity.
  synopsis?: string // Short description of the entity.
  seasonNumber?: number // For TV seasons, the season number. For TV episodes, the season that the episode belongs to.
  seasonCount?: number // For TV series, seasons, and episodes, the total number of seasons.
  episodeNumber?: number // For TV episodes, the episode number.
  episodeCount?: number // For TV seasons and episodes, the total number of episodes in the current season.
  releaseDate?: string // The date that the program or entity was released or first aired.
  contentRatings?: ContentRating[] // A list of ContentRating objects, describing the entity's ratings in various rating schemes.
}
```

See also:

Entertainment.ContentRating

---

### EntityDetails

```typescript
type EntityDetails = {
  identifiers: void
  info?: Metadata
  waysToWatch?: WayToWatch[] // An array of ways a user is might watch this entity, regardless of entitlements.
}
```

See also:

[Metadata](#metadata)
Entertainment.WayToWatch

---
