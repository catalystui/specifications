<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagasalin. -->

<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos ma-verify ang salin. -->

# I18NSPEC

<br/>

> **Ispesipikasyon ng Internasyonalisasyon**<br/>
> Rebisyon 1<br/>
> Hulyo 8, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Ang mga depinisyon, kinakailangan, at konseptong inilalahad dito ay naglalarawan ng praktikal na suporta sa internasyonalisasyon at maaaring malayang ipahayag muli.

<a id="introduction"></a>
## Panimula

Itinatatag ng **Internationalization Specification (I18NSPEC)** ang mga pangunahing konsepto, terminolohiya, at kinakailangang ginagamit upang suriin ang multilingual support sa loob ng ecosystem ng CatalystUI. Layunin nitong magbigay ng malinaw na pamantayan para matukoy kung ang isang system, serbisyo, framework, application, o implementation ay nagbibigay ng sapat na suporta sa wika upang maituring na within spec.

Mahalaga ang internasyonalisasyon dahil hindi malinaw na makikipagkomunikasyon ang isang user interface kung ang mahahalagang kahulugan nito ay nasa iisang wika lamang. Maaaring gumagana ang isang system sa teknikal na paraan, ngunit kung hindi nauunawaan ng mga user ang mga label, instruction, control, setting, babala, error, o pangunahing workflow nito, hindi nito naibibigay ang isang makabuluhang interface para sa mga user na iyon.

Hindi sinusubukan ng ispesipikasyong ito na sukatin ang perpektong kalidad ng salin, istilong pampanitikan, cultural adaptation, legal compliance, o ganap na regional localization. Sa halip, tinutukoy nito ang pinakamababang multilingual foundation na kailangan upang makahulugan na ma-access at mapatakbo ng mga user ang mahahalagang bahagi ng isang system sa buong required CatalystUI locale set.

Sa mas simpleng salita, tatlong pangunahing tanong ang itinatanong ng I18NSPEC:

1. Maa-access ba ng mga user ang mahahalagang bahagi ng system sa bawat required language?
2. Makakapili ba nang makatwiran ang mga user ng wikang nauunawaan nila?
3. Napapanatili ba ng system ang sapat na kahulugan sa iba’t ibang wika upang manatili itong usable?

> [!IMPORTANT]
>
> Tinutukoy ng I18NSPEC ang mga kinakailangan sa internasyonalisasyon para sa verification. Hindi ito hiwalay na ispesipikasyon para sa bawat wika. Sinusuri ang bawat required locale laban sa parehong ispesipikasyon.

<a id="table-of-contents"></a>
## Talaan ng Nilalaman

* [I18NSPEC](#i18nspec)

  * [Panimula](#introduction)
  * [Talaan ng Nilalaman](#table-of-contents)
  * [Conformance](#conformance)
  * [Required Locale Set](#required-locale-set)
  * [Nilalamang Nakaharap sa User](#user-facing-content)

    * [Nilalamang Nakaharap sa User](#user-facing-content-1)
    * [Mahalagang Nilalamang Nakaharap sa User](#essential-user-facing-content)
    * [Kritikal na Nilalamang Nakaharap sa User](#critical-user-facing-content)
    * [Hindi Mahalagang Nilalaman](#nonessential-content)
  * [Coverage ng Salin](#translation-coverage)

    * [Mahalagang Coverage ng Salin](#essential-translation-coverage)
    * [Kinakailangan sa Coverage](#coverage-requirement)
    * [Kinakailangan sa Kritikal na Nilalaman](#critical-content-requirement)
  * [Pagpili ng Wika](#language-selection)

    * [Active Locale](#active-locale)
    * [Default Locale](#default-locale)
    * [Mekanismo sa Pagpili ng Wika](#language-selection-mechanism)
    * [Mga Label ng Opsyon sa Wika](#language-option-labels)
  * [Mga Fallback at Locale Equivalence](#fallbacks-and-locale-equivalence)

    * [Fallback Locale](#fallback-locale)
    * [Fallback Behavior](#fallback-behavior)
    * [Locale Equivalence](#locale-equivalence)
  * [Mga Kinakailangan sa Implementation](#implementation-requirements)

    * [Stable Translation Mechanism](#stable-translation-mechanism)
    * [Pagpapanatili ng Kahulugan](#preservation-of-meaning)
    * [Mga Wikang Sensitibo sa Direksyon](#direction-sensitive-languages)
    * [Mga Value na Sensitibo sa Locale](#locale-sensitive-values)
  * [Verification](#verification)

    * [Within Spec](#within-spec)
    * [Mga Babala](#warnings)
    * [Mga Failure](#failures)
    * [Validity ng Verification](#verification-validity)

<a id="conformance"></a>
## Conformance

Itinuturing na conformant sa I18NSPEC ang isang system kapag natutugunan nito ang mga kinakailangang tinutukoy ng dokumentong ito para sa bawat locale sa required locale set.

Ang isang conforming system ay dapat:

1. Suportahan ang bawat locale sa required locale set.
2. Magbigay ng naisaling nilalaman para sa higit sa 75% ng essential user-facing content sa bawat required locale.
3. Magbigay ng naisaling nilalaman para sa lahat ng critical user-facing content sa bawat required locale.
4. Magbigay ng makatwirang mekanismo para mapili ng end-user ang active locale.
5. Gumamit ng stable translation mechanism na angkop sa system.
6. Panatilihin ang mahalagang kahulugan ng translated user-facing content.
7. Iwasang umasa sa fallback content upang angkinin ang translation coverage, maliban kung tinanggap ang locale equivalence sa panahon ng review.

Hindi kailangang gumamit ang isang system ng iisang tiyak na implementation pattern upang umayon sa ispesipikasyong ito. Maaari itong gumamit ng resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations, o iba pang stable mechanism na angkop sa system.

Ang verification ay nakatuon sa praktikal na access ng user at mahalagang kahulugan, hindi sa iisang mahigpit na teknikal na arkitektura.

<a id="required-locale-set"></a>
## Required Locale Set

Tinutukoy ng required locale set ang mga wika at regional variants na kailangang suriin para sa CatalystUI Internationalization Verification.

Kasama sa kasalukuyang required locale set ang mga sumusunod na locale:

| Locale    | Wika                     |
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

Dapat magbigay ang isang system ng sapat na essential translation support para sa bawat nakalistang locale upang maituring na within spec.

Hindi nilalayon ng required locale set na katawanin ang bawat wika, dayalekto, rehiyon, o script. Sa halip, nagtatatag ito ng praktikal na baseline para sa malawak na international usability sa maraming karaniwang technology-facing language group.

<a id="user-facing-content"></a>
## Nilalamang Nakaharap sa User

<a id="user-facing-content-1"></a>
### Nilalamang Nakaharap sa User

Ang user-facing content ay anumang nilalaman na nilalayong maramdaman, mabasa, marinig, mapili, maunawaan, o pagkilosan ng isang end-user.

Maaaring kabilang sa user-facing content ang:

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

Hindi kailangang visual ang user-facing content. Maaari rin itong maging auditory, tactile, symbolic, o multisensory content kapag ang nilalamang iyon ay nagpaparating ng kahulugan sa user.

<a id="essential-user-facing-content"></a>
### Mahalagang Nilalamang Nakaharap sa User

Ang essential user-facing content ay user-facing content na makatuwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, o mapatakbo ang essential behavior ng isang system.

Maaaring kabilang sa essential user-facing content ang:

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

Hindi kailangang isalin ng system ang bawat optional page, hidden message, internal label, o nonessential text upang matugunan ang I18NSPEC. Gayunman, ang nilalamang kailangan para sa ordinaryong essential use ay dapat isalin ayon sa mga kinakailangan ng ispesipikasyong ito.

<a id="critical-user-facing-content"></a>
### Kritikal na Nilalamang Nakaharap sa User

Ang critical user-facing content ay essential user-facing content kung saan ang maling pagkaunawa ay maaaring pumigil sa makahulugang paggamit, lumikha ng seryosong error, o magdulot sa user na gumawa ng mahalagang pasya nang hindi nauunawaan ang kahihinatnan.

Maaaring kabilang sa critical user-facing content ang:

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

Dapat maisalin ang critical user-facing content para sa bawat required locale.

Hindi dapat gamitin ang 75% essential translation coverage threshold upang maiwang hindi naisalin ang critical content.

<a id="nonessential-content"></a>
### Hindi Mahalagang Nilalaman

Ang nonessential content ay nilalamang hindi makatuwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, o mapatakbo ang essential behavior ng isang system.

Maaaring kabilang sa nonessential content ang:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* nonessential legal or business text outside the reviewed scope
* third-party content not controlled by the reviewed system

Maaaring isalin ang nonessential content, ngunit hindi ito kinakailangan para sa I18NSPEC conformance maliban kung nagiging kailangan ito para sa essential user understanding o operation.

<a id="translation-coverage"></a>
## Coverage ng Salin

<a id="essential-translation-coverage"></a>
### Mahalagang Coverage ng Salin

Ang essential translation coverage ay ang dami ng essential user-facing content na naisalin para sa isang partikular na locale.

Dapat suriin ang coverage sa pamamagitan ng meaningful user-facing content units sa halip na file size, byte count, line count, repository size, o bilang ng pages.

Halimbawa, maaaring mas mahalaga ang isang hindi naisaling button na kumokontrol sa essential action kaysa sa malaking hindi naisaling optional paragraph na hindi nakakaapekto sa ordinaryong paggamit.

Dapat hatulan ang translation coverage batay sa kung makahulugan bang nauunawaan at napapatakbo ng user ang essential system sa reviewed locale.

<a id="coverage-requirement"></a>
### Kinakailangan sa Coverage

Natutugunan ng isang system ang translation coverage requirement para sa isang locale kapag higit sa 75% ng essential user-facing content ay naisalin para sa locale na iyon.

Natutugunan ng isang system ang I18NSPEC coverage requirement kapag natutugunan nito ang threshold na ito para sa bawat locale sa required locale set.

Sa praktikal na review, maaaring katawanin ito bilang:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

Ang locale na may 75% coverage o mas mababa ay hindi nakakatugon sa coverage requirement.

Ang locale na may higit sa 75% coverage ay maaari pa ring bumagsak kung hindi naisalin ang critical user-facing content.

<a id="critical-content-requirement"></a>
### Kinakailangan sa Kritikal na Nilalaman

Dapat maisalin ang lahat ng critical user-facing content para sa bawat required locale.

Maaaring bumagsak ang isang system sa I18NSPEC kahit natutugunan nito ang general coverage threshold kung may isa o higit pang critical user-facing content item na nawawala, hindi naisalin, nakakalito, o hindi makahulugang nauunawaan.

Halimbawa, hindi dapat ituring na within spec ang isang system kung naisalin ang pangkalahatang interface ngunit nananatiling hindi naisalin ang account deletion warning, purchase confirmation, security warning, o language selector.

<a id="language-selection"></a>
## Pagpili ng Wika

<a id="active-locale"></a>
### Active Locale

Ang active locale ay ang locale na kasalukuyang napili para sa karanasan ng user.

Tinutukoy ng active locale kung aling translated content ang dapat ipakita, ibigay, o ipabatid sa user sa ibang paraan.

<a id="default-locale"></a>
### Default Locale

Ang default locale ay ang locale na ginagamit kapag hindi pa pumipili ang user ng active locale o kapag walang available na user preference.

Dapat magtakda ang isang system ng default locale.

Dapat dokumentado ang default locale o makatuwirang mahinuha ng reviewer.

<a id="language-selection-mechanism"></a>
### Mekanismo sa Pagpili ng Wika

Dapat magbigay ang isang conforming system ng makatwirang paraan para baguhin ng end-user ang active locale.

Dapat maging available ang language selection mechanism nang hindi kinakailangang ang user ay:

* magbago ng source code
* gumamit ng developer tools
* mag-edit ng undocumented configuration files
* mag-install ng unofficial patches
* umasa sa hidden behavior
* makipag-ugnayan sa support para sa ordinaryong pagbabago ng wika

Maaaring ibigay ang language selection mechanism sa pamamagitan ng:

* application settings
* account preferences
* isang language selector
* startup prompt
* browser settings
* operating system settings
* device settings
* isa pang angkop na mekanismong naa-access ng end-user

Hindi kailangang sumunod ang mekanismo sa iisang tiyak na design pattern. Dapat nitong makatwirang payagan ang user na pumili ng supported language.

<a id="language-option-labels"></a>
### Mga Label ng Opsyon sa Wika

Kapag ipinapakita ang language options, dapat tukuyin ng system ang bawat wika sa paraang nauunawaan ng mga user na nagsasalita ng wikang iyon.

Maaaring kabilang sa isang language option ang:

* pangalan ng wika sa wikang iyon
* pangalan ng wika sa kasalukuyang active language
* locale code
* regional label
* script label

Halimbawa:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Maaaring mag-iba ang eksaktong formatting.

Ang layunin ay dapat makilala ng mga user ang sarili nilang wika, maunawaan ang kasalukuyang ipinapakitang pangalan ng wika kapag maaari, at matukoy ang kaugnay na locale code.

<a id="fallbacks-and-locale-equivalence"></a>
## Mga Fallback at Locale Equivalence

<a id="fallback-locale"></a>
### Fallback Locale

Ang fallback locale ay locale na ginagamit kapag hindi available ang translated content para sa active locale.

Maaaring makatulong ang fallback locales upang mapanatili ang usability, ngunit hindi awtomatikong itinuturing na translated content para sa active locale ang fallback content.

Halimbawa, kung ang system ay naka-set sa `es-MX` ngunit nagpapakita ng `en-US` text dahil nawawala ang Spanish translation, maaaring kapaki-pakinabang ang English text bilang fallback, ngunit hindi ito dapat bilangin bilang Spanish translation coverage.

<a id="fallback-behavior"></a>
### Fallback Behavior

Maaaring gumamit ang isang conforming system ng fallback behavior kapag hindi available ang localized content.

Dapat iwasan ng fallback behavior ang sira, walang laman, o nakakalitong output.

Hindi dapat gamitin ang fallback behavior upang maling angkinin ang translation coverage para sa isang required locale.

Maaaring makatanggap ang isang system ng warning o failure kung labis, nakakalito, hindi dokumentado, o nagdudulot ang fallback behavior na lumitaw na hindi naisalin ang essential content sa isang required locale.

<a id="locale-equivalence"></a>
### Locale Equivalence

Nangyayari ang locale equivalence kapag ang isang salin ay makatuwirang makapagsilbi sa higit sa isang locale nang hindi pinipigilan ang essential understanding o operation.

Halimbawa, maaaring gumamit ang isang system ng iisang English translation para sa `en-US`, `en-GB`, at `en-IN` kung nananatiling malinaw ang essential meaning para sa mga user ng bawat locale.

Maaaring tanggapin ang locale equivalence sa panahon ng review kapag maliit ang regional differences at hindi materyal na nakakaapekto sa essential usability.

Hindi dapat gamitin ang locale equivalence kapag ang nawawalang locale ay lilikha ng makabuluhang kalituhan, mag-iiwan ng mahalagang regional terminology, sisira sa essential behavior, o pipigil sa mga user na maunawaan ang system.

Halimbawa, hindi dapat ipagpalagay ng system na equivalent ang magkakahiwalay na wika dahil pareho ang writing direction, geographic region, script family, o malawak na cultural category.

Ang locale equivalence ay review judgment, hindi automatic rule.

<a id="implementation-requirements"></a>
## Mga Kinakailangan sa Implementation

<a id="stable-translation-mechanism"></a>
### Stable Translation Mechanism

Dapat gumamit ang isang conforming system ng stable translation mechanism na angkop sa system na sinusuri.

Dapat payagan ng stable translation mechanism na mapanatili, ma-update, ma-review, at mapalawak ang translated content nang hindi umaasa sa fragile o undocumented behavior.

Maaaring kabilang sa stable translation mechanism ang:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* isa pang dokumentadong translation structure

Dapat iwasan ng isang system ang hardcoding ng essential user-facing content sa paraang pumipigil sa required translation support.

<a id="preservation-of-meaning"></a>
### Pagpapanatili ng Kahulugan

Napapanatili ng isang salin ang kahulugan kapag makatuwirang nauunawaan ng user ang parehong essential instruction, label, warning, control, setting, o workflow gaya ng mga user ng source language.

Hindi kailangang word-for-word na magkapareho ang salin sa source content.

Maaaring baguhin ng salin ang word order, grammar, sentence structure, idiom, tono, o phrasing kapag kailangan upang maiparating ang parehong essential meaning sa target language.

Maaaring bumagsak sa review ang isang salin kung ito ay nakakalito, hindi kumpleto, walang saysay, machine-corrupted, o makabuluhang naiiba sa source content sa paraang nakakaapekto sa essential use.

<a id="direction-sensitive-languages"></a>
### Mga Wikang Sensitibo sa Direksyon

May ilang required locales na karaniwang gumagamit ng right-to-left text direction.

Hindi dapat pigilan ng isang conforming system na mabasa, maunawaan, mapili, o magawan ng aksyon ang essential translated content dahil gumagamit ang active locale ng ibang text direction.

Dapat panatilihin ng system ang nababasang ordering, punctuation behavior, at control association para sa direction-sensitive languages.

Maaaring kailanganin ng hiwalay na review ang full visual polish, typography quality, accessibility behavior, at layout refinement. Gayunman, dapat manatiling makahulugang usable ang essential translated content.

<a id="locale-sensitive-values"></a>
### Mga Value na Sensitibo sa Locale

Ang locale-sensitive values ay mga value na maaaring mag-iba ang kahulugan o readability batay sa wika, rehiyon, script, o kultura.

Maaaring kabilang sa locale-sensitive values ang:

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

Hindi hinihingi ng I18NSPEC ang kumpletong localization ng bawat locale-sensitive value maliban kung mahalaga ang value na iyon sa pag-unawa o pagpapatakbo ng system.

Kapag mahalaga ang locale-sensitive values, dapat katawanin ng system ang mga ito sa paraang makatuwirang mauunawaan ng mga user ng active locale.

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

Itinuturing na within spec ang isang system kapag nasuri ito ng CatalystUI Team at makatuwirang napagpasyahang natutugunan nito ang I18NSPEC.

Maaaring within spec ang isang system kapag:

* sinusuportahan ang bawat required locale
* higit sa 75% ng essential user-facing content ay naisalin para sa bawat required locale
* lahat ng critical user-facing content ay naisalin para sa bawat required locale
* makatuwirang makakapili ang mga user ng active locale
* hindi ginagamit ang fallback behavior upang maling angkinin ang translation coverage
* ang locale equivalence, kung ginamit, ay makatwiran at dokumentado
* pinapanatili ng translated content ang essential meaning

Maaaring within spec ang isang system kahit may ilang nonessential content na nananatiling hindi naisalin.

Maaaring within spec ang isang system kahit hindi perpekto ang mga salin, basta napapanatili ang essential meaning at natutugunan ang mga kinakailangan ng ispesipikasyong ito.

<a id="warnings"></a>
### Mga Babala

Maaaring maglabas ng warning kapag ang isang system ay mukhang natutugunan ang I18NSPEC ngunit may mga concern na dapat idokumento.

Maaaring kabilang sa warnings ang:

* minor untranslated nonessential content
* inconsistent terminology across locales
* hindi perpekto ngunit nauunawaang mga salin
* katanggap-tanggap na locale equivalence na dapat idokumento
* limitadong fallback behavior
* partially translated optional pages
* direction-sensitive layout concerns na hindi pumipigil sa essential use
* locale-sensitive values na nauunawaan ngunit hindi ideal

Hindi palaging pinipigilan ng warnings ang verification.

<a id="failures"></a>
### Mga Failure

Nangyayari ang failure kapag hindi natutugunan ng isang system ang isa o higit pang required conditions ng I18NSPEC.

Maaaring kabilang sa failures ang:

* nawawalang support para sa isang required locale
* essential translation coverage na nasa 75% o mas mababa para sa isang required locale
* hindi naisaling critical user-facing content
* walang makatwirang language selection mechanism
* language selection na nangangailangan ng source code modification
* language selection na nangangailangan ng developer tools
* sirang translation loading
* nakakalitong locale claims
* labis na fallback behavior
* fallback content na binilang bilang translated content nang walang valid locale equivalence
* direction-sensitive content na hindi mabasa o hindi magamit
* essential workflows na hindi available sa isa o higit pang required locales

Pinipigilan ng failures ang verification hanggang maresolba ang mga ito.

<a id="verification-validity"></a>
### Validity ng Verification

Nalalapat lamang ang I18NSPEC verification sa reviewed state ng system sa oras na ibinigay ang verification.

Maaaring mapanatili ng isang system ang verification sa mga susunod na update hangga’t pinapanatili nito ang verified internationalization foundation.

Hindi awtomatikong ini-invalidate ng minor wording changes, added translations, improved translations, at ordinary content updates ang verification.

Maaaring kailanganin ang bagong review kung ang isang system ay:

* nag-aalis ng required locale support
* sumisira sa language selection
* malaking binabawasan ang essential translation coverage
* nag-iiwan ng bagong essential workflows na hindi naisalin
* nagpapalit ng translated content ng fallback content
* nagbabago ng translation architecture sa paraang nakakaapekto sa verified behavior
* nagpapakilala ng malalaking user-facing changes na nagbabago sa reviewed scope

Sa madaling salita, karaniwang ayos lang ang pagpapabuti ng translation support.

Ang pagsira sa verified multilingual foundation ay maaaring mangailangan ng review.
