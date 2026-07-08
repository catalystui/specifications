<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদক দ্বারা পর্যালোচনা করা উচিত। -->

<!-- অনুবাদ যাচাই হয়ে গেলে pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

CatalystUI-এর internationalization যাচাইকরণ ডকুমেন্টেশনে স্বাগতম।

**CatalystUI Verified for Internationalization** নির্দেশ করে যে কোনো system, service, framework, application, অথবা implementation CatalystUI Team দ্বারা পর্যালোচিত হয়েছে এবং CatalystUI-এর প্রয়োজনীয় internationalization language set-এর জন্য যথেষ্ট বহুভাষিক সহায়তা প্রদান করে বলে পাওয়া গেছে।

এই যাচাইকরণ অনুবাদের গুণমান, লেখার ধরন, localization-এর গভীরতা, অথবা সাংস্কৃতিক অভিযোজনের সাধারণ র‍্যাঙ্কিং নয়। এর পরিবর্তে, এটি নির্ধারণ করে পর্যালোচিত system ব্যবহারকারীদের জন্য প্রয়োজনীয় সমর্থিত ভাষাগুলিতে তার essential functionality-তে প্রবেশের জন্য স্থিতিশীল ও ব্যবহারিক ভিত্তি প্রদান করে কি না।

সহজভাবে বললে, এই যাচাইকরণ জিজ্ঞেস করে ব্যবহারকারীরা প্রয়োজনীয় ভাষাগুলিতে কোনো system-এর essential অংশগুলি অর্থপূর্ণভাবে ব্যবহার করতে পারে কি না, এবং তারা যে ভাষা বোঝে সেটি বেছে নেওয়ার জন্য একটি যুক্তিসঙ্গত উপায় পায় কি না।

## উদ্দেশ্য

Internationalization গুরুত্বপূর্ণ, কারণ কোনো system-এর essential meaning যদি এক ভাষার ভিতর আটকে থাকে, তবে সেটিকে বিস্তৃতভাবে accessible বলা যায় না।

CatalystUI নির্মিত হয়েছে clarity, consistency, এবং human-computer interaction-এর faithful representation ঘিরে। ভাষা সেই interaction-এর অংশ। কোনো user যদি system-এর labels, instructions, warnings, controls, settings, অথবা essential content বুঝতে না পারে, তবে underlying functionality প্রযুক্তিগতভাবে কাজ করলেও systemটি স্পষ্টভাবে যোগাযোগ করতে ব্যর্থ হয়েছে।

Internationalization Verification এমন systems চিহ্নিত করার জন্য আছে যা CatalystUI-এর required language set জুড়ে users-দের জন্য যথেষ্ট translated support দেয়। উদ্দেশ্য হলো প্রতিটি optional word, hidden developer message, অথবা nonessential page-এর নিখুঁত অনুবাদ দাবি করা নয়। উদ্দেশ্য হলো নির্ধারণ করা যে প্রতিটি required language-এ system-এর essential অংশগুলি মানুষ বুঝতে ও ব্যবহার করতে পারে কি না।

## যাচাইকরণের অর্থ

এই section-এ তালিকাভুক্ত requirements-এর বিরুদ্ধে review করা হয়ে systemটি within spec পাওয়া গেলে systemটি **CatalystUI Verified for Internationalization** হয়।

যাচাইকৃত হতে হলে একটি system-কে প্রতিটি required language-এ essential user-facing অংশের 75%-এর বেশি অংশের translation প্রদান করতে হবে। active language পরিবর্তনের জন্য end-user-এর কাছে একটি reasonable mechanism-ও থাকতে হবে।

একটি system-এর প্রতিটি internal identifier, developer-facing implementation detail, debug string, optional marketing page, অথবা nonessential support text অনুবাদ করার প্রয়োজন নেই। তবে essential system বুঝতে ও চালাতে প্রয়োজনীয় user-facing অংশগুলি প্রতিটি required language-এ available থাকতে হবে।

## প্রয়োজনীয় ভাষা

বর্তমান CatalystUI internationalization language set নির্বাচন করা হয়েছে technology context-এ সাধারণভাবে প্রয়োজনীয় ভাষার ব্যবহারিক review থেকে; এর মধ্যে global speaker reach, common online usage, multilingual software expectations, এবং broad regional accessibility needs অন্তর্ভুক্ত।

এই language set প্রতিটি ভাষা, প্রতিটি dialect, অথবা প্রতিটি regional variant উপস্থাপন করার উদ্দেশ্যে নয়। এর পরিবর্তে, এটি বিশ্বের অনেক common technology-facing language group জুড়ে broad international usability চাওয়া systems-এর জন্য একটি practical baseline স্থাপন করে।

বর্তমান CatalystUI internationalization language set-এ নিম্নলিখিত locales অন্তর্ভুক্ত:

| Locale    | Language                 |
| --------- | ------------------------ |
| `ar-SA`   | Arabic (Saudi Arabia)    |
| `bn-BD`   | Bengali (Bangladesh)     |
| `de-DE`   | German (Germany)         |
| `en-GB`   | English (United Kingdom) |
| `en-IN`   | English (India)          |
| `en-US`   | English (United States)  |
| `es-ES`   | Spanish (Spain)          |
| `es-MX`   | Spanish (Mexico)         |
| `fa-IR`   | Persian (Iran)           |
| `fr-FR`   | French (France)          |
| `hi-IN`   | Hindi (India)            |
| `id-ID`   | Indonesian (Indonesia)   |
| `it-IT`   | Italian (Italy)          |
| `ja-JP`   | Japanese (Japan)         |
| `ko-KR`   | Korean (South Korea)     |
| `nl-NL`   | Dutch (Netherlands)      |
| `pl-PL`   | Polish (Poland)          |
| `pt-BR`   | Portuguese (Brazil)      |
| `ru-RU`   | Russian (Russia)         |
| `tl-PH`   | Tagalog (Philippines)    |
| `tr-TR`   | Turkish (Turkey)         |
| `uk-UA`   | Ukrainian (Ukraine)      |
| `ur-PK`   | Urdu (Pakistan)          |
| `vi-VN`   | Vietnamese (Vietnam)     |
| `zh-CN`   | Chinese (China)          |
| `zh-Hans` | Chinese (Simplified)     |

within spec বিবেচিত হতে প্রতিটি তালিকাভুক্ত language group-এর জন্য system-কে যথেষ্ট essential translation coverage প্রদান করতে হবে।

তবে regional variants যুক্তিসঙ্গত নমনীয়তার সঙ্গে review করা যেতে পারে যখন variants-এর পার্থক্য সামান্য এবং user-এর system বোঝা বা চালানোর সক্ষমতাকে তা materially affect করে না। উদাহরণস্বরূপ, কোনো system একটি strong English translation প্রদান করলেও আলাদা করে প্রতিটি English regional variant অনুবাদ না করলে verification-এর যোগ্য থাকতে পারে, যদি essential meaning, navigation, instructions, warnings, এবং controls missing variants-এর users-দের কাছে clear থাকে।

এই flexibility প্রযোজ্য নয় যখন missing variant meaningful confusion তৈরি করবে, regionally important terminology বাদ দেবে, locale-sensitive behavior ভেঙে দেবে, অথবা users-দের system-এর essential অংশ বোঝা থেকে আটকাবে।

## Essential Translation Coverage

Internationalization Verification-এর ক্ষেত্রে, **essential translation coverage** বলতে system-এর সেই অংশগুলি বোঝায় যা একজন user যুক্তিসঙ্গতভাবে system বুঝতে, navigate করতে, configure করতে এবং operate করতে প্রয়োজন করে।

Essential অংশগুলির মধ্যে থাকতে পারে:

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
* core workflows needed for normal use

প্রতিটি required language-এ essential user-facing content-এর 75%-এর বেশি available থাকলে systemটি translation coverage requirement পূরণ করে বলে বিবেচিত হয়।

এই threshold আছে কারণ internationalization work বড়, চলমান, এবং context-dependent হতে পারে। কিছু nonessential বা lower-priority content untranslated থাকলেও system within spec থাকতে পারে। তবে essential experience প্রতিটি required language-এ meaningfully available থাকতে হবে।

## ভাষা নির্বাচন

একটি verified system-কে end-user-এর active language পরিবর্তনের জন্য একটি reasonable way প্রদান করতে হবে।

language selection mechanism সহজে খুঁজে পাওয়া যায়, বোঝা যায়, এবং technical knowledge ছাড়াই ব্যবহারযোগ্য হওয়া উচিত। শুধু language পরিবর্তন করার জন্য users-দের configuration files edit করা, source code modify করা, developer tools install করা, অথবা undocumented behavior-এর ওপর নির্ভর করা উচিত নয়।

language options প্রদর্শনের সময়, system-এর উচিত প্রতিটি language এমনভাবে চিহ্নিত করা যা সেই language-ভাষী users এবং বর্তমানে অন্য selected language ব্যবহার করা users—উভয়ের কাছেই বোধ্য।

উদাহরণস্বরূপ, একটি language option এভাবে প্রদর্শিত হতে পারে:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

নির্দিষ্ট formatting ভিন্ন হতে পারে, কিন্তু intent একই থাকা উচিত: users যেন নিজের language চিনতে পারে, সম্ভব হলে বর্তমানে প্রদর্শিত language name বুঝতে পারে, এবং সংশ্লিষ্ট locale code শনাক্ত করতে পারে।

## “Within Spec” এর অর্থ

যখন কোনো system **within spec** বিবেচিত হয়, তার অর্থ CatalystUI Team systemটি manually reviewed করেছে এবং এই verification category-তে বর্ণিত internationalization requirements পূরণ করে বলে reasonable conclusion পাওয়া গেছে।

এর জন্য একটি rigid implementation pattern প্রয়োজন নেই। একটি system resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs, অথবা system-এর জন্য উপযুক্ত অন্য কোনো stable mechanism-এর মাধ্যমে requirement পূরণ করতে পারে।

Verification-এর বিষয় হলো required languages-এ users-এর essential system access করার practical ability; system একটি নির্দিষ্ট translation architecture ব্যবহার করছে কি না তা নয়।

## যাচাইকরণের অর্থ নয় যা

CatalystUI Verified for Internationalization নিশ্চয়তা দেয় না যে প্রতিটি translation perfect, literary, idiomatic, culturally complete, অথবা প্রতিটি region-এর জন্য legally sufficient।

এটি accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance, অথবা regional business requirements-ও automatically verify করে না, যদি না সেই concerns reviewed internationalization scope-এর মধ্যে অন্তর্ভুক্ত থাকে।

একটি system strong translation coverage প্রদান করলেও accessibility, localization quality, regional compliance, অথবা অন্যান্য specialized concerns-এর জন্য আলাদা review প্রয়োজন হতে পারে।

## এই যাচাইকরণ কেন আছে

User interface তখনই useful যখন user বুঝতে পারে সেটি কী communicate করছে।

অনেক system language support দাবি করে, কিন্তু experience-এর ছোট অংশ অনুবাদ করে, language selection লুকায়, important messages বাদ দেয়, অথবা essential workflows আংশিক untranslated রাখে। এতে confusion তৈরি হয় এবং users system-কে trust করতে পারে না।

Internationalization Verification একটি clearer standard স্থাপনের জন্য আছে। এটি এমন systems চিহ্নিত করে যা required CatalystUI language set জুড়ে users-দের support করার serious, practical effort করে এবং users-দের প্রয়োজনীয় language select করার reasonable way প্রদান করে।

## যাচাইকরণের পরিসর

CatalystUI Verification for Internationalization review করা system, service, framework, application, অথবা implementation-এর সেই অবস্থায় প্রযোজ্য, যে অবস্থায় verification issued হয়েছিল।

একটি verified system required languages-এর জন্য sufficient essential translation coverage প্রদান করে। এটি নিশ্চয়তা দেয় না যে ভবিষ্যতের প্রতিটি page, feature, release, plugin, extension, অথবা third-party integration automatically within spec।

Separate products, modules, services, language packs, অথবা major revisions requested verification category অনুযায়ী নিজস্ব review প্রয়োজন করতে পারে।

## যাচাইকরণের বৈধতা

CatalystUI Verification কেবল system-এর reviewed state-এ প্রযোজ্য, verification issued হওয়ার সময়।

systemটি পরবর্তী updates জুড়ে verification ধরে রাখতে পারে, যদি verified internationalization foundation সংরক্ষণ করে। Minor wording changes, added translations, এবং ordinary content updates automatically verification invalid করে না।

নতুন review প্রয়োজন হতে পারে যদি system required language support সরিয়ে দেয়, language selection ভেঙে দেয়, essential translation coverage উল্লেখযোগ্যভাবে কমায়, অথবা verified behavior-কে affect করে এমনভাবে internationalization architecture পরিবর্তন করে।

অন্যভাবে বললে, translation support উন্নত করা সাধারণত ঠিক আছে। verified multilingual base ভেঙে দিলে review প্রয়োজন হতে পারে।

## যাচাইকৃত সিস্টেম

Internationalization-এর জন্য পরিচিত verified systems উপযুক্ত CatalystUI Verified page-এ আলাদাভাবে তালিকাভুক্ত করা হয়েছে।
