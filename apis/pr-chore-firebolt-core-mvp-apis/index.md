---
title: Firebolt APIs

layout: default
---

[![semantic-release: conventional](https://img.shields.io/badge/semantic--release-conventional-e10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)

# Firebolt APIs
Firebolt APIs are defined by [OpenRPC schemas](https://spec.open-rpc.org).

The schemas are used to generate SDK and Documentation artifacts.

## Methods
Capability prefix `xrn:firebolt:capability` trimmed for readability.
| Method | Level | Capability |
|-|-|-|
| [Accessibility.audioDescriptionSettings](./core/Accessibility/#audiodescriptionsettings) | **MUST** | `accessibility:audiodescriptions`  |
| [Accessibility.onAudioDescriptionSettingsChanged](./core/Accessibility/#audiodescriptionsettingschanged) | **MUST** | `accessibility:audiodescriptions`  |
| ~~[Accessibility.closedCaptions](./core/Accessibility/#closedcaptions)~~ | **MUST** | `accessibility:closedcaptions`  |
| [Accessibility.closedCaptionsSettings](./core/Accessibility/#closedcaptionssettings) | **MUST** | `accessibility:closedcaptions`  |
| [Accessibility.onClosedCaptionsSettingsChanged](./core/Accessibility/#closedcaptionssettingschanged) | **MUST** | `accessibility:closedcaptions`  |
| [Accessibility.highContrastUI](./core/Accessibility/#highcontrastui) | **MUST** | `accessibility:highcontrastui`  |
| [Accessibility.onHighContrastUIChanged](./core/Accessibility/#highcontrastuichanged) | **MUST** | `accessibility:highcontrastui`  |
| ~~[Accessibility.voiceGuidance](./core/Accessibility/#voiceguidance)~~ | **MUST** | `accessibility:voiceguidance`  |
| [Accessibility.voiceGuidanceSettings](./core/Accessibility/#voiceguidancesettings) | **MUST** | `accessibility:voiceguidance`  |
| [Accessibility.onVoiceGuidanceSettingsChanged](./core/Accessibility/#voiceguidancesettingschanged) | **MUST** | `accessibility:voiceguidance`  |
| [Account.id](./core/Account/#id) | **COULD** | `account:id`  |
| [Account.uid](./core/Account/#uid) | **COULD** | `account:uid`  |
| [Advertising.advertisingId](./core/Advertising/#advertisingid) | **MUST** | `advertising:identifier`  |
| [Advertising.appBundleId](./core/Advertising/#appbundleid) | **COULD** | `advertising:configuration`  |
| [Advertising.config](./core/Advertising/#config) | **COULD** | `advertising:configuration`  |
| [Advertising.deviceAttributes](./core/Advertising/#deviceattributes) | **COULD** | `advertising:configuration`  |
| [Advertising.policy](./core/Advertising/#policy) | **COULD** | `advertising:policy`  |
| [Advertising.onPolicyChanged](./core/Advertising/#policychanged) | **COULD** | `advertising:policy`  |
| [Authentication.device](./core/Authentication/#device) | **COULD** | `token:device`  |
| [Authentication.root](./core/Authentication/#root) | **COULD** | `token:root`  |
| [Authentication.session](./core/Authentication/#session) | **COULD** | `token:session`  |
| ~~[Authentication.token](./core/Authentication/#token)~~ | **COULD** | `token:platform`  |
| [Capabilities.available](./core/Capabilities/#available) | **COULD** | `capabilities:info`  |
| [Capabilities.onAvailable](./core/Capabilities/#available) | **COULD** | `capabilities:info`  |
| [Capabilities.granted](./core/Capabilities/#granted) | **COULD** | `capabilities:info`  |
| [Capabilities.onGranted](./core/Capabilities/#granted) | **COULD** | `capabilities:info`  |
| [Capabilities.info](./core/Capabilities/#info) | **COULD** | `capabilities:info`  |
| [Capabilities.permitted](./core/Capabilities/#permitted) | **COULD** | `capabilities:info`  |
| [Capabilities.request](./core/Capabilities/#request) | **COULD** | `capabilities:request`  |
| [Capabilities.onRevoked](./core/Capabilities/#revoked) | **COULD** | `capabilities:info`  |
| [Capabilities.supported](./core/Capabilities/#supported) | **COULD** | `capabilities:info`  |
| [Capabilities.onUnavailable](./core/Capabilities/#unavailable) | **COULD** | `capabilities:info`  |
| [Device.audio](./core/Device/#audio) | **MUST** | `device:info`  |
| [Device.onAudioChanged](./core/Device/#audiochanged) | **MUST** | `device:info`  |
| ~~[Device.onDeviceNameChanged](./core/Device/#devicenamechanged)~~ | **COULD** | `device:name`  |
| [Device.distributor](./core/Device/#distributor) | **COULD** | `device:distributor`  |
| [Device.hdcp](./core/Device/#hdcp) | **MUST** | `device:info`  |
| [Device.onHdcpChanged](./core/Device/#hdcpchanged) | **MUST** | `device:info`  |
| [Device.hdr](./core/Device/#hdr) | **MUST** | `device:info`  |
| [Device.onHdrChanged](./core/Device/#hdrchanged) | **MUST** | `device:info`  |
| [Device.id](./core/Device/#id) | **COULD** | `device:id`  |
| [Device.make](./core/Device/#make) | **MUST** | `device:make`  |
| [Device.model](./core/Device/#model) | **MUST** | `device:model`  |
| [Device.name](./core/Device/#name) | **COULD** | `device:name`  |
| [Device.onNameChanged](./core/Device/#namechanged) | **COULD** | `device:name`  |
| [Device.network](./core/Device/#network) | **MUST** | `network:status`  |
| [Device.onNetworkChanged](./core/Device/#networkchanged) | **MUST** | `network:status`  |
| ~~[Device.platform](./core/Device/#platform)~~ | **MUST** | `device:info`  |
| ~~[Device.screenResolution](./core/Device/#screenresolution)~~ | **MUST** | `device:info`  |
| ~~[Device.onScreenResolutionChanged](./core/Device/#screenresolutionchanged)~~ | **MUST** | `device:info`  |
| [Device.sku](./core/Device/#sku) | **COULD** | `device:sku`  |
| [Device.type](./core/Device/#type) | **MUST** | `device:info`  |
| [Device.uid](./core/Device/#uid) | **MUST** | `device:uid`  |
| [Device.version](./core/Device/#version) | **MUST** | `device:info`  |
| [Device.videoResolution](./core/Device/#videoresolution) | **MUST** | `device:info`  |
| [Device.onVideoResolutionChanged](./core/Device/#videoresolutionchanged) | **MUST** | `device:info`  |
| [Discovery.clearContentAccess](./core/Discovery/#clearcontentaccess) | **COULD** | `discovery:content-access`  |
| [Discovery.contentAccess](./core/Discovery/#contentaccess) | **COULD** | `discovery:content-access`  |
| ~~[Discovery.entitlements](./core/Discovery/#entitlements)~~ | **COULD** | `discovery:content-access`  |
| ~~[Discovery.entityInfo](./core/Discovery/#entityinfo)~~ | **COULD** | `discovery:entity-info`  (provides) |
| [Discovery.launch](./core/Discovery/#launch) | **COULD** | `lifecycle:launch`  |
| [Discovery.onNavigateTo](./core/Discovery/#navigateto) | **MUST** | `discovery:navigate-to`  |
| [Discovery.policy](./core/Discovery/#policy) | **SHOULD** | `discovery:policy`  |
| [Discovery.onPolicyChanged](./core/Discovery/#policychanged) | **SHOULD** | `discovery:policy`  |
| ~~[Discovery.onPullEntityInfo](./core/Discovery/#pullentityinfo)~~ | **COULD** | `discovery:entity-info`  (provides) |
| ~~[Discovery.onPullPurchasedContent](./core/Discovery/#pullpurchasedcontent)~~ | **COULD** | `discovery:purchased-content`  (provides) |
| ~~[Discovery.purchasedContent](./core/Discovery/#purchasedcontent)~~ | **COULD** | `discovery:purchased-content`  (provides) |
| [Discovery.onRequestUserInterest](./core/Discovery/#requestuserinterest) | **COULD** | `discovery:interest`  (provides) |
| [Discovery.signIn](./core/Discovery/#signin) | **SHOULD** | `discovery:sign-in-status`  |
| [Discovery.signOut](./core/Discovery/#signout) | **SHOULD** | `discovery:sign-in-status`  |
| [Discovery.userInterest](./core/Discovery/#userinterest) | **COULD** | `discovery:interest`  (provides) |
| [Discovery.userInterestError](./core/Discovery/#userinteresterror) | **COULD** | `discovery:interest`  (provides) |
| [Discovery.userInterestResponse](./core/Discovery/#userinterestresponse) | **COULD** | `discovery:interest`  (provides) |
| [Discovery.watchNext](./core/Discovery/#watchnext) | **COULD** | `discovery:watch-next`  |
| [Discovery.watched](./core/Discovery/#watched) | **SHOULD** | `discovery:watched`  |
| [Internal.initialize](./core/Internal/#initialize) | **COULD** | `lifecycle:initialize`  |
| [Keyboard.email](./core/Keyboard/#email) | **SHOULD** | `input:keyboard`  |
| [Keyboard.password](./core/Keyboard/#password) | **SHOULD** | `input:keyboard`  |
| [Keyboard.standard](./core/Keyboard/#standard) | **SHOULD** | `input:keyboard`  |
| [Lifecycle.onBackground](./core/Lifecycle/#background) | **MUST** | `lifecycle:state`  |
| [Lifecycle.close](./core/Lifecycle/#close) | **MUST** | `lifecycle:state`  |
| [Lifecycle.finished](./core/Lifecycle/#finished) | **MUST** | `lifecycle:state`  |
| [Lifecycle.onForeground](./core/Lifecycle/#foreground) | **MUST** | `lifecycle:state`  |
| [Lifecycle.onInactive](./core/Lifecycle/#inactive) | **MUST** | `lifecycle:state`  |
| [Lifecycle.ready](./core/Lifecycle/#ready) | **MUST** | `lifecycle:ready`  |
| [Lifecycle.state](./core/Lifecycle/#state) | **MUST** | `lifecycle:state`  |
| [Lifecycle.onSuspended](./core/Lifecycle/#suspended) | **MUST** | `lifecycle:state`  |
| [Lifecycle.onUnloading](./core/Lifecycle/#unloading) | **MUST** | `lifecycle:state`  |
| [Localization.additionalInfo](./core/Localization/#additionalinfo) | **COULD** | `localization:additional-info`  |
| [Localization.countryCode](./core/Localization/#countrycode) | **MUST** | `localization:country-code`  |
| [Localization.onCountryCodeChanged](./core/Localization/#countrycodechanged) | **MUST** | `localization:country-code`  |
| ~~[Localization.language](./core/Localization/#language)~~ | **MUST** | `localization:language`  |
| ~~[Localization.onLanguageChanged](./core/Localization/#languagechanged)~~ | **MUST** | `localization:language`  |
| [Localization.latlon](./core/Localization/#latlon) | **COULD** | `localization:location`  |
| [Localization.locale](./core/Localization/#locale) | **MUST** | `localization:locale`  |
| [Localization.onLocaleChanged](./core/Localization/#localechanged) | **MUST** | `localization:locale`  |
| [Localization.locality](./core/Localization/#locality) | **COULD** | `localization:locality`  |
| [Localization.onLocalityChanged](./core/Localization/#localitychanged) | **COULD** | `localization:locality`  |
| [Localization.postalCode](./core/Localization/#postalcode) | **COULD** | `localization:postal-code`  |
| [Localization.onPostalCodeChanged](./core/Localization/#postalcodechanged) | **COULD** | `localization:postal-code`  |
| [Localization.preferredAudioLanguages](./core/Localization/#preferredaudiolanguages) | **MUST** | `localization:language`  |
| [Localization.onPreferredAudioLanguagesChanged](./core/Localization/#preferredaudiolanguageschanged) | **MUST** | `localization:language`  |
| [Metrics.action](./core/Metrics/#action) | **MUST** | `metrics:general`  |
| [Metrics.appInfo](./core/Metrics/#appinfo) | **MUST** | `metrics:general`  |
| [Metrics.error](./core/Metrics/#error) | **MUST** | `metrics:general`  |
| [Metrics.mediaEnded](./core/Metrics/#mediaended) | **MUST** | `metrics:media`  |
| [Metrics.mediaLoadStart](./core/Metrics/#medialoadstart) | **MUST** | `metrics:media`  |
| [Metrics.mediaPause](./core/Metrics/#mediapause) | **MUST** | `metrics:media`  |
| [Metrics.mediaPlay](./core/Metrics/#mediaplay) | **MUST** | `metrics:media`  |
| [Metrics.mediaPlaying](./core/Metrics/#mediaplaying) | **MUST** | `metrics:media`  |
| [Metrics.mediaProgress](./core/Metrics/#mediaprogress) | **MUST** | `metrics:media`  |
| [Metrics.mediaRateChange](./core/Metrics/#mediaratechange) | **MUST** | `metrics:media`  |
| [Metrics.mediaRenditionChange](./core/Metrics/#mediarenditionchange) | **MUST** | `metrics:media`  |
| [Metrics.mediaSeeked](./core/Metrics/#mediaseeked) | **MUST** | `metrics:media`  |
| [Metrics.mediaSeeking](./core/Metrics/#mediaseeking) | **MUST** | `metrics:media`  |
| [Metrics.mediaWaiting](./core/Metrics/#mediawaiting) | **MUST** | `metrics:media`  |
| [Metrics.page](./core/Metrics/#page) | **MUST** | `metrics:general`  |
| [Metrics.ready](./core/Metrics/#ready) | **MUST** | `metrics:general`  |
| [Metrics.signIn](./core/Metrics/#signin) | **MUST** | `metrics:general`  |
| [Metrics.signOut](./core/Metrics/#signout) | **MUST** | `metrics:general`  |
| [Metrics.startContent](./core/Metrics/#startcontent) | **MUST** | `metrics:general`  |
| [Metrics.stopContent](./core/Metrics/#stopcontent) | **MUST** | `metrics:general`  |
| [Profile.approveContentRating](./core/Profile/#approvecontentrating) | **SHOULD** | `approve:content`  |
| [Profile.approvePurchase](./core/Profile/#approvepurchase) | **COULD** | `approve:purchase`  |
| [Profile.flags](./core/Profile/#flags) | **COULD** | `profile:flags`  |
| [SecondScreen.onCloseRequest](./core/SecondScreen/#closerequest) | **COULD** | `protocol:dial`  |
| [SecondScreen.device](./core/SecondScreen/#device) | **COULD** | `protocol:dial`  |
| [SecondScreen.friendlyName](./core/SecondScreen/#friendlyname) | **COULD** | `protocol:dial`  |
| [SecondScreen.onFriendlyNameChanged](./core/SecondScreen/#friendlynamechanged) | **COULD** | `protocol:dial`  |
| [SecondScreen.onLaunchRequest](./core/SecondScreen/#launchrequest) | **COULD** | `protocol:dial`  |
| [SecondScreen.protocols](./core/SecondScreen/#protocols) | **COULD** | `secondscreen:protocol`  |
| [SecureStorage.clear](./core/SecureStorage/#clear) | **SHOULD** | `storage:secure`  |
| [SecureStorage.get](./core/SecureStorage/#get) | **SHOULD** | `storage:secure`  |
| [SecureStorage.remove](./core/SecureStorage/#remove) | **SHOULD** | `storage:secure`  |
| [SecureStorage.set](./core/SecureStorage/#set) | **SHOULD** | `storage:secure`  |

## Capailities
| Capability | Level | Uses | Provides |
|-|-|-|-|
| `xrn:firebolt:capability:accessibility:audiodescriptions` | **MUST** | <details><summary>2</summary>[Accessibility.audioDescriptionSettings](./core/Accessibility/#audiodescriptionsettings)<br/>[Accessibility.onAudioDescriptionSettingsChanged](./core/Accessibility/#audiodescriptionsettingschanged)</details> |  |
| `xrn:firebolt:capability:accessibility:closedcaptions` | **MUST** | <details><summary>3</summary>[Accessibility.closedCaptions](./core/Accessibility/#closedcaptions)<br/>[Accessibility.closedCaptionsSettings](./core/Accessibility/#closedcaptionssettings)<br/>[Accessibility.onClosedCaptionsSettingsChanged](./core/Accessibility/#closedcaptionssettingschanged)</details> |  |
| `xrn:firebolt:capability:accessibility:highcontrastui` | **MUST** | <details><summary>2</summary>[Accessibility.highContrastUI](./core/Accessibility/#highcontrastui)<br/>[Accessibility.onHighContrastUIChanged](./core/Accessibility/#highcontrastuichanged)</details> |  |
| `xrn:firebolt:capability:accessibility:voiceguidance` | **MUST** | <details><summary>3</summary>[Accessibility.voiceGuidance](./core/Accessibility/#voiceguidance)<br/>[Accessibility.voiceGuidanceSettings](./core/Accessibility/#voiceguidancesettings)<br/>[Accessibility.onVoiceGuidanceSettingsChanged](./core/Accessibility/#voiceguidancesettingschanged)</details> |  |
| `xrn:firebolt:capability:account:id` | **COULD** | <details><summary>1</summary>[Account.id](./core/Account/#id)</details> |  |
| `xrn:firebolt:capability:account:uid` | **COULD** | <details><summary>1</summary>[Account.uid](./core/Account/#uid)</details> |  |
| `xrn:firebolt:capability:advertising:configuration` | **COULD** | <details><summary>3</summary>[Advertising.config](./core/Advertising/#config)<br/>[Advertising.deviceAttributes](./core/Advertising/#deviceattributes)<br/>[Advertising.appBundleId](./core/Advertising/#appbundleid)</details> |  |
| `xrn:firebolt:capability:advertising:identifier` | **MUST** | <details><summary>1</summary>[Advertising.advertisingId](./core/Advertising/#advertisingid)</details> |  |
| `xrn:firebolt:capability:advertising:policy` | **COULD** | <details><summary>2</summary>[Advertising.policy](./core/Advertising/#policy)<br/>[Advertising.onPolicyChanged](./core/Advertising/#policychanged)</details> |  |
| `xrn:firebolt:capability:approve:content` | **SHOULD** | <details><summary>1</summary>[Profile.approveContentRating](./core/Profile/#approvecontentrating)</details> |  |
| `xrn:firebolt:capability:approve:purchase` | **COULD** | <details><summary>1</summary>[Profile.approvePurchase](./core/Profile/#approvepurchase)</details> |  |
| `xrn:firebolt:capability:capabilities:info` | **COULD** | <details><summary>9</summary>[Capabilities.supported](./core/Capabilities/#supported)<br/>[Capabilities.available](./core/Capabilities/#available)<br/>[Capabilities.permitted](./core/Capabilities/#permitted)<br/>[Capabilities.granted](./core/Capabilities/#granted)<br/>[Capabilities.info](./core/Capabilities/#info)<br/>[Capabilities.onAvailable](./core/Capabilities/#available)<br/>[Capabilities.onUnavailable](./core/Capabilities/#unavailable)<br/>[Capabilities.onGranted](./core/Capabilities/#granted)<br/>[Capabilities.onRevoked](./core/Capabilities/#revoked)</details> |  |
| `xrn:firebolt:capability:capabilities:request` | **COULD** | <details><summary>1</summary>[Capabilities.request](./core/Capabilities/#request)</details> |  |
| `xrn:firebolt:capability:device:distributor` | **COULD** | <details><summary>1</summary>[Device.distributor](./core/Device/#distributor)</details> |  |
| `xrn:firebolt:capability:device:id` | **COULD** | <details><summary>1</summary>[Device.id](./core/Device/#id)</details> |  |
| `xrn:firebolt:capability:device:info` | **MUST** | <details><summary>13</summary>[Device.platform](./core/Device/#platform)<br/>[Device.type](./core/Device/#type)<br/>[Device.version](./core/Device/#version)<br/>[Device.hdcp](./core/Device/#hdcp)<br/>[Device.hdr](./core/Device/#hdr)<br/>[Device.audio](./core/Device/#audio)<br/>[Device.screenResolution](./core/Device/#screenresolution)<br/>[Device.videoResolution](./core/Device/#videoresolution)<br/>[Device.onHdcpChanged](./core/Device/#hdcpchanged)<br/>[Device.onHdrChanged](./core/Device/#hdrchanged)<br/>[Device.onAudioChanged](./core/Device/#audiochanged)<br/>[Device.onScreenResolutionChanged](./core/Device/#screenresolutionchanged)<br/>[Device.onVideoResolutionChanged](./core/Device/#videoresolutionchanged)</details> |  |
| `xrn:firebolt:capability:device:make` | **MUST** | <details><summary>1</summary>[Device.make](./core/Device/#make)</details> |  |
| `xrn:firebolt:capability:device:model` | **MUST** | <details><summary>1</summary>[Device.model](./core/Device/#model)</details> |  |
| `xrn:firebolt:capability:device:name` | **COULD** | <details><summary>3</summary>[Device.name](./core/Device/#name)<br/>[Device.onDeviceNameChanged](./core/Device/#devicenamechanged)<br/>[Device.onNameChanged](./core/Device/#namechanged)</details> |  |
| `xrn:firebolt:capability:device:sku` | **COULD** | <details><summary>1</summary>[Device.sku](./core/Device/#sku)</details> |  |
| `xrn:firebolt:capability:device:uid` | **MUST** | <details><summary>1</summary>[Device.uid](./core/Device/#uid)</details> |  |
| `xrn:firebolt:capability:discovery:content-access` | **COULD** | <details><summary>3</summary>[Discovery.entitlements](./core/Discovery/#entitlements)<br/>[Discovery.contentAccess](./core/Discovery/#contentaccess)<br/>[Discovery.clearContentAccess](./core/Discovery/#clearcontentaccess)</details> |  |
| `xrn:firebolt:capability:discovery:entity-info` | **COULD** |  | <details><summary>2</summary>[Discovery.entityInfo](./core/Discovery/#entityinfo)<br/>[Discovery.onPullEntityInfo](./core/Discovery/#pullentityinfo)</details> |
| `xrn:firebolt:capability:discovery:interest` | **COULD** |  | <details><summary>4</summary>[Discovery.userInterest](./core/Discovery/#userinterest)<br/>[Discovery.onRequestUserInterest](./core/Discovery/#requestuserinterest)<br/>[Discovery.userInterestResponse](./core/Discovery/#userinterestresponse)<br/>[Discovery.userInterestError](./core/Discovery/#userinteresterror)</details> |
| `xrn:firebolt:capability:discovery:navigate-to` | **MUST** | <details><summary>1</summary>[Discovery.onNavigateTo](./core/Discovery/#navigateto)</details> |  |
| `xrn:firebolt:capability:discovery:policy` | **SHOULD** | <details><summary>2</summary>[Discovery.policy](./core/Discovery/#policy)<br/>[Discovery.onPolicyChanged](./core/Discovery/#policychanged)</details> |  |
| `xrn:firebolt:capability:discovery:purchased-content` | **COULD** |  | <details><summary>2</summary>[Discovery.purchasedContent](./core/Discovery/#purchasedcontent)<br/>[Discovery.onPullPurchasedContent](./core/Discovery/#pullpurchasedcontent)</details> |
| `xrn:firebolt:capability:discovery:sign-in-status` | **SHOULD** | <details><summary>2</summary>[Discovery.signIn](./core/Discovery/#signin)<br/>[Discovery.signOut](./core/Discovery/#signout)</details> |  |
| `xrn:firebolt:capability:discovery:watch-next` | **COULD** | <details><summary>1</summary>[Discovery.watchNext](./core/Discovery/#watchnext)</details> |  |
| `xrn:firebolt:capability:discovery:watched` | **SHOULD** | <details><summary>1</summary>[Discovery.watched](./core/Discovery/#watched)</details> |  |
| `xrn:firebolt:capability:input:keyboard` | **SHOULD** | <details><summary>3</summary>[Keyboard.email](./core/Keyboard/#email)<br/>[Keyboard.password](./core/Keyboard/#password)<br/>[Keyboard.standard](./core/Keyboard/#standard)</details> |  |
| `xrn:firebolt:capability:lifecycle:initialize` | **COULD** | <details><summary>1</summary>[Internal.initialize](./core/Internal/#initialize)</details> |  |
| `xrn:firebolt:capability:lifecycle:launch` | **COULD** | <details><summary>1</summary>[Discovery.launch](./core/Discovery/#launch)</details> |  |
| `xrn:firebolt:capability:lifecycle:ready` | **MUST** | <details><summary>1</summary>[Lifecycle.ready](./core/Lifecycle/#ready)</details> |  |
| `xrn:firebolt:capability:lifecycle:state` | **MUST** | <details><summary>8</summary>[Lifecycle.close](./core/Lifecycle/#close)<br/>[Lifecycle.finished](./core/Lifecycle/#finished)<br/>[Lifecycle.state](./core/Lifecycle/#state)<br/>[Lifecycle.onInactive](./core/Lifecycle/#inactive)<br/>[Lifecycle.onForeground](./core/Lifecycle/#foreground)<br/>[Lifecycle.onBackground](./core/Lifecycle/#background)<br/>[Lifecycle.onSuspended](./core/Lifecycle/#suspended)<br/>[Lifecycle.onUnloading](./core/Lifecycle/#unloading)</details> |  |
| `xrn:firebolt:capability:localization:additional-info` | **COULD** | <details><summary>1</summary>[Localization.additionalInfo](./core/Localization/#additionalinfo)</details> |  |
| `xrn:firebolt:capability:localization:country-code` | **MUST** | <details><summary>2</summary>[Localization.countryCode](./core/Localization/#countrycode)<br/>[Localization.onCountryCodeChanged](./core/Localization/#countrycodechanged)</details> |  |
| `xrn:firebolt:capability:localization:language` | **MUST** | <details><summary>4</summary>[Localization.language](./core/Localization/#language)<br/>[Localization.preferredAudioLanguages](./core/Localization/#preferredaudiolanguages)<br/>[Localization.onLanguageChanged](./core/Localization/#languagechanged)<br/>[Localization.onPreferredAudioLanguagesChanged](./core/Localization/#preferredaudiolanguageschanged)</details> |  |
| `xrn:firebolt:capability:localization:locale` | **MUST** | <details><summary>2</summary>[Localization.locale](./core/Localization/#locale)<br/>[Localization.onLocaleChanged](./core/Localization/#localechanged)</details> |  |
| `xrn:firebolt:capability:localization:locality` | **COULD** | <details><summary>2</summary>[Localization.locality](./core/Localization/#locality)<br/>[Localization.onLocalityChanged](./core/Localization/#localitychanged)</details> |  |
| `xrn:firebolt:capability:localization:location` | **COULD** | <details><summary>1</summary>[Localization.latlon](./core/Localization/#latlon)</details> |  |
| `xrn:firebolt:capability:localization:postal-code` | **COULD** | <details><summary>2</summary>[Localization.postalCode](./core/Localization/#postalcode)<br/>[Localization.onPostalCodeChanged](./core/Localization/#postalcodechanged)</details> |  |
| `xrn:firebolt:capability:metrics:general` | **MUST** | <details><summary>9</summary>[Metrics.ready](./core/Metrics/#ready)<br/>[Metrics.signIn](./core/Metrics/#signin)<br/>[Metrics.signOut](./core/Metrics/#signout)<br/>[Metrics.startContent](./core/Metrics/#startcontent)<br/>[Metrics.stopContent](./core/Metrics/#stopcontent)<br/>[Metrics.page](./core/Metrics/#page)<br/>[Metrics.action](./core/Metrics/#action)<br/>[Metrics.error](./core/Metrics/#error)<br/>[Metrics.appInfo](./core/Metrics/#appinfo)</details> |  |
| `xrn:firebolt:capability:metrics:media` | **MUST** | <details><summary>11</summary>[Metrics.mediaLoadStart](./core/Metrics/#medialoadstart)<br/>[Metrics.mediaPlay](./core/Metrics/#mediaplay)<br/>[Metrics.mediaPlaying](./core/Metrics/#mediaplaying)<br/>[Metrics.mediaPause](./core/Metrics/#mediapause)<br/>[Metrics.mediaWaiting](./core/Metrics/#mediawaiting)<br/>[Metrics.mediaProgress](./core/Metrics/#mediaprogress)<br/>[Metrics.mediaSeeking](./core/Metrics/#mediaseeking)<br/>[Metrics.mediaSeeked](./core/Metrics/#mediaseeked)<br/>[Metrics.mediaRateChange](./core/Metrics/#mediaratechange)<br/>[Metrics.mediaRenditionChange](./core/Metrics/#mediarenditionchange)<br/>[Metrics.mediaEnded](./core/Metrics/#mediaended)</details> |  |
| `xrn:firebolt:capability:network:status` | **MUST** | <details><summary>2</summary>[Device.network](./core/Device/#network)<br/>[Device.onNetworkChanged](./core/Device/#networkchanged)</details> |  |
| `xrn:firebolt:capability:profile:flags` | **COULD** | <details><summary>1</summary>[Profile.flags](./core/Profile/#flags)</details> |  |
| `xrn:firebolt:capability:protocol:dial` | **COULD** | <details><summary>5</summary>[SecondScreen.device](./core/SecondScreen/#device)<br/>[SecondScreen.friendlyName](./core/SecondScreen/#friendlyname)<br/>[SecondScreen.onLaunchRequest](./core/SecondScreen/#launchrequest)<br/>[SecondScreen.onCloseRequest](./core/SecondScreen/#closerequest)<br/>[SecondScreen.onFriendlyNameChanged](./core/SecondScreen/#friendlynamechanged)</details> |  |
| `xrn:firebolt:capability:secondscreen:protocol` | **COULD** | <details><summary>1</summary>[SecondScreen.protocols](./core/SecondScreen/#protocols)</details> |  |
| `xrn:firebolt:capability:storage:secure` | **SHOULD** | <details><summary>4</summary>[SecureStorage.get](./core/SecureStorage/#get)<br/>[SecureStorage.set](./core/SecureStorage/#set)<br/>[SecureStorage.remove](./core/SecureStorage/#remove)<br/>[SecureStorage.clear](./core/SecureStorage/#clear)</details> |  |
| `xrn:firebolt:capability:token:device` | **COULD** | <details><summary>1</summary>[Authentication.device](./core/Authentication/#device)</details> |  |
| `xrn:firebolt:capability:token:platform` | **COULD** | <details><summary>1</summary>[Authentication.token](./core/Authentication/#token)</details> |  |
| `xrn:firebolt:capability:token:root` | **COULD** | <details><summary>1</summary>[Authentication.root](./core/Authentication/#root)</details> |  |
| `xrn:firebolt:capability:token:session` | **COULD** | <details><summary>1</summary>[Authentication.session](./core/Authentication/#session)</details> |  |
