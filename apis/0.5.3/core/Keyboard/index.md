---
title: Keyboard
---

# Keyboard Module
---
Version 0.5.3

## OpenRPC
This document was generated from an OpenRPC JSON-Schema, and is intended to provide a human readable overview and examples of the methods contained in the module.

For the full schema, see the link below.

| Schema |
|--------|
| [keyboard.json](https://github.com/rdkcentral/firebolt-core-sdk/blob/main/src/modules/keyboard.json) |


## Table of Contents
 - [Usage](#usage)
 - [Overview](#overview)
 - [Events](#events)

 - [Methods](#methods)
    - [email](#email)
    - [password](#password)
    - [standard](#standard)
 - [Schemas](#schemas)
    - [EmailUsage](#emailusage)

<span></span>

## Usage
To use the Keyboard module, you can import it into your project from the Firebolt SDK:

```javascript
import { Keyboard } from '@firebolt-js/sdk'
```
## Overview
Methods for prompting users to enter text with task-oriented UX

## Events


## Methods
### email
Prompt the user for their email address with a simplified list of choices.

```typescript
function email(type: EmailUsage, message?: string): Promise<string>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `type` | [`EmailUsage`](#emailusage) | true | Why the email is being requested, e.g. sign on or sign up  |
| `message` | `string` | false | The message to display while prompting  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the selected or entered email |


---

#### Examples

##### Prompt the user to select or type an email address
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Keyboard } from '@firebolt-js/sdk'

Keyboard.email("signIn", "Enter your email to sign into this app")
    .then(email => {
        console.log(email)
    })
```
Value of `email`

```javascript
"user@domain.com"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "keyboard.email",
  "params": {
    "type": "signIn",
    "message": "Enter your email to sign into this app"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "user@domain.com"
}
```

</details>

##### Prompt the user to type an email address to sign up
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Keyboard } from '@firebolt-js/sdk'

Keyboard.email("signUp", "Enter your email to sign up for this app")
    .then(email => {
        console.log(email)
    })
```
Value of `email`

```javascript
"user@domain.com"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "keyboard.email",
  "params": {
    "type": "signUp",
    "message": "Enter your email to sign up for this app"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "user@domain.com"
}
```

</details>




---

### password
Show the password entry keyboard, with typing obfuscated from visibility

```typescript
function password(message?: string): Promise<string>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `message` | `string` | false | The message to display while prompting  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the selected or entered password |


---

#### Examples

##### Prompt the user to enter their password
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Keyboard } from '@firebolt-js/sdk'

Keyboard.password("Enter your password")
    .then(value => {
        console.log(value)
    })
```
Value of `value`

```javascript
"abc123"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "keyboard.password",
  "params": {
    "message": "Enter your password"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "abc123"
}
```

</details>




---

### standard
Show the standard platform keyboard, and return the submitted value

```typescript
function standard(message: string): Promise<string>
```
#### Parameters

| Param                  | Type                 | Required                 | Summary                 |
| ---------------------- | -------------------- | ------------------------ | ----------------------- |
| `message` | `string` | true | The message to display while prompting  |

#### Promise Resolution

| Type | Description |
| ---- | ----------- |
| `string` | the selected or entered text |


---

#### Examples

##### Prompt the user for an arbitrary string
<details>
  <summary><b>JavaScript</b></summary>

```javascript
import { Keyboard } from '@firebolt-js/sdk'

Keyboard.standard("Enter the name you'd like to associate with this device")
    .then(value => {
        console.log(value)
    })
```
Value of `value`

```javascript
"Living Room"
```

</details>
<details>
  <summary><b>JSON-RPC</b></summary>

###### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "keyboard.standard",
  "params": {
    "message": "Enter the name you'd like to associate with this device"
  }
}
```

###### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "Living Room"
}
```

</details>




---



## Schemas

### EmailUsage

```typescript
type EmailUsage = 'signIn' | 'signUp'
```





---


