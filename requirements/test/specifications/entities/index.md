---

version: test
layout: default
title: Firebolt Entities
category: requirements
type: specification
---
# Firebolt Entities

Document Status: Working Draft

See [Firebolt Requirements Governance](../../governance) for more info.

## 1. Overview
Entities are object which identify a piece of content that an end-user may consume within an app.

Firebolt uses Entities or Entity Ids as parameters and/or results of content-centric Firebolt APIs that an App may interact with.

The key words "**MUST**", "**MUST NOT**", "**REQUIRED**", "**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**", "**RECOMMENDED**", "**NOT RECOMMENDED**", "**MAY**", and "**OPTIONAL**" in this document are to be interpreted as described in [BCP 14](https://www.rfc-editor.org/rfc/rfc2119.txt) [RFC2119] [RFC8174] when, and only when, they appear in all capitals, as shown here.

## 2. Table of Contents
- [1. Overview](#1-overview)
- [2. Table of Contents](#2-table-of-contents)
- [3. Entities](#3-entities)
- [4. Entity Specifications](#4-entity-specifications)

## 3. Entities
Every Entity **MUST** be of type `object`.

Every Entity object **MUST** have a `string` property named `entityId`, which identifies the entity. The scope of entity identifiers **SHOULD** be defined by the app providing or receiving the Entity, so that the App may work across Firebolt distrubutions without mapping IDs from a distributor space to the App's space.

Every Entity object **MAY** have a `string` property named `appContentData`, limited to 256 characters, which provides additional information useful for targeting that Entity, e.g. a deeplink path.

An example Entity:

```json
{
    "entityId": "entity/abc"
}
```

Another example Entity:

```json
{
    "entityId": "entity/abc",
    "appContentData": "xyz"
}
```

Firebolt platforms **MUST NOT** infer anything from the values of these fields, although back-office systems operated by Firebolt distributors may.

## 4. Entity Specifications

- [Program Entities](./programs)
- [Channel Entities](./channels)
- [Music Entities](./music)