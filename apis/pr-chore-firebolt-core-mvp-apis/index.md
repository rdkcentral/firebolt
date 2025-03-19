---
title: Firebolt APIs

layout: default
---

[![semantic-release: conventional](https://img.shields.io/badge/semantic--release-conventional-e10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)

# Firebolt APIs
Firebolt APIs are defined by [OpenRPC schemas](https://spec.open-rpc.org).

The schemas are used to generate SDK and Documentation artifacts.

## Capailities
| Capability | Level | Uses | Provides | Manages |
|-|-|-|-|-|
| `xrn:firebolt:capability:accessibility:audiodescriptions` | **MUST** | <details><summary>4</summary>[Accessibility.audioDescriptionSettings](./core/Accessibility/#audiodescriptionsettings)<br/>[Accessibility.onAudioDescriptionSettingsChanged](./core/Accessibility/#audiodescriptionsettingschanged)<br/>[AudioDescriptions.enabled](./manage/AudioDescriptions/#enabled)<br/>[AudioDescriptions.onEnabledChanged](./manage/AudioDescriptions/#enabledchanged)</details> |  | <details><summary>1</summary>[AudioDescriptions.setEnabled](./manage/AudioDescriptions/#setenabled)</details> |
| `xrn:firebolt:capability:accessibility:closedcaptions` | **MUST** | <details><summary>31</summary>[Accessibility.closedCaptions](./core/Accessibility/#closedcaptions)<br/>[Accessibility.closedCaptionsSettings](./core/Accessibility/#closedcaptionssettings)<br/>[Accessibility.onClosedCaptionsSettingsChanged](./core/Accessibility/#closedcaptionssettingschanged)<br/>[ClosedCaptions.enabled](./manage/ClosedCaptions/#enabled)<br/>[ClosedCaptions.fontFamily](./manage/ClosedCaptions/#fontfamily)<br/>[ClosedCaptions.fontSize](./manage/ClosedCaptions/#fontsize)<br/>[ClosedCaptions.fontColor](./manage/ClosedCaptions/#fontcolor)<br/>[ClosedCaptions.fontEdge](./manage/ClosedCaptions/#fontedge)<br/>[ClosedCaptions.fontEdgeColor](./manage/ClosedCaptions/#fontedgecolor)<br/>[ClosedCaptions.fontOpacity](./manage/ClosedCaptions/#fontopacity)<br/>[ClosedCaptions.backgroundColor](./manage/ClosedCaptions/#backgroundcolor)<br/>[ClosedCaptions.backgroundOpacity](./manage/ClosedCaptions/#backgroundopacity)<br/>[ClosedCaptions.textAlign](./manage/ClosedCaptions/#textalign)<br/>[ClosedCaptions.textAlignVertical](./manage/ClosedCaptions/#textalignvertical)<br/>[ClosedCaptions.windowColor](./manage/ClosedCaptions/#windowcolor)<br/>[ClosedCaptions.windowOpacity](./manage/ClosedCaptions/#windowopacity)<br/>[ClosedCaptions.preferredLanguages](./manage/ClosedCaptions/#preferredlanguages)<br/>[ClosedCaptions.onEnabledChanged](./manage/ClosedCaptions/#enabledchanged)<br/>[ClosedCaptions.onFontFamilyChanged](./manage/ClosedCaptions/#fontfamilychanged)<br/>[ClosedCaptions.onFontSizeChanged](./manage/ClosedCaptions/#fontsizechanged)<br/>[ClosedCaptions.onFontColorChanged](./manage/ClosedCaptions/#fontcolorchanged)<br/>[ClosedCaptions.onFontEdgeChanged](./manage/ClosedCaptions/#fontedgechanged)<br/>[ClosedCaptions.onFontEdgeColorChanged](./manage/ClosedCaptions/#fontedgecolorchanged)<br/>[ClosedCaptions.onFontOpacityChanged](./manage/ClosedCaptions/#fontopacitychanged)<br/>[ClosedCaptions.onBackgroundColorChanged](./manage/ClosedCaptions/#backgroundcolorchanged)<br/>[ClosedCaptions.onBackgroundOpacityChanged](./manage/ClosedCaptions/#backgroundopacitychanged)<br/>[ClosedCaptions.onTextAlignChanged](./manage/ClosedCaptions/#textalignchanged)<br/>[ClosedCaptions.onTextAlignVerticalChanged](./manage/ClosedCaptions/#textalignverticalchanged)<br/>[ClosedCaptions.onWindowColorChanged](./manage/ClosedCaptions/#windowcolorchanged)<br/>[ClosedCaptions.onWindowOpacityChanged](./manage/ClosedCaptions/#windowopacitychanged)<br/>[ClosedCaptions.onPreferredLanguagesChanged](./manage/ClosedCaptions/#preferredlanguageschanged)</details> |  | <details><summary>14</summary>[ClosedCaptions.setEnabled](./manage/ClosedCaptions/#setenabled)<br/>[ClosedCaptions.setFontFamily](./manage/ClosedCaptions/#setfontfamily)<br/>[ClosedCaptions.setFontSize](./manage/ClosedCaptions/#setfontsize)<br/>[ClosedCaptions.setFontColor](./manage/ClosedCaptions/#setfontcolor)<br/>[ClosedCaptions.setFontEdge](./manage/ClosedCaptions/#setfontedge)<br/>[ClosedCaptions.setFontEdgeColor](./manage/ClosedCaptions/#setfontedgecolor)<br/>[ClosedCaptions.setFontOpacity](./manage/ClosedCaptions/#setfontopacity)<br/>[ClosedCaptions.setBackgroundColor](./manage/ClosedCaptions/#setbackgroundcolor)<br/>[ClosedCaptions.setBackgroundOpacity](./manage/ClosedCaptions/#setbackgroundopacity)<br/>[ClosedCaptions.setTextAlign](./manage/ClosedCaptions/#settextalign)<br/>[ClosedCaptions.setTextAlignVertical](./manage/ClosedCaptions/#settextalignvertical)<br/>[ClosedCaptions.setWindowColor](./manage/ClosedCaptions/#setwindowcolor)<br/>[ClosedCaptions.setWindowOpacity](./manage/ClosedCaptions/#setwindowopacity)<br/>[ClosedCaptions.setPreferredLanguages](./manage/ClosedCaptions/#setpreferredlanguages)</details> |
| `xrn:firebolt:capability:accessibility:highcontrastui` | **MUST** | <details><summary>2</summary>[Accessibility.highContrastUI](./core/Accessibility/#highcontrastui)<br/>[Accessibility.onHighContrastUIChanged](./core/Accessibility/#highcontrastuichanged)</details> |  |  |
| `xrn:firebolt:capability:accessibility:voiceguidance` | **MUST** | <details><summary>11</summary>[Accessibility.voiceGuidance](./core/Accessibility/#voiceguidance)<br/>[Accessibility.voiceGuidanceSettings](./core/Accessibility/#voiceguidancesettings)<br/>[Accessibility.onVoiceGuidanceSettingsChanged](./core/Accessibility/#voiceguidancesettingschanged)<br/>[VoiceGuidance.enabled](./manage/VoiceGuidance/#enabled)<br/>[VoiceGuidance.navigationHints](./manage/VoiceGuidance/#navigationhints)<br/>[VoiceGuidance.rate](./manage/VoiceGuidance/#rate)<br/>[VoiceGuidance.speed](./manage/VoiceGuidance/#speed)<br/>[VoiceGuidance.onEnabledChanged](./manage/VoiceGuidance/#enabledchanged)<br/>[VoiceGuidance.onNavigationHintsChanged](./manage/VoiceGuidance/#navigationhintschanged)<br/>[VoiceGuidance.onRateChanged](./manage/VoiceGuidance/#ratechanged)<br/>[VoiceGuidance.onSpeedChanged](./manage/VoiceGuidance/#speedchanged)</details> |  | <details><summary>4</summary>[VoiceGuidance.setEnabled](./manage/VoiceGuidance/#setenabled)<br/>[VoiceGuidance.setNavigationHints](./manage/VoiceGuidance/#setnavigationhints)<br/>[VoiceGuidance.setRate](./manage/VoiceGuidance/#setrate)<br/>[VoiceGuidance.setSpeed](./manage/VoiceGuidance/#setspeed)</details> |
| `xrn:firebolt:capability:account:id` | **COULD** | <details><summary>1</summary>[Account.id](./core/Account/#id)</details> |  | <details><summary>1</summary>[Device.provision](./manage/Device/#provision)</details> |
| `xrn:firebolt:capability:account:uid` | **COULD** | <details><summary>1</summary>[Account.uid](./core/Account/#uid)</details> |  |  |
| `xrn:firebolt:capability:advertising:configuration` | **COULD** | <details><summary>3</summary>[Advertising.config](./core/Advertising/#config)<br/>[Advertising.deviceAttributes](./core/Advertising/#deviceattributes)<br/>[Advertising.appBundleId](./core/Advertising/#appbundleid)</details> |  | <details><summary>3</summary>[Advertising.skipRestriction](./manage/Advertising/#skiprestriction)<br/>[Advertising.onSkipRestrictionChanged](./manage/Advertising/#skiprestrictionchanged)<br/>[Advertising.setSkipRestriction](./manage/Advertising/#setskiprestriction)</details> |
| `xrn:firebolt:capability:advertising:identifier` | **SHOULD** | <details><summary>1</summary>[Advertising.advertisingId](./core/Advertising/#advertisingid)</details> |  | <details><summary>1</summary>[Advertising.resetIdentifier](./manage/Advertising/#resetidentifier)</details> |
| `xrn:firebolt:capability:advertising:policy` | **COULD** | <details><summary>2</summary>[Advertising.policy](./core/Advertising/#policy)<br/>[Advertising.onPolicyChanged](./core/Advertising/#policychanged)</details> |  |  |
| `xrn:firebolt:capability:approve:content` | **SHOULD** | <details><summary>1</summary>[Profile.approveContentRating](./core/Profile/#approvecontentrating)</details> |  |  |
| `xrn:firebolt:capability:approve:purchase` | **COULD** | <details><summary>1</summary>[Profile.approvePurchase](./core/Profile/#approvepurchase)</details> |  |  |
| `xrn:firebolt:capability:capabilities:info` | **MUST** | <details><summary>9</summary>[Capabilities.supported](./core/Capabilities/#supported)<br/>[Capabilities.available](./core/Capabilities/#available)<br/>[Capabilities.permitted](./core/Capabilities/#permitted)<br/>[Capabilities.granted](./core/Capabilities/#granted)<br/>[Capabilities.info](./core/Capabilities/#info)<br/>[Capabilities.onAvailable](./core/Capabilities/#available)<br/>[Capabilities.onUnavailable](./core/Capabilities/#unavailable)<br/>[Capabilities.onGranted](./core/Capabilities/#granted)<br/>[Capabilities.onRevoked](./core/Capabilities/#revoked)</details> |  |  |
| `xrn:firebolt:capability:capabilities:request` | **MUST** | <details><summary>1</summary>[Capabilities.request](./core/Capabilities/#request)</details> |  |  |
| `xrn:firebolt:capability:device:distributor` | **MUST** | <details><summary>1</summary>[Device.distributor](./core/Device/#distributor)</details> |  | <details><summary>1</summary>[Device.provision](./manage/Device/#provision)</details> |
| `xrn:firebolt:capability:device:id` | **COULD** | <details><summary>1</summary>[Device.id](./core/Device/#id)</details> |  | <details><summary>1</summary>[Device.provision](./manage/Device/#provision)</details> |
| `xrn:firebolt:capability:device:info` | **MUST** | <details><summary>13</summary>[Device.platform](./core/Device/#platform)<br/>[Device.type](./core/Device/#type)<br/>[Device.version](./core/Device/#version)<br/>[Device.hdcp](./core/Device/#hdcp)<br/>[Device.hdr](./core/Device/#hdr)<br/>[Device.audio](./core/Device/#audio)<br/>[Device.screenResolution](./core/Device/#screenresolution)<br/>[Device.videoResolution](./core/Device/#videoresolution)<br/>[Device.onHdcpChanged](./core/Device/#hdcpchanged)<br/>[Device.onHdrChanged](./core/Device/#hdrchanged)<br/>[Device.onAudioChanged](./core/Device/#audiochanged)<br/>[Device.onScreenResolutionChanged](./core/Device/#screenresolutionchanged)<br/>[Device.onVideoResolutionChanged](./core/Device/#videoresolutionchanged)</details> |  |  |
| `xrn:firebolt:capability:device:make` | **MUST** | <details><summary>1</summary>[Device.make](./core/Device/#make)</details> |  |  |
| `xrn:firebolt:capability:device:model` | **MUST** | <details><summary>1</summary>[Device.model](./core/Device/#model)</details> |  |  |
| `xrn:firebolt:capability:device:name` | **SHOULD** | <details><summary>3</summary>[Device.name](./core/Device/#name)<br/>[Device.onDeviceNameChanged](./core/Device/#devicenamechanged)<br/>[Device.onNameChanged](./core/Device/#namechanged)</details> |  | <details><summary>1</summary>[Device.setName](./manage/Device/#setname)</details> |
| `xrn:firebolt:capability:device:sku` | **COULD** | <details><summary>1</summary>[Device.sku](./core/Device/#sku)</details> |  |  |
| `xrn:firebolt:capability:device:uid` | **COULD** | <details><summary>1</summary>[Device.uid](./core/Device/#uid)</details> |  |  |
| `xrn:firebolt:capability:discovery:content-access` | **MUST** | <details><summary>3</summary>[Discovery.entitlements](./core/Discovery/#entitlements)<br/>[Discovery.contentAccess](./core/Discovery/#contentaccess)<br/>[Discovery.clearContentAccess](./core/Discovery/#clearcontentaccess)</details> |  |  |
| `xrn:firebolt:capability:discovery:entity-info` | **COULD** |  | <details><summary>2</summary>[Discovery.entityInfo](./core/Discovery/#entityinfo)<br/>[Discovery.onPullEntityInfo](./core/Discovery/#pullentityinfo)</details> |  |
| `xrn:firebolt:capability:discovery:interest` | **MUST** | <details><summary>2</summary>[Content.requestUserInterest](./manage/Content/#requestuserinterest)<br/>[Content.onUserInterest](./manage/Content/#userinterest)</details> | <details><summary>4</summary>[Discovery.userInterest](./core/Discovery/#userinterest)<br/>[Discovery.onRequestUserInterest](./core/Discovery/#requestuserinterest)<br/>[Discovery.userInterestResponse](./core/Discovery/#userinterestresponse)<br/>[Discovery.userInterestError](./core/Discovery/#userinteresterror)</details> |  |
| `xrn:firebolt:capability:discovery:navigate-to` | **MUST** | <details><summary>1</summary>[Discovery.onNavigateTo](./core/Discovery/#navigateto)</details> |  |  |
| `xrn:firebolt:capability:discovery:policy` | **MUST** | <details><summary>2</summary>[Discovery.policy](./core/Discovery/#policy)<br/>[Discovery.onPolicyChanged](./core/Discovery/#policychanged)</details> |  |  |
| `xrn:firebolt:capability:discovery:purchased-content` | **COULD** |  | <details><summary>2</summary>[Discovery.purchasedContent](./core/Discovery/#purchasedcontent)<br/>[Discovery.onPullPurchasedContent](./core/Discovery/#pullpurchasedcontent)</details> |  |
| `xrn:firebolt:capability:discovery:sign-in-status` | **MUST** | <details><summary>2</summary>[Discovery.signIn](./core/Discovery/#signin)<br/>[Discovery.signOut](./core/Discovery/#signout)</details> |  | <details><summary>2</summary>[Discovery.onSignIn](./manage/Discovery/#signin)<br/>[Discovery.onSignOut](./manage/Discovery/#signout)</details> |
| `xrn:firebolt:capability:discovery:watch-next` | **COULD** | <details><summary>1</summary>[Discovery.watchNext](./core/Discovery/#watchnext)</details> |  |  |
| `xrn:firebolt:capability:discovery:watched` | **MUST** | <details><summary>1</summary>[Discovery.watched](./core/Discovery/#watched)</details> |  |  |
| `xrn:firebolt:capability:grants:state` | **MUST** | <details><summary>3</summary>[UserGrants.app](./manage/UserGrants/#app)<br/>[UserGrants.device](./manage/UserGrants/#device)<br/>[UserGrants.capability](./manage/UserGrants/#capability)</details> |  | <details><summary>4</summary>[UserGrants.grant](./manage/UserGrants/#grant)<br/>[UserGrants.deny](./manage/UserGrants/#deny)<br/>[UserGrants.clear](./manage/UserGrants/#clear)<br/>[UserGrants.request](./manage/UserGrants/#request)</details> |
| `xrn:firebolt:capability:input:keyboard` | **SHOULD** | <details><summary>3</summary>[Keyboard.email](./core/Keyboard/#email)<br/>[Keyboard.password](./core/Keyboard/#password)<br/>[Keyboard.standard](./core/Keyboard/#standard)</details> | <details><summary>12</summary>[Keyboard.onRequestStandard](./manage/Keyboard/#requeststandard)<br/>[Keyboard.onRequestPassword](./manage/Keyboard/#requestpassword)<br/>[Keyboard.onRequestEmail](./manage/Keyboard/#requestemail)<br/>[Keyboard.standardFocus](./manage/Keyboard/#standardfocus)<br/>[Keyboard.passwordFocus](./manage/Keyboard/#passwordfocus)<br/>[Keyboard.emailFocus](./manage/Keyboard/#emailfocus)<br/>[Keyboard.standardResponse](./manage/Keyboard/#standardresponse)<br/>[Keyboard.standardError](./manage/Keyboard/#standarderror)<br/>[Keyboard.passwordResponse](./manage/Keyboard/#passwordresponse)<br/>[Keyboard.passwordError](./manage/Keyboard/#passworderror)<br/>[Keyboard.emailResponse](./manage/Keyboard/#emailresponse)<br/>[Keyboard.emailError](./manage/Keyboard/#emailerror)</details> |  |
| `xrn:firebolt:capability:inputs:hdmi` | **SHOULD** | <details><summary>11</summary>[HDMIInput.ports](./manage/HDMIInput/#ports)<br/>[HDMIInput.port](./manage/HDMIInput/#port)<br/>[HDMIInput.onConnectionChanged](./manage/HDMIInput/#connectionchanged)<br/>[HDMIInput.onSignalChanged](./manage/HDMIInput/#signalchanged)<br/>[HDMIInput.lowLatencyMode](./manage/HDMIInput/#lowlatencymode)<br/>[HDMIInput.onAutoLowLatencyModeSignalChanged](./manage/HDMIInput/#autolowlatencymodesignalchanged)<br/>[HDMIInput.autoLowLatencyModeCapable](./manage/HDMIInput/#autolowlatencymodecapable)<br/>[HDMIInput.edidVersion](./manage/HDMIInput/#edidversion)<br/>[HDMIInput.onLowLatencyModeChanged](./manage/HDMIInput/#lowlatencymodechanged)<br/>[HDMIInput.onAutoLowLatencyModeCapableChanged](./manage/HDMIInput/#autolowlatencymodecapablechanged)<br/>[HDMIInput.onEdidVersionChanged](./manage/HDMIInput/#edidversionchanged)</details> |  | <details><summary>5</summary>[HDMIInput.open](./manage/HDMIInput/#open)<br/>[HDMIInput.close](./manage/HDMIInput/#close)<br/>[HDMIInput.setLowLatencyMode](./manage/HDMIInput/#setlowlatencymode)<br/>[HDMIInput.setAutoLowLatencyModeCapable](./manage/HDMIInput/#setautolowlatencymodecapable)<br/>[HDMIInput.setEdidVersion](./manage/HDMIInput/#setedidversion)</details> |
| `xrn:firebolt:capability:lifecycle:initialize` | **MUST** | <details><summary>1</summary>[Internal.initialize](./core/Internal/#initialize)</details> |  |  |
| `xrn:firebolt:capability:lifecycle:launch` | **COULD** | <details><summary>1</summary>[Discovery.launch](./core/Discovery/#launch)</details> |  |  |
| `xrn:firebolt:capability:lifecycle:ready` | **MUST** | <details><summary>1</summary>[Lifecycle.ready](./core/Lifecycle/#ready)</details> |  |  |
| `xrn:firebolt:capability:lifecycle:state` | **MUST** | <details><summary>9</summary>[Lifecycle.close](./core/Lifecycle/#close)<br/>[Lifecycle.finished](./core/Lifecycle/#finished)<br/>[Lifecycle.state](./core/Lifecycle/#state)<br/>[Lifecycle.onInactive](./core/Lifecycle/#inactive)<br/>[Lifecycle.onForeground](./core/Lifecycle/#foreground)<br/>[Lifecycle.onBackground](./core/Lifecycle/#background)<br/>[Lifecycle.onSuspended](./core/Lifecycle/#suspended)<br/>[Lifecycle.onUnloading](./core/Lifecycle/#unloading)<br/>[Parameters.initialization](./core/Parameters/#initialization)</details> |  |  |
| `xrn:firebolt:capability:localization:additional-info` | **COULD** | <details><summary>1</summary>[Localization.additionalInfo](./core/Localization/#additionalinfo)</details> |  | <details><summary>2</summary>[Localization.addAdditionalInfo](./manage/Localization/#addadditionalinfo)<br/>[Localization.removeAdditionalInfo](./manage/Localization/#removeadditionalinfo)</details> |
| `xrn:firebolt:capability:localization:country-code` | **MUST** | <details><summary>2</summary>[Localization.countryCode](./core/Localization/#countrycode)<br/>[Localization.onCountryCodeChanged](./core/Localization/#countrycodechanged)</details> |  | <details><summary>1</summary>[Localization.setCountryCode](./manage/Localization/#setcountrycode)</details> |
| `xrn:firebolt:capability:localization:language` | **MUST** | <details><summary>4</summary>[Localization.language](./core/Localization/#language)<br/>[Localization.preferredAudioLanguages](./core/Localization/#preferredaudiolanguages)<br/>[Localization.onLanguageChanged](./core/Localization/#languagechanged)<br/>[Localization.onPreferredAudioLanguagesChanged](./core/Localization/#preferredaudiolanguageschanged)</details> |  | <details><summary>2</summary>[Localization.setLanguage](./manage/Localization/#setlanguage)<br/>[Localization.setPreferredAudioLanguages](./manage/Localization/#setpreferredaudiolanguages)</details> |
| `xrn:firebolt:capability:localization:locale` | **MUST** | <details><summary>2</summary>[Localization.locale](./core/Localization/#locale)<br/>[Localization.onLocaleChanged](./core/Localization/#localechanged)</details> |  | <details><summary>1</summary>[Localization.setLocale](./manage/Localization/#setlocale)</details> |
| `xrn:firebolt:capability:localization:locality` | **COULD** | <details><summary>2</summary>[Localization.locality](./core/Localization/#locality)<br/>[Localization.onLocalityChanged](./core/Localization/#localitychanged)</details> |  | <details><summary>1</summary>[Localization.setLocality](./manage/Localization/#setlocality)</details> |
| `xrn:firebolt:capability:localization:location` | **COULD** | <details><summary>1</summary>[Localization.latlon](./core/Localization/#latlon)</details> |  |  |
| `xrn:firebolt:capability:localization:postal-code` | **COULD** | <details><summary>2</summary>[Localization.postalCode](./core/Localization/#postalcode)<br/>[Localization.onPostalCodeChanged](./core/Localization/#postalcodechanged)</details> |  | <details><summary>1</summary>[Localization.setPostalCode](./manage/Localization/#setpostalcode)</details> |
| `xrn:firebolt:capability:localization:time-zone` | **MUST** | <details><summary>2</summary>[Localization.timeZone](./manage/Localization/#timezone)<br/>[Localization.onTimeZoneChanged](./manage/Localization/#timezonechanged)</details> |  | <details><summary>1</summary>[Localization.setTimeZone](./manage/Localization/#settimezone)</details> |
| `xrn:firebolt:capability:metrics:distributor` | **COULD** | <details><summary>1</summary>[Metrics.event](./manage/Metrics/#event)</details> |  |  |
| `xrn:firebolt:capability:metrics:general` | **MUST** | <details><summary>9</summary>[Metrics.ready](./core/Metrics/#ready)<br/>[Metrics.signIn](./core/Metrics/#signin)<br/>[Metrics.signOut](./core/Metrics/#signout)<br/>[Metrics.startContent](./core/Metrics/#startcontent)<br/>[Metrics.stopContent](./core/Metrics/#stopcontent)<br/>[Metrics.page](./core/Metrics/#page)<br/>[Metrics.action](./core/Metrics/#action)<br/>[Metrics.error](./core/Metrics/#error)<br/>[Metrics.appInfo](./core/Metrics/#appinfo)</details> |  |  |
| `xrn:firebolt:capability:metrics:media` | **MUST** | <details><summary>11</summary>[Metrics.mediaLoadStart](./core/Metrics/#medialoadstart)<br/>[Metrics.mediaPlay](./core/Metrics/#mediaplay)<br/>[Metrics.mediaPlaying](./core/Metrics/#mediaplaying)<br/>[Metrics.mediaPause](./core/Metrics/#mediapause)<br/>[Metrics.mediaWaiting](./core/Metrics/#mediawaiting)<br/>[Metrics.mediaProgress](./core/Metrics/#mediaprogress)<br/>[Metrics.mediaSeeking](./core/Metrics/#mediaseeking)<br/>[Metrics.mediaSeeked](./core/Metrics/#mediaseeked)<br/>[Metrics.mediaRateChange](./core/Metrics/#mediaratechange)<br/>[Metrics.mediaRenditionChange](./core/Metrics/#mediarenditionchange)<br/>[Metrics.mediaEnded](./core/Metrics/#mediaended)</details> |  |  |
| `xrn:firebolt:capability:network:status` | **MUST** | <details><summary>2</summary>[Device.network](./core/Device/#network)<br/>[Device.onNetworkChanged](./core/Device/#networkchanged)</details> |  |  |
| `xrn:firebolt:capability:privacy:settings` | **COULD** | <details><summary>25</summary>[Privacy.allowResumePoints](./manage/Privacy/#allowresumepoints)<br/>[Privacy.allowUnentitledResumePoints](./manage/Privacy/#allowunentitledresumepoints)<br/>[Privacy.allowWatchHistory](./manage/Privacy/#allowwatchhistory)<br/>[Privacy.allowProductAnalytics](./manage/Privacy/#allowproductanalytics)<br/>[Privacy.allowPersonalization](./manage/Privacy/#allowpersonalization)<br/>[Privacy.allowUnentitledPersonalization](./manage/Privacy/#allowunentitledpersonalization)<br/>[Privacy.allowRemoteDiagnostics](./manage/Privacy/#allowremotediagnostics)<br/>[Privacy.allowPrimaryContentAdTargeting](./manage/Privacy/#allowprimarycontentadtargeting)<br/>[Privacy.allowPrimaryBrowseAdTargeting](./manage/Privacy/#allowprimarybrowseadtargeting)<br/>[Privacy.allowAppContentAdTargeting](./manage/Privacy/#allowappcontentadtargeting)<br/>[Privacy.allowACRCollection](./manage/Privacy/#allowacrcollection)<br/>[Privacy.allowCameraAnalytics](./manage/Privacy/#allowcameraanalytics)<br/>[Privacy.settings](./manage/Privacy/#settings)<br/>[Privacy.onAllowResumePointsChanged](./manage/Privacy/#allowresumepointschanged)<br/>[Privacy.onAllowUnentitledResumePointsChanged](./manage/Privacy/#allowunentitledresumepointschanged)<br/>[Privacy.onAllowWatchHistoryChanged](./manage/Privacy/#allowwatchhistorychanged)<br/>[Privacy.onAllowProductAnalyticsChanged](./manage/Privacy/#allowproductanalyticschanged)<br/>[Privacy.onAllowPersonalizationChanged](./manage/Privacy/#allowpersonalizationchanged)<br/>[Privacy.onAllowUnentitledPersonalizationChanged](./manage/Privacy/#allowunentitledpersonalizationchanged)<br/>[Privacy.onAllowRemoteDiagnosticsChanged](./manage/Privacy/#allowremotediagnosticschanged)<br/>[Privacy.onAllowPrimaryContentAdTargetingChanged](./manage/Privacy/#allowprimarycontentadtargetingchanged)<br/>[Privacy.onAllowPrimaryBrowseAdTargetingChanged](./manage/Privacy/#allowprimarybrowseadtargetingchanged)<br/>[Privacy.onAllowAppContentAdTargetingChanged](./manage/Privacy/#allowappcontentadtargetingchanged)<br/>[Privacy.onAllowACRCollectionChanged](./manage/Privacy/#allowacrcollectionchanged)<br/>[Privacy.onAllowCameraAnalyticsChanged](./manage/Privacy/#allowcameraanalyticschanged)</details> |  | <details><summary>12</summary>[Privacy.setAllowResumePoints](./manage/Privacy/#setallowresumepoints)<br/>[Privacy.setAllowUnentitledResumePoints](./manage/Privacy/#setallowunentitledresumepoints)<br/>[Privacy.setAllowWatchHistory](./manage/Privacy/#setallowwatchhistory)<br/>[Privacy.setAllowProductAnalytics](./manage/Privacy/#setallowproductanalytics)<br/>[Privacy.setAllowPersonalization](./manage/Privacy/#setallowpersonalization)<br/>[Privacy.setAllowUnentitledPersonalization](./manage/Privacy/#setallowunentitledpersonalization)<br/>[Privacy.setAllowRemoteDiagnostics](./manage/Privacy/#setallowremotediagnostics)<br/>[Privacy.setAllowPrimaryContentAdTargeting](./manage/Privacy/#setallowprimarycontentadtargeting)<br/>[Privacy.setAllowPrimaryBrowseAdTargeting](./manage/Privacy/#setallowprimarybrowseadtargeting)<br/>[Privacy.setAllowAppContentAdTargeting](./manage/Privacy/#setallowappcontentadtargeting)<br/>[Privacy.setAllowACRCollection](./manage/Privacy/#setallowacrcollection)<br/>[Privacy.setAllowCameraAnalytics](./manage/Privacy/#setallowcameraanalytics)</details> |
| `xrn:firebolt:capability:profile:flags` | **COULD** | <details><summary>1</summary>[Profile.flags](./core/Profile/#flags)</details> |  |  |
| `xrn:firebolt:capability:protocol:dial` | **COULD** | <details><summary>5</summary>[SecondScreen.device](./core/SecondScreen/#device)<br/>[SecondScreen.friendlyName](./core/SecondScreen/#friendlyname)<br/>[SecondScreen.onLaunchRequest](./core/SecondScreen/#launchrequest)<br/>[SecondScreen.onCloseRequest](./core/SecondScreen/#closerequest)<br/>[SecondScreen.onFriendlyNameChanged](./core/SecondScreen/#friendlynamechanged)</details> |  |  |
| `xrn:firebolt:capability:protocol:wifi` | **COULD** | <details><summary>4</summary>[Wifi.scan](./manage/Wifi/#scan)<br/>[Wifi.connect](./manage/Wifi/#connect)<br/>[Wifi.disconnect](./manage/Wifi/#disconnect)<br/>[Wifi.wps](./manage/Wifi/#wps)</details> |  |  |
| `xrn:firebolt:capability:rpc:discover` | **SHOULD** | <details><summary>1</summary>[rpc.discover](./manage/rpc/#discover)</details> |  |  |
| `xrn:firebolt:capability:secondscreen:protocol` | **COULD** | <details><summary>1</summary>[SecondScreen.protocols](./core/SecondScreen/#protocols)</details> |  |  |
| `xrn:firebolt:capability:storage:secure` | **SHOULD** | <details><summary>4</summary>[SecureStorage.get](./core/SecureStorage/#get)<br/>[SecureStorage.set](./core/SecureStorage/#set)<br/>[SecureStorage.remove](./core/SecureStorage/#remove)<br/>[SecureStorage.clear](./core/SecureStorage/#clear)</details> |  | <details><summary>3</summary>[SecureStorage.setForApp](./manage/SecureStorage/#setforapp)<br/>[SecureStorage.removeForApp](./manage/SecureStorage/#removeforapp)<br/>[SecureStorage.clearForApp](./manage/SecureStorage/#clearforapp)</details> |
| `xrn:firebolt:capability:token:account` | **COULD** |  |  | <details><summary>1</summary>[Account.session](./manage/Account/#session)</details> |
| `xrn:firebolt:capability:token:device` | **COULD** | <details><summary>1</summary>[Authentication.device](./core/Authentication/#device)</details> |  |  |
| `xrn:firebolt:capability:token:platform` | **COULD** | <details><summary>1</summary>[Authentication.token](./core/Authentication/#token)</details> |  |  |
| `xrn:firebolt:capability:token:root` | **COULD** | <details><summary>1</summary>[Authentication.root](./core/Authentication/#root)</details> |  |  |
| `xrn:firebolt:capability:token:session` | **COULD** | <details><summary>1</summary>[Authentication.session](./core/Authentication/#session)</details> |  |  |
| `xrn:firebolt:capability:usergrant:acknowledgechallenge` | **MUST** |  | <details><summary>4</summary>[AcknowledgeChallenge.onRequestChallenge](./manage/AcknowledgeChallenge/#requestchallenge)<br/>[AcknowledgeChallenge.challengeFocus](./manage/AcknowledgeChallenge/#challengefocus)<br/>[AcknowledgeChallenge.challengeResponse](./manage/AcknowledgeChallenge/#challengeresponse)<br/>[AcknowledgeChallenge.challengeError](./manage/AcknowledgeChallenge/#challengeerror)</details> |  |
| `xrn:firebolt:capability:usergrant:pinchallenge` | **SHOULD** |  | <details><summary>4</summary>[PinChallenge.onRequestChallenge](./manage/PinChallenge/#requestchallenge)<br/>[PinChallenge.challengeFocus](./manage/PinChallenge/#challengefocus)<br/>[PinChallenge.challengeResponse](./manage/PinChallenge/#challengeresponse)<br/>[PinChallenge.challengeError](./manage/PinChallenge/#challengeerror)</details> |  |

## Methods
Capability prefix `xrn:firebolt:capability` let off for readability.
| Method | Level | Uses | Provides | Manages |
|-|-|-|-|-|
| [rpc.discover](./manage/rpc/#discover) | **SHOULD** | `rpc:discover` |  |  |
| [Internal.initialize](./core/Internal/#initialize) | **MUST** | `lifecycle:initialize` |  |  |
| [Accessibility.closedCaptions](./core/Accessibility/#closedcaptions) | **MUST** | `accessibility:closedcaptions` |  |  |
| [Accessibility.closedCaptionsSettings](./core/Accessibility/#closedcaptionssettings) | **MUST** | `accessibility:closedcaptions` |  |  |
| [Accessibility.highContrastUI](./core/Accessibility/#highcontrastui) | **MUST** | `accessibility:highcontrastui` |  |  |
| [Accessibility.voiceGuidance](./core/Accessibility/#voiceguidance) | **MUST** | `accessibility:voiceguidance` |  |  |
| [Accessibility.voiceGuidanceSettings](./core/Accessibility/#voiceguidancesettings) | **MUST** | `accessibility:voiceguidance` |  |  |
| [Accessibility.audioDescriptionSettings](./core/Accessibility/#audiodescriptionsettings) | **MUST** | `accessibility:audiodescriptions` |  |  |
| [Accessibility.onClosedCaptionsSettingsChanged](./core/Accessibility/#closedcaptionssettingschanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [Accessibility.onHighContrastUIChanged](./core/Accessibility/#highcontrastuichanged) | **MUST** | `accessibility:highcontrastui` |  |  |
| [Accessibility.onVoiceGuidanceSettingsChanged](./core/Accessibility/#voiceguidancesettingschanged) | **MUST** | `accessibility:voiceguidance` |  |  |
| [Accessibility.onAudioDescriptionSettingsChanged](./core/Accessibility/#audiodescriptionsettingschanged) | **MUST** | `accessibility:audiodescriptions` |  |  |
| [Account.id](./core/Account/#id) | **COULD** | `account:id` |  |  |
| [Account.uid](./core/Account/#uid) | **COULD** | `account:uid` |  |  |
| [Account.session](./manage/Account/#session) | **COULD** |  |  | `token:account` |
| [AcknowledgeChallenge.onRequestChallenge](./manage/AcknowledgeChallenge/#requestchallenge) | **MUST** |  | `usergrant:acknowledgechallenge` |  |
| [AcknowledgeChallenge.challengeFocus](./manage/AcknowledgeChallenge/#challengefocus) | **MUST** |  | `usergrant:acknowledgechallenge` |  |
| [AcknowledgeChallenge.challengeResponse](./manage/AcknowledgeChallenge/#challengeresponse) | **MUST** |  | `usergrant:acknowledgechallenge` |  |
| [AcknowledgeChallenge.challengeError](./manage/AcknowledgeChallenge/#challengeerror) | **MUST** |  | `usergrant:acknowledgechallenge` |  |
| [Advertising.config](./core/Advertising/#config) | **COULD** | `advertising:configuration` |  |  |
| [Advertising.policy](./core/Advertising/#policy) | **COULD** | `advertising:policy` |  |  |
| [Advertising.skipRestriction](./manage/Advertising/#skiprestriction) | **COULD** |  |  | `advertising:configuration` |
| [Advertising.advertisingId](./core/Advertising/#advertisingid) | **SHOULD** | `advertising:identifier` |  |  |
| [Advertising.deviceAttributes](./core/Advertising/#deviceattributes) | **COULD** | `advertising:configuration` |  |  |
| [Advertising.appBundleId](./core/Advertising/#appbundleid) | **COULD** | `advertising:configuration` |  |  |
| [Advertising.resetIdentifier](./manage/Advertising/#resetidentifier) | **SHOULD** |  |  | `advertising:identifier` |
| [Advertising.onSkipRestrictionChanged](./manage/Advertising/#skiprestrictionchanged) | **COULD** |  |  | `advertising:configuration` |
| [Advertising.onPolicyChanged](./core/Advertising/#policychanged) | **COULD** | `advertising:policy` |  |  |
| [Advertising.setSkipRestriction](./manage/Advertising/#setskiprestriction) | **COULD** |  |  | `advertising:configuration` |
| [AudioDescriptions.enabled](./manage/AudioDescriptions/#enabled) | **MUST** | `accessibility:audiodescriptions` |  |  |
| [AudioDescriptions.onEnabledChanged](./manage/AudioDescriptions/#enabledchanged) | **MUST** | `accessibility:audiodescriptions` |  |  |
| [AudioDescriptions.setEnabled](./manage/AudioDescriptions/#setenabled) | **MUST** |  |  | `accessibility:audiodescriptions` |
| [Authentication.token](./core/Authentication/#token) | **COULD** | `token:platform` |  |  |
| [Authentication.device](./core/Authentication/#device) | **COULD** | `token:device` |  |  |
| [Authentication.session](./core/Authentication/#session) | **COULD** | `token:session` |  |  |
| [Authentication.root](./core/Authentication/#root) | **COULD** | `token:root` |  |  |
| [Capabilities.supported](./core/Capabilities/#supported) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.available](./core/Capabilities/#available) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.permitted](./core/Capabilities/#permitted) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.granted](./core/Capabilities/#granted) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.info](./core/Capabilities/#info) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.request](./core/Capabilities/#request) | **MUST** | `capabilities:request` |  |  |
| [Capabilities.onAvailable](./core/Capabilities/#available) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.onUnavailable](./core/Capabilities/#unavailable) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.onGranted](./core/Capabilities/#granted) | **MUST** | `capabilities:info` |  |  |
| [Capabilities.onRevoked](./core/Capabilities/#revoked) | **MUST** | `capabilities:info` |  |  |
| [ClosedCaptions.enabled](./manage/ClosedCaptions/#enabled) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontFamily](./manage/ClosedCaptions/#fontfamily) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontSize](./manage/ClosedCaptions/#fontsize) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontColor](./manage/ClosedCaptions/#fontcolor) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontEdge](./manage/ClosedCaptions/#fontedge) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontEdgeColor](./manage/ClosedCaptions/#fontedgecolor) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.fontOpacity](./manage/ClosedCaptions/#fontopacity) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.backgroundColor](./manage/ClosedCaptions/#backgroundcolor) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.backgroundOpacity](./manage/ClosedCaptions/#backgroundopacity) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.textAlign](./manage/ClosedCaptions/#textalign) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.textAlignVertical](./manage/ClosedCaptions/#textalignvertical) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.windowColor](./manage/ClosedCaptions/#windowcolor) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.windowOpacity](./manage/ClosedCaptions/#windowopacity) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.preferredLanguages](./manage/ClosedCaptions/#preferredlanguages) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onEnabledChanged](./manage/ClosedCaptions/#enabledchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontFamilyChanged](./manage/ClosedCaptions/#fontfamilychanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontSizeChanged](./manage/ClosedCaptions/#fontsizechanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontColorChanged](./manage/ClosedCaptions/#fontcolorchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontEdgeChanged](./manage/ClosedCaptions/#fontedgechanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontEdgeColorChanged](./manage/ClosedCaptions/#fontedgecolorchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onFontOpacityChanged](./manage/ClosedCaptions/#fontopacitychanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onBackgroundColorChanged](./manage/ClosedCaptions/#backgroundcolorchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onBackgroundOpacityChanged](./manage/ClosedCaptions/#backgroundopacitychanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onTextAlignChanged](./manage/ClosedCaptions/#textalignchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onTextAlignVerticalChanged](./manage/ClosedCaptions/#textalignverticalchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onWindowColorChanged](./manage/ClosedCaptions/#windowcolorchanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onWindowOpacityChanged](./manage/ClosedCaptions/#windowopacitychanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.onPreferredLanguagesChanged](./manage/ClosedCaptions/#preferredlanguageschanged) | **MUST** | `accessibility:closedcaptions` |  |  |
| [ClosedCaptions.setEnabled](./manage/ClosedCaptions/#setenabled) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontFamily](./manage/ClosedCaptions/#setfontfamily) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontSize](./manage/ClosedCaptions/#setfontsize) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontColor](./manage/ClosedCaptions/#setfontcolor) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontEdge](./manage/ClosedCaptions/#setfontedge) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontEdgeColor](./manage/ClosedCaptions/#setfontedgecolor) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setFontOpacity](./manage/ClosedCaptions/#setfontopacity) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setBackgroundColor](./manage/ClosedCaptions/#setbackgroundcolor) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setBackgroundOpacity](./manage/ClosedCaptions/#setbackgroundopacity) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setTextAlign](./manage/ClosedCaptions/#settextalign) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setTextAlignVertical](./manage/ClosedCaptions/#settextalignvertical) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setWindowColor](./manage/ClosedCaptions/#setwindowcolor) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setWindowOpacity](./manage/ClosedCaptions/#setwindowopacity) | **MUST** |  |  | `accessibility:closedcaptions` |
| [ClosedCaptions.setPreferredLanguages](./manage/ClosedCaptions/#setpreferredlanguages) | **MUST** |  |  | `accessibility:closedcaptions` |
| [Content.requestUserInterest](./manage/Content/#requestuserinterest) | **MUST** | `discovery:interest` |  |  |
| [Content.onUserInterest](./manage/Content/#userinterest) | **MUST** | `discovery:interest` |  |  |
| [Device.id](./core/Device/#id) | **COULD** | `device:id` |  |  |
| [Device.distributor](./core/Device/#distributor) | **MUST** | `device:distributor` |  |  |
| [Device.platform](./core/Device/#platform) | **MUST** | `device:info` |  |  |
| [Device.uid](./core/Device/#uid) | **COULD** | `device:uid` |  |  |
| [Device.type](./core/Device/#type) | **MUST** | `device:info` |  |  |
| [Device.model](./core/Device/#model) | **MUST** | `device:model` |  |  |
| [Device.sku](./core/Device/#sku) | **COULD** | `device:sku` |  |  |
| [Device.make](./core/Device/#make) | **MUST** | `device:make` |  |  |
| [Device.version](./core/Device/#version) | **MUST** | `device:info` |  |  |
| [Device.hdcp](./core/Device/#hdcp) | **MUST** | `device:info` |  |  |
| [Device.hdr](./core/Device/#hdr) | **MUST** | `device:info` |  |  |
| [Device.audio](./core/Device/#audio) | **MUST** | `device:info` |  |  |
| [Device.screenResolution](./core/Device/#screenresolution) | **MUST** | `device:info` |  |  |
| [Device.videoResolution](./core/Device/#videoresolution) | **MUST** | `device:info` |  |  |
| [Device.name](./core/Device/#name) | **SHOULD** | `device:name` |  |  |
| [Device.onDeviceNameChanged](./core/Device/#devicenamechanged) | **SHOULD** | `device:name` |  |  |
| [Device.network](./core/Device/#network) | **MUST** | `network:status` |  |  |
| [Device.provision](./manage/Device/#provision) | **MUST** |  |  | `account:id`, `device:id`, `device:distributor` |
| [Device.onNameChanged](./core/Device/#namechanged) | **SHOULD** | `device:name` |  |  |
| [Device.onHdcpChanged](./core/Device/#hdcpchanged) | **MUST** | `device:info` |  |  |
| [Device.onHdrChanged](./core/Device/#hdrchanged) | **MUST** | `device:info` |  |  |
| [Device.onAudioChanged](./core/Device/#audiochanged) | **MUST** | `device:info` |  |  |
| [Device.onScreenResolutionChanged](./core/Device/#screenresolutionchanged) | **MUST** | `device:info` |  |  |
| [Device.onVideoResolutionChanged](./core/Device/#videoresolutionchanged) | **MUST** | `device:info` |  |  |
| [Device.onNetworkChanged](./core/Device/#networkchanged) | **MUST** | `network:status` |  |  |
| [Device.setName](./manage/Device/#setname) | **SHOULD** |  |  | `device:name` |
| [Discovery.policy](./core/Discovery/#policy) | **MUST** | `discovery:policy` |  |  |
| [Discovery.entityInfo](./core/Discovery/#entityinfo) | **COULD** |  | `discovery:entity-info` |  |
| [Discovery.purchasedContent](./core/Discovery/#purchasedcontent) | **COULD** |  | `discovery:purchased-content` |  |
| [Discovery.watched](./core/Discovery/#watched) | **MUST** | `discovery:watched` |  |  |
| [Discovery.watchNext](./core/Discovery/#watchnext) | **COULD** | `discovery:watch-next` |  |  |
| [Discovery.entitlements](./core/Discovery/#entitlements) | **MUST** | `discovery:content-access` |  |  |
| [Discovery.contentAccess](./core/Discovery/#contentaccess) | **MUST** | `discovery:content-access` |  |  |
| [Discovery.clearContentAccess](./core/Discovery/#clearcontentaccess) | **MUST** | `discovery:content-access` |  |  |
| [Discovery.launch](./core/Discovery/#launch) | **COULD** | `lifecycle:launch` |  |  |
| [Discovery.onNavigateTo](./core/Discovery/#navigateto) | **MUST** | `discovery:navigate-to` |  |  |
| [Discovery.signIn](./core/Discovery/#signin) | **MUST** | `discovery:sign-in-status` |  |  |
| [Discovery.signOut](./core/Discovery/#signout) | **MUST** | `discovery:sign-in-status` |  |  |
| [Discovery.onSignIn](./manage/Discovery/#signin) | **MUST** |  |  | `discovery:sign-in-status` |
| [Discovery.onSignOut](./manage/Discovery/#signout) | **MUST** |  |  | `discovery:sign-in-status` |
| [Discovery.userInterest](./core/Discovery/#userinterest) | **MUST** |  | `discovery:interest` |  |
| [Discovery.onRequestUserInterest](./core/Discovery/#requestuserinterest) | **MUST** |  | `discovery:interest` |  |
| [Discovery.onPolicyChanged](./core/Discovery/#policychanged) | **MUST** | `discovery:policy` |  |  |
| [Discovery.onPullEntityInfo](./core/Discovery/#pullentityinfo) | **COULD** |  | `discovery:entity-info` |  |
| [Discovery.onPullPurchasedContent](./core/Discovery/#pullpurchasedcontent) | **COULD** |  | `discovery:purchased-content` |  |
| [Discovery.userInterestResponse](./core/Discovery/#userinterestresponse) | **MUST** |  | `discovery:interest` |  |
| [Discovery.userInterestError](./core/Discovery/#userinteresterror) | **MUST** |  | `discovery:interest` |  |
| [HDMIInput.ports](./manage/HDMIInput/#ports) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.port](./manage/HDMIInput/#port) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.open](./manage/HDMIInput/#open) | **SHOULD** |  |  | `inputs:hdmi` |
| [HDMIInput.close](./manage/HDMIInput/#close) | **SHOULD** |  |  | `inputs:hdmi` |
| [HDMIInput.onConnectionChanged](./manage/HDMIInput/#connectionchanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.onSignalChanged](./manage/HDMIInput/#signalchanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.lowLatencyMode](./manage/HDMIInput/#lowlatencymode) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.onAutoLowLatencyModeSignalChanged](./manage/HDMIInput/#autolowlatencymodesignalchanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.autoLowLatencyModeCapable](./manage/HDMIInput/#autolowlatencymodecapable) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.edidVersion](./manage/HDMIInput/#edidversion) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.onLowLatencyModeChanged](./manage/HDMIInput/#lowlatencymodechanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.onAutoLowLatencyModeCapableChanged](./manage/HDMIInput/#autolowlatencymodecapablechanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.onEdidVersionChanged](./manage/HDMIInput/#edidversionchanged) | **SHOULD** | `inputs:hdmi` |  |  |
| [HDMIInput.setLowLatencyMode](./manage/HDMIInput/#setlowlatencymode) | **SHOULD** |  |  | `inputs:hdmi` |
| [HDMIInput.setAutoLowLatencyModeCapable](./manage/HDMIInput/#setautolowlatencymodecapable) | **SHOULD** |  |  | `inputs:hdmi` |
| [HDMIInput.setEdidVersion](./manage/HDMIInput/#setedidversion) | **SHOULD** |  |  | `inputs:hdmi` |
| [Keyboard.email](./core/Keyboard/#email) | **SHOULD** | `input:keyboard` |  |  |
| [Keyboard.password](./core/Keyboard/#password) | **SHOULD** | `input:keyboard` |  |  |
| [Keyboard.standard](./core/Keyboard/#standard) | **SHOULD** | `input:keyboard` |  |  |
| [Keyboard.onRequestStandard](./manage/Keyboard/#requeststandard) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.onRequestPassword](./manage/Keyboard/#requestpassword) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.onRequestEmail](./manage/Keyboard/#requestemail) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.standardFocus](./manage/Keyboard/#standardfocus) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.passwordFocus](./manage/Keyboard/#passwordfocus) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.emailFocus](./manage/Keyboard/#emailfocus) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.standardResponse](./manage/Keyboard/#standardresponse) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.standardError](./manage/Keyboard/#standarderror) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.passwordResponse](./manage/Keyboard/#passwordresponse) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.passwordError](./manage/Keyboard/#passworderror) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.emailResponse](./manage/Keyboard/#emailresponse) | **SHOULD** |  | `input:keyboard` |  |
| [Keyboard.emailError](./manage/Keyboard/#emailerror) | **SHOULD** |  | `input:keyboard` |  |
| [Lifecycle.ready](./core/Lifecycle/#ready) | **MUST** | `lifecycle:ready` |  |  |
| [Lifecycle.close](./core/Lifecycle/#close) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.finished](./core/Lifecycle/#finished) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.state](./core/Lifecycle/#state) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.onInactive](./core/Lifecycle/#inactive) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.onForeground](./core/Lifecycle/#foreground) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.onBackground](./core/Lifecycle/#background) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.onSuspended](./core/Lifecycle/#suspended) | **MUST** | `lifecycle:state` |  |  |
| [Lifecycle.onUnloading](./core/Lifecycle/#unloading) | **MUST** | `lifecycle:state` |  |  |
| [Localization.locality](./core/Localization/#locality) | **COULD** | `localization:locality` |  |  |
| [Localization.postalCode](./core/Localization/#postalcode) | **COULD** | `localization:postal-code` |  |  |
| [Localization.countryCode](./core/Localization/#countrycode) | **MUST** | `localization:country-code` |  |  |
| [Localization.language](./core/Localization/#language) | **MUST** | `localization:language` |  |  |
| [Localization.preferredAudioLanguages](./core/Localization/#preferredaudiolanguages) | **MUST** | `localization:language` |  |  |
| [Localization.locale](./core/Localization/#locale) | **MUST** | `localization:locale` |  |  |
| [Localization.latlon](./core/Localization/#latlon) | **COULD** | `localization:location` |  |  |
| [Localization.additionalInfo](./core/Localization/#additionalinfo) | **COULD** | `localization:additional-info` |  |  |
| [Localization.addAdditionalInfo](./manage/Localization/#addadditionalinfo) | **COULD** |  |  | `localization:additional-info` |
| [Localization.removeAdditionalInfo](./manage/Localization/#removeadditionalinfo) | **COULD** |  |  | `localization:additional-info` |
| [Localization.timeZone](./manage/Localization/#timezone) | **MUST** | `localization:time-zone` |  |  |
| [Localization.onLocalityChanged](./core/Localization/#localitychanged) | **COULD** | `localization:locality` |  |  |
| [Localization.onPostalCodeChanged](./core/Localization/#postalcodechanged) | **COULD** | `localization:postal-code` |  |  |
| [Localization.onCountryCodeChanged](./core/Localization/#countrycodechanged) | **MUST** | `localization:country-code` |  |  |
| [Localization.onLanguageChanged](./core/Localization/#languagechanged) | **MUST** | `localization:language` |  |  |
| [Localization.onPreferredAudioLanguagesChanged](./core/Localization/#preferredaudiolanguageschanged) | **MUST** | `localization:language` |  |  |
| [Localization.onLocaleChanged](./core/Localization/#localechanged) | **MUST** | `localization:locale` |  |  |
| [Localization.onTimeZoneChanged](./manage/Localization/#timezonechanged) | **MUST** | `localization:time-zone` |  |  |
| [Localization.setLocality](./manage/Localization/#setlocality) | **COULD** |  |  | `localization:locality` |
| [Localization.setPostalCode](./manage/Localization/#setpostalcode) | **COULD** |  |  | `localization:postal-code` |
| [Localization.setCountryCode](./manage/Localization/#setcountrycode) | **MUST** |  |  | `localization:country-code` |
| [Localization.setLanguage](./manage/Localization/#setlanguage) | **MUST** |  |  | `localization:language` |
| [Localization.setPreferredAudioLanguages](./manage/Localization/#setpreferredaudiolanguages) | **MUST** |  |  | `localization:language` |
| [Localization.setLocale](./manage/Localization/#setlocale) | **MUST** |  |  | `localization:locale` |
| [Localization.setTimeZone](./manage/Localization/#settimezone) | **MUST** |  |  | `localization:time-zone` |
| [Metrics.ready](./core/Metrics/#ready) | **MUST** | `metrics:general` |  |  |
| [Metrics.signIn](./core/Metrics/#signin) | **MUST** | `metrics:general` |  |  |
| [Metrics.signOut](./core/Metrics/#signout) | **MUST** | `metrics:general` |  |  |
| [Metrics.startContent](./core/Metrics/#startcontent) | **MUST** | `metrics:general` |  |  |
| [Metrics.stopContent](./core/Metrics/#stopcontent) | **MUST** | `metrics:general` |  |  |
| [Metrics.page](./core/Metrics/#page) | **MUST** | `metrics:general` |  |  |
| [Metrics.action](./core/Metrics/#action) | **MUST** | `metrics:general` |  |  |
| [Metrics.error](./core/Metrics/#error) | **MUST** | `metrics:general` |  |  |
| [Metrics.mediaLoadStart](./core/Metrics/#medialoadstart) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaPlay](./core/Metrics/#mediaplay) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaPlaying](./core/Metrics/#mediaplaying) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaPause](./core/Metrics/#mediapause) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaWaiting](./core/Metrics/#mediawaiting) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaProgress](./core/Metrics/#mediaprogress) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaSeeking](./core/Metrics/#mediaseeking) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaSeeked](./core/Metrics/#mediaseeked) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaRateChange](./core/Metrics/#mediaratechange) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaRenditionChange](./core/Metrics/#mediarenditionchange) | **MUST** | `metrics:media` |  |  |
| [Metrics.mediaEnded](./core/Metrics/#mediaended) | **MUST** | `metrics:media` |  |  |
| [Metrics.event](./manage/Metrics/#event) | **COULD** | `metrics:distributor` |  |  |
| [Metrics.appInfo](./core/Metrics/#appinfo) | **MUST** | `metrics:general` |  |  |
| [Parameters.initialization](./core/Parameters/#initialization) | **MUST** | `lifecycle:state` |  |  |
| [PinChallenge.onRequestChallenge](./manage/PinChallenge/#requestchallenge) | **SHOULD** |  | `usergrant:pinchallenge` |  |
| [PinChallenge.challengeFocus](./manage/PinChallenge/#challengefocus) | **SHOULD** |  | `usergrant:pinchallenge` |  |
| [PinChallenge.challengeResponse](./manage/PinChallenge/#challengeresponse) | **SHOULD** |  | `usergrant:pinchallenge` |  |
| [PinChallenge.challengeError](./manage/PinChallenge/#challengeerror) | **SHOULD** |  | `usergrant:pinchallenge` |  |
| [Privacy.allowResumePoints](./manage/Privacy/#allowresumepoints) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowUnentitledResumePoints](./manage/Privacy/#allowunentitledresumepoints) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowWatchHistory](./manage/Privacy/#allowwatchhistory) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowProductAnalytics](./manage/Privacy/#allowproductanalytics) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowPersonalization](./manage/Privacy/#allowpersonalization) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowUnentitledPersonalization](./manage/Privacy/#allowunentitledpersonalization) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowRemoteDiagnostics](./manage/Privacy/#allowremotediagnostics) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowPrimaryContentAdTargeting](./manage/Privacy/#allowprimarycontentadtargeting) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowPrimaryBrowseAdTargeting](./manage/Privacy/#allowprimarybrowseadtargeting) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowAppContentAdTargeting](./manage/Privacy/#allowappcontentadtargeting) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowACRCollection](./manage/Privacy/#allowacrcollection) | **COULD** | `privacy:settings` |  |  |
| [Privacy.allowCameraAnalytics](./manage/Privacy/#allowcameraanalytics) | **COULD** | `privacy:settings` |  |  |
| [Privacy.settings](./manage/Privacy/#settings) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowResumePointsChanged](./manage/Privacy/#allowresumepointschanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowUnentitledResumePointsChanged](./manage/Privacy/#allowunentitledresumepointschanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowWatchHistoryChanged](./manage/Privacy/#allowwatchhistorychanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowProductAnalyticsChanged](./manage/Privacy/#allowproductanalyticschanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowPersonalizationChanged](./manage/Privacy/#allowpersonalizationchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowUnentitledPersonalizationChanged](./manage/Privacy/#allowunentitledpersonalizationchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowRemoteDiagnosticsChanged](./manage/Privacy/#allowremotediagnosticschanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowPrimaryContentAdTargetingChanged](./manage/Privacy/#allowprimarycontentadtargetingchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowPrimaryBrowseAdTargetingChanged](./manage/Privacy/#allowprimarybrowseadtargetingchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowAppContentAdTargetingChanged](./manage/Privacy/#allowappcontentadtargetingchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowACRCollectionChanged](./manage/Privacy/#allowacrcollectionchanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.onAllowCameraAnalyticsChanged](./manage/Privacy/#allowcameraanalyticschanged) | **COULD** | `privacy:settings` |  |  |
| [Privacy.setAllowResumePoints](./manage/Privacy/#setallowresumepoints) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowUnentitledResumePoints](./manage/Privacy/#setallowunentitledresumepoints) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowWatchHistory](./manage/Privacy/#setallowwatchhistory) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowProductAnalytics](./manage/Privacy/#setallowproductanalytics) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowPersonalization](./manage/Privacy/#setallowpersonalization) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowUnentitledPersonalization](./manage/Privacy/#setallowunentitledpersonalization) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowRemoteDiagnostics](./manage/Privacy/#setallowremotediagnostics) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowPrimaryContentAdTargeting](./manage/Privacy/#setallowprimarycontentadtargeting) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowPrimaryBrowseAdTargeting](./manage/Privacy/#setallowprimarybrowseadtargeting) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowAppContentAdTargeting](./manage/Privacy/#setallowappcontentadtargeting) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowACRCollection](./manage/Privacy/#setallowacrcollection) | **COULD** |  |  | `privacy:settings` |
| [Privacy.setAllowCameraAnalytics](./manage/Privacy/#setallowcameraanalytics) | **COULD** |  |  | `privacy:settings` |
| [Profile.approveContentRating](./core/Profile/#approvecontentrating) | **SHOULD** | `approve:content` |  |  |
| [Profile.approvePurchase](./core/Profile/#approvepurchase) | **COULD** | `approve:purchase` |  |  |
| [Profile.flags](./core/Profile/#flags) | **COULD** | `profile:flags` |  |  |
| [SecondScreen.protocols](./core/SecondScreen/#protocols) | **COULD** | `secondscreen:protocol` |  |  |
| [SecondScreen.device](./core/SecondScreen/#device) | **COULD** | `protocol:dial` |  |  |
| [SecondScreen.friendlyName](./core/SecondScreen/#friendlyname) | **COULD** | `protocol:dial` |  |  |
| [SecondScreen.onLaunchRequest](./core/SecondScreen/#launchrequest) | **COULD** | `protocol:dial` |  |  |
| [SecondScreen.onCloseRequest](./core/SecondScreen/#closerequest) | **COULD** | `protocol:dial` |  |  |
| [SecondScreen.onFriendlyNameChanged](./core/SecondScreen/#friendlynamechanged) | **COULD** | `protocol:dial` |  |  |
| [SecureStorage.get](./core/SecureStorage/#get) | **SHOULD** | `storage:secure` |  |  |
| [SecureStorage.set](./core/SecureStorage/#set) | **SHOULD** | `storage:secure` |  |  |
| [SecureStorage.remove](./core/SecureStorage/#remove) | **SHOULD** | `storage:secure` |  |  |
| [SecureStorage.setForApp](./manage/SecureStorage/#setforapp) | **SHOULD** |  |  | `storage:secure` |
| [SecureStorage.removeForApp](./manage/SecureStorage/#removeforapp) | **SHOULD** |  |  | `storage:secure` |
| [SecureStorage.clearForApp](./manage/SecureStorage/#clearforapp) | **SHOULD** |  |  | `storage:secure` |
| [SecureStorage.clear](./core/SecureStorage/#clear) | **SHOULD** | `storage:secure` |  |  |
| [UserGrants.app](./manage/UserGrants/#app) | **MUST** | `grants:state` |  |  |
| [UserGrants.device](./manage/UserGrants/#device) | **MUST** | `grants:state` |  |  |
| [UserGrants.capability](./manage/UserGrants/#capability) | **MUST** | `grants:state` |  |  |
| [UserGrants.grant](./manage/UserGrants/#grant) | **MUST** |  |  | `grants:state` |
| [UserGrants.deny](./manage/UserGrants/#deny) | **MUST** |  |  | `grants:state` |
| [UserGrants.clear](./manage/UserGrants/#clear) | **MUST** |  |  | `grants:state` |
| [UserGrants.request](./manage/UserGrants/#request) | **MUST** |  |  | `grants:state` |
| [VoiceGuidance.enabled](./manage/VoiceGuidance/#enabled) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.navigationHints](./manage/VoiceGuidance/#navigationhints) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.rate](./manage/VoiceGuidance/#rate) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.speed](./manage/VoiceGuidance/#speed) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.onEnabledChanged](./manage/VoiceGuidance/#enabledchanged) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.onNavigationHintsChanged](./manage/VoiceGuidance/#navigationhintschanged) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.onRateChanged](./manage/VoiceGuidance/#ratechanged) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.onSpeedChanged](./manage/VoiceGuidance/#speedchanged) | **MUST** | `accessibility:voiceguidance` |  |  |
| [VoiceGuidance.setEnabled](./manage/VoiceGuidance/#setenabled) | **MUST** |  |  | `accessibility:voiceguidance` |
| [VoiceGuidance.setNavigationHints](./manage/VoiceGuidance/#setnavigationhints) | **MUST** |  |  | `accessibility:voiceguidance` |
| [VoiceGuidance.setRate](./manage/VoiceGuidance/#setrate) | **MUST** |  |  | `accessibility:voiceguidance` |
| [VoiceGuidance.setSpeed](./manage/VoiceGuidance/#setspeed) | **MUST** |  |  | `accessibility:voiceguidance` |
| [Wifi.scan](./manage/Wifi/#scan) | **COULD** | `protocol:wifi` |  |  |
| [Wifi.connect](./manage/Wifi/#connect) | **COULD** | `protocol:wifi` |  |  |
| [Wifi.disconnect](./manage/Wifi/#disconnect) | **COULD** | `protocol:wifi` |  |  |
| [Wifi.wps](./manage/Wifi/#wps) | **COULD** | `protocol:wifi` |  |  |
