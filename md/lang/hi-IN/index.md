<!-- यह अनुवाद ChatGPT द्वारा तैयार किया गया है और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->

<!-- अनुवाद सत्यापित हो जाने के बाद pull request में इन पंक्तियों को हटा दें। -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

CatalystUI की accessibility verification documentation में आपका स्वागत है।

**CatalystUI Verified for Accessibility** यह दर्शाता है कि किसी service, framework, application, library, या system की CatalystUI Team द्वारा समीक्षा की गई है और यह पाया गया है कि user-interface interaction में शामिल तीन primary senses में से कोई एक sense अलग से उपलब्ध न होने पर भी वह reasonably usable बना रहता है।

इस verification के लिए, CatalystUI तीन primary accessibility senses को **sight**, **sound**, और **touch** के रूप में पहचानता है। किसी verified system को इन senses में से कोई एक unavailable होने पर भी बाकी उपलब्ध sensory domains के सहारे अपनी essential functionality तक reasonable access बनाए रखना चाहिए।

सरल शब्दों में, यह verification यह पूछता है कि क्या कोई user sight, sound, या touch पर अलग-अलग निर्भर न रह पाने पर भी system के essential parts को अर्थपूर्ण ढंग से समझ, navigate, और operate कर सकता है।

## उद्देश्य

Accessibility इसलिए महत्त्वपूर्ण है क्योंकि user interface को पूरी तरह किसी एक sensory pathway पर निर्भर नहीं होना चाहिए, जब वही essential meaning किसी दूसरे pathway से reasonably communicate किया जा सकता हो।

CatalystUI systems और human perception के बीच data की faithful movement के आधार पर design किया गया है। यदि important information केवल दिखाई देती है, केवल सुनाई देती है, या केवल touch के माध्यम से उपलब्ध है, तो वह system उन users के लिए unusable हो सकता है जो उस sense पर निर्भर नहीं रह सकते। Accessibility Verification ऐसे systems की पहचान करने के लिए मौजूद है जो essential information और interaction को alternate sensory routes के माध्यम से जारी रखकर access को preserve करते हैं।

लक्ष्य हर possible interaction method, हर assistive technology, या हर specialized accommodation को require करना नहीं है। लक्ष्य यह निर्धारित करना है कि sight, sound, या touch में से कोई एक अलग से unavailable होने पर essential system meaningfully usable रहता है या नहीं।

## Verification का अर्थ

कोई system **CatalystUI Verified for Accessibility** तब बनता है जब इस section में listed requirements के विरुद्ध उसकी review की जाती है और उसे within spec पाया जाता है।

Verified होने के लिए, किसी system को नीचे दिए गए प्रत्येक case में reasonably usable रहना चाहिए:

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | System को sound और touch के माध्यम से reasonably usable रहना चाहिए। |
| Sound             | System को sight और touch के माध्यम से reasonably usable रहना चाहिए। |
| Touch             | System को sight और sound के माध्यम से reasonably usable रहना चाहिए। |

किसी system को हर sensory path में identical experiences देने की आवश्यकता नहीं है। Non-visual experience visual experience से धीमा हो सकता है। Sound-free experience में captions, visual indicators, या अन्य substitutions की आवश्यकता हो सकती है। Touch-free experience में alternate controls, voice interaction, keyboard navigation, pointer navigation, या अन्य non-touch methods की आवश्यकता हो सकती है।

महत्त्वपूर्ण बात यह है कि unavailable sense को require किए बिना essential functionality accessible, understandable, और operable बनी रहे।

## Essential Functionality

Accessibility Verification के लिए, **essential functionality** system के उन parts को संदर्भित करती है जिनकी user को system को समझने, navigate करने, configure करने, और operate करने के लिए reasonably आवश्यकता होती है।

Essential functionality में शामिल हो सकते हैं:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* normal use के लिए required कोई भी interaction

यदि decorative, redundant, optional, या nonessential features हर sensory path में समान रूप से उपलब्ध नहीं हैं, तब भी कोई system within spec हो सकता है। फिर भी user missing sense के कारण essential system का उपयोग करने से blocked नहीं होना चाहिए।

## Sight Unavailable

जब sight unavailable हो, तो system को sound और touch के माध्यम से reasonably usable रहना चाहिए।

इसमें spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions, या essential information communicate करने का कोई और reasonable non-visual method शामिल हो सकता है।

किसी system को visual position, color, shape, animation, icons, या layout पर exclusively निर्भर नहीं रहना चाहिए जब वह information essential functionality को समझने या operate करने के लिए required हो।

## Sound Unavailable

जब sound unavailable हो, तो system को sight और touch के माध्यम से reasonably usable रहना चाहिए।

इसमें captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback, या essential information communicate करने का कोई और reasonable non-auditory method शामिल हो सकता है।

किसी system को sound effects, spoken instructions, alerts, alarms, music cues, या audio-only prompts पर exclusively निर्भर नहीं रहना चाहिए जब वह information essential functionality को समझने या operate करने के लिए required हो।

## Touch Unavailable

जब touch unavailable हो, तो system को sight और sound के माध्यम से reasonably usable रहना चाहिए।

इसमें voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation, या कोई और reasonable method शामिल हो सकता है जिसे touch-based interaction या tactile perception की आवश्यकता न हो।

किसी system को touch gestures, haptic feedback, physical texture, vibration, force, pressure, या touch-only controls पर exclusively निर्भर नहीं रहना चाहिए जब वे interactions essential functionality को समझने या operate करने के लिए required हों।

## Additional Sensory Domains

CatalystUI **taste** और **smell** को भी sensory domains के रूप में पहचानता है। जब system इनका meaningful use करता है, तब accessibility review के दौरान इन domains पर विचार किया जा सकता है।

Taste और smell verification के लिए **inclusive** हैं, अर्थात जब वे meaningful alternate access या additional context देते हैं, तो वे accessibility review को strengthen या support कर सकते हैं।

Taste और smell अभी failure के लिए **exclusive** नहीं हैं, अर्थात कोई system Accessibility Verification में केवल इसलिए fail नहीं होता क्योंकि वह taste-based या smell-based interaction प्रदान नहीं करता।

CatalystUI Accessibility Verification मुख्य रूप से इस बात से संबंधित है कि sight, sound, या touch में से कोई एक अलग से unavailable होने पर system reasonably usable रहता है या नहीं।

## “Within Spec” का अर्थ

जब किसी system को **within spec** माना जाता है, तो इसका अर्थ है कि CatalystUI Team ने manually उस system की review की है और यह निष्कर्ष निकालना reasonable पाया है कि वह इस verification category द्वारा described accessibility requirements को satisfy करता है।

इसके लिए एक ही rigid implementation pattern आवश्यक नहीं है। कोई system native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration, या system के लिए appropriate किसी अन्य stable mechanism के माध्यम से accessibility requirements satisfy कर सकता है।

Verification इस बात से संबंधित है कि users primary sense unavailable होने पर essential system तक practically access कर सकते हैं या नहीं, न कि system किसी specific accessibility architecture का उपयोग करता है या नहीं।

## Verification का अर्थ क्या नहीं है

CatalystUI Verified for Accessibility यह guarantee नहीं करता कि हर possible disability, device, assistive technology, medical condition, legal requirement, regional standard, या specialized use case की पूरी review हो चुकी है।

यह internationalization, translation quality, typography, localization, regional compliance, या general design quality को भी automatically verify नहीं करता, जब तक ये concerns reviewed accessibility scope में शामिल न हों।

CatalystUI के accessibility model के अंतर्गत कोई system reasonably accessible हो सकता है और फिर भी legal compliance, platform certification, specialized assistive technology support, या अन्य accessibility standards के लिए अलग review की आवश्यकता हो सकती है।

## यह Verification क्यों मौजूद है

User interface तभी सफल होता है जब users वास्तव में उसका उपयोग कर सकें।

कई systems accessibility को human-computer interaction के fundamental part के बजाय afterthought, checklist, या narrow technical requirement की तरह मानते हैं। CatalystUI एक सरल और अधिक direct approach अपनाता है: यदि कोई system human perception पर निर्भर करता है, तो primary sensory path unavailable होने पर उसे essential meaning preserve करना चाहिए।

Accessibility Verification ऐसे systems की पहचान करने के लिए मौजूद है जो इस responsibility को serious लेते हैं। यह उन systems को recognize करता है जो meaningful alternate access देते हैं, essential functionality preserve करते हैं, और users को एक ही required sense के पीछे trap करने से बचते हैं।

## Verification Scope

CatalystUI Verification for Accessibility उस reviewed system, service, framework, application, library, या implementation पर लागू होती है जैसा वह verification जारी होने के समय मौजूद था।

Verified system reviewed conditions के अंतर्गत अपनी essential functionality के लिए reasonable accessibility प्रदान करता है। यह guarantee नहीं करता कि हर future page, feature, release, plugin, extension, third-party integration, device, या platform-specific version automatically within spec है।

अलग products, modules, services, major revisions, या platform-specific builds को requested verification category के आधार पर अपनी अलग review की आवश्यकता हो सकती है।

## Verification Validity

CatalystUI Verification केवल verification जारी होने के समय system की reviewed state पर लागू होती है।

कोई system later updates में अपनी verification बनाए रख सकता है, यदि वह verified accessibility foundation को preserve करता रहे। Minor wording changes, visual refinements, performance improvements, और ordinary content updates verification को automatically invalidate नहीं करते।

नई review की आवश्यकता हो सकती है यदि कोई system alternate access paths हटाता है, assistive-technology support तोड़ता है, essential navigation को substantially बदलता है, required accessibility settings हटाता है, या interaction behavior को इस तरह बदलता है कि verified accessibility foundation प्रभावित हो।

दूसरे शब्दों में, accessibility improve करना आमतौर पर ठीक है। Verified access model को break करना review require कर सकता है।

## Verified Systems

Accessibility के लिए verified known systems appropriate CatalystUI Verified page पर अलग से listed हैं।
