---

version: pr-app-passthrough-additions
layout: default
title: App Pass-through APIs
category: requirements
type: specification
---
# App Pass-through APIs

Document Status: Working Draft

See [Firebolt Requirements Governance](../../../governance) for more info.

| Contributor     | Organization   |
|-----------------|----------------|
| Jeremy LaCivita | Comcast        |
| Kevin Pearson   | Comcast        |
| Yuri Pasquali   | Sky            |

## 1. Overview
This document describes how one Firebolt App can provide a capability that may be used by another Firebolt App, with the platform as a permission broker that passes the requests and responses to each app without feature-specific logic.

This document covers the App Pass-through Firebolt OpenRPC extension as well as how Firebolt implementations should detect and execute app provided pass-through APIs.

Some APIs require an app to fulfill the request on behalf of another app, e.g. to provide a UX or cross-app data sharing. Generally the calling app doesn't care, or have a say in, which other app provides the API, that is up to the Firebolt distributor.

To facilitate these APIs, Firebolt denotes an OpenRPC tag with OpenRPC extensions to connect the `provide` API to the `use` API.

This document is written using the [IETF Best Common Practice 14](https://www.rfc-editor.org/rfc/rfc2119.txt) and should include the following summary in the Overview section:

The key words "**MUST**", "**MUST NOT**", "**REQUIRED**", "**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**", "**RECOMMENDED**", "**NOT RECOMMENDED**", "**MAY**", and "**OPTIONAL**" in this document are to be interpreted as described in [BCP 14](https://www.rfc-editor.org/rfc/rfc2119.txt) [RFC2119] [RFC8174] when, and only when, they appear in all capitals, as shown here.

## 2. Table of Contents
- [1. Overview](#1-overview)
- [2. Table of Contents](#2-table-of-contents)
- [3. Open RPC Extensions](#3-open-rpc-extensions)
  - [3.1. Provided By Extension](#31-provided-by-extension)
- [4. Routing App pass-through APIs](#4-routing-app-pass-through-apis)
  - [4.1. No available providers](#41-no-available-providers)
  - [4.2. Direct pass-through](#42-direct-pass-through)
  - [4.4. Pass-through notifications](#44-pass-through-notifications)
- [5. Provider Candidates](#5-provider-candidates)
- [6. Best Candidate](#6-best-candidate)
- [7. Application Context](#7-application-context)
    - [7.1 Application Context Sharing](#71-application-context-sharing)
    - [7.2 Application Context Setting](#72-application-context-setting)
- [8. API Gateway](#9-api-gateway)
- [9. Example: User Interest](#10-example-user-interest)
  - [9.1. User Interest Pull](#101-user-interest-pull)
  - [9.2. User Interest Push](#102-user-interest-push)

## 3. Open RPC Extensions

### 3.1. Provided By Extension
Firebolt OpenRPC **MUST** support a `string` `x-provided-by` extension property on the `capabilities` tag that denotes a method is provided by some app on the device registering for the specified provider API, e.g.:

```json
{
    "methods": [
        {
            "name": "Keyboard.standard",
            "tags": [
                {
                    "name": "capabilities",
                    "x-provided-by": "Keyboard.onRequestStandard",
                    "x-uses": [
                        "xrn:firebolt:capability:input:keyboard"
                    ]
                }
            ]
        }
    ]
}
```

The method denoted by `x-provided-by` is referred to as the "*provider*" or "*provider method*" for the remainder of this document.

The method with the `x-provided-by` extension is referred to as the "*platform method*" for the remainder of this document.

To prevent unresolvable chaining of methods the `x-provided-by` extension **MUST NOT** be used on a method with any value in the `x-provides` extension.

To prevent compound methods a platform method **MUST** `use` a single capability or `manage` a single capability, but not both.

The provider method **MUST** provide the same capability that the platform method either uses or manages.

If a platform method has no provider method then it is not a valid Firebolt OpenRPC method schema, and a validation error **MUST** be generated.

## 4. Routing App pass-through APIs
App pass-through APIs may be routed in one of several ways.

When an app calls a platform method, i.e. one with an `x-provided-by` extension, the platform **MUST** use one of the routing methods defined in this section based on various properties of the method.

### 4.1. No available providers
When an app calls a platform method with an `x-provided-by` extension, the platform **MUST** return an unavailable error if there is no [candidate app](#7-provider-candidates) to execute the provider method.

```json
{
    "id": 1,
    "error": {
        "code": -50300,
        "message": "Capability <XRN> is unavailable."
    }
}
```

Where `<XRN>` is the capability XRN string, e.g. `xrn:firebolt:capabilities:example:foo`.

### 4.2. Direct pass-through
A direct pass-through is where a single app provides a single response to a single request by another app.

This section only applies to app provider methods that do not have an `event` tag.

The platform method result schema **MUST** either:

> Match the `x-response` schema on the provider method so that the result can be passed through.
>
> or
> 
> Have a property that matches the `x-response-name` string and `x-response` schema on the
> provider method so that the result can be composed and passed through.

The platform **MUST** call the provider method from the [best candidate](#8-best-candidate) app and acquire the result.

If the platform method result schema matches the `x-response` schema on the provider method then the value **MUST** be used as-is.

Otherwise if the platform method result schema has a property that matches the `x-response` schema on the provider method then the value **MUST** be composed into an object under the corresponding property name and the platform **MUST** apply any [result transformations](#9-result-transformations) to the composed result.

### 4.4. Pass-through notifications
Firebolt events have a synchronous subscriber registration method, e.g. `Lifecycle.onInactive(true)`, in addition to asynchronous notifications when the event actually happens. For events powered by an app pass-through, only the asynchronous notifications are passed in by the providing app. The initial event registration is handled by the platform, and the success response is not handled by the providing app.

This section only applies to platform methods that have an `event` tag.

App provided event registration **MUST** not return an availability error due to a lack of providers, since one may be launched at a future point.

To ensure that event provider methods all behave the same the provider method **MUST** have a `result` schema with `"type"` set to `"null"`, since it will not expect any data in the response from the platform after pushing the notification.

The platform method result schema **MUST** either:

> Match the *last* parameter schema on the provider method so that the result can be passed through.
>
> Have a property that matches the *last* parameter name and schema on the provider method so that the result can be passed through.

Example platform method with context:
```json
{
    "name": "onFoo",
    "tags": [
        {
            "name": "capabilities",
            "x-uses": [
                "xrn:firebolt:capabilities:example:foo"
            ],
            "x-provided-by": "foo"
        },
        {
            "name": "event"
        }
    ],
    "params": [
        {
            "name": "context1",
            "schema":{
                "type": "string"
            }
        },
        {
            "name": "context2",
            "schema": {
                "type": "number"
            }
        }
    ],
    "result": {
        "name": "value",
        "schema": {
            "type": "boolean"
        }
    }
}
```

Matching provider method:

```json
{
    "name": "foo",
    "tags": [
        {
            "name": "capabilities",
            "x-provides": "xrn:firebolt:capabilities:example:foo"
        }
    ],
    "params": [
        {
            "name": "context1",
            "schema":{
                "type": "string"
            }
        },
        {
            "name": "context2",
            "schema": {
                "type": "number"
            }
        },
        {
            "name": "value",
            "schema": {
                "type": "boolean"
            }
        }
    ]
}
```

When a provider app calls a provider method mapped to an event the platform **MUST** ignore the notification if the app is not a [candidate app](#7-provider-candidates) for this capability.

If the platform method result schema matches the *last* parameter schema on the provider method then the value **MUST** be used as-is.

Otherwise if the platform method result schema has a property that matches the *last* parameter schema on the provider method then the value **MUST** be composed into an object under the corresponding property name and the platform **MUST** apply any [result transformations](#9-result-transformations) to the composed result.

If the value was composed into the platform method result under a matching property, then any context parameter values from the provider method that correspond to a property name and schema in the platform method result **MUST** also be composed into the platform method result under those properties.

Finally the platform **MUST** dispatch the notification to the app that registered for the event via the original platform method, using all but the last parameter as context.

## 5. Provider Candidates
When a platform method with an `x-provided-by` extension is called, then
all loaded apps that have permission to provide the capability **MUST** be
considered as candidates to fulfill the method.

## 6. Best Candidate
Any provider candidates that have not registered to provide the method in
question **MUST NOT** be considered the best candidate and removed from
consideration.

If there is only one candidate left then it **MUST** be the best candidate.

If appId is set in the request [(See Application Context Setting)](#72-application-context-setting), then that app must be used for selecting the provider.

If there is more than one candidate left, then the candidate app that most recently had RCU input focus **MUST** be the best candidate.

If none of the candidates have had focus yet, then the candidate app that was most recently launched **MUST** be the best candidate.


## 7. Application Context

Application Context provides a mechanism for applications to know the identity of the applications they are communicating with. Application Context can be given in both directions. An application that uses a capability can know which app is providing that capability. An application that provides a capability can know which app is using that capability.

### 7.1 Application Context Sharing

Application Context is shared by having either a "composite result" or a "composite request".

If a "composite result" was used to wrap the provider method value and the platform method's schema has an `appId` `string` property at the top level then the property's value **MUST** be set to the the appId of the providing app for that result.

If a platform method is an `event` and the event result is a "composite result" with an `appId` `string` property at the top level, then the property **MUST** be set to the appId that initiated the provider (push) call.

If the provider method is a "composite request" with `appId` `string` property at the top level but the platform method does not have `appId`, then the id of app that initiated the platform method call should be used to set the `appId` in the provider method request.

### 7.2 Application Context Setting

When a platform method is invoked, the gateway will find the provider using the `Provider Candidate` rules as described above. However, some Firebolt APIs allow selecting the provider that should be used. If a platform method request schema is a "composite request" with `appId` `string` property at the top level but the provider method request schema is not a composite request, then the given appId shall be used to select the provider. 
If "appId" is a required parameter in the platform method request schema, then it must be supplied. If it is not, then the request should fail with invalid parameters. If it is an optional parameter and it is not supplied, then the gateway should use rules in "Provider Candidate" section for selecting the candidate.

## 8. API Gateway
The Firebolt API Gateway **MUST** detect app-passthrough APIs and map the `use`/`manage` APIs to the corresponding `provide` APIs by parsing the Firebolt OpenRPC Specification and following the logic outline in this document.

## 9. Example: User Interest

The following schemas are referenced by these examples:

```json
{
    "components": {
        "schemas": {
            "InterestType": {
                "type": "string",
                "enum": [
                    "interest",
                    "disinterest"
                ]
            },
            "InterestReason": {
                "type": "string",
                "enum": [
                    "playlist"
                ]
            },
            "EntityDetailsFromApp": {
                "type": "object",
                "properties": {
                    "appId": {
                        "type": "string"
                    },
                    "entity": {
                        "$ref": "https://meta.comcast.com/firebolt/entity#/definitions/EntityDetails"
                    }
                },
                "required": [
                    "appId",
                    "entity"
                ]
            }
        }
    }
}
```

### 9.1. User Interest Pull

Platform method:

```json
{
    "methods": [
        {
            "name": "requestUserInterest",
            "tags": [
                {
                    "name": "capabilities",
                    "x-provided-by": "Discovery.onRequestUserInterest",
                    "x-uses": [
                        "xrn:firebolt:capability:discovery:interest"
                    ]
                }
            ],
            "params": [
                {
                    "name": "type",
                    "required": true,
                    "schema": {
                        "$ref": "#/components/schemas/InterestType"
                    }
                },
                {
                    "name": "reason",
                    "required": true,
                    "schema": {
                        "$ref": "#/components/schemas/InterestReason"
                    }
                }
            ],
            "result": {
                "name": "interest",
                "schema": {
                    "$ref": "#/components/schemas/EntityDetailsFromApp",
                }
            }
        }
    ]
}
```

Provider method:

```json
{
    "methods": [
        {
            "name": "onRequestUserInterest",
            "tags": [
                {
                    "name": "capabilities",
                    "x-provides": "xrn:firebolt:capability:discovery:interest"
                },
                {
                    "name": "event",
                    "x-response": {
                        "$ref": "https://meta.comcast.com/firebolt/entity#/definitions/EntityDetails"
                    }
                }
            ],
            "result": {
                "name": "request",
                "schema": {
                    "type": "object",
                    "properties": {
                        "type": {
                            "$ref": "#/components/schemas/InterestType",
                        },
                        "reason": {
                            "$ref": "#/components/schemas/InterestReason",
                        }
                    }
                }
            }
        }
    ]
}
```

### 9.2. User Interest Push

Provider method:

```json
{
    "methods": [
        {
            "name": "userInterest",
            "tags": [
                {
                    "name": "capabilities",
                    "x-provides": "xrn:firebolt:capability:discovery:interest"
                }
            ],
            "params": [
                {
                  "name": "type",
                  "schema": {
                      "$ref": "#/components/schemas/InterestType",
                  }
                },
                {
                  "name": "reason",
                  "schema": {
                      "$ref": "#/components/schemas/InterestReason",
                  }
                },
                {
                  "name": "entity",
                  "schema": {
                      "$ref": "https://meta.comcast.com/firebolt/entity#/definitions/EntityDetails"
                  }                    
                }
            ],
            "result": {
                "name": "result",
                "schema": {
                    "type": "null"
                }
            }
        }
    ]
}
```

Platform Method:

```json
{
    "methods": [
        {
            "name": "onUserInterest",
            "tags": [
                {
                    "name": "capabilities",
                    "x-provided-by": "Discovery.userInterest",
                    "x-uses": [
                        "xrn:firebolt:capability:discovery:interest"
                    ]
                },
                {
                    "name": "event"
                }
            ],
            "params": [],
            "result": {
                "name": "interest",
                "schema": {
                    "type": "object",
                    "properties": {
                        "appId": {
                            "type": "string"
                        },
                        "type": {
                            "$ref": "#/components/schemas/InterestType"
                        },
                        "reason": {
                            "$ref": "#/components/schemas/InterestReason"
                        },
                        "entity": {
                            "$ref": "https://meta.comcast.com/firebolt/entity#/definitions/EntityDetails"
                        }
                    }
                    
                }
            }
        }
    ]
}
```
