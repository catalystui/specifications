<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# Programming Languages के लिए CatalystUI Verified

Programming languages के लिए CatalystUI Verification दस्तावेज़ों में आपका स्वागत है।

**Programming Languages के लिए CatalystUI Verified** यह दर्शाता है कि किसी programming language की CatalystUI Team द्वारा समीक्षा की गई है और पाया गया है कि वह CatalystUI-compatible systems को व्यक्त करने के लिए आवश्यक foundational data representations और relational structures प्रदान कर सकती है।

यह verification programming languages की कोई सामान्य ranking नहीं है। यह तय नहीं करता कि कोई language दूसरी language से बेहतर, तेज़, आसान, नई, लोकप्रिय, या अधिक आनंददायक है या नहीं। इसके बजाय, यह पहचानता है कि वह language CatalystUI Verification के लिए आवश्यक specifications हेतु एक स्थिर और व्यावहारिक foundation प्रदान करती है या नहीं।

सरल शब्दों में, यह verification पूछता है कि क्या कोई programming language CatalystUI जिन मूल data और relationships पर निर्भर करता है, उन्हें विश्वसनीय रूप से represent कर सकती है।

## उद्देश्य

Programming languages हर CatalystUI implementation के नीचे स्थित representational foundation बनाती हैं। किसी framework, library, runtime, application, या service के CatalystUI Stack का पालन करने से पहले, उसे बनाने में प्रयुक्त language को उन foundational concepts को व्यक्त करने में सक्षम होना चाहिए जिन पर model निर्भर करता है।

Programming languages के लिए, इसका मुख्य अर्थ दो बातें हैं:

1. Language foundational data को represent करने में सक्षम होनी चाहिए।
2. Language data के बीच foundational relationships को represent करने में सक्षम होनी चाहिए।

ये विषय foundational CatalystUI specifications के माध्यम से परिभाषित किए जाते हैं। FDEFSPEC expected foundational data representations को परिभाषित करता है। FRELSPEC उन representations के बीच expected foundational relations को परिभाषित करता है, जिनमें collections, memory relationships, operations, threading relationships, और composites शामिल हैं।

एक verified programming language developers को इतनी clarity और control देती है कि वे CatalystUI-compatible systems बना सकें, बिना उन basic concepts के लिए fragile, unclear, या unstable workarounds पर निर्भर हुए जिनकी CatalystUI को आवश्यकता है।

## Verification का अर्थ

कोई programming language तब **CatalystUI Verified** बनती है जब इस section में listed specifications के विरुद्ध उसकी समीक्षा की जाती है और उसे within spec पाया जाता है।

Programming Language Verification में review इस बात पर केंद्रित होता है कि language applicable specifications द्वारा परिभाषित foundational requirements को व्यक्त कर सकती है या नहीं। इसका अर्थ यह नहीं है कि language स्वयं CatalystUI implementation है। इसका अर्थ है कि language एक उपयुक्त foundation प्रदान करती है, जिससे CatalystUI-compatible implementations बनाई जा सकती हैं।

किसी language को ये requirements किसी दूसरी language की तरह ही पूरी करने की आवश्यकता नहीं है। अलग-अलग languages अलग syntax, type systems, standard libraries, compilers, runtimes, और design patterns का उपयोग करती हैं। CatalystUI Verification इन भिन्नताओं की अनुमति देता है, जब तक required concepts स्पष्ट, विश्वसनीय, और consistent रूप से व्यक्त किए जा सकते हैं।

## “Within Spec” का अर्थ

जब किसी programming language को **within spec** माना जाता है, तो इसका अर्थ है कि CatalystUI Team ने language की manual review की है और यह निष्कर्ष निकालना उचित पाया है कि applicable specifications में वर्णित required behavior उस language में व्यक्त किया जा सकता है।

इसके लिए कोई एक कठोर implementation pattern आवश्यक नहीं है। कोई language built-in primitives, standard library features, compiler behavior, runtime behavior, documented guarantees, या उस language के लिए उपयुक्त किसी अन्य stable mechanism के माध्यम से requirement पूरी कर सकती है।

Verification specification के meaning को represent और preserve करने की practical ability से संबंधित है; यह इस बात से संबंधित नहीं है कि language specification text जैसे exact names, structures, syntax, या internal design का ही उपयोग करती है या नहीं।

## यह Verification क्यों मौजूद है

CatalystUI clarity, consistency, और humans तथा computers के interact करने के तरीके की faithful representation के आधार पर design किया गया है। Programming languages मायने रखती हैं क्योंकि वे निर्धारित करती हैं कि developers वास्तव में क्या express कर सकते हैं, उन systems को कितनी safely model किया जा सकता है, और higher-level implementations कितनी clearly बनाई जा सकती हैं।

यदि कोई language required foundational concepts को stable तरीके से प्रदान नहीं कर सकती, तो higher-level CatalystUI implementations पर भरोसा करना कठिन हो जाता है। Developers को ऐसे ideas व्यक्त करने के लिए unclear abstractions, unpredictable behavior, fragile dependencies, या unnecessary rewrites की ओर धकेला जा सकता है जो शुरुआत से ही reliable होने चाहिए।

Programming Language Verification यह पहचानने के लिए मौजूद है कि कौन-सी languages CatalystUI work के लिए पर्याप्त रूप से मजबूत foundation प्रदान करती हैं। यह developers, language designers, और organizations को यह समझने में सहायता देता है कि कोई language CatalystUI-compatible systems बनाने के लिए उपयुक्त है या नहीं।

## कोई Language Verified कैसे बनती है

**Programming Languages के लिए CatalystUI Verified** बनने के लिए, किसी language की इस section में listed specifications के विरुद्ध review की जानी चाहिए।

सामान्य प्रक्रिया यह है:

1. Applicable CatalystUI specifications की पहचान की जाती है।
2. Language की प्रत्येक required specification के विरुद्ध review की जाती है।
3. CatalystUI Team निर्धारित करती है कि language specifications के intent और requirements को satisfy करती है या नहीं।
4. यदि language within spec पाई जाती है, तो उसे CatalystUI Verification दिया जा सकता है।
5. Verified होने के बाद, language को [Verified Languages](/verified/) page पर सूचीबद्ध किया जा सकता है।

Review में official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, और अन्य evidence पर विचार किया जा सकता है ताकि यह निर्धारित किया जा सके कि language requirements पूरी करती है या नहीं।

Compiler और runtime behavior को review के दौरान तब माना जा सकता है जब वह behavior language के common और official उपयोग का हिस्सा हो। हालांकि, किसी programming language को verify करना उस language के ecosystem में हर compiler, runtime, package, framework, library, application, या tool को automatically verify नहीं करता।

## Applicable Specifications

इस section में listed specifications Programming Language Verification के लिए उपयोग की जाने वाली requirements को परिभाषित करती हैं।

Programming languages के लिए active foundation फिलहाल निम्न specification categories पर केंद्रित है:

* **FDEFSPEC**, जो foundational data representations को परिभाषित करता है।
* **FRELSPEC**, जो data representations के बीच foundational relations को परिभाषित करता है।

साथ मिलकर, ये specifications किसी programming language द्वारा CatalystUI-compatible systems को represent करने के लिए आवश्यक minimum foundation स्थापित करती हैं।

भविष्य में अधिक specialized verification categories के लिए additional specifications introduce की जा सकती हैं। वे specifications higher-level implementation, platform, accessibility, internationalization, framework, service, या runtime requirements को परिभाषित कर सकती हैं। हालांकि, वे बाद की specifications foundation को replace करने के बजाय उसी पर build करती हैं।

Programming language इस category के लिए required specifications को satisfy करके verified बनती है। उससे unrelated implementation-specific requirements को satisfy करने की अपेक्षा नहीं की जाती, जब तक वे requirements Programming Language Verification में जोड़ी न जाएँ।

## Verification Scope

Programming Languages के लिए CatalystUI Verification उस programming language पर लागू होता है जैसी उसकी review की गई है।

Verified language CatalystUI-compatible development के लिए उपयुक्त foundation प्रदान करती है। यह guarantee नहीं देती कि उस language में लिखा गया हर project CatalystUI को सही तरीके से follow करता है, और न ही यह surrounding ecosystem को automatically verify करती है।

Separate tools, libraries, frameworks, runtimes, applications, services, या implementations को requested verification category के आधार पर अपनी अलग review की आवश्यकता हो सकती है।

इसलिए Programming Language Verification को foundation check के रूप में समझना चाहिए। यह पुष्टि करता है कि language required concepts को represent कर सकती है। यह पुष्टि नहीं करता कि language का हर उपयोग उन concepts को सही तरीके से apply करता है।

## Verification Validity

CatalystUI Verification केवल उस समय programming language की reviewed state पर लागू होता है जब verification issue किया जाता है।

Programming languages को special case माना जाता है क्योंकि कई languages कई versions में compatibility बनाए रखती हैं। कोई language बाद के versions में भी अपनी verification बनाए रख सकती है, जब तक वह उन features, primitives, representations, और behavior के साथ backward compatibility preserve करती है जिन पर original review निर्भर थी।

नई language features अकेले verification को invalidate नहीं करतीं। किसी future version को नई review की आवश्यकता केवल तभी हो सकती है जब वह verified foundation को remove, break, या substantially change कर दे।

दूसरे शब्दों में, language को extend करना आम तौर पर ठीक है। Verified base को तोड़ना review की आवश्यकता पैदा कर सकता है।

## Verified Languages

Known verified programming languages अलग से [Verified Languages](/verified/) page पर listed हैं।
