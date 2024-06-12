---
title: Discovery

version: next-major
layout: default
sdk: core
---

# Discovery Module

---

Version Discovery 0.0.0-unknown.0

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Usage](#usage)
- [Overview](#overview)
  - [Localization](#localization)
- [Methods](#methods)
  - [clearContentAccess](#clearcontentaccess)
  - [contentAccess](#contentaccess)
  - [entitlements](#entitlements)
  - [entityInfo](#entityinfo)
  - [launch](#launch)
  - [policy](#policy)
  - [provideInterest](#provideinterest)
  - [purchasedContent](#purchasedcontent)
  - [signIn](#signin)
  - [signOut](#signout)
  - [watched](#watched)
  - [watchNext](#watchnext)
  - [listen](#listen)
  - [once](#once)
- [Events](#events)
  - [navigateTo](#navigateto)
  - [policyChanged](#policychanged)
- [Provider Interfaces](#provider-interfaces)
  - [Interest](#interest)
- [Types](#types)
  - [DiscoveryPolicy](#discoverypolicy)
  - [Availability](#availability)
  - [ContentAccessIdentifiers](#contentaccessidentifiers)
  - [FederatedRequest](#federatedrequest)
  - [EntityInfoParameters](#entityinfoparameters)
  - [EntityInfoFederatedRequest](#entityinfofederatedrequest)
  - [PurchasedContentParameters](#purchasedcontentparameters)
  - [PurchasedContentFederatedRequest](#purchasedcontentfederatedrequest)

## Usage

To use the Discovery module, you can import it into your project from the Firebolt SDK:

```javascript
import { Discovery } from '@firebolt-js/sdk'
```

## Overview

Your App likely wants to integrate with the Platform's discovery capabilities. For example to add a "Watch Next" tile that links to your app from the platform's home screen.

Getting access to this information requires to connect to lower level APIs made available by the platform. Since implementations differ between operators and platforms, the Firebolt SDK offers a Discovery module, that exposes a generic, agnostic interface to the developer.

Under the hood, an underlaying transport layer will then take care of calling the right APIs for the actual platform implementation that your App is running on.

The Discovery plugin is used to _send_ information to the Platform.

### Localization

Apps should provide all user-facing strings in the device's language, as specified by the Firebolt `Localization.language` property.

Apps should provide prices in the same currency presented in the app. If multiple currencies are supported in the app, the app should provide prices in the user's current default currency.

## Methods

### clearContentAccess

Clear both availabilities and entitlements from the subscriber. This is equivalent of calling `Discovery.contentAccess({ availabilities: [], entitlements: []})`. This is typically called when the user signs out of an account.

```typescript
function clearContentAccess(): Promise<void>
```

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

---

### contentAccess

Inform the platform of what content the user can access either by discovering it or consuming it. Availabilities determine which content is discoverable to a user, while entitlements determine if the user can currently consume that content. Content can be available but not entitled, this means that user can see the content but when they try to open it they must gain an entitlement either through purchase or subscription upgrade. In case the access changed off-device, this API should be called any time the app comes to the foreground to refresh the access. This API should also be called any time the availabilities or entitlements change within the app for any reason. Typical reasons may include the user signing into an account or upgrading a subscription. Less common cases can cause availabilities to change, such as moving to a new service location. When availabilities or entitlements are removed from the subscriber (such as when the user signs out), then an empty array should be given. To clear both, use the Discovery.clearContentAccess convenience API.

```typescript
function contentAccess(ids: ContentAccessIdentifiers): Promise<void>
```

Parameters:

| Param | Type                       | Required | Description                                                                                        |
| ----- | -------------------------- | -------- | -------------------------------------------------------------------------------------------------- |
| `ids` | `ContentAccessIdentifiers` | true     | A list of identifiers that represent content that is discoverable or consumable for the subscriber |

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

---

### entitlements

Inform the platform of the users latest entitlements w/in this app.

```typescript
function entitlements(
  entitlements: Entertainment.Entitlement[],
): Promise<boolean>
```

Parameters:

| Param          | Type                          | Required | Description                  |
| -------------- | ----------------------------- | -------- | ---------------------------- |
| `entitlements` | `Entertainment.Entitlement[]` | true     | Array of entitlement objects |

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:content-access |

#### Examples

---

### entityInfo

Provide information about a program entity and its available watchable assets, such as entitlement status and price, via either a push or pull call flow. Includes information about the program entity and its relevant associated entities, such as extras, previews, and, in the case of TV series, seasons and episodes.

See the `EntityInfo` and `WayToWatch` data structures below for more information.

The app only needs to implement Pull support for `entityInfo` at this time.

To allow the platform to pull data, use `entityInfo(callback: Function)`:

```typescript
function entityInfo(
  callback: (parameters: EntityInfoParameters) => Promise<EntityInfoResult>,
): Promise<boolean>
```

Parameters:

| Param      | Type       | Required | Summary                                                      |
| ---------- | ---------- | -------- | ------------------------------------------------------------ |
| `callback` | `Function` | Yes      | A callback for the platform to pull EntityInfoResult objects |

Callback parameters:

| Param        | Type                   | Required | Summary                                                                     |
| ------------ | ---------------------- | -------- | --------------------------------------------------------------------------- |
| `parameters` | `EntityInfoParameters` | Yes      | An object describing the platform's query for an `EntityInfoResult` object. |

```typescript
type EntityInfoParameters = {
  entityId: string
  assetId?: string
}
```

Callback promise resolution:

```typescript

```

See also: [EntityInfoResult](#entityinforesult-1)

#### Examples

To push data to the platform, e.g. during app launch, use `entityInfo(result: EntityInfoResult)`:

```typescript
function entityInfo(result: EntityInfoResult): Promise<boolean>
```

Parameters:

| Param    | Type               | Required | Summary                                             |
| -------- | ------------------ | -------- | --------------------------------------------------- |
| `result` | `EntityInfoResult` | Yes      | The `EntityInfoResult` data to push to the platform |

```typescript

```

See also: [EntityInfo](#entityinfo-1)

Promise resolution:

| Type      | Summary                                |
| --------- | -------------------------------------- |
| `boolean` | Whether or not the push was successful |

#### Examples

---

### launch

Launch or foreground the specified app, and optionally instructs it to navigate to the specified user action.
For the Primary Experience, the appId can be any one of:

- xrn:firebolt:application-type:main

- xrn:firebolt:application-type:settings

```typescript
function launch(
  appId: string,
  intent: Intents.NavigationIntent,
): Promise<boolean>
```

Parameters:

| Param    | Type                       | Required | Description                                                                                                                      |
| -------- | -------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `appId`  | `string`                   | true     | The durable app Id of the app to launch                                                                                          |
| `intent` | `Intents.NavigationIntent` | false    | An optional `NavigationIntent` with details about what part of the app to show first, and context around how/why it was launched |

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:lifecycle:launch |

#### Examples

---

### policy

get the discovery policy

To get the value of `policy` call the method like this:

```typescript
function policy(): Promise<DiscoveryPolicy>
```

Promise resolution:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:discovery:policy |

#### Examples

---

To subscribe to notifications when the value changes, call the method like this:

```typescript
function policy(callback: (value) => null): Promise<number>
```

Promise resolution:

```
number
```

#### Examples

---

### provideInterest

Register an app's Interest interface.

```typescript
function provideInterest(enabled: boolean): Promise<void>
```

Parameters:

| Param     | Type      | Required | Description |
| --------- | --------- | -------- | ----------- |
| `enabled` | `boolean` | true     |             |

Promise resolution:

Capabilities:

| Role     | Capability                                 |
| -------- | ------------------------------------------ |
| provides | xrn:firebolt:capability:discovery:interest |

#### Examples

---

### purchasedContent

Return content purchased by the user, such as rentals and electronic sell through purchases.

The app should return the user's 100 most recent purchases in `entries`. The total count of purchases must be provided in `count`. If `count` is greater than the total number of `entries`, the UI may provide a link into the app to see the complete purchase list.

The `EntityInfo` object returned is not required to have `waysToWatch` populated, but it is recommended that it do so in case the UI wants to surface additional information on the purchases screen.

The app should implement both Push and Pull methods for `purchasedContent`.

The app should actively push `purchasedContent` when:

- The app becomes Active.
- When the state of the purchasedContent set has changed.
- The app goes into Inactive or Background state, if there is a chance a change event has been missed.

To allow the platform to pull data, use `purchasedContent(callback: Function)`:

```typescript
function purchasedContent(
  callback: (
    parameters: PurchasedContentParameters,
  ) => Promise<PurchasedContentResult>,
): Promise<boolean>
```

Parameters:

| Param      | Type       | Required | Summary                                                            |
| ---------- | ---------- | -------- | ------------------------------------------------------------------ |
| `callback` | `Function` | Yes      | A callback for the platform to pull PurchasedContentResult objects |

Callback parameters:

| Param        | Type                         | Required | Summary                                                                           |
| ------------ | ---------------------------- | -------- | --------------------------------------------------------------------------------- |
| `parameters` | `PurchasedContentParameters` | Yes      | An object describing the platform's query for an `PurchasedContentResult` object. |

```typescript
type PurchasedContentParameters = {
  limit: number
  offeringType?: Entertainment.OfferingType // The offering type of the WayToWatch.
  programType?: Entertainment.ProgramType // In the case of a program `entityType`, specifies the program type.
}
```

Callback promise resolution:

```typescript

```

See also: [PurchasedContentResult](#purchasedcontentresult-1)

#### Examples

To push data to the platform, e.g. during app launch, use `purchasedContent(result: PurchasedContentResult)`:

```typescript
function purchasedContent(result: PurchasedContentResult): Promise<boolean>
```

Parameters:

| Param    | Type                     | Required | Summary                                                   |
| -------- | ------------------------ | -------- | --------------------------------------------------------- |
| `result` | `PurchasedContentResult` | Yes      | The `PurchasedContentResult` data to push to the platform |

```typescript

```

See also: [PurchasedContent](#purchasedcontent-1)

Promise resolution:

| Type      | Summary                                |
| --------- | -------------------------------------- |
| `boolean` | Whether or not the push was successful |

#### Examples

---

### signIn

Inform the platform that your user is signed in, for increased visibility in search & discovery. Sign-in state is used separately from what content can be access through entitlements and availabilities. Sign-in state may be used when deciding whether to choose this app to handle a user intent. For instance, if the user tries to launch something generic like playing music from an artist, only a signed-in app will be chosen. If the user wants to tune to a channel, only a signed-in app will be chosen to handle that intent. While signIn can optionally include entitlements as those typically change at signIn time, it is recommended to make a separate call to Discovery.contentAccess for entitlements. signIn is not only for when a user explicitly enters login credentials. If an app does not require any credentials from the user to consume content, such as in a free app, then the app should call signIn immediately on launch.

```typescript
function signIn(entitlements: Entertainment.Entitlement[]): Promise<boolean>
```

Parameters:

| Param          | Type                          | Required | Description                                                                                             |
| -------------- | ----------------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `entitlements` | `Entertainment.Entitlement[]` | false    | Optional array of Entitlements, in case of a different user account, or a long time since last sign-in. |

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:sign-in-status |

#### Examples

---

### signOut

Inform the platform that your user has signed out. See `Discovery.signIn` for more details on how the sign-in state is used.signOut will NOT clear entitlements, the app should make a separate call to Discovery.clearContentAccess. Apps should also call signOut when a login token has expired and the user is now in a signed-out state.

```typescript
function signOut(): Promise<boolean>
```

Promise resolution:

Capabilities:

| Role | Capability                                       |
| ---- | ------------------------------------------------ |
| uses | xrn:firebolt:capability:discovery:sign-in-status |

#### Examples

---

### watched

Notify the platform that content was partially or completely watched

```typescript
function watched(
  entityId: string,
  progress: number,
  completed: boolean,
  watchedOn: string,
): Promise<boolean>
```

Parameters:

| Param       | Type      | Required | Description                                                                                                      |
| ----------- | --------- | -------- | ---------------------------------------------------------------------------------------------------------------- |
| `entityId`  | `string`  | true     | The entity Id of the watched content.                                                                            |
| `progress`  | `number`  | false    | How much of the content has been watched (percentage as 0-1 for VOD, number of seconds for live) <br/>minumum: 0 |
| `completed` | `boolean` | false    | Whether or not this viewing is considered "complete," per the app's definition thereof                           |
| `watchedOn` | `string`  | false    | Date/Time the content was watched, ISO 8601 Date/Time <br/>format: date-time                                     |

Promise resolution:

Capabilities:

| Role | Capability                                |
| ---- | ----------------------------------------- |
| uses | xrn:firebolt:capability:discovery:watched |

#### Examples

---

### watchNext

Suggest a call-to-action for this app on the platform home screen

```typescript
function watchNext(
  title: Types.LocalizedString,
  identifiers: Entertainment.ContentIdentifiers,
  expires: string,
  images: object,
): Promise<boolean>
```

Parameters:

| Param         | Type                               | Required | Description                                                                            |
| ------------- | ---------------------------------- | -------- | -------------------------------------------------------------------------------------- |
| `title`       | `Types.LocalizedString`            | true     | The title of this call to action                                                       |
| `identifiers` | `Entertainment.ContentIdentifiers` | true     | A set of content identifiers for this call to action                                   |
| `expires`     | `string`                           | false    | When this call to action should no longer be presented to users <br/>format: date-time |
| `images`      | `object`                           | false    | A set of images for this call to action                                                |

Promise resolution:

Capabilities:

| Role | Capability                                   |
| ---- | -------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:watch-next |

#### Examples

---

### listen

To listen to a specific event pass the event name as the first parameter:

```typescript
listen(event: string, callback: (data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to all events from this module pass only a callback, without specifying an event name:

```typescript
listen(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

### once

To listen to a single instance of a specific event pass the event name as the first parameter:

```typescript
once(event: string, callback: (data: any) => void): Promise<number>
```

The `once` method will only pass the next instance of this event, and then dicard the listener you provided.

Parameters:

| Param      | Type       | Required | Summary                                                |
| ---------- | ---------- | -------- | ------------------------------------------------------ |
| `event`    | `string`   | Yes      | The event to listen for, see [Events](#events).        |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

Callback parameters:

| Param  | Type  | Required | Summary                                                                        |
| ------ | ----- | -------- | ------------------------------------------------------------------------------ |
| `data` | `any` | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

To listen to the next instance only of any events from this module pass only a callback, without specifying an event name:

```typescript
once(callback: (event: string, data: any) => void): Promise<number>
```

Parameters:

| Param      | Type       | Required | Summary                                                                                                                        |
| ---------- | ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| _callback_ | `function` | Yes      | A function that will be invoked when the event occurs. The event data depends on which event is firing, see [Events](#events). |

Callback parameters:

| Param   | Type     | Required | Summary                                                                        |
| ------- | -------- | -------- | ------------------------------------------------------------------------------ |
| `event` | `string` | Yes      | The event that has occured listen for, see [Events](#events).                  |
| `data`  | `any`    | Yes      | The event data, which depends on which event is firing, see [Events](#events). |

Promise resolution:

| Type     | Description                                                                                       |
| -------- | ------------------------------------------------------------------------------------------------- |
| `number` | Listener ID to clear the callback method and stop receiving the event, e.g. `Discovery.clear(id)` |

See [Listening for events](../../docs/listening-for-events/) for more information and examples.

## Events

### navigateTo

```typescript
function listen('navigateTo', (Intents.NavigationIntent) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                                    |
| ---- | --------------------------------------------- |
| uses | xrn:firebolt:capability:discovery:navigate-to |

#### Examples

---

### policyChanged

```typescript
function listen('policyChanged', (DiscoveryPolicy) => void): Promise<number>
```

See also: [listen()](#listen), [once()](#listen), [clear()](#listen).

Event value:

Capabilities:

| Role | Capability                               |
| ---- | ---------------------------------------- |
| uses | xrn:firebolt:capability:discovery:policy |

#### Examples

---

## Provider Interfaces

### Interest

The provider interface for the `Interest` capability.

```typescript
interface Interest {
  userInterest(
    type: InterestType,
    reason: InterestReason,
    session: ProviderSession,
  ): Promise<Entity.EntityDetails>
}
```

Usage:

```typescript
Discovery.provide('Interest', provider: Interest | object)
```

#### Examples

**Register your app to provide the `Interest` capability.**

```javascript
import { Discovery } from '@firebolt-js/sdk'

class MyInterest {

    async Interest.userInterest(parameters, session) {
        return {
            "identifiers": {
                "entityId": "345",
                "entityType": "program",
                "programType": "movie"
            },
            "info": {}
        }
    }

}

Discovery.provide('Interest', new MyInterest())
```

<details markdown="1" >
    <summary>JSON-RPC</summary>

**Register to recieve each provider API**

Request:

```json
{
  "id": 1,
  "method": "Discovery.onRequestInterest.userInterest",
  "params": {
    "listen": true
  }
}
```

Response:

```json
{
  "id": 1,
  "result": {
    "listening": true,
    "event": "Discovery.onRequestInterest.userInterest"
  }
}
```

**Asynchronous event to initiate Interest.userInterest()**

Event Response:

```json
{
  "id": 1,
  "result": {
    "correlationId": "",
    "parameters": "interest"
  }
}
```

**App initiated response to event**

Request:

```json
{
  "id": 2,
  "method": "Discovery.Interest.userInterestResponse",
  "params": {
    "correlationId": "",
    "result": {
      "identifiers": {
        "entityId": "345",
        "entityType": "program",
        "programType": "movie"
      },
      "info": {}
    }
  }
}
```

Response:

```json
{
  "id": 2,
  "result": true
}
```

</details>

## Types

### DiscoveryPolicy

```typescript
type DiscoveryPolicy = {
  enableRecommendations: boolean // Whether or not to the user has enabled history-based recommendations
  shareWatchHistory: boolean // Whether or not the user has enabled app watch history data to be shared with the platform
  rememberWatchedPrograms: boolean // Whether or not the user has enabled watch history
}
```

---

### Availability

```typescript
type Availability = {
  type: 'channel-lineup' | 'program-lineup'
  id: string
  catalogId?: string
  startTime?: string
  endTime?: string
}
```

---

### ContentAccessIdentifiers

```typescript
type ContentAccessIdentifiers = {
  availabilities?: Availability[] // A list of identifiers that represent what content is discoverable for the subscriber. Excluding availabilities will cause no change to the availabilities that are stored for this subscriber. Providing an empty array will clear the subscriber's availabilities
  entitlements?: Entertainment.Entitlement[] // A list of identifiers that represent what content is consumable for the subscriber. Excluding entitlements will cause no change to the entitlements that are stored for this subscriber. Providing an empty array will clear the subscriber's entitlements
}
```

See also:

Availability
Entertainment.Entitlement

---

### FederatedRequest

```typescript
type FederatedRequest = {
  correlationId: string
}
```

---

### EntityInfoParameters

```typescript
type EntityInfoParameters = {
  entityId: string
  assetId?: string
}
```

---

### EntityInfoFederatedRequest

```typescript
type EntityInfoFederatedRequest = {
  parameters: EntityInfoParameters
  correlationId: string
}
```

See also:

FederatedRequest
EntityInfoParameters

---

### PurchasedContentParameters

```typescript
type PurchasedContentParameters = {
  limit: number
  offeringType?: Entertainment.OfferingType // The offering type of the WayToWatch.
  programType?: Entertainment.ProgramType // In the case of a program `entityType`, specifies the program type.
}
```

See also:

Entertainment.OfferingType
Entertainment.ProgramType

---

### PurchasedContentFederatedRequest

```typescript
type PurchasedContentFederatedRequest = {
  parameters: PurchasedContentParameters
  correlationId: string
}
```

See also:

FederatedRequest
PurchasedContentParameters

---
