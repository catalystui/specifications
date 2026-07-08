<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->

<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# Internationalization için CatalystUI Verified

Internationalization için CatalystUI Verification documentation'a hoş geldiniz.

**CatalystUI Verified for Internationalization**, bir sistemin, hizmetin, framework'ün, uygulamanın veya implementation'ın CatalystUI Team tarafından incelendiğini ve required CatalystUI internationalization language set için yeterli multilingual support sağladığının bulunduğunu belirtir.

Bu verification, çeviri kalitesi, yazım üslubu, localization depth veya cultural adaptation için genel bir sıralama değildir. Bunun yerine, reviewed system'in kullanıcıların essential functionality'ye required supported languages genelinde erişebilmesi için kararlı ve pratik bir foundation sağlayıp sağlamadığını belirler.

Daha basit ifadeyle, bu verification kullanıcıların bir sistemin essential parts'ını required languages içinde anlamlı biçimde kullanıp kullanamadığını ve anladıkları dili seçmeleri için makul bir yol sağlanıp sağlanmadığını sorar.

<a id="purpose"></a>
## Amaç

Uluslararasılaştırma önemlidir çünkü bir system, essential meaning'i tek bir dilin arkasında kilitliyse broadly accessible kabul edilemez.

CatalystUI clarity, consistency ve human-computer interaction'ın faithful representation'ı etrafında tasarlanmıştır. Dil bu interaction'ın bir parçasıdır. Bir kullanıcı sistemin labels, instructions, warnings, controls, settings veya essential content'ini anlayamıyorsa, underlying functionality teknik olarak çalışsa bile sistem açık iletişim kuramamış olur.

Internationalization Verification, required CatalystUI language set genelinde kullanıcılar için yeterli translated support sağlayan sistemleri belirlemek için vardır. Amaç her optional word, hidden developer message veya nonessential page için mükemmel çeviri talep etmek değildir. Amaç, sistemin essential parts'ının her required language içindeki insanlar tarafından anlaşılıp kullanılabildiğini belirlemektir.

<a id="what-verification-means"></a>
## Verification Ne Anlama Gelir

Bir sistem, bu bölümde listelenen gereksinimlere göre review edildiğinde ve within spec bulunduğunda **CatalystUI Verified for Internationalization** olur.

Verified olmak için bir sistem, her required language içinde sistemin essential user-facing parts'ının %75'inden fazlası için çeviri sağlamalıdır. Ayrıca active language'i değiştirmek için makul bir end-user mechanism sağlamalıdır.

Bir sistemin her internal identifier'ı, developer-facing implementation detail'i, debug string'i, optional marketing page'i veya nonessential support text'i çevirmesi gerekmez. Ancak essential system'i anlamak ve kullanmak için gereken user-facing portions her required language içinde mevcut olmalıdır.

<a id="required-languages"></a>
## Required Languages

Mevcut CatalystUI internationalization language set, global speaker reach, common online usage, multilingual software expectations ve broad regional accessibility needs dahil olmak üzere teknoloji bağlamlarında yaygın olarak ihtiyaç duyulan dillerin pratik review'undan seçilmiştir.

Bu language set her dili, her lehçeyi veya her regional variant'ı temsil etmeyi amaçlamaz. Bunun yerine, dünyanın en yaygın technology-facing language groups'ının çoğunda geniş international usability isteyen sistemler için pratik bir baseline oluşturur.

Mevcut CatalystUI internationalization language set şu locale'leri içerir:

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

Bir sistemin within spec kabul edilebilmesi için listelenen her language group için yeterli essential translation coverage sağlaması gerekir.

Ancak regional variants arasındaki farklar küçük olduğunda ve kullanıcının sistemi anlama veya kullanma yeteneğini materially affect etmediğinde review sırasında makul flexibility uygulanabilir. Örneğin, bir sistem tek bir güçlü English translation sağlıyor ancak her English regional variant'ı ayrı ayrı çevirmiyorsa, essential meaning, navigation, instructions, warnings ve controls missing variants kullanıcıları için açık kaldığı sürece verification için yine de eligible olabilir.

Bu flexibility, missing variant anlamlı karışıklık yaratacaksa, regionally important terminology'i atlayacaksa, locale-sensitive behavior'ı bozacaksa veya kullanıcıların system'in essential parts'ını anlamasını engelleyecekse uygulanmaz.

<a id="essential-translation-coverage"></a>
## Temel Çeviri Kapsamı

Internationalization Verification için **essential translation coverage**, kullanıcının sistemi anlaması, içinde gezinmesi, yapılandırması ve kullanması için makul biçimde ihtiyaç duyduğu bölümleri ifade eder.

Essential parts şunları içerebilir:

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

Bir system, essential user-facing content'inin %75'inden fazlası her required language içinde mevcut olduğunda translation coverage requirement'ı karşılıyor kabul edilir.

Bu eşik vardır çünkü internationalization work büyük, sürekli ve context-dependent olabilir. Bazı nonessential veya lower-priority content çevrilmeden kalsa bile bir system within spec olabilir. Ancak essential experience her required language içinde anlamlı biçimde mevcut olmalıdır.

<a id="language-selection"></a>
## Dil Seçimi

Verified system, end-user'ın active language'i değiştirmesi için makul bir yol sağlamalıdır.

Language selection mechanism kolay bulunabilir, anlaşılır ve technical knowledge gerektirmeden kullanılabilir olmalıdır. Kullanıcıların yalnızca dili değiştirmek için configuration files düzenlemesi, source code değiştirmesi, developer tools yüklemesi veya undocumented behavior'a güvenmesi gerekmemelidir.

Language options gösterilirken sistem her dili hem o dili konuşan kullanıcılar hem de şu anda başka bir selected language kullanan kullanıcılar tarafından anlaşılabilecek şekilde tanımlamalıdır.

Örneğin bir language option şu şekilde gösterilebilir:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Tam formatting değişebilir; ancak amaç aynı kalmalıdır: kullanıcılar kendi dillerini tanıyabilmeli, mümkün olduğunda şu anda gösterilen dil adını anlayabilmeli ve ilişkili locale code'u belirleyebilmelidir.

<a id="what-within-spec-means"></a>
## “Within Spec” Ne Anlama Gelir

Bir system **within spec** kabul edildiğinde, CatalystUI Team'in sistemi manuel olarak review ettiği ve bu verification category tarafından açıklanan internationalization requirements'ı karşıladığı sonucuna varmayı makul bulduğu anlamına gelir.

Bu, tek bir katı implementation pattern gerektirmez. Bir system requirement'ı resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs veya sisteme uygun başka bir stable mechanism aracılığıyla karşılayabilir.

Verification, system'in tek bir belirli translation architecture kullanıp kullanmadığından çok kullanıcıların essential system'e required languages içinde pratik olarak erişebilmesiyle ilgilenir.

<a id="what-verification-does-not-mean"></a>
## Verification Ne Anlama Gelmez

CatalystUI Verified for Internationalization her çevirinin mükemmel, edebî, idiomatic, culturally complete veya her region için legally sufficient olduğunu garanti etmez.

Ayrıca accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance veya regional business requirements'ı, bu konular reviewed internationalization scope içine dahil edilmedikçe otomatik olarak verify etmez.

Bir system güçlü translation coverage sağlayabilir ve yine de accessibility, localization quality, regional compliance veya diğer specialized concerns için ayrı review gerektirebilir.

<a id="why-this-verification-exists"></a>
## Bu Verification Neden Var

Bir user interface ancak kullanıcı ilettiği şeyi anlayabildiğinde yararlıdır.

Birçok system language support iddiasında bulunurken deneyimin yalnızca küçük bir bölümünü çevirir, language selection'ı gizler, önemli messages'ı atlar veya essential workflows'u kısmen çevrilmemiş bırakır. Bu durum confusion oluşturur ve kullanıcıların system'e güvenmesini engeller.

Internationalization Verification daha açık bir standart belirlemek için vardır. Required CatalystUI language set genelinde kullanıcıları desteklemek için ciddi ve pratik çaba gösteren ve kullanıcıların ihtiyaç duydukları dili seçmeleri için makul bir yol sağlayan sistemleri tanımlar.

<a id="verification-scope"></a>
## Verification Kapsamı

CatalystUI Verification for Internationalization, verification verildiği sırada var olduğu haliyle reviewed system, service, framework, application veya implementation için geçerlidir.

Verified system required languages için yeterli essential translation coverage sağlar. Her future page, feature, release, plugin, extension veya third-party integration'ın otomatik olarak within spec olduğunu garanti etmez.

Separate products, modules, services, language packs veya major revisions, istenen verification category'ye bağlı olarak kendi review'larını gerektirebilir.

<a id="verification-validity"></a>
## Verification Geçerliliği

CatalystUI Verification yalnızca verification'ın verildiği sıradaki reviewed state of the system için geçerlidir.

Bir system, verified internationalization foundation'ı koruduğu sürece sonraki updates boyunca verification'ını koruyabilir. Minor wording changes, added translations ve ordinary content updates verification'ı otomatik olarak geçersiz kılmaz.

Bir system required language support'u kaldırırsa, language selection'ı bozarsa, essential translation coverage'ı önemli ölçüde azaltırsa veya internationalization architecture'ını verified behavior'ı etkileyen şekilde değiştirirse yeni review gerekebilir.

Başka bir deyişle, translation support'u iyileştirmek genellikle sorun değildir. Verified multilingual base'i bozmak review gerektirebilir.

<a id="verified-systems"></a>
## Verified Systems

Internationalization için verified olduğu bilinen sistemler uygun CatalystUI Verified page üzerinde ayrı olarak listelenir.
