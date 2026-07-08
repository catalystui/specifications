<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagasalin. -->

<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos ma-verify ang salin. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified para sa Internasyonalisasyon

Maligayang pagdating sa CatalystUI Verification documentation para sa internasyonalisasyon.

Ang **CatalystUI Verified for Internationalization** ay nagpapahiwatig na ang isang system, serbisyo, framework, application, o implementation ay na-review ng CatalystUI Team at napatunayang nagbibigay ng sapat na multilingual support para sa required CatalystUI internationalization language set.

Ang verification na ito ay hindi pangkalahatang ranggo ng kalidad ng salin, istilo ng pagsulat, lalim ng localization, o cultural adaptation. Sa halip, tinutukoy nito kung ang reviewed system ay nagbibigay ng stable at praktikal na foundation para ma-access ng mga user ang essential functionality nito sa mga required supported languages.

Sa mas simpleng salita, tinatanong ng verification na ito kung makahulugang magagamit ng mga user ang mahahalagang bahagi ng isang system sa mga required language, at kung binibigyan sila ng makatwirang paraan upang piliin ang wikang nauunawaan nila.

<a id="purpose"></a>
## Layunin

Mahalaga ang internasyonalisasyon dahil hindi maituturing na broadly accessible ang isang system kung ang mahalagang kahulugan nito ay nakakandado sa iisang wika.

Dinisenyo ang CatalystUI sa paligid ng clarity, consistency, at tapat na representation ng human-computer interaction. Bahagi ng interaction na iyon ang wika. Kung hindi nauunawaan ng user ang labels, instructions, warnings, controls, settings, o essential content ng isang system, nabigo ang system na makipagkomunikasyon nang malinaw, kahit gumagana ang underlying functionality sa teknikal na paraan.

Umiiral ang Internationalization Verification upang tukuyin ang mga system na nagbibigay ng sapat na translated support para sa mga user sa required CatalystUI language set. Hindi layunin na hingin ang perpektong salin ng bawat optional word, hidden developer message, o nonessential page. Ang layunin ay matukoy kung mauunawaan at magagamit ng mga tao sa bawat required language ang essential parts ng system.

<a id="what-verification-means"></a>
## Ano ang Kahulugan ng Verification

Nagiging **CatalystUI Verified for Internationalization** ang isang system kapag na-review ito laban sa mga kinakailangan na nakalista sa seksyong ito at napatunayang within spec.

Upang ma-verify, dapat magbigay ang isang system ng mga salin para sa higit sa 75% ng essential user-facing parts ng system sa bawat required language. Dapat din itong magbigay ng makatwirang end-user mechanism para baguhin ang active language.

Hindi kailangang isalin ng system ang bawat internal identifier, developer-facing implementation detail, debug string, optional marketing page, o nonessential support text. Gayunman, ang user-facing portions na kailangan upang maunawaan at mapatakbo ang essential system ay dapat maging available sa bawat required language.

<a id="required-languages"></a>
## Mga Required Language

Pinili ang kasalukuyang CatalystUI internationalization language set mula sa praktikal na review ng mga wikang karaniwang kailangan sa technology contexts, kabilang ang global speaker reach, common online usage, multilingual software expectations, at broad regional accessibility needs.

Hindi nilalayon ng language set na ito na katawanin ang bawat wika, bawat dayalekto, o bawat regional variant. Sa halip, nagtatatag ito ng praktikal na baseline para sa mga system na naghahangad ng malawak na international usability sa maraming pinakakaraniwang technology-facing language group sa mundo.

Kasama sa kasalukuyang CatalystUI internationalization language set ang mga sumusunod na locale:

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

Dapat magbigay ang isang system ng sapat na essential translation coverage para sa bawat nakalistang language group upang maituring na within spec.

Gayunman, maaaring i-review ang regional variants nang may makatwirang flexibility kapag maliit ang pagkakaiba ng variants at hindi materyal na nakakaapekto sa kakayahan ng user na maunawaan o mapatakbo ang system. Halimbawa, maaari pa ring maging eligible para sa verification ang isang system kung nagbibigay ito ng isang malakas na English translation ngunit hindi hiwalay na isinasalin ang bawat English regional variant, basta nananatiling malinaw sa users ng missing variants ang essential meaning, navigation, instructions, warnings, at controls.

Hindi nalalapat ang flexibility na ito kapag ang missing variant ay lilikha ng makabuluhang kalituhan, mag-iiwan ng mahalagang regional terminology, sisira sa locale-sensitive behavior, o pipigil sa users na maunawaan ang essential parts ng system.

<a id="essential-translation-coverage"></a>
## Mahalagang Coverage ng Salin

Para sa Internationalization Verification, tumutukoy ang **essential translation coverage** sa mga bahagi ng isang system na makatuwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, at mapatakbo ang system.

Maaaring kabilang sa essential parts ang:

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

Itinuturing na natutugunan ng system ang translation coverage requirement kapag higit sa 75% ng essential user-facing content nito ay available sa bawat required language.

Umiiral ang threshold na ito dahil maaaring malaki, tuloy-tuloy, at nakadepende sa konteksto ang internationalization work. Maaari pa ring within spec ang isang system kahit may ilang nonessential o lower-priority content na nananatiling hindi naisalin. Gayunman, dapat makahulugang available ang essential experience sa bawat required language.

<a id="language-selection"></a>
## Pagpili ng Wika

Dapat magbigay ang verified system ng makatwirang paraan para baguhin ng end-user ang active language.

Dapat madaling mahanap, maunawaan, at magamit ang language selection mechanism nang hindi nangangailangan ng technical knowledge. Hindi dapat kailanganin ng mga user na mag-edit ng configuration files, magbago ng source code, mag-install ng developer tools, o umasa sa undocumented behavior para lang palitan ang wika.

Kapag ipinapakita ang language options, dapat tukuyin ng system ang bawat wika sa paraang nauunawaan kapwa ng users na nagsasalita ng wikang iyon at ng users na kasalukuyang gumagamit ng ibang selected language.

Halimbawa, maaaring ipakita ang language option gamit ang:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Maaaring mag-iba ang eksaktong formatting, ngunit dapat manatili ang layunin: dapat makilala ng users ang kanilang sariling wika, maunawaan ang kasalukuyang ipinapakitang pangalan ng wika kapag maaari, at matukoy ang kaugnay na locale code.

<a id="what-within-spec-means"></a>
## Ano ang Ibig Sabihin ng “Within Spec”

Kapag itinuturing na **within spec** ang isang system, ibig sabihin ay mano-manong na-review ng CatalystUI Team ang system at makatuwirang napagpasyahang natutugunan nito ang internationalization requirements na inilalarawan ng verification category na ito.

Hindi nito kailangan ang iisang mahigpit na implementation pattern. Maaaring matugunan ng system ang requirement sa pamamagitan ng resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs, o iba pang stable mechanism na angkop sa system.

Nakatuon ang verification sa praktikal na kakayahan ng users na ma-access ang essential system sa required languages, hindi kung gumagamit ang system ng iisang partikular na translation architecture.

<a id="what-verification-does-not-mean"></a>
## Ano ang Hindi Ibig Sabihin ng Verification

Hindi ginagarantiya ng CatalystUI Verified for Internationalization na perpekto, literary, idiomatic, culturally complete, o legally sufficient para sa bawat rehiyon ang bawat salin.

Hindi rin nito awtomatikong vine-verify ang accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance, o regional business requirements maliban kung kasama ang mga concern na iyon sa reviewed internationalization scope.

Maaaring magbigay ang system ng malakas na translation coverage at kailangan pa rin ng hiwalay na review para sa accessibility, localization quality, regional compliance, o iba pang specialized concerns.

<a id="why-this-verification-exists"></a>
## Bakit Umiiral ang Verification na Ito

Kapaki-pakinabang lamang ang user interface kapag nauunawaan ng user ang ipinapahayag nito.

Maraming system ang nagsasabing may language support habang maliit na bahagi lamang ng experience ang isinasalin, nakatago ang language selection, nawawala ang mahahalagang messages, o bahagyang hindi naisalin ang essential workflows. Lumilikha ito ng kalituhan at pumipigil sa users na magtiwala sa system.

Umiiral ang Internationalization Verification upang magtakda ng mas malinaw na pamantayan. Tinutukoy nito ang mga system na gumagawa ng seryoso at praktikal na pagsisikap na suportahan ang users sa required CatalystUI language set at nagbibigay ng makatwirang paraan para piliin ng users ang wikang kailangan nila.

<a id="verification-scope"></a>
## Saklaw ng Verification

Nalalapat ang CatalystUI Verification for Internationalization sa reviewed system, service, framework, application, o implementation ayon sa estado nito noong ibinigay ang verification.

Ang verified system ay nagbibigay ng sapat na essential translation coverage para sa required languages. Hindi nito ginagarantiya na ang bawat future page, feature, release, plugin, extension, o third-party integration ay awtomatikong within spec.

Maaaring kailanganin ng hiwalay na review ang separate products, modules, services, language packs, o major revisions depende sa verification category na hinihiling.

<a id="verification-validity"></a>
## Validity ng Verification

Nalalapat lamang ang CatalystUI Verification sa reviewed state ng system sa oras na ibinigay ang verification.

Maaaring mapanatili ng system ang verification nito sa mga susunod na update hangga’t pinapanatili nito ang verified internationalization foundation. Hindi awtomatikong ini-invalidate ng minor wording changes, added translations, at ordinary content updates ang verification.

Maaaring kailanganin ang bagong review kung ang system ay nag-aalis ng required language support, sumisira sa language selection, malaking binabawasan ang essential translation coverage, o nagbabago ng internationalization architecture sa paraang nakakaapekto sa verified behavior.

Sa madaling salita, karaniwang ayos lang ang pagpapabuti ng translation support. Ang pagsira sa verified multilingual base ay maaaring mangailangan ng review.

<a id="verified-systems"></a>
## Verified Systems

Ang mga kilalang system na verified para sa internationalization ay nakalista nang hiwalay sa naaangkop na CatalystUI Verified page.
