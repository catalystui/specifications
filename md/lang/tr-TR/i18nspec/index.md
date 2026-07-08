<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->

<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# I18NSPEC

<br/>

> **Uluslararasılaştırma Şartnamesi**<br/>
> Revizyon 1<br/>
> 8 Temmuz 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Burada sunulan tanımlar, gereksinimler ve kavramlar pratik uluslararasılaştırma desteğini açıklar ve serbestçe yeniden ifade edilebilir.

<a id="introduction"></a>
## Giriş

**Internationalization Specification (I18NSPEC)**, CatalystUI ekosistemi içinde çok dilli desteği değerlendirmek için kullanılan temel kavramları, terminolojiyi ve gereksinimleri belirler. Amacı, bir sistemin, hizmetin, framework'ün, uygulamanın veya implementation'ın within spec kabul edilebilmesi için yeterli dil desteği sağlayıp sağlamadığını belirlemeye yönelik açık bir standart sunmaktır.

Uluslararasılaştırma önemlidir çünkü bir user interface, temel anlamı yalnızca tek bir dilde mevcutsa açık şekilde iletişim kuramaz. Bir sistem teknik olarak işlevsel olabilir; ancak kullanıcılar etiketlerini, yönergelerini, kontrollerini, ayarlarını, uyarılarını, hatalarını veya temel iş akışlarını anlayamıyorsa, sistem bu kullanıcılar için anlamlı bir interface sağlamamış olur.

Bu şartname mükemmel çeviri kalitesini, edebî üslubu, kültürel uyarlamayı, yasal uygunluğu veya eksiksiz bölgesel yerelleştirmeyi ölçmeye çalışmaz. Bunun yerine, kullanıcıların bir sistemin temel bölümlerine required CatalystUI locale set genelinde anlamlı biçimde erişebilmesi ve bunları kullanabilmesi için gereken asgari çok dilli temeli tanımlar.

Daha basit bir ifadeyle I18NSPEC üç ana soru sorar:

1. Kullanıcılar sistemin temel bölümlerine her required language içinde erişebiliyor mu?
2. Kullanıcılar anladıkları dili makul biçimde seçebiliyor mu?
3. Sistem, diller arasında kullanılabilir kalmaya yetecek kadar anlamı koruyor mu?

> [!IMPORTANT]
>
> I18NSPEC, verification için uluslararasılaştırma gereksinimlerini tanımlar. Her dil için ayrı bir şartname değildir. Her required locale aynı şartnameye göre kontrol edilir.

<a id="table-of-contents"></a>
## İçindekiler

* [I18NSPEC](#i18nspec)

  * [Giriş](#introduction)
  * [İçindekiler](#table-of-contents)
  * [Uygunluk](#conformance)
  * [Gerekli Locale Seti](#required-locale-set)
  * [Kullanıcıya Yönelik İçerik](#user-facing-content)

    * [Kullanıcıya Yönelik İçerik](#user-facing-content-1)
    * [Temel Kullanıcıya Yönelik İçerik](#essential-user-facing-content)
    * [Kritik Kullanıcıya Yönelik İçerik](#critical-user-facing-content)
    * [Temel Olmayan İçerik](#nonessential-content)
  * [Çeviri Kapsamı](#translation-coverage)

    * [Temel Çeviri Kapsamı](#essential-translation-coverage)
    * [Kapsam Gereksinimi](#coverage-requirement)
    * [Kritik İçerik Gereksinimi](#critical-content-requirement)
  * [Dil Seçimi](#language-selection)

    * [Aktif Locale](#active-locale)
    * [Varsayılan Locale](#default-locale)
    * [Dil Seçimi Mekanizması](#language-selection-mechanism)
    * [Dil Seçenek Etiketleri](#language-option-labels)
  * [Fallback'ler ve Locale Eşdeğerliği](#fallbacks-and-locale-equivalence)

    * [Fallback Locale](#fallback-locale)
    * [Fallback Davranışı](#fallback-behavior)
    * [Locale Eşdeğerliği](#locale-equivalence)
  * [Implementation Gereksinimleri](#implementation-requirements)

    * [Kararlı Çeviri Mekanizması](#stable-translation-mechanism)
    * [Anlamın Korunması](#preservation-of-meaning)
    * [Yöne Duyarlı Diller](#direction-sensitive-languages)
    * [Locale'e Duyarlı Değerler](#locale-sensitive-values)
  * [Verification](#verification)

    * [Within Spec](#within-spec)
    * [Uyarılar](#warnings)
    * [Failure'lar](#failures)
    * [Verification Geçerliliği](#verification-validity)

<a id="conformance"></a>
## Uygunluk

Bir sistem, required locale set içindeki her locale için bu belgede tanımlanan gereksinimleri karşıladığında I18NSPEC ile uyumlu kabul edilir.

Uyumlu bir sistem şunları yapmalıdır:

1. Required locale set içindeki her locale'i desteklemelidir.
2. Her required locale içinde essential user-facing content'in %75'inden fazlası için çevrilmiş içerik sağlamalıdır.
3. Her required locale içinde tüm critical user-facing content için çevrilmiş içerik sağlamalıdır.
4. End-user'ın active locale'i seçebilmesi için makul bir mekanizma sağlamalıdır.
5. Sisteme uygun kararlı bir çeviri mekanizması kullanmalıdır.
6. Çevrilmiş user-facing content'in temel anlamını korumalıdır.
7. Review sırasında locale equivalence kabul edilen durumlar dışında, translation coverage iddiası için fallback content'e güvenmekten kaçınmalıdır.

Bir sistemin bu şartnameye uyması için tek bir belirli implementation pattern kullanması gerekmez. Resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations veya sisteme uygun başka bir stable mechanism kullanabilir.

Verification, tek ve katı bir teknik mimariden çok pratik kullanıcı erişimi ve temel anlam ile ilgilenir.

<a id="required-locale-set"></a>
## Gerekli Locale Seti

Required locale set, CatalystUI Internationalization Verification için incelenmesi gereken dilleri ve bölgesel varyantları tanımlar.

Mevcut required locale set şu locale'leri içerir:

| Locale    | Dil                      |
| --------- | ------------------------ |
| `ar-SA`   | Arapça (Suudi Arabistan) |
| `bn-BD`   | Bengalce (Bangladeş)     |
| `de-DE`   | Almanca (Almanya)        |
| `en-GB`   | İngilizce (Birleşik Krallık) |
| `en-IN`   | İngilizce (Hindistan)    |
| `en-US`   | İngilizce (Amerika Birleşik Devletleri) |
| `es-ES`   | İspanyolca (İspanya)     |
| `es-MX`   | İspanyolca (Meksika)     |
| `fa-IR`   | Farsça (İran)            |
| `fr-FR`   | Fransızca (Fransa)       |
| `hi-IN`   | Hintçe (Hindistan)       |
| `id-ID`   | Endonezce (Endonezya)    |
| `it-IT`   | İtalyanca (İtalya)       |
| `ja-JP`   | Japonca (Japonya)        |
| `ko-KR`   | Korece (Güney Kore)      |
| `nl-NL`   | Felemenkçe (Hollanda)    |
| `pl-PL`   | Lehçe (Polonya)          |
| `pt-BR`   | Portekizce (Brezilya)    |
| `ru-RU`   | Rusça (Rusya)            |
| `tl-PH`   | Tagalogca (Filipinler)   |
| `tr-TR`   | Türkçe (Türkiye)         |
| `uk-UA`   | Ukraynaca (Ukrayna)      |
| `ur-PK`   | Urduca (Pakistan)        |
| `vi-VN`   | Vietnamca (Vietnam)      |
| `zh-CN`   | Çince (Çin)              |
| `zh-Hans` | Çince (Basitleştirilmiş) |

Bir sistemin within spec kabul edilebilmesi için listelenen her locale için yeterli essential translation support sağlaması gerekir.

Required locale set her dili, lehçeyi, bölgeyi veya yazı sistemini temsil etmeyi amaçlamaz. Bunun yerine, teknolojiye yönelik birçok yaygın dil grubu genelinde geniş uluslararası kullanılabilirlik için pratik bir baseline oluşturur.

<a id="user-facing-content"></a>
## Kullanıcıya Yönelik İçerik

<a id="user-facing-content-1"></a>
### Kullanıcıya Yönelik İçerik

User-facing content, bir end-user tarafından algılanması, okunması, duyulması, seçilmesi, anlaşılması veya üzerine eylem yapılması amaçlanan her türlü içeriktir.

User-facing content şunları içerebilir:

* navigation
* labels
* buttons
* menus
* controls
* headings
* dialogs
* settings
* instructions
* prompts
* warnings
* errors
* confirmations
* status messages
* onboarding text
* required help text
* language selection controls
* core workflow content

User-facing content'in görsel olması gerekmez. İçerik kullanıcıya anlam iletiyorsa auditory, tactile, symbolic veya multisensory content de olabilir.

<a id="essential-user-facing-content"></a>
### Temel Kullanıcıya Yönelik İçerik

Essential user-facing content, kullanıcının bir sistemin essential behavior'ını anlaması, içinde gezinmesi, yapılandırması veya kullanması için makul biçimde ihtiyaç duyduğu user-facing content'tir.

Essential user-facing content şunları içerebilir:

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

Bir sistemin I18NSPEC'i karşılaması için her optional page'i, hidden message'ı, internal label'ı veya nonessential text'i çevirmesi gerekmez. Ancak sıradan essential use için gerekli içerik bu şartnamenin gereksinimlerine göre çevrilmelidir.

<a id="critical-user-facing-content"></a>
### Kritik Kullanıcıya Yönelik İçerik

Critical user-facing content, yanlış anlaşılmasının anlamlı kullanımı engelleyebileceği, ciddi bir hata oluşturabileceği veya kullanıcının sonucu anlamadan önemli bir karar vermesine neden olabileceği essential user-facing content'tir.

Critical user-facing content şunları içerebilir:

* language selection controls
* destructive action warnings
* account deletion warnings
* payment confirmations
* purchase confirmations
* privacy choices
* security warnings
* consent prompts
* required safety instructions
* required setup instructions
* required error messages
* core navigation required to reach language settings

Critical user-facing content her required locale için çevrilmelidir.

%75 essential translation coverage eşiği critical content'i çevrilmemiş bırakmak için kullanılmamalıdır.

<a id="nonessential-content"></a>
### Temel Olmayan İçerik

Nonessential content, kullanıcının bir sistemin essential behavior'ını anlaması, içinde gezinmesi, yapılandırması veya kullanması için makul biçimde gerekli olmayan içeriktir.

Nonessential content şunları içerebilir:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* nonessential legal or business text outside the reviewed scope
* third-party content not controlled by the reviewed system

Nonessential content çevrilebilir, ancak essential user understanding veya operation için gerekli hale gelmedikçe I18NSPEC conformance için zorunlu değildir.

<a id="translation-coverage"></a>
## Çeviri Kapsamı

<a id="essential-translation-coverage"></a>
### Temel Çeviri Kapsamı

Essential translation coverage, belirli bir locale için çevrilmiş essential user-facing content miktarıdır.

Coverage, file size, byte count, line count, repository size veya page sayısı yerine meaningful user-facing content units üzerinden değerlendirilmelidir.

Örneğin, temel bir eylemi kontrol eden çevrilmemiş tek bir button, sıradan kullanımı etkilemeyen büyük bir çevrilmemiş optional paragraph'tan daha önemli olabilir.

Translation coverage, kullanıcının reviewed locale içinde essential system'i anlamlı biçimde anlayıp kullanabilmesine göre değerlendirilmelidir.

<a id="coverage-requirement"></a>
### Kapsam Gereksinimi

Bir sistem, bir locale için essential user-facing content'in %75'inden fazlası o locale için çevrildiğinde translation coverage requirement'ı karşılar.

Bir sistem, required locale set içindeki her locale için bu eşiği karşıladığında I18NSPEC coverage requirement'ı karşılar.

Pratik review içinde bu şöyle temsil edilebilir:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

%75 coverage veya daha azına sahip bir locale coverage requirement'ı karşılamaz.

%75'ten fazla coverage'a sahip bir locale, critical user-facing content çevrilmemişse yine de fail edebilir.

<a id="critical-content-requirement"></a>
### Kritik İçerik Gereksinimi

Tüm critical user-facing content her required locale için çevrilmelidir.

Bir veya daha fazla critical user-facing content item eksik, çevrilmemiş, yanıltıcı veya anlamlı biçimde anlaşılır değilse, sistem genel coverage threshold'u karşılasa bile I18NSPEC'te fail edebilir.

Örneğin, genel interface çevrilmiş olsa bile account deletion warning, purchase confirmation, security warning veya language selector çevrilmemiş kalıyorsa, sistem within spec kabul edilmemelidir.

<a id="language-selection"></a>
## Dil Seçimi

<a id="active-locale"></a>
### Aktif Locale

Active locale, kullanıcının deneyimi için şu anda seçilmiş olan locale'dir.

Active locale, hangi translated content'in kullanıcıya gösterilmesi, sağlanması veya başka şekilde iletilmesi gerektiğini belirler.

<a id="default-locale"></a>
### Varsayılan Locale

Default locale, kullanıcı active locale seçmediğinde veya hiçbir user preference mevcut olmadığında kullanılan locale'dir.

Bir sistem default locale tanımlamalıdır.

Default locale belgelenmiş olmalı veya reviewer tarafından makul biçimde çıkarılabilir olmalıdır.

<a id="language-selection-mechanism"></a>
### Dil Seçimi Mekanizması

Uyumlu bir sistem, end-user'ın active locale'i değiştirmesi için makul bir yol sağlamalıdır.

Language selection mechanism, kullanıcının şunları yapmasını gerektirmeden kullanılabilir olmalıdır:

* source code değiştirmek
* developer tools kullanmak
* undocumented configuration files düzenlemek
* unofficial patches yüklemek
* hidden behavior'a güvenmek
* sıradan dil değişiklikleri için support ile iletişime geçmek

Language selection mechanism şunlar aracılığıyla sağlanabilir:

* application settings
* account preferences
* bir language selector
* startup prompt
* browser settings
* operating system settings
* device settings
* end-user tarafından erişilebilir başka uygun bir mekanizma

Mekanizmanın tek bir belirli design pattern izlemesi gerekmez. Kullanıcının desteklenen bir dili makul biçimde seçmesine izin vermelidir.

<a id="language-option-labels"></a>
### Dil Seçenek Etiketleri

Dil seçenekleri gösterilirken, sistem her dili o dili konuşan kullanıcıların anlayabileceği bir şekilde tanımlamalıdır.

Bir language option şunları içerebilir:

* dilin o dildeki adı
* dilin şu anda active language içindeki adı
* locale code
* regional label
* script label

Örneğin:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Tam formatting değişebilir.

Amaç, kullanıcıların kendi dillerini tanıyabilmesi, mümkün olduğunda şu anda gösterilen dil adını anlayabilmesi ve ilişkili locale code'u belirleyebilmesidir.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallback'ler ve Locale Eşdeğerliği

<a id="fallback-locale"></a>
### Fallback Locale

Fallback locale, active locale için translated content mevcut olmadığında kullanılan locale'dir.

Fallback locales kullanılabilirliği korumaya yardımcı olabilir, ancak fallback content active locale için otomatik olarak translated content kabul edilmez.

Örneğin, bir sistem `es-MX` olarak ayarlanmışsa ancak Spanish translation eksik olduğu için `en-US` text gösteriyorsa, bu English text fallback olarak yararlı olabilir; ancak Spanish translation coverage olarak sayılmamalıdır.

<a id="fallback-behavior"></a>
### Fallback Davranışı

Uyumlu bir sistem, localized content mevcut olmadığında fallback behavior kullanabilir.

Fallback behavior bozuk, boş veya yanıltıcı output'tan kaçınmalıdır.

Fallback behavior, required locale için translation coverage'ı yanlış biçimde iddia etmek amacıyla kullanılmamalıdır.

Fallback behavior aşırı, kafa karıştırıcı, belgelenmemişse veya essential content'in required locale içinde çevrilmemiş görünmesine neden oluyorsa bir sistem warning veya failure alabilir.

<a id="locale-equivalence"></a>
### Locale Eşdeğerliği

Locale equivalence, bir çevirinin essential understanding veya operation'ı engellemeden birden fazla locale'e makul biçimde hizmet edebilmesi durumunda ortaya çıkar.

Örneğin, essential meaning her locale'in kullanıcıları için açık kalıyorsa bir sistem `en-US`, `en-GB` ve `en-IN` için tek bir English translation kullanabilir.

Regional differences küçük olduğunda ve essential usability'i materially affect etmediğinde locale equivalence review sırasında kabul edilebilir.

Eksik bir locale anlamlı karışıklık yaratacaksa, önemli regional terminology'i atlayacaksa, essential behavior'ı bozacaksa veya kullanıcıların sistemi anlamasını engelleyecekse locale equivalence kullanılmamalıdır.

Örneğin, bir sistem ilişkili olmayan dillerin aynı writing direction, geographic region, script family veya geniş cultural category paylaşmaları nedeniyle equivalent olduğunu varsaymamalıdır.

Locale equivalence otomatik bir kural değil, review judgment'tır.

<a id="implementation-requirements"></a>
## Implementation Gereksinimleri

<a id="stable-translation-mechanism"></a>
### Kararlı Çeviri Mekanizması

Uyumlu bir sistem, incelenen sisteme uygun stable translation mechanism kullanmalıdır.

Stable translation mechanism, fragile veya undocumented behavior'a dayanmadan translated content'in korunmasına, güncellenmesine, review edilmesine ve genişletilmesine izin vermelidir.

Stable translation mechanism şunları içerebilir:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* başka bir belgelenmiş translation structure

Bir sistem, essential user-facing content'i required translation support'u engelleyecek şekilde hardcode etmekten kaçınmalıdır.

<a id="preservation-of-meaning"></a>
### Anlamın Korunması

Bir çeviri, kullanıcı source language kullanıcılarıyla aynı essential instruction, label, warning, control, setting veya workflow'u makul biçimde anlayabildiğinde anlamı korur.

Bir çevirinin source content ile word-for-word aynı olması gerekmez.

Bir çeviri, aynı essential meaning'i target language içinde iletmek için gerektiğinde word order, grammar, sentence structure, idiom, tone veya phrasing'i değiştirebilir.

Bir çeviri yanıltıcı, eksik, anlamsız, machine-corrupted veya essential use'ı etkileyen biçimde source content'ten anlamlı ölçüde farklıysa review'da fail edebilir.

<a id="direction-sensitive-languages"></a>
### Yöne Duyarlı Diller

Bazı required locales yaygın olarak right-to-left text direction kullanır.

Uyumlu bir sistem, active locale farklı bir text direction kullandığı için essential translated content'in okunmasını, anlaşılmasını, seçilmesini veya üzerinde işlem yapılmasını engellememelidir.

Sistem, direction-sensitive languages için readable ordering'i, punctuation behavior'ı ve control association'ı korumalıdır.

Full visual polish, typography quality, accessibility behavior ve layout refinement ayrı review gerektirebilir. Ancak essential translated content anlamlı biçimde usable kalmalıdır.

<a id="locale-sensitive-values"></a>
### Locale'e Duyarlı Değerler

Locale-sensitive values, anlamı veya okunabilirliği dile, bölgeye, script'e veya kültüre göre değişebilen value'lardır.

Locale-sensitive values şunları içerebilir:

* dates
* times
* numbers
* currencies
* measurements
* plural forms
* grammatical gender
* sorting order
* address formats
* phone number formats

I18NSPEC, bir value sistemi anlamak veya kullanmak için essential olmadıkça her locale-sensitive value'nun eksiksiz localization'ını gerektirmez.

Locale-sensitive values essential olduğunda, sistem bunları active locale kullanıcılarının makul biçimde anlayabileceği şekilde temsil etmelidir.

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

Bir sistem, CatalystUI Team tarafından incelendiğinde ve I18NSPEC'i karşıladığı sonucuna varmak makul olduğunda within spec kabul edilir.

Bir sistem şu durumlarda within spec olabilir:

* her required locale desteklenir
* her required locale için essential user-facing content'in %75'inden fazlası çevrilmiştir
* her required locale için tüm critical user-facing content çevrilmiştir
* kullanıcılar active locale'i makul biçimde seçebilir
* fallback behavior translation coverage'ı yanlış iddia etmez
* locale equivalence kullanıldıysa makul ve belgelenmiştir
* translated content essential meaning'i korur

Bazı nonessential content çevrilmeden kalsa bile bir sistem within spec olabilir.

Çeviriler mükemmel olmasa bile essential meaning korunuyorsa ve bu şartnamenin gereksinimleri karşılanıyorsa bir sistem within spec olabilir.

<a id="warnings"></a>
### Uyarılar

Bir sistem I18NSPEC'i karşılıyor gibi görünürken belgelenmesi gereken concerns içeriyorsa warning verilebilir.

Warnings şunları içerebilir:

* küçük çevrilmemiş nonessential content
* locale'ler arasında tutarsız terminology
* mükemmel olmayan ama anlaşılır çeviriler
* belgelenmesi gereken kabul edilebilir locale equivalence
* sınırlı fallback behavior
* kısmen çevrilmiş optional pages
* essential use'ı engellemeyen direction-sensitive layout concerns
* anlaşılır ama ideal olmayan locale-sensitive values

Warnings verification'ı zorunlu olarak engellemez.

<a id="failures"></a>
### Failure'lar

Bir sistem I18NSPEC'in bir veya daha fazla required condition'ını karşılamadığında failure oluşur.

Failures şunları içerebilir:

* required locale için eksik support
* required locale için %75 veya altında essential translation coverage
* çevrilmemiş critical user-facing content
* makul language selection mechanism olmaması
* language selection'ın source code modification gerektirmesi
* language selection'ın developer tools gerektirmesi
* bozuk translation loading
* yanıltıcı locale claims
* aşırı fallback behavior
* valid locale equivalence olmadan translated content olarak sayılan fallback content
* okunamaz veya kullanılamaz direction-sensitive content
* bir veya daha fazla required locale içinde unavailable olan essential workflows

Failures, çözülene kadar verification'ı engeller.

<a id="verification-validity"></a>
### Verification Geçerliliği

I18NSPEC verification yalnızca verification'ın verildiği andaki reviewed state of the system için geçerlidir.

Bir sistem verified internationalization foundation'ı koruduğu sürece sonraki updates boyunca verification'ı koruyabilir.

Minor wording changes, added translations, improved translations ve ordinary content updates verification'ı otomatik olarak geçersiz kılmaz.

Bir sistem şu durumlarda yeni review gerektirebilir:

* required locale support'u kaldırırsa
* language selection'ı bozarsa
* essential translation coverage'ı önemli ölçüde azaltırsa
* yeni essential workflows'u çevrilmemiş bırakırsa
* translated content'i fallback content ile değiştirirse
* translation architecture'ı verified behavior'ı etkileyen şekilde değiştirirse
* reviewed scope'u değiştiren major user-facing changes getirirse

Başka bir deyişle, translation support'u iyileştirmek genellikle sorun değildir.

Verified multilingual foundation'ı bozmak review gerektirebilir.
