<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagasalin. -->

<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos ma-verify ang salin. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Maligayang pagdating sa dokumentasyon ng CatalystUI Verification para sa accessibility.

Ipinapahiwatig ng **CatalystUI Verified for Accessibility** na ang isang service, framework, application, library, o system ay nirepaso ng CatalystUI Team at napatunayang nananatiling makatwirang nagagamit kapag ang isa sa tatlong pangunahing pandamang kasangkot sa user-interface interaction ay hindi available nang paisa-isa.

Para sa verification na ito, tinutukoy ng CatalystUI ang tatlong pangunahing accessibility senses bilang **paningin**, **tunog**, at **haplos**. Dapat mapanatili ng isang verified system ang makatwirang access sa essential functionality nito kapag alinman sa mga pandamang ito ay hindi available, sa pamamagitan ng pag-asa sa natitirang available sensory domains.

Sa mas simpleng salita, tinatanong ng verification na ito kung ang isang user ay maaari pa ring makahulugang makaunawa, makapag-navigate, at makapagpatakbo ng mahahalagang bahagi ng isang system kung hindi siya makaaasa sa paningin, tunog, o haplos nang paisa-isa.

## Layunin

Mahalaga ang accessibility dahil ang user interface ay hindi dapat lubos na nakadepende sa isang sensory pathway kapag ang parehong essential meaning ay makatwirang maipapahayag sa ibang paraan.

Idinisenyo ang CatalystUI sa tapat na paggalaw ng data sa pagitan ng systems at human perception. Kung ang mahalagang impormasyon ay nakikita lamang, naririnig lamang, o available lamang sa pamamagitan ng haplos, maaaring maging unusable ang system para sa mga user na hindi makaaasa sa pandamang iyon. Umiiral ang Accessibility Verification upang tukuyin ang mga system na nagpapanatili ng access sa pamamagitan ng pagpapahintulot sa essential information at interaction na magpatuloy sa alternate sensory routes.

Ang layunin ay hindi ang i-require ang bawat posibleng interaction method, bawat assistive technology, o bawat specialized accommodation. Ang layunin ay tukuyin kung nananatiling meaningfully usable ang essential system kapag ang paningin, tunog, o haplos ay hindi available nang paisa-isa.

## Ano ang Ibig Sabihin ng Verification

Nagiging **CatalystUI Verified for Accessibility** ang isang system kapag nirepaso ito laban sa requirements na nakalista sa seksyong ito at napatunayang within spec.

Upang ma-verify, dapat manatiling makatwirang nagagamit ang isang system sa bawat sumusunod na kaso:

| Hindi Available na Pandama | Kinakailangang Accessibility Behavior |
| -------------------------- | ------------------------------------- |
| Paningin                   | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng tunog at haplos. |
| Tunog                      | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at haplos. |
| Haplos                     | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at tunog. |

Hindi kailangang magbigay ang isang system ng magkakaparehong experiences sa bawat sensory path. Maaaring mas mabagal ang non-visual experience kaysa sa visual. Maaaring mangailangan ang sound-free experience ng captions, visual indicators, o iba pang substitutions. Maaaring mangailangan ang touch-free experience ng alternate controls, voice interaction, keyboard navigation, pointer navigation, o iba pang non-touch methods.

Ang mahalaga ay kung nananatiling accessible, understandable, at operable ang essential functionality nang hindi nire-require ang unavailable sense.

## Essential Functionality

Para sa Accessibility Verification, ang **essential functionality** ay tumutukoy sa mga bahagi ng isang system na makatwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, at mapatakbo ang system.

Maaaring kabilang sa essential functionality ang:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* anumang interaction na kailangan para sa normal na paggamit

Maaaring within spec pa rin ang isang system kung ang decorative, redundant, optional, o nonessential features ay hindi pantay na available sa bawat sensory path. Gayunpaman, dapat pa ring magamit ng user ang essential system nang hindi nahaharangan ng nawawalang pandama.

## Hindi Available ang Paningin

Kapag hindi available ang paningin, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng tunog at haplos.

Maaaring kabilang dito ang spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions, o ibang makatwirang non-visual method para ipahayag ang essential information.

Hindi dapat umasa nang eksklusibo ang isang system sa visual position, color, shape, animation, icons, o layout kapag kailangan ang impormasyong iyon upang maunawaan o mapatakbo ang essential functionality.

## Hindi Available ang Tunog

Kapag hindi available ang tunog, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at haplos.

Maaaring kabilang dito ang captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback, o ibang makatwirang non-auditory method para ipahayag ang essential information.

Hindi dapat umasa nang eksklusibo ang isang system sa sound effects, spoken instructions, alerts, alarms, music cues, o audio-only prompts kapag kailangan ang impormasyong iyon upang maunawaan o mapatakbo ang essential functionality.

## Hindi Available ang Haplos

Kapag hindi available ang haplos, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at tunog.

Maaaring kabilang dito ang voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation, o ibang makatwirang method na hindi nangangailangan ng touch-based interaction o tactile perception.

Hindi dapat umasa nang eksklusibo ang isang system sa touch gestures, haptic feedback, physical texture, vibration, force, pressure, o touch-only controls kapag kailangan ang mga interaction na iyon upang maunawaan o mapatakbo ang essential functionality.

## Karagdagang Sensory Domains

Kinikilala rin ng CatalystUI ang **panlasa** at **pang-amoy** bilang sensory domains. Maaaring isaalang-alang ang mga domain na ito sa accessibility review kapag makahulugan ang paggamit ng system sa kanila.

Ang panlasa at pang-amoy ay **inclusive** para sa verification, ibig sabihin maaari nilang palakasin o suportahan ang accessibility review kapag nagbibigay sila ng meaningful alternate access o karagdagang context.

Ang panlasa at pang-amoy ay hindi kasalukuyang **exclusive** para sa failure, ibig sabihin hindi bumabagsak ang isang system sa Accessibility Verification dahil lamang hindi ito nagbibigay ng taste-based o smell-based interaction.

Pangunahing inaalam ng CatalystUI Accessibility Verification kung nananatiling makatwirang nagagamit ang system kapag ang paningin, tunog, o haplos ay hindi available nang paisa-isa.

## Ano ang Ibig Sabihin ng “Within Spec”

Kapag ang isang system ay itinuturing na **within spec**, nangangahulugan ito na manu-manong nirepaso ng CatalystUI Team ang system at napatunayang makatwirang ipalagay na natutugunan nito ang accessibility requirements na inilalarawan ng verification category na ito.

Hindi nito nire-require ang isang matigas na implementation pattern. Maaaring matugunan ng isang system ang accessibility requirements sa pamamagitan ng native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration, o ibang stable mechanism na angkop sa system.

Nakatuon ang verification sa praktikal na kakayahan ng users na ma-access ang essential system kapag ang isang primary sense ay hindi available, hindi sa kung gumagamit ang system ng isang partikular na accessibility architecture.

## Ano ang Hindi Ibig Sabihin ng Verification

Hindi ginagarantiyahan ng CatalystUI Verified for Accessibility na ang bawat posibleng disability, device, assistive technology, medical condition, legal requirement, regional standard, o specialized use case ay ganap nang narepaso.

Hindi rin nito awtomatikong bine-verify ang internationalization, translation quality, typography, localization, regional compliance, o general design quality maliban kung kasama ang mga iyon sa reviewed accessibility scope.

Maaaring maging makatwirang accessible ang isang system sa ilalim ng accessibility model ng CatalystUI at kailangan pa rin ng hiwalay na review para sa legal compliance, platform certification, specialized assistive technology support, o iba pang accessibility standards.

## Bakit Umiiral ang Verification na Ito

Nagiging matagumpay lamang ang user interface kapag talagang nagagamit ito ng users.

Maraming system ang tumuturing sa accessibility bilang afterthought, checklist, o makitid na technical requirement sa halip na fundamental na bahagi ng human-computer interaction. Mas simple at mas direkta ang approach ng CatalystUI: kung ang isang system ay nakadepende sa human perception, dapat nitong panatilihin ang essential meaning kapag ang isang primary sensory path ay hindi available.

Umiiral ang Accessibility Verification upang tukuyin ang mga system na seryosong tinatrato ang responsibilidad na ito. Kinikilala nito ang mga system na nagbibigay ng meaningful alternate access, nagpapanatili ng essential functionality, at umiiwas na ikulong ang users sa likod ng isang required sense.

## Saklaw ng Verification

Nalalapat ang CatalystUI Verification for Accessibility sa reviewed system, service, framework, application, library, o implementation ayon sa kalagayan nito noong inilabas ang verification.

Nagbibigay ang verified system ng reasonable accessibility para sa essential functionality nito sa ilalim ng reviewed conditions. Hindi nito ginagarantiyahan na bawat future page, feature, release, plugin, extension, third-party integration, device, o platform-specific version ay awtomatikong within spec.

Maaaring mangailangan ng sariling review ang hiwalay na products, modules, services, major revisions, o platform-specific builds depende sa verification category na hinihiling.

## Bisa ng Verification

Nalalapat lamang ang CatalystUI Verification sa reviewed state ng system sa oras na inilabas ang verification.

Maaaring panatilihin ng isang system ang verification nito sa mga susunod na updates hangga't pinapanatili nito ang verified accessibility foundation. Hindi awtomatikong nagpapawalang-bisa sa verification ang minor wording changes, visual refinements, performance improvements, at ordinary content updates.

Maaaring kailanganin ang bagong review kung nag-aalis ang system ng alternate access paths, sinisira ang assistive-technology support, malaki ang pagbabago sa essential navigation, inaalis ang required accessibility settings, o binabago ang interaction behavior sa paraang nakaaapekto sa verified accessibility foundation.

Sa madaling salita, karaniwang ayos lang ang pagpapahusay ng accessibility. Ang pagsira sa verified access model ay maaaring mangailangan ng review.

## Verified Systems

Ang mga kilalang system na verified para sa accessibility ay nakalista nang hiwalay sa angkop na CatalystUI Verified page.
