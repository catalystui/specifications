<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Programming Languages-এর জন্য CatalystUI Verified

programming languages-এর জন্য CatalystUI Verification documentation-এ স্বাগতম।

**CatalystUI Verified for Programming Languages** নির্দেশ করে যে একটি programming language CatalystUI Team দ্বারা review করা হয়েছে এবং CatalystUI-compatible systems প্রকাশ করার জন্য প্রয়োজনীয় foundational data representations ও relational structures প্রদান করে বলে পাওয়া গেছে।

এই verification programming languages-এর সাধারণ ranking নয়। এটি কোনো language অন্য language-এর চেয়ে ভালো, দ্রুত, সহজ, নতুন, জনপ্রিয়, অথবা বেশি enjoyable কি না তা নির্ধারণ করে না। বরং এটি শনাক্ত করে language-টি CatalystUI Verification-এর জন্য প্রয়োজনীয় specifications-এর একটি stable এবং practical foundation প্রদান করে কি না।

সহজভাবে বললে, এই verification জিজ্ঞাসা করে একটি programming language CatalystUI যার উপর নির্ভর করে সেই basic data এবং relationships faithfulভাবে represent করতে পারে কি না।

## উদ্দেশ্য

Programming languages প্রত্যেক CatalystUI implementation-এর নিচে থাকা representational foundation তৈরি করে। কোনো framework, library, runtime, application, বা service CatalystUI Stack অনুসরণ করার আগে, সেটি তৈরি করতে ব্যবহৃত language-টি model যার উপর নির্ভর করে সেই foundational concepts প্রকাশ করতে সক্ষম হতে হবে।

Programming languages-এর ক্ষেত্রে এর অর্থ প্রধানত দুইটি বিষয়:

1. language-টি foundational data represent করতে সক্ষম হতে হবে।
2. language-টি data-এর মধ্যে foundational relationships represent করতে সক্ষম হতে হবে।

এই concerns foundational CatalystUI specifications-এর মাধ্যমে defined। FDEFSPEC expected foundational data representations define করে। FRELSPEC এই representations-এর মধ্যে expected foundational relations define করে, যার মধ্যে collections, memory relationships, operations, threading relationships, এবং composites অন্তর্ভুক্ত।

একটি verified programming language developers-দের যথেষ্ট clarity এবং control দেয় যাতে তারা CatalystUI-compatible systems তৈরি করতে পারে, CatalystUI যার basic concepts দাবি করে সেগুলির জন্য fragile, unclear, বা unstable workarounds-এর ওপর নির্ভর না করে।

## Verification কী বোঝায়

একটি programming language **CatalystUI Verified** হয় যখন এটি এই section-এ listed specifications-এর বিরুদ্ধে review করা হয় এবং within spec বলে পাওয়া যায়।

Programming Language Verification-এর জন্য review-টি applicable specifications দ্বারা defined foundational requirements language-টি express করতে পারে কি না তার উপর focused। এর অর্থ এই নয় যে language নিজেই CatalystUI implementation। এর অর্থ language-টি এমন suitable foundation প্রদান করে যেখান থেকে CatalystUI-compatible implementations তৈরি করা যেতে পারে।

একটি language-কে অন্য language-এর মতো একইভাবে এই requirements satisfy করতে হবে না। Different languages different syntax, type systems, standard libraries, compilers, runtimes, এবং design patterns ব্যবহার করে। CatalystUI Verification এই differences allow করে, যতক্ষণ required concepts clearly, reliably, এবং consistently express করা যায়।

## “Within Spec” কী বোঝায়

যখন একটি programming language **within spec** হিসেবে বিবেচিত হয়, তখন এর অর্থ CatalystUI Team language-টি manually reviewed করেছে এবং applicable specifications-এ described required behavior সেই language-এর মধ্যে express করা যায় বলে reasonable conclusion পাওয়া গেছে।

এর জন্য একটিমাত্র rigid implementation pattern প্রয়োজন হয় না। একটি language built-in primitives, standard library features, compiler behavior, runtime behavior, documented guarantees, অথবা সেই language-এর উপযোগী অন্য stable mechanism-এর মাধ্যমে কোনো requirement satisfy করতে পারে।

Verification specification-এর meaning represent এবং preserve করার practical ability নিয়ে concerned; language-টি specification text-এর exact একই names, structures, syntax, বা internal design ব্যবহার করে কি না তা নয়।

## এই Verification কেন আছে

CatalystUI clarity, consistency, এবং humans ও computers কীভাবে interact করে তার faithful representation ঘিরে design করা হয়েছে। Programming languages গুরুত্বপূর্ণ কারণ এগুলি নির্ধারণ করে developers বাস্তবে কী express করতে পারে, সেই systems কত safely model করা যায়, এবং higher-level implementations কত clearly তৈরি করা যায়।

যদি কোনো language required foundational concepts stableভাবে প্রদান করতে না পারে, তবে higher-level CatalystUI implementations trust করা কঠিন হয়ে যায়। Developers-দের unclear abstractions, unpredictable behavior, fragile dependencies, অথবা unnecessary rewrites-এর দিকে ঠেলে দেওয়া হতে পারে—শুধু এমন ideas express করার জন্য, যেগুলি শুরু থেকেই reliable হওয়া উচিত।

Programming Language Verification আছে কোন languages CatalystUI work-এর জন্য যথেষ্ট শক্ত foundation প্রদান করে তা শনাক্ত করার জন্য। এটি developers, language designers, এবং organizations-কে একটি clearer understanding দেয় যে language-টি CatalystUI-compatible systems তৈরির জন্য suitable কি না।

## একটি Language কীভাবে Verified হয়

**CatalystUI Verified for Programming Languages** হতে, একটি language-কে এই section-এ listed specifications-এর বিরুদ্ধে review করা আবশ্যক।

সাধারণ process হলো:

1. applicable CatalystUI specifications শনাক্ত করা হয়।
2. language-টি প্রতিটি required specification-এর বিরুদ্ধে review করা হয়।
3. CatalystUI Team নির্ধারণ করে language-টি specifications-এর intent এবং requirements satisfy করে কি না।
4. language-টি within spec পাওয়া গেলে, তাকে CatalystUI Verification দেওয়া যেতে পারে।
5. verified হলে, language-টি [Verified Languages](/verified/) page-এ listed হতে পারে।

review official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, এবং language requirements পূরণ করে কি না নির্ধারণের জন্য প্রয়োজনীয় অন্যান্য evidence consider করতে পারে।

Compiler এবং runtime behavior review-এর সময় consider করা হতে পারে, যখন সেই behavior language সাধারণভাবে এবং officially যেভাবে ব্যবহৃত হয় তার অংশ। তবে একটি programming language verify করা language ecosystem-এর প্রত্যেক compiler, runtime, package, framework, library, application, বা tool-কে automatically verify করে না।

## Applicable Specifications

এই section-এ listed specifications Programming Language Verification-এর জন্য ব্যবহৃত requirements define করে।

Programming languages-এর জন্য active foundation বর্তমানে নিম্নের specification categories-কেন্দ্রিক:

* **FDEFSPEC**, যা foundational data representations define করে।
* **FRELSPEC**, যা data representations-এর মধ্যে foundational relations define করে।

একসঙ্গে, এই specifications একটি programming language-এর জন্য CatalystUI-compatible systems represent করতে required minimum foundation establish করে।

More specialized verification categories-এর জন্য পরে additional specifications introduce করা হতে পারে। সেই specifications higher-level implementation, platform, accessibility, internationalization, framework, service, বা runtime requirements define করতে পারে। তবে সেই later specifications foundation-কে replace না করে তার উপর build করে।

একটি programming language এই category-র required specifications satisfy করার মাধ্যমে verified হয়। Programming Language Verification-এ সেই requirements যোগ না করা হলে unrelated implementation-specific requirements satisfy করা expected নয়।

## Verification Scope

Programming Languages-এর জন্য CatalystUI Verification reviewed state অনুযায়ী programming language-এর ওপর প্রযোজ্য।

একটি verified language CatalystUI-compatible development-এর জন্য suitable foundation প্রদান করে। এটি guarantee করে না যে সেই language-এ লেখা প্রত্যেক project CatalystUI সঠিকভাবে অনুসরণ করে, এবং surrounding ecosystem-কে automatically verify করে না।

Separate tools, libraries, frameworks, runtimes, applications, services, বা implementations requested verification category অনুযায়ী তাদের নিজস্ব review require করতে পারে।

তাই Programming Language Verification-কে foundation check হিসেবে বোঝা উচিত। এটি confirm করে যে language required concepts represent করতে পারে। এটি confirm করে না যে language-এর প্রত্যেক use সেই concepts সঠিকভাবে apply করে।

## Verification Validity

CatalystUI Verification শুধুমাত্র verification issued হওয়ার সময় programming language-এর reviewed state-এর ওপর প্রযোজ্য।

Programming languages-কে special case হিসেবে বিবেচনা করা হয় কারণ বহু language multiple versions জুড়ে compatibility preserve করে। একটি language পরবর্তী versions জুড়েও verification retain করতে পারে, যতক্ষণ এটি original review যে features, primitives, representations, এবং behavior-এর ওপর নির্ভর করেছিল তার backward compatibility preserve করে।

শুধু new language features verification invalidate করে না। future version নতুন review require করতে পারে কেবল যদি এটি verified foundation remove, break, অথবা substantially change করে।

অন্য কথায়, language extend করা সাধারণত fine। verified base ভেঙে গেলে review require হতে পারে।

## Verified Languages

Known verified programming languages আলাদাভাবে [Verified Languages](/verified/) page-এ listed।
