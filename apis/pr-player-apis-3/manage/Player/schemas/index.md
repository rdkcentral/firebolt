---
title: Player

version: pr-player-apis-3
layout: default
sdk: manage
---

# Player

---

Version Player 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Types](#types)
  - [PlayerRequest](#playerrequest)
  - [PlayerProviderRequest](#playerproviderrequest)

## Overview

undefined

## Types

### PlayerRequest

```typescript
type PlayerRequest = {
  playerId: string // The id of the player instance to play in
}
```

---

### PlayerProviderRequest

```typescript
type PlayerProviderRequest = {
  correlationId: string // An id to correlate the provider response with this request
  parameters: PlayerRequest
}
```

See also:

[PlayerRequest](#playerrequest)

---
