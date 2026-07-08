<!-- یہ ترجمہ ChatGPT کے ذریعے تیار کیا گیا ہے اور اسے کسی انسانی مترجم سے نظرثانی کروانی چاہیے۔ -->

<!-- ترجمے کی تصدیق کے بعد pull request میں یہ سطریں ہٹا دیں۔ -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Internationalization کے لیے CatalystUI Verification documentation میں خوش آمدید۔

**CatalystUI Verified for Internationalization** یہ ظاہر کرتا ہے کہ کسی system، service، framework، application، یا implementation کا CatalystUI Team نے review کیا ہے اور اسے required CatalystUI internationalization language set کے لیے کافی multilingual support فراہم کرنے والا پایا ہے۔

یہ verification translation quality، writing style، localization depth، یا cultural adaptation کی عمومی درجہ بندی نہیں ہے۔ اس کے بجائے یہ دیکھتا ہے کہ reviewed system صارفین کو required supported languages میں essential functionality تک رسائی کے لیے ایک stable اور practical foundation فراہم کرتا ہے یا نہیں۔

آسان الفاظ میں، یہ verification پوچھتا ہے کہ کیا صارفین required languages میں system کے essential parts کو meaningfully استعمال کر سکتے ہیں، اور کیا انہیں اپنی سمجھ میں آنے والی language منتخب کرنے کا reasonable way دیا گیا ہے۔

<a id="purpose"></a>
## مقصد

Internationalization اس لیے اہم ہے کیونکہ کوئی system broadly accessible نہیں سمجھا جا سکتا اگر اس کا essential meaning صرف ایک language کے پیچھے بند ہو۔

CatalystUI کو clarity، consistency، اور human-computer interaction کی faithful representation کے گرد ڈیزائن کیا گیا ہے۔ Language اس interaction کا حصہ ہے۔ اگر صارف system کے labels، instructions، warnings، controls، settings، یا essential content کو نہیں سمجھ سکتا، تو system واضح communication میں ناکام رہا ہے، چاہے underlying functionality تکنیکی طور پر کام کر رہی ہو۔

Internationalization Verification ان systems کی شناخت کے لیے ہے جو required CatalystUI language set میں صارفین کے لیے کافی translated support فراہم کرتے ہیں۔ مقصد ہر optional word، hidden developer message، یا nonessential page کا perfect translation مانگنا نہیں ہے۔ مقصد یہ طے کرنا ہے کہ system کے essential parts ہر required language کے لوگوں کے لیے سمجھے اور استعمال کیے جا سکتے ہیں یا نہیں۔

<a id="what-verification-means"></a>
## Verification کا مطلب

کوئی system **CatalystUI Verified for Internationalization** تب بنتا ہے جب اس section میں درج requirements کے مطابق اس کا review کیا جائے اور اسے within spec پایا جائے۔

Verified ہونے کے لیے system کو ہر required language میں system کے essential user-facing parts کے 75% سے زیادہ کے translations فراہم کرنے چاہئیں۔ اسے active language تبدیل کرنے کے لیے ایک reasonable end-user mechanism بھی فراہم کرنا چاہیے۔

System کو ہر internal identifier، developer-facing implementation detail، debug string، optional marketing page، یا nonessential support text ترجمہ کرنے کی ضرورت نہیں۔ تاہم essential system کو سمجھنے اور operate کرنے کے لیے required user-facing portions ہر required language میں available ہونے چاہئیں۔

<a id="required-languages"></a>
## Required Languages

موجودہ CatalystUI internationalization language set کو technology contexts میں عام طور پر درکار languages کے practical review سے منتخب کیا گیا ہے، جس میں global speaker reach، common online usage، multilingual software expectations، اور broad regional accessibility needs شامل ہیں۔

یہ language set ہر language، ہر dialect، یا ہر regional variant کی نمائندگی کے لیے نہیں ہے۔ اس کے بجائے یہ دنیا کے بہت سے عام technology-facing language groups میں broad international usability چاہنے والے systems کے لیے ایک practical baseline قائم کرتا ہے۔

موجودہ CatalystUI internationalization language set میں درج ذیل locales شامل ہیں:

| Locale    | زبان                     |
| --------- | ------------------------ |
| `ar-SA`   | عربی (سعودی عرب)         |
| `bn-BD`   | بنگالی (بنگلہ دیش)       |
| `de-DE`   | جرمن (جرمنی)             |
| `en-GB`   | انگریزی (برطانیہ)        |
| `en-IN`   | انگریزی (بھارت)          |
| `en-US`   | انگریزی (ریاستہائے متحدہ) |
| `es-ES`   | ہسپانوی (اسپین)          |
| `es-MX`   | ہسپانوی (میکسیکو)        |
| `fa-IR`   | فارسی (ایران)            |
| `fr-FR`   | فرانسیسی (فرانس)         |
| `hi-IN`   | ہندی (بھارت)             |
| `id-ID`   | انڈونیشیائی (انڈونیشیا)  |
| `it-IT`   | اطالوی (اٹلی)            |
| `ja-JP`   | جاپانی (جاپان)           |
| `ko-KR`   | کوریائی (جنوبی کوریا)    |
| `nl-NL`   | ڈچ (نیدرلینڈز)           |
| `pl-PL`   | پولش (پولینڈ)            |
| `pt-BR`   | پرتگالی (برازیل)         |
| `ru-RU`   | روسی (روس)               |
| `tl-PH`   | ٹیگالاگ (فلپائن)         |
| `tr-TR`   | ترکی (ترکیہ)             |
| `uk-UA`   | یوکرینی (یوکرین)         |
| `ur-PK`   | اردو (پاکستان)           |
| `vi-VN`   | ویتنامی (ویتنام)         |
| `zh-CN`   | چینی (چین)               |
| `zh-Hans` | چینی (آسان رسم الخط)     |

System کو within spec سمجھنے کے لیے ہر listed language group کے لیے کافی essential translation coverage فراہم کرنا چاہیے۔

تاہم regional variants کا review reasonable flexibility کے ساتھ کیا جا سکتا ہے جب variants کے درمیان فرق minor ہوں اور user کی system کو understand یا operate کرنے کی ability پر materially affect نہ کریں۔ مثال کے طور پر، اگر کوئی system ایک مضبوط English translation فراہم کرتا ہے لیکن ہر English regional variant کو الگ translate نہیں کرتا، تو وہ verification کے لیے پھر بھی eligible ہو سکتا ہے، بشرطیکہ essential meaning، navigation، instructions، warnings، اور controls missing variants کے users کے لیے clear رہیں۔

یہ flexibility اس وقت apply نہیں ہوتی جب missing variant meaningful confusion پیدا کرے، regionally important terminology چھوڑ دے، locale-sensitive behavior کو break کرے، یا users کو system کے essential parts سمجھنے سے روکے۔

<a id="essential-translation-coverage"></a>
## Essential Translation Coverage

Internationalization Verification کے لیے **essential translation coverage** سے مراد system کے وہ حصے ہیں جن کی user کو reasonably ضرورت ہوتی ہے تاکہ وہ system کو understand، navigate، configure، اور operate کر سکے۔

Essential parts میں شامل ہو سکتے ہیں:

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

System کو translation coverage requirement پورا سمجھا جاتا ہے جب اس کے essential user-facing content کا 75% سے زیادہ ہر required language میں available ہو۔

یہ threshold اس لیے ہے کیونکہ internationalization work بڑی، ongoing، اور context-dependent ہو سکتی ہے۔ کوئی system پھر بھی within spec ہو سکتا ہے اگر کچھ nonessential یا lower-priority content untranslated رہے۔ تاہم essential experience ہر required language میں meaningfully available ہونی چاہیے۔

<a id="language-selection"></a>
## Language Selection

Verified system کو end-user کے لیے active language تبدیل کرنے کا reasonable way فراہم کرنا چاہیے۔

Language selection mechanism آسانی سے ملنے والا، سمجھ میں آنے والا، اور technical knowledge کے بغیر available ہونا چاہیے۔ Users کو صرف language بدلنے کے لیے configuration files edit کرنے، source code modify کرنے، developer tools install کرنے، یا undocumented behavior پر rely کرنے کی ضرورت نہیں ہونی چاہیے۔

Language options دکھاتے وقت system کو ہر language اس طرح identify کرنی چاہیے جو اس language بولنے والے users اور currently selected دوسری language استعمال کرنے والے users دونوں کے لیے understandable ہو۔

مثال کے طور پر language option یوں دکھایا جا سکتا ہے:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Exact formatting مختلف ہو سکتی ہے، مگر intent وہی رہنا چاہیے: users اپنی language recognize کر سکیں، ممکن ہو تو currently displayed language name سمجھ سکیں، اور associated locale code identify کر سکیں۔

<a id="what-within-spec-means"></a>
## “Within Spec” کا مطلب

جب کوئی system **within spec** سمجھا جاتا ہے، اس کا مطلب ہے CatalystUI Team نے system کا manually review کیا ہے اور یہ conclusion reasonable پایا ہے کہ system اس verification category میں بیان کردہ internationalization requirements کو satisfy کرتا ہے۔

اس کے لیے one rigid implementation pattern required نہیں۔ System resource files، translation tables، locale-aware routing، compiled language assets، database-backed translations، runtime language packs، یا system کے لیے مناسب کسی دوسرے stable mechanism کے ذریعے requirement satisfy کر سکتا ہے۔

Verification users کی practical ability سے متعلق ہے کہ وہ required languages میں essential system تک access حاصل کر سکیں، نہ کہ اس بات سے کہ system کوئی one specific translation architecture استعمال کرتا ہے۔

<a id="what-verification-does-not-mean"></a>
## Verification کا مطلب یہ نہیں

CatalystUI Verified for Internationalization یہ guarantee نہیں کرتا کہ ہر translation perfect، literary، idiomatic، culturally complete، یا ہر region کے لیے legally sufficient ہے۔

یہ accessibility، typography، right-to-left layout، locale-specific formatting، currency formatting، date formatting، legal compliance، یا regional business requirements کو بھی automatically verify نہیں کرتا، جب تک یہ concerns reviewed internationalization scope میں شامل نہ ہوں۔

System strong translation coverage فراہم کر سکتا ہے اور پھر بھی accessibility، localization quality، regional compliance، یا دیگر specialized concerns کے لیے separate review کی ضرورت ہو سکتی ہے۔

<a id="why-this-verification-exists"></a>
## یہ Verification کیوں موجود ہے

User interface تبھی useful ہے جب user سمجھ سکے کہ وہ کیا communicate کر رہا ہے۔

بہت سے systems language support کا دعویٰ کرتے ہیں مگر experience کا صرف چھوٹا حصہ translate کرتے ہیں، language selection چھپاتے ہیں، important messages چھوڑ دیتے ہیں، یا essential workflows کو partially untranslated چھوڑ دیتے ہیں۔ یہ confusion پیدا کرتا ہے اور users کو system پر trust کرنے سے روکتا ہے۔

Internationalization Verification ایک clearer standard مقرر کرنے کے لیے موجود ہے۔ یہ ان systems کی شناخت کرتا ہے جو required CatalystUI language set میں users کو support کرنے کے لیے serious، practical effort کرتے ہیں اور users کو اپنی needed language select کرنے کا reasonable way فراہم کرتے ہیں۔

<a id="verification-scope"></a>
## Verification Scope

CatalystUI Verification for Internationalization reviewed system، service، framework، application، یا implementation پر اسی state میں apply ہوتی ہے جس میں verification issue ہونے کے وقت وہ موجود تھا۔

Verified system required languages کے لیے کافی essential translation coverage فراہم کرتا ہے۔ یہ guarantee نہیں کرتا کہ ہر future page، feature، release، plugin، extension، یا third-party integration automatically within spec ہے۔

Separate products، modules، services، language packs، یا major revisions کو requested verification category کے لحاظ سے اپنا review درکار ہو سکتا ہے۔

<a id="verification-validity"></a>
## Verification Validity

CatalystUI Verification صرف system کی reviewed state پر apply ہوتی ہے، اس وقت جب verification issue کی جاتی ہے۔

System later updates کے بعد verification retain کر سکتا ہے جب تک وہ verified internationalization foundation کو preserve کرتا ہے۔ Minor wording changes، added translations، اور ordinary content updates verification کو automatically invalidate نہیں کرتے۔

New review اس وقت required ہو سکتا ہے جب system required language support remove کرے، language selection break کرے، essential translation coverage کو substantially reduce کرے، یا internationalization architecture کو اس طرح change کرے کہ verified behavior affect ہو۔

دوسرے الفاظ میں، translation support improve کرنا عموماً ٹھیک ہے۔ Verified multilingual base کو break کرنا review require کر سکتا ہے۔

<a id="verified-systems"></a>
## Verified Systems

Internationalization کے لیے known verified systems مناسب CatalystUI Verified page پر الگ listed ہوتے ہیں۔
