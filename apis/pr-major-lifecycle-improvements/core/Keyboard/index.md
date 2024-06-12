---
title: Keyboard

version: pr-major-lifecycle-improvements
layout: default
sdk: core
---

# Keyboard Module

---

Version Keyboard 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
- [Methods](#methods)
  - [email](#email)
  - [password](#password)
  - [standard](#standard)
- [Types](#types)
  - [EmailUsage](#emailusage)

## Usage

To use the Keyboard module, you can import it into your project from the Firebolt SDK:

```javascript
import { Keyboard } from '@firebolt-js/sdk'
```

## Overview

Methods for prompting users to enter text with task-oriented UX

## Methods

### email

Prompt the user for their email address with a simplified list of choices.

```typescript
function email(type: EmailUsage, message: string): Promise<string>
```

Parameters:

| Param     | Type         | Required | Description                                                                                   |
| --------- | ------------ | -------- | --------------------------------------------------------------------------------------------- |
| `type`    | `EmailUsage` | true     | Why the email is being requested, e.g. sign on or sign up <br/>values: `'signIn' \| 'signUp'` |
| `message` | `string`     | false    | The message to display while prompting                                                        |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

---

### password

Show the password entry keyboard, with typing obfuscated from visibility

```typescript
function password(message: string): Promise<string>
```

Parameters:

| Param     | Type     | Required | Description                            |
| --------- | -------- | -------- | -------------------------------------- |
| `message` | `string` | false    | The message to display while prompting |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

---

### standard

Show the standard platform keyboard, and return the submitted value

```typescript
function standard(message: string): Promise<string>
```

Parameters:

| Param     | Type     | Required | Description                            |
| --------- | -------- | -------- | -------------------------------------- |
| `message` | `string` | true     | The message to display while prompting |

Promise resolution:

Capabilities:

| Role | Capability                             |
| ---- | -------------------------------------- |
| uses | xrn:firebolt:capability:input:keyboard |

#### Examples

---

## Types

### EmailUsage

```typescript
enum EmailUsage {
  SIGN_IN = 'signIn',
  SIGN_UP = 'signUp',
}
```

---
