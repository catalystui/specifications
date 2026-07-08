<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagapagsalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos mapatunayan ang salin. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified para sa mga Wikang Pamprograma

Maligayang pagdating sa dokumentasyon ng CatalystUI Verification para sa mga wikang pamprograma.

Ang **CatalystUI Verified para sa mga Wikang Pamprograma** ay nangangahulugang sinuri ng CatalystUI Team ang isang wikang pamprograma at nakitang nagbibigay ito ng mga pundasyong representasyon ng data at mga relasyonal na istrukturang kailangan upang maipahayag ang mga sistemang compatible sa CatalystUI.

Ang beripikasyong ito ay hindi pangkalahatang ranggo ng mga wikang pamprograma. Hindi nito hinuhusgahan kung mas mabuti, mas mabilis, mas madali, mas bago, mas popular, o mas masayang gamitin ang isang wika kaysa sa iba. Sa halip, tinutukoy nito kung nagbibigay ang wika ng matatag at praktikal na pundasyon para sa mga espesipikasyong kailangan ng CatalystUI Verification.

Sa mas payak na salita, tinatanong ng beripikasyong ito kung kayang katawanin nang tapat ng isang wikang pamprograma ang pangunahing data at mga ugnayang pinagbabatayan ng CatalystUI.

## Layunin

Ang mga wikang pamprograma ang bumubuo sa representasyonal na pundasyon ng bawat implementasyon ng CatalystUI. Bago masundan ng isang framework, library, runtime, application, o serbisyo ang CatalystUI Stack, ang wikang ginagamit sa pagbuo nito ay dapat may kakayahang ipahayag ang mga pundasyong konseptong pinagbabatayan ng modelo.

Para sa mga wikang pamprograma, pangunahing nangangahulugan ito ng dalawang bagay:

1. Dapat kayang katawanin ng wika ang pundasyong data.
2. Dapat kayang katawanin ng wika ang mga pundasyong ugnayan sa pagitan ng data.

Ang mga usaping ito ay tinutukoy sa pamamagitan ng mga pundasyong espesipikasyon ng CatalystUI. Tinutukoy ng FDEFSPEC ang inaasahang mga pundasyong representasyon ng data. Tinutukoy ng FRELSPEC ang inaasahang mga pundasyong ugnayan sa pagitan ng mga representasyong iyon, kabilang ang collections, memory relationships, operations, threading relationships, at composites.

Ang beripikadong wikang pamprograma ay nagbibigay sa mga developer ng sapat na linaw at kontrol upang makabuo ng mga sistemang compatible sa CatalystUI nang hindi umaasa sa marupok, malabo, o hindi matatag na workaround para sa mga pangunahing konseptong kailangan ng CatalystUI.

## Ano ang Ibig Sabihin ng Beripikasyon

Nagiging **CatalystUI Verified** ang isang wikang pamprograma kapag nasuri ito laban sa mga espesipikasyong nakalista sa seksyong ito at napatunayang within spec.

Para sa Programming Language Verification, nakatuon ang pagsusuri sa kung kaya ng wika na ipahayag ang mga pundasyong requirement na tinukoy ng mga naaangkop na espesipikasyon. Hindi ibig sabihin nito na ang wika mismo ay isang implementasyon ng CatalystUI. Ibig sabihin nito, nagbibigay ang wika ng angkop na pundasyon kung saan maaaring bumuo ng mga implementasyong compatible sa CatalystUI.

Hindi kailangang tugunan ng isang wika ang mga requirement na ito sa parehong paraan ng ibang wika. Iba-iba ang syntax, type system, standard library, compiler, runtime, at design pattern ng bawat wika. Pinapayagan ng CatalystUI Verification ang mga pagkakaibang iyon basta maipahayag nang malinaw, maaasahan, at consistent ang mga kinakailangang konsepto.

## Ano ang Ibig Sabihin ng “Within Spec”

Kapag itinuturing na **within spec** ang isang wikang pamprograma, ibig sabihin ay manu-manong sinuri ng CatalystUI Team ang wika at makatuwirang napagpasyahan na ang kinakailangang behavior na inilalarawan ng mga naaangkop na espesipikasyon ay maaaring ipahayag sa wikang iyon.

Hindi nito kailangan ang iisang mahigpit na pattern ng implementasyon. Maaaring matugunan ng isang wika ang requirement sa pamamagitan ng built-in primitives, standard library features, compiler behavior, runtime behavior, documented guarantees, o iba pang matatag na mekanismong angkop sa wikang iyon.

Ang mahalaga sa beripikasyon ay ang praktikal na kakayahang katawanin at panatilihin ang kahulugan ng espesipikasyon, hindi kung ginagamit ba ng wika ang eksaktong parehong mga pangalan, istruktura, syntax, o panloob na disenyo gaya ng teksto ng espesipikasyon.

## Bakit Umiiral ang Beripikasyong Ito

Idinisenyo ang CatalystUI sa paligid ng linaw, consistency, at tapat na representasyon ng paraan ng pakikipag-ugnayan ng tao at computer. Mahalaga ang mga wikang pamprograma dahil tinutukoy nila kung ano ang realistiko at kayang ipahayag ng mga developer, gaano kaligtas mamodelo ang mga sistemang iyon, at gaano kalinaw mabubuo ang mas mataas na antas ng implementasyon.

Kung hindi kayang ibigay ng isang wika ang kinakailangang mga pundasyong konsepto sa matatag na paraan, nagiging mas mahirap pagkatiwalaan ang mas mataas na antas ng mga implementasyon ng CatalystUI. Maaaring mapilitan ang mga developer sa malalabong abstraction, hindi mahulaang behavior, marurupok na dependency, o hindi kailangang rewrite para lang maipahayag ang mga ideyang dapat ay maaasahan na mula sa simula.

Umiiral ang Programming Language Verification upang tukuyin kung aling mga wika ang nagbibigay ng sapat na matibay na pundasyon para sa CatalystUI work. Nagbibigay ito sa mga developer, designer ng wika, at organisasyon ng mas malinaw na pagkaunawa kung ang isang wika ay angkop sa pagbuo ng mga sistemang compatible sa CatalystUI.

## How a Language Becomes Verified

To become **CatalystUI Verified for Programming Languages**, a language must be reviewed against the specifications listed in this section.

The general process is:

1. The applicable CatalystUI specifications are identified.
2. The language is reviewed against each required specification.
3. The CatalystUI Team determines whether the language satisfies the intent and requirements of the specifications.
4. If the language is found to be within spec, it may be granted CatalystUI Verification.
5. Once verified, the language may be listed on the [Verified Languages](/verified/) page.

The review may consider official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, and other evidence needed to determine whether the language meets the requirements.

Compiler and runtime behavior may be considered during review when that behavior is part of how the language is commonly and officially used. However, verifying a programming language does not automatically verify every compiler, runtime, package, framework, library, application, or tool in that language’s ecosystem.

## Applicable Specifications

The specifications listed in this section define the requirements used for Programming Language Verification.

For programming languages, the active foundation is currently centered on the following specification categories:

* **FDEFSPEC**, which defines foundational data representations.
* **FRELSPEC**, which defines foundational relations between data representations.

Together, these specifications establish the minimum foundation required for a programming language to represent CatalystUI-compatible systems.

Additional specifications may be introduced later for more specialized verification categories. Those specifications may define higher-level implementation, platform, accessibility, internationalization, framework, service, or runtime requirements. However, those later specifications build on the foundation rather than replacing it.

A programming language becomes verified by satisfying the required specifications for this category. It is not expected to satisfy unrelated implementation-specific requirements unless those requirements are added to Programming Language Verification.

## Saklaw ng Beripikasyon

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable foundation for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, services, or implementations may require their own review depending on the verification category being requested.

Programming Language Verification should therefore be understood as a foundation check. It confirms that the language can represent the required concepts. It does not confirm that every use of the language applies those concepts correctly.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

New language features alone do not invalidate verification. A future version may require a new review only if it removes, breaks, or substantially changes the verified foundation.

In other words, extending a language is usually fine. Breaking the verified base may require review.

## Mga Beripikadong Wika

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
