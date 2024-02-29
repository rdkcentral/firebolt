---
title: Firebolt APIs

layout: default
---

[![semantic-release: conventional](https://img.shields.io/badge/semantic--release-conventional-e10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)

# Firebolt APIs
Firebolt APIs are defined by [OpenRPC schemas](https://spec.open-rpc.org).

The schemas are used to generate SDK and Documentation artifacts.

### `xrn:firebolt:capability:accessibility:audiodescriptions`

| Uses |
| ---- |
| [Accessibility.audioDescriptionSettings](./core/Accessibility/#audiodescriptionsettings)<br/>[Accessibility.onAudioDescriptionSettingsChanged](./core/Accessibility/#audiodescriptionsettingschanged)<br/>[AudioDescriptions.enabled](./manage/AudioDescriptions/#enabled)<br/>[AudioDescriptions.onEnabledChanged](./manage/AudioDescriptions/#enabledchanged) |



| Manages |
| ------- |
| [AudioDescriptions.setEnabled](./manage/AudioDescriptions/#setenabled) |


### `xrn:firebolt:capability:accessibility:closedcaptions`

| Uses |
| ---- |
| [Accessibility.closedCaptions](./core/Accessibility/#closedcaptions)<br/>[Accessibility.closedCaptionsSettings](./core/Accessibility/#closedcaptionssettings)<br/>[Accessibility.onClosedCaptionsSettingsChanged](./core/Accessibility/#closedcaptionssettingschanged)<br/>[ClosedCaptions.enabled](./manage/ClosedCaptions/#enabled)<br/>[ClosedCaptions.fontFamily](./manage/ClosedCaptions/#fontfamily)<br/>[ClosedCaptions.fontSize](./manage/ClosedCaptions/#fontsize)<br/>[ClosedCaptions.fontColor](./manage/ClosedCaptions/#fontcolor)<br/>[ClosedCaptions.fontEdge](./manage/ClosedCaptions/#fontedge)<br/>[ClosedCaptions.fontEdgeColor](./manage/ClosedCaptions/#fontedgecolor)<br/>[ClosedCaptions.fontOpacity](./manage/ClosedCaptions/#fontopacity)<br/>[ClosedCaptions.backgroundColor](./manage/ClosedCaptions/#backgroundcolor)<br/>[ClosedCaptions.backgroundOpacity](./manage/ClosedCaptions/#backgroundopacity)<br/>[ClosedCaptions.textAlign](./manage/ClosedCaptions/#textalign)<br/>[ClosedCaptions.textAlignVertical](./manage/ClosedCaptions/#textalignvertical)<br/>[ClosedCaptions.windowColor](./manage/ClosedCaptions/#windowcolor)<br/>[ClosedCaptions.windowOpacity](./manage/ClosedCaptions/#windowopacity)<br/>[ClosedCaptions.preferredLanguages](./manage/ClosedCaptions/#preferredlanguages)<br/>[ClosedCaptions.onEnabledChanged](./manage/ClosedCaptions/#enabledchanged)<br/>[ClosedCaptions.onFontFamilyChanged](./manage/ClosedCaptions/#fontfamilychanged)<br/>[ClosedCaptions.onFontSizeChanged](./manage/ClosedCaptions/#fontsizechanged)<br/>[ClosedCaptions.onFontColorChanged](./manage/ClosedCaptions/#fontcolorchanged)<br/>[ClosedCaptions.onFontEdgeChanged](./manage/ClosedCaptions/#fontedgechanged)<br/>[ClosedCaptions.onFontEdgeColorChanged](./manage/ClosedCaptions/#fontedgecolorchanged)<br/>[ClosedCaptions.onFontOpacityChanged](./manage/ClosedCaptions/#fontopacitychanged)<br/>[ClosedCaptions.onBackgroundColorChanged](./manage/ClosedCaptions/#backgroundcolorchanged)<br/>[ClosedCaptions.onBackgroundOpacityChanged](./manage/ClosedCaptions/#backgroundopacitychanged)<br/>[ClosedCaptions.onTextAlignChanged](./manage/ClosedCaptions/#textalignchanged)<br/>[ClosedCaptions.onTextAlignVerticalChanged](./manage/ClosedCaptions/#textalignverticalchanged)<br/>[ClosedCaptions.onWindowColorChanged](./manage/ClosedCaptions/#windowcolorchanged)<br/>[ClosedCaptions.onWindowOpacityChanged](./manage/ClosedCaptions/#windowopacitychanged)<br/>[ClosedCaptions.onPreferredLanguagesChanged](./manage/ClosedCaptions/#preferredlanguageschanged) |



| Manages |
| ------- |
| [ClosedCaptions.setEnabled](./manage/ClosedCaptions/#setenabled)<br/>[ClosedCaptions.setFontFamily](./manage/ClosedCaptions/#setfontfamily)<br/>[ClosedCaptions.setFontSize](./manage/ClosedCaptions/#setfontsize)<br/>[ClosedCaptions.setFontColor](./manage/ClosedCaptions/#setfontcolor)<br/>[ClosedCaptions.setFontEdge](./manage/ClosedCaptions/#setfontedge)<br/>[ClosedCaptions.setFontEdgeColor](./manage/ClosedCaptions/#setfontedgecolor)<br/>[ClosedCaptions.setFontOpacity](./manage/ClosedCaptions/#setfontopacity)<br/>[ClosedCaptions.setBackgroundColor](./manage/ClosedCaptions/#setbackgroundcolor)<br/>[ClosedCaptions.setBackgroundOpacity](./manage/ClosedCaptions/#setbackgroundopacity)<br/>[ClosedCaptions.setTextAlign](./manage/ClosedCaptions/#settextalign)<br/>[ClosedCaptions.setTextAlignVertical](./manage/ClosedCaptions/#settextalignvertical)<br/>[ClosedCaptions.setWindowColor](./manage/ClosedCaptions/#setwindowcolor)<br/>[ClosedCaptions.setWindowOpacity](./manage/ClosedCaptions/#setwindowopacity)<br/>[ClosedCaptions.setPreferredLanguages](./manage/ClosedCaptions/#setpreferredlanguages) |


### `xrn:firebolt:capability:accessibility:voiceguidance`

| Uses |
| ---- |
| [Accessibility.voiceGuidance](./core/Accessibility/#voiceguidance)<br/>[Accessibility.voiceGuidanceSettings](./core/Accessibility/#voiceguidancesettings)<br/>[Accessibility.onVoiceGuidanceSettingsChanged](./core/Accessibility/#voiceguidancesettingschanged)<br/>[VoiceGuidance.enabled](./manage/VoiceGuidance/#enabled)<br/>[VoiceGuidance.speed](./manage/VoiceGuidance/#speed)<br/>[VoiceGuidance.onEnabledChanged](./manage/VoiceGuidance/#enabledchanged)<br/>[VoiceGuidance.onSpeedChanged](./manage/VoiceGuidance/#speedchanged) |



| Manages |
| ------- |
| [VoiceGuidance.setEnabled](./manage/VoiceGuidance/#setenabled)<br/>[VoiceGuidance.setSpeed](./manage/VoiceGuidance/#setspeed) |


### `xrn:firebolt:capability:account:id`

| Uses |
| ---- |
| [Account.id](./core/Account/#id) |



| Manages |
| ------- |
| [Device.provision](./manage/Device/#provision) |


### `xrn:firebolt:capability:account:uid`

| Uses |
| ---- |
| [Account.uid](./core/Account/#uid) |


### `xrn:firebolt:capability:advertising:configuration`

| Uses |
| ---- |
| [Advertising.config](./core/Advertising/#config)<br/>[Advertising.policy](./core/Advertising/#policy)<br/>[Advertising.deviceAttributes](./core/Advertising/#deviceattributes)<br/>[Advertising.appBundleId](./core/Advertising/#appbundleid)<br/>[Advertising.onPolicyChanged](./core/Advertising/#policychanged) |



| Manages |
| ------- |
| [Advertising.skipRestriction](./manage/Advertising/#skiprestriction)<br/>[Advertising.onSkipRestrictionChanged](./manage/Advertising/#skiprestrictionchanged)<br/>[Advertising.setSkipRestriction](./manage/Advertising/#setskiprestriction) |


### `xrn:firebolt:capability:advertising:identifier`

| Uses |
| ---- |
| [Advertising.advertisingId](./core/Advertising/#advertisingid) |



| Manages |
| ------- |
| [Advertising.resetIdentifier](./manage/Advertising/#resetidentifier) |


### `xrn:firebolt:capability:approve:content`

| Uses |
| ---- |
| [Profile.approveContentRating](./core/Profile/#approvecontentrating) |


### `xrn:firebolt:capability:approve:purchase`

| Uses |
| ---- |
| [Profile.approvePurchase](./core/Profile/#approvepurchase) |


### `xrn:firebolt:capability:capabilities:info`

| Uses |
| ---- |
| [Capabilities.supported](./core/Capabilities/#supported)<br/>[Capabilities.available](./core/Capabilities/#available)<br/>[Capabilities.permitted](./core/Capabilities/#permitted)<br/>[Capabilities.granted](./core/Capabilities/#granted)<br/>[Capabilities.info](./core/Capabilities/#info)<br/>[Capabilities.onAvailable](./core/Capabilities/#available)<br/>[Capabilities.onUnavailable](./core/Capabilities/#unavailable)<br/>[Capabilities.onGranted](./core/Capabilities/#granted)<br/>[Capabilities.onRevoked](./core/Capabilities/#revoked) |


### `xrn:firebolt:capability:capabilities:request`

| Uses |
| ---- |
| [Capabilities.request](./core/Capabilities/#request) |


### `xrn:firebolt:capability:device:distributor`

| Uses |
| ---- |
| [Device.distributor](./core/Device/#distributor) |



| Manages |
| ------- |
| [Device.provision](./manage/Device/#provision) |


### `xrn:firebolt:capability:device:id`

| Uses |
| ---- |
| [Device.id](./core/Device/#id) |



| Manages |
| ------- |
| [Device.provision](./manage/Device/#provision) |


### `xrn:firebolt:capability:device:info`

| Uses |
| ---- |
| [Device.platform](./core/Device/#platform)<br/>[Device.type](./core/Device/#type)<br/>[Device.version](./core/Device/#version)<br/>[Device.hdcp](./core/Device/#hdcp)<br/>[Device.hdr](./core/Device/#hdr)<br/>[Device.audio](./core/Device/#audio)<br/>[Device.screenResolution](./core/Device/#screenresolution)<br/>[Device.videoResolution](./core/Device/#videoresolution)<br/>[Device.onHdcpChanged](./core/Device/#hdcpchanged)<br/>[Device.onHdrChanged](./core/Device/#hdrchanged)<br/>[Device.onAudioChanged](./core/Device/#audiochanged)<br/>[Device.onScreenResolutionChanged](./core/Device/#screenresolutionchanged)<br/>[Device.onVideoResolutionChanged](./core/Device/#videoresolutionchanged)<br/>[SecondScreen.protocols](./core/SecondScreen/#protocols) |


### `xrn:firebolt:capability:device:make`

| Uses |
| ---- |
| [Device.make](./core/Device/#make) |


### `xrn:firebolt:capability:device:model`

| Uses |
| ---- |
| [Device.model](./core/Device/#model) |


### `xrn:firebolt:capability:device:name`

| Uses |
| ---- |
| [Device.name](./core/Device/#name)<br/>[Device.onDeviceNameChanged](./core/Device/#devicenamechanged)<br/>[Device.onNameChanged](./core/Device/#namechanged) |



| Manages |
| ------- |
| [Device.setName](./manage/Device/#setname) |


### `xrn:firebolt:capability:device:sku`

| Uses |
| ---- |
| [Device.sku](./core/Device/#sku) |


### `xrn:firebolt:capability:device:uid`

| Uses |
| ---- |
| [Device.uid](./core/Device/#uid) |


### `xrn:firebolt:capability:discovery:content-access`

| Uses |
| ---- |
| [Discovery.entitlements](./core/Discovery/#entitlements)<br/>[Discovery.contentAccess](./core/Discovery/#contentaccess)<br/>[Discovery.clearContentAccess](./core/Discovery/#clearcontentaccess) |


### `xrn:firebolt:capability:discovery:entity-info`

| Provides |
| -------- |
| [Discovery.entityInfo](./core/Discovery/#entityinfo)<br/>[Discovery.onPullEntityInfo](./core/Discovery/#pullentityinfo) |


### `xrn:firebolt:capability:discovery:navigate-to`

| Uses |
| ---- |
| [Discovery.onNavigateTo](./core/Discovery/#navigateto) |


### `xrn:firebolt:capability:discovery:policy`

| Uses |
| ---- |
| [Discovery.policy](./core/Discovery/#policy)<br/>[Discovery.onPolicyChanged](./core/Discovery/#policychanged) |


### `xrn:firebolt:capability:discovery:purchased-content`

| Provides |
| -------- |
| [Discovery.purchasedContent](./core/Discovery/#purchasedcontent)<br/>[Discovery.onPullPurchasedContent](./core/Discovery/#pullpurchasedcontent) |


### `xrn:firebolt:capability:discovery:sign-in-status`

| Uses |
| ---- |
| [Discovery.signIn](./core/Discovery/#signin)<br/>[Discovery.signOut](./core/Discovery/#signout) |



| Manages |
| ------- |
| [Discovery.onSignIn](./manage/Discovery/#signin)<br/>[Discovery.onSignOut](./manage/Discovery/#signout) |


### `xrn:firebolt:capability:discovery:watch-next`

| Uses |
| ---- |
| [Discovery.watchNext](./core/Discovery/#watchnext) |


### `xrn:firebolt:capability:discovery:watched`

| Uses |
| ---- |
| [Discovery.watched](./core/Discovery/#watched) |


### `xrn:firebolt:capability:grants:state`

| Uses |
| ---- |
| [UserGrants.app](./manage/UserGrants/#app)<br/>[UserGrants.device](./manage/UserGrants/#device)<br/>[UserGrants.capability](./manage/UserGrants/#capability) |



| Manages |
| ------- |
| [UserGrants.grant](./manage/UserGrants/#grant)<br/>[UserGrants.deny](./manage/UserGrants/#deny)<br/>[UserGrants.clear](./manage/UserGrants/#clear)<br/>[UserGrants.request](./manage/UserGrants/#request) |


### `xrn:firebolt:capability:input:keyboard`

| Uses |
| ---- |
| [Keyboard.email](./core/Keyboard/#email)<br/>[Keyboard.password](./core/Keyboard/#password)<br/>[Keyboard.standard](./core/Keyboard/#standard) |



| Provides |
| -------- |
| [Keyboard.onRequestStandard](./manage/Keyboard/#requeststandard)<br/>[Keyboard.onRequestPassword](./manage/Keyboard/#requestpassword)<br/>[Keyboard.onRequestEmail](./manage/Keyboard/#requestemail)<br/>[Keyboard.standardFocus](./manage/Keyboard/#standardfocus)<br/>[Keyboard.passwordFocus](./manage/Keyboard/#passwordfocus)<br/>[Keyboard.emailFocus](./manage/Keyboard/#emailfocus)<br/>[Keyboard.standardResponse](./manage/Keyboard/#standardresponse)<br/>[Keyboard.standardError](./manage/Keyboard/#standarderror)<br/>[Keyboard.passwordResponse](./manage/Keyboard/#passwordresponse)<br/>[Keyboard.passwordError](./manage/Keyboard/#passworderror)<br/>[Keyboard.emailResponse](./manage/Keyboard/#emailresponse)<br/>[Keyboard.emailError](./manage/Keyboard/#emailerror) |


### `xrn:firebolt:capability:inputs:hdmi`

| Uses |
| ---- |
| [HDMIInput.ports](./manage/HDMIInput/#ports)<br/>[HDMIInput.port](./manage/HDMIInput/#port)<br/>[HDMIInput.onConnectionChanged](./manage/HDMIInput/#connectionchanged)<br/>[HDMIInput.onSignalChanged](./manage/HDMIInput/#signalchanged)<br/>[HDMIInput.lowLatencyMode](./manage/HDMIInput/#lowlatencymode)<br/>[HDMIInput.onAutoLowLatencyModeSignalChanged](./manage/HDMIInput/#autolowlatencymodesignalchanged)<br/>[HDMIInput.autoLowLatencyModeCapable](./manage/HDMIInput/#autolowlatencymodecapable)<br/>[HDMIInput.edidVersion](./manage/HDMIInput/#edidversion)<br/>[HDMIInput.onLowLatencyModeChanged](./manage/HDMIInput/#lowlatencymodechanged)<br/>[HDMIInput.onAutoLowLatencyModeCapableChanged](./manage/HDMIInput/#autolowlatencymodecapablechanged)<br/>[HDMIInput.onEdidVersionChanged](./manage/HDMIInput/#edidversionchanged) |



| Manages |
| ------- |
| [HDMIInput.open](./manage/HDMIInput/#open)<br/>[HDMIInput.close](./manage/HDMIInput/#close)<br/>[HDMIInput.setLowLatencyMode](./manage/HDMIInput/#setlowlatencymode)<br/>[HDMIInput.setAutoLowLatencyModeCapable](./manage/HDMIInput/#setautolowlatencymodecapable)<br/>[HDMIInput.setEdidVersion](./manage/HDMIInput/#setedidversion) |


### `xrn:firebolt:capability:lifecycle:initialize`

| Uses |
| ---- |
| [Internal.initialize](./core/Internal/#initialize) |


### `xrn:firebolt:capability:lifecycle:launch`

| Uses |
| ---- |
| [Discovery.launch](./core/Discovery/#launch) |


### `xrn:firebolt:capability:lifecycle:ready`

| Uses |
| ---- |
| [Lifecycle.ready](./core/Lifecycle/#ready) |


### `xrn:firebolt:capability:lifecycle:state`

| Uses |
| ---- |
| [Lifecycle.close](./core/Lifecycle/#close)<br/>[Lifecycle.finished](./core/Lifecycle/#finished)<br/>[Lifecycle.state](./core/Lifecycle/#state)<br/>[Lifecycle.onInactive](./core/Lifecycle/#inactive)<br/>[Lifecycle.onForeground](./core/Lifecycle/#foreground)<br/>[Lifecycle.onBackground](./core/Lifecycle/#background)<br/>[Lifecycle.onSuspended](./core/Lifecycle/#suspended)<br/>[Lifecycle.onUnloading](./core/Lifecycle/#unloading)<br/>[Parameters.initialization](./core/Parameters/#initialization) |


### `xrn:firebolt:capability:localization:additional-info`

| Uses |
| ---- |
| [Localization.additionalInfo](./core/Localization/#additionalinfo) |



| Manages |
| ------- |
| [Localization.addAdditionalInfo](./manage/Localization/#addadditionalinfo)<br/>[Localization.removeAdditionalInfo](./manage/Localization/#removeadditionalinfo) |


### `xrn:firebolt:capability:localization:country-code`

| Uses |
| ---- |
| [Localization.countryCode](./core/Localization/#countrycode)<br/>[Localization.onCountryCodeChanged](./core/Localization/#countrycodechanged) |



| Manages |
| ------- |
| [Localization.setCountryCode](./manage/Localization/#setcountrycode) |


### `xrn:firebolt:capability:localization:language`

| Uses |
| ---- |
| [Localization.language](./core/Localization/#language)<br/>[Localization.preferredAudioLanguages](./core/Localization/#preferredaudiolanguages)<br/>[Localization.onLanguageChanged](./core/Localization/#languagechanged)<br/>[Localization.onPreferredAudioLanguagesChanged](./core/Localization/#preferredaudiolanguageschanged) |



| Manages |
| ------- |
| [Localization.setLanguage](./manage/Localization/#setlanguage)<br/>[Localization.setPreferredAudioLanguages](./manage/Localization/#setpreferredaudiolanguages) |


### `xrn:firebolt:capability:localization:locale`

| Uses |
| ---- |
| [Localization.locale](./core/Localization/#locale)<br/>[Localization.onLocaleChanged](./core/Localization/#localechanged) |



| Manages |
| ------- |
| [Localization.setLocale](./manage/Localization/#setlocale) |


### `xrn:firebolt:capability:localization:locality`

| Uses |
| ---- |
| [Localization.locality](./core/Localization/#locality)<br/>[Localization.onLocalityChanged](./core/Localization/#localitychanged) |



| Manages |
| ------- |
| [Localization.setLocality](./manage/Localization/#setlocality) |


### `xrn:firebolt:capability:localization:location`

| Uses |
| ---- |
| [Localization.latlon](./core/Localization/#latlon) |


### `xrn:firebolt:capability:localization:postal-code`

| Uses |
| ---- |
| [Localization.postalCode](./core/Localization/#postalcode)<br/>[Localization.onPostalCodeChanged](./core/Localization/#postalcodechanged) |



| Manages |
| ------- |
| [Localization.setPostalCode](./manage/Localization/#setpostalcode) |


### `xrn:firebolt:capability:localization:time-zone`

| Uses |
| ---- |
| [Localization.timeZone](./manage/Localization/#timezone)<br/>[Localization.onTimeZoneChanged](./manage/Localization/#timezonechanged) |



| Manages |
| ------- |
| [Localization.setTimeZone](./manage/Localization/#settimezone) |


### `xrn:firebolt:capability:metrics:distributor`

| Uses |
| ---- |
| [Metrics.event](./manage/Metrics/#event) |


### `xrn:firebolt:capability:metrics:general`

| Uses |
| ---- |
| [Metrics.ready](./core/Metrics/#ready)<br/>[Metrics.signIn](./core/Metrics/#signin)<br/>[Metrics.signOut](./core/Metrics/#signout)<br/>[Metrics.startContent](./core/Metrics/#startcontent)<br/>[Metrics.stopContent](./core/Metrics/#stopcontent)<br/>[Metrics.page](./core/Metrics/#page)<br/>[Metrics.action](./core/Metrics/#action)<br/>[Metrics.error](./core/Metrics/#error) |


### `xrn:firebolt:capability:metrics:media`

| Uses |
| ---- |
| [Metrics.mediaLoadStart](./core/Metrics/#medialoadstart)<br/>[Metrics.mediaPlay](./core/Metrics/#mediaplay)<br/>[Metrics.mediaPlaying](./core/Metrics/#mediaplaying)<br/>[Metrics.mediaPause](./core/Metrics/#mediapause)<br/>[Metrics.mediaWaiting](./core/Metrics/#mediawaiting)<br/>[Metrics.mediaProgress](./core/Metrics/#mediaprogress)<br/>[Metrics.mediaSeeking](./core/Metrics/#mediaseeking)<br/>[Metrics.mediaSeeked](./core/Metrics/#mediaseeked)<br/>[Metrics.mediaRateChange](./core/Metrics/#mediaratechange)<br/>[Metrics.mediaRenditionChange](./core/Metrics/#mediarenditionchange)<br/>[Metrics.mediaEnded](./core/Metrics/#mediaended) |


### `xrn:firebolt:capability:network:status`

| Uses |
| ---- |
| [Device.network](./core/Device/#network)<br/>[Device.onNetworkChanged](./core/Device/#networkchanged) |


### `xrn:firebolt:capability:privacy:advertising`

| Uses |
| ---- |
| [Advertising.policy](./core/Advertising/#policy)<br/>[Advertising.onPolicyChanged](./core/Advertising/#policychanged) |


### `xrn:firebolt:capability:privacy:settings`

| Uses |
| ---- |
| [Privacy.allowResumePoints](./manage/Privacy/#allowresumepoints)<br/>[Privacy.allowUnentitledResumePoints](./manage/Privacy/#allowunentitledresumepoints)<br/>[Privacy.allowWatchHistory](./manage/Privacy/#allowwatchhistory)<br/>[Privacy.allowProductAnalytics](./manage/Privacy/#allowproductanalytics)<br/>[Privacy.allowPersonalization](./manage/Privacy/#allowpersonalization)<br/>[Privacy.allowUnentitledPersonalization](./manage/Privacy/#allowunentitledpersonalization)<br/>[Privacy.allowRemoteDiagnostics](./manage/Privacy/#allowremotediagnostics)<br/>[Privacy.allowPrimaryContentAdTargeting](./manage/Privacy/#allowprimarycontentadtargeting)<br/>[Privacy.allowPrimaryBrowseAdTargeting](./manage/Privacy/#allowprimarybrowseadtargeting)<br/>[Privacy.allowAppContentAdTargeting](./manage/Privacy/#allowappcontentadtargeting)<br/>[Privacy.allowACRCollection](./manage/Privacy/#allowacrcollection)<br/>[Privacy.allowCameraAnalytics](./manage/Privacy/#allowcameraanalytics)<br/>[Privacy.settings](./manage/Privacy/#settings)<br/>[Privacy.onAllowResumePointsChanged](./manage/Privacy/#allowresumepointschanged)<br/>[Privacy.onAllowUnentitledResumePointsChanged](./manage/Privacy/#allowunentitledresumepointschanged)<br/>[Privacy.onAllowWatchHistoryChanged](./manage/Privacy/#allowwatchhistorychanged)<br/>[Privacy.onAllowProductAnalyticsChanged](./manage/Privacy/#allowproductanalyticschanged)<br/>[Privacy.onAllowPersonalizationChanged](./manage/Privacy/#allowpersonalizationchanged)<br/>[Privacy.onAllowUnentitledPersonalizationChanged](./manage/Privacy/#allowunentitledpersonalizationchanged)<br/>[Privacy.onAllowRemoteDiagnosticsChanged](./manage/Privacy/#allowremotediagnosticschanged)<br/>[Privacy.onAllowPrimaryContentAdTargetingChanged](./manage/Privacy/#allowprimarycontentadtargetingchanged)<br/>[Privacy.onAllowPrimaryBrowseAdTargetingChanged](./manage/Privacy/#allowprimarybrowseadtargetingchanged)<br/>[Privacy.onAllowAppContentAdTargetingChanged](./manage/Privacy/#allowappcontentadtargetingchanged)<br/>[Privacy.onAllowACRCollectionChanged](./manage/Privacy/#allowacrcollectionchanged)<br/>[Privacy.onAllowCameraAnalyticsChanged](./manage/Privacy/#allowcameraanalyticschanged) |



| Manages |
| ------- |
| [Privacy.setAllowResumePoints](./manage/Privacy/#setallowresumepoints)<br/>[Privacy.setAllowUnentitledResumePoints](./manage/Privacy/#setallowunentitledresumepoints)<br/>[Privacy.setAllowWatchHistory](./manage/Privacy/#setallowwatchhistory)<br/>[Privacy.setAllowProductAnalytics](./manage/Privacy/#setallowproductanalytics)<br/>[Privacy.setAllowPersonalization](./manage/Privacy/#setallowpersonalization)<br/>[Privacy.setAllowUnentitledPersonalization](./manage/Privacy/#setallowunentitledpersonalization)<br/>[Privacy.setAllowRemoteDiagnostics](./manage/Privacy/#setallowremotediagnostics)<br/>[Privacy.setAllowPrimaryContentAdTargeting](./manage/Privacy/#setallowprimarycontentadtargeting)<br/>[Privacy.setAllowPrimaryBrowseAdTargeting](./manage/Privacy/#setallowprimarybrowseadtargeting)<br/>[Privacy.setAllowAppContentAdTargeting](./manage/Privacy/#setallowappcontentadtargeting)<br/>[Privacy.setAllowACRCollection](./manage/Privacy/#setallowacrcollection)<br/>[Privacy.setAllowCameraAnalytics](./manage/Privacy/#setallowcameraanalytics) |


### `xrn:firebolt:capability:profile:flags`

| Uses |
| ---- |
| [Profile.flags](./core/Profile/#flags) |


### `xrn:firebolt:capability:protocol:dial`

| Uses |
| ---- |
| [SecondScreen.device](./core/SecondScreen/#device)<br/>[SecondScreen.friendlyName](./core/SecondScreen/#friendlyname)<br/>[SecondScreen.onLaunchRequest](./core/SecondScreen/#launchrequest)<br/>[SecondScreen.onCloseRequest](./core/SecondScreen/#closerequest)<br/>[SecondScreen.onFriendlyNameChanged](./core/SecondScreen/#friendlynamechanged) |


### `xrn:firebolt:capability:protocol:wifi`

| Uses |
| ---- |
| [Wifi.scan](./manage/Wifi/#scan)<br/>[Wifi.connect](./manage/Wifi/#connect)<br/>[Wifi.disconnect](./manage/Wifi/#disconnect)<br/>[Wifi.wps](./manage/Wifi/#wps) |


### `xrn:firebolt:capability:rpc:discover`

| Uses |
| ---- |
| [rpc.discover](./manage/rpc/#discover) |


### `xrn:firebolt:capability:storage:secure`

| Uses |
| ---- |
| [SecureStorage.get](./core/SecureStorage/#get)<br/>[SecureStorage.set](./core/SecureStorage/#set)<br/>[SecureStorage.remove](./core/SecureStorage/#remove)<br/>[SecureStorage.clear](./core/SecureStorage/#clear) |



| Manages |
| ------- |
| [SecureStorage.setForApp](./manage/SecureStorage/#setforapp)<br/>[SecureStorage.removeForApp](./manage/SecureStorage/#removeforapp)<br/>[SecureStorage.clearForApp](./manage/SecureStorage/#clearforapp) |


### `xrn:firebolt:capability:token:account`

| Manages |
| ------- |
| [Account.session](./manage/Account/#session) |


### `xrn:firebolt:capability:token:device`

| Uses |
| ---- |
| [Authentication.device](./core/Authentication/#device) |


### `xrn:firebolt:capability:token:platform`

| Uses |
| ---- |
| [Authentication.token](./core/Authentication/#token) |


### `xrn:firebolt:capability:token:root`

| Uses |
| ---- |
| [Authentication.root](./core/Authentication/#root) |


### `xrn:firebolt:capability:token:session`

| Uses |
| ---- |
| [Authentication.session](./core/Authentication/#session) |


### `xrn:firebolt:capability:usergrant:acknowledgechallenge`

| Provides |
| -------- |
| [AcknowledgeChallenge.onRequestChallenge](./manage/AcknowledgeChallenge/#requestchallenge)<br/>[AcknowledgeChallenge.challengeFocus](./manage/AcknowledgeChallenge/#challengefocus)<br/>[AcknowledgeChallenge.challengeResponse](./manage/AcknowledgeChallenge/#challengeresponse)<br/>[AcknowledgeChallenge.challengeError](./manage/AcknowledgeChallenge/#challengeerror) |


### `xrn:firebolt:capability:usergrant:pinchallenge`

| Provides |
| -------- |
| [PinChallenge.onRequestChallenge](./manage/PinChallenge/#requestchallenge)<br/>[PinChallenge.challengeFocus](./manage/PinChallenge/#challengefocus)<br/>[PinChallenge.challengeResponse](./manage/PinChallenge/#challengeresponse)<br/>[PinChallenge.challengeError](./manage/PinChallenge/#challengeerror) |


