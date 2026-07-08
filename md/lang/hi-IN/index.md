<!-- यह अनुवाद ChatGPT द्वारा बनाया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->

<!-- अनुवाद सत्यापित होने के बाद pull request में इन पंक्तियों को हटा दें। -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Internationalization के लिए CatalystUI Verification documentation में आपका स्वागत है।

**CatalystUI Verified for Internationalization** यह दर्शाता है कि किसी system, service, framework, application, या implementation की CatalystUI Team द्वारा समीक्षा की गई है और उसे आवश्यक CatalystUI internationalization language set के लिए पर्याप्त multilingual support प्रदान करने वाला पाया गया है।

यह verification translation quality, writing style, localization depth, या cultural adaptation की कोई सामान्य ranking नहीं है। इसके बजाय, यह पहचानता है कि reviewed system उपयोगकर्ताओं को required supported languages में अपनी essential functionality तक पहुँचने के लिए स्थिर और व्यावहारिक आधार देता है या नहीं।

सरल शब्दों में, यह verification पूछता है कि क्या users किसी system के essential parts को required languages में meaningfully उपयोग कर सकते हैं, और क्या उन्हें अपनी समझ की भाषा चुनने का एक reasonable तरीका दिया गया है।

<a id="purpose"></a>
## उद्देश्य

Internationalization इसलिए महत्वपूर्ण है क्योंकि किसी system को broadly accessible नहीं माना जा सकता यदि उसका essential meaning केवल एक भाषा में बंद हो।

CatalystUI clarity, consistency, और human-computer interaction के faithful representation के आधार पर बनाया गया है। भाषा उसी interaction का हिस्सा है। यदि कोई user किसी system के labels, instructions, warnings, controls, settings, या essential content को नहीं समझ सकता, तो system ने साफ़ communication नहीं किया, भले ही underlying functionality तकनीकी रूप से काम करती हो।

Internationalization Verification उन systems की पहचान करने के लिए मौजूद है जो required CatalystUI language set में users के लिए पर्याप्त translated support प्रदान करते हैं। लक्ष्य हर optional word, hidden developer message, या nonessential page की perfect translation मांगना नहीं है। लक्ष्य यह तय करना है कि system के essential parts हर required language में समझे और उपयोग किए जा सकते हैं या नहीं।

<a id="what-verification-means"></a>
## Verification का अर्थ

कोई system तब **CatalystUI Verified for Internationalization** बनता है जब इस section में listed requirements के विरुद्ध उसकी समीक्षा की जाती है और उसे within spec पाया जाता है।

Verified होने के लिए, system को हर required language में essential user-facing parts के 75% से अधिक के लिए translations देनी होंगी। उसे active language बदलने के लिए end-user को एक reasonable mechanism भी देना होगा।

किसी system को हर internal identifier, developer-facing implementation detail, debug string, optional marketing page, या nonessential support text translate करने की आवश्यकता नहीं है। फिर भी, essential system को समझने और operate करने के लिए required user-facing portions हर required language में उपलब्ध होने चाहिए।

<a id="required-languages"></a>
## Required Languages

वर्तमान CatalystUI internationalization language set को technology contexts में सामान्यतः आवश्यक भाषाओं की practical review से चुना गया है, जिसमें global speaker reach, common online usage, multilingual software expectations, और broad regional accessibility needs शामिल हैं।

यह language set हर language, हर dialect, या हर regional variant को represent करने के लिए नहीं है। इसके बजाय, यह उन systems के लिए practical baseline स्थापित करता है जो दुनिया के कई common technology-facing language groups में broad international usability चाहते हैं।

वर्तमान CatalystUI internationalization language set में निम्न locales शामिल हैं:

| Locale    | भाषा                     |
| --------- | ------------------------ |
| `ar-SA`   | अरबी (सऊदी अरब)          |
| `bn-BD`   | बंगाली (बांग्लादेश)      |
| `de-DE`   | जर्मन (जर्मनी)           |
| `en-GB`   | अंग्रेज़ी (यूनाइटेड किंगडम) |
| `en-IN`   | अंग्रेज़ी (भारत)         |
| `en-US`   | अंग्रेज़ी (संयुक्त राज्य) |
| `es-ES`   | स्पेनिश (स्पेन)          |
| `es-MX`   | स्पेनिश (मेक्सिको)       |
| `fa-IR`   | फ़ारसी (ईरान)            |
| `fr-FR`   | फ़्रेंच (फ़्रांस)        |
| `hi-IN`   | हिंदी (भारत)             |
| `id-ID`   | इंडोनेशियाई (इंडोनेशिया) |
| `it-IT`   | इतालवी (इटली)            |
| `ja-JP`   | जापानी (जापान)           |
| `ko-KR`   | कोरियाई (दक्षिण कोरिया)  |
| `nl-NL`   | डच (नीदरलैंड)            |
| `pl-PL`   | पोलिश (पोलैंड)           |
| `pt-BR`   | पुर्तगाली (ब्राज़ील)     |
| `ru-RU`   | रूसी (रूस)               |
| `tl-PH`   | तागालोग (फ़िलिपींस)     |
| `tr-TR`   | तुर्की (तुर्किये)        |
| `uk-UA`   | यूक्रेनी (यूक्रेन)       |
| `ur-PK`   | उर्दू (पाकिस्तान)        |
| `vi-VN`   | वियतनामी (वियतनाम)       |
| `zh-CN`   | चीनी (चीन)               |
| `zh-Hans` | चीनी (सरलीकृत)           |

Within spec माने जाने के लिए system को हर listed language group के लिए पर्याप्त essential translation coverage प्रदान करनी होगी।

हालाँकि, regional variants की review reasonable flexibility के साथ की जा सकती है जब variants के बीच differences minor हों और user की system को समझने या operate करने की ability पर materially असर न डालें। उदाहरण के लिए, कोई system एक strong English translation देता है लेकिन हर English regional variant को अलग से translate नहीं करता, तो भी वह verification के लिए eligible हो सकता है, जब तक essential meaning, navigation, instructions, warnings, और controls missing variants के users के लिए clear रहें।

यह flexibility तब लागू नहीं होती जब missing variant meaningful confusion पैदा करे, regionally important terminology छोड़ दे, locale-sensitive behavior तोड़ दे, या users को system के essential parts समझने से रोक दे।

<a id="essential-translation-coverage"></a>
## Essential Translation Coverage

Internationalization Verification में **essential translation coverage** system के उन parts को कहता है जिनकी user को system को समझने, navigate करने, configure करने, और operate करने के लिए reasonably आवश्यकता होती है।

Essential parts में शामिल हो सकते हैं:

* primary navigation
* core screens and views
* settings and preferences
* user-facing labels
* user-facing controls
* required instructions
* important warnings
* important errors
* essential prompts
* required confirmation messages
* language selection controls
* normal use के लिए required core workflows

किसी system को translation coverage requirement पूरा माना जाता है जब उसका 75% से अधिक essential user-facing content हर required language में उपलब्ध हो।

यह threshold इसलिए मौजूद है क्योंकि internationalization work बड़ा, ongoing, और context-dependent हो सकता है। कुछ nonessential या lower-priority content untranslated रह जाने पर भी system within spec हो सकता है। लेकिन essential experience हर required language में meaningfully available होना चाहिए।

<a id="language-selection"></a>
## Language Selection

Verified system को end-user को active language बदलने का reasonable तरीका देना होगा।

Language selection mechanism आसानी से मिलने वाला, समझ में आने वाला, और technical knowledge के बिना उपलब्ध होना चाहिए। Users को केवल language बदलने के लिए configuration files edit करने, source code modify करने, developer tools install करने, या undocumented behavior पर rely करने की आवश्यकता नहीं होनी चाहिए।

Language options दिखाते समय, system को हर language को इस तरह identify करना चाहिए जो उस language को बोलने वाले users और किसी दूसरी selected language का उपयोग कर रहे users, दोनों के लिए understandable हो।

उदाहरण के लिए, language option इस तरह दिखाई जा सकती है:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Exact formatting अलग हो सकती है, लेकिन intent वही रहना चाहिए: users अपनी language पहचान सकें, जब संभव हो currently displayed language name समझ सकें, और associated locale code पहचान सकें।

<a id="what-within-spec-means"></a>
## “Within Spec” का अर्थ

जब कोई system **within spec** माना जाता है, तो इसका अर्थ है कि CatalystUI Team ने system की manually review की है और यह निष्कर्ष निकालना reasonable पाया है कि वह इस verification category द्वारा described internationalization requirements को satisfy करता है।

इसके लिए कोई एक rigid implementation pattern required नहीं है। कोई system resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs, या system के लिए appropriate किसी अन्य stable mechanism के माध्यम से requirement satisfy कर सकता है।

Verification users की practical ability से संबंधित है कि वे required languages में essential system तक access कर सकें, न कि system किसी specific translation architecture का उपयोग करता है या नहीं।

<a id="what-verification-does-not-mean"></a>
## Verification का अर्थ क्या नहीं है

CatalystUI Verified for Internationalization यह guarantee नहीं करता कि हर translation perfect, literary, idiomatic, culturally complete, या हर region के लिए legally sufficient है।

यह accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance, या regional business requirements को automatic रूप से verify नहीं करता, जब तक ये concerns reviewed internationalization scope में included न हों।

कोई system strong translation coverage दे सकता है और फिर भी accessibility, localization quality, regional compliance, या अन्य specialized concerns के लिए separate review की आवश्यकता रख सकता है।

<a id="why-this-verification-exists"></a>
## यह Verification क्यों मौजूद है

User interface तभी उपयोगी है जब user समझ सके कि वह क्या communicate कर रहा है।

कई systems language support का दावा करते हैं, जबकि experience का केवल छोटा हिस्सा translate करते हैं, language selection छिपाते हैं, important messages छोड़ देते हैं, या essential workflows को partially untranslated छोड़ते हैं। इससे confusion पैदा होती है और users system पर trust नहीं कर पाते।

Internationalization Verification एक clearer standard set करने के लिए मौजूद है। यह उन systems को identify करता है जो required CatalystUI language set में users को support करने के लिए serious, practical effort करते हैं और users को अपनी required language select करने का reasonable तरीका देते हैं।

<a id="verification-scope"></a>
## Verification Scope

CatalystUI Verification for Internationalization reviewed system, service, framework, application, या implementation पर उसी रूप में लागू होता है जैसा वह verification जारी होने के समय मौजूद था।

Verified system required languages के लिए sufficient essential translation coverage देता है। यह guarantee नहीं करता कि हर future page, feature, release, plugin, extension, या third-party integration automatic रूप से within spec है।

Separate products, modules, services, language packs, या major revisions को requested verification category के आधार पर अपनी review की आवश्यकता हो सकती है।

<a id="verification-validity"></a>
## Verification Validity

CatalystUI Verification केवल system की reviewed state पर लागू होता है, उसी समय जब verification जारी किया गया था।

System बाद के updates में verification बनाए रख सकता है, जब तक वह verified internationalization foundation को preserve करता है। Minor wording changes, added translations, और ordinary content updates automatic रूप से verification को invalidate नहीं करते।

नई review आवश्यक हो सकती है यदि system required language support हटाता है, language selection तोड़ता है, essential translation coverage को substantially कम करता है, या अपनी internationalization architecture को इस तरह बदलता है जिससे verified behavior प्रभावित हो।

दूसरे शब्दों में, translation support सुधारना सामान्यतः ठीक है। Verified multilingual base को तोड़ना review की आवश्यकता पैदा कर सकता है।

<a id="verified-systems"></a>
## Verified Systems

Internationalization के लिए verified known systems उपयुक्त CatalystUI Verified page पर अलग से listed होते हैं।
