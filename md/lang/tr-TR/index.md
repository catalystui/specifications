<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->

<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

CatalystUI Verification belgelerinin accessibility bölümüne hoş geldiniz.

**CatalystUI Verified for Accessibility**, bir service, framework, application, library veya system’ın CatalystUI Team tarafından incelendiğini ve user-interface interaction içinde yer alan üç temel duyudan biri tek başına kullanılamadığında makul ölçüde kullanılabilir kalmaya devam ettiğinin belirlendiğini gösterir.

Bu verification için CatalystUI üç primary accessibility senses öğesini **görme**, **ses** ve **dokunma** olarak tanımlar. Verified system, bu duyulardan herhangi biri kullanılamadığında, kalan available sensory domains üzerinden essential functionality için reasonable access sağlamalıdır.

Daha basit şekilde, bu verification bir user’ın görme, ses veya dokunmaya tek tek güvenemediği durumda system’ın essential parts bölümünü hâlâ anlamlı biçimde anlayıp anlayamadığını, gezip gezemediğini ve çalıştırıp çalıştıramadığını sorar.

## Amaç

Accessibility önemlidir, çünkü bir user interface aynı essential meaning makul şekilde başka bir yolla iletilebiliyorsa tek bir sensory pathway’e tamamen bağlı olmamalıdır.

CatalystUI, data’nın systems ile human perception arasında sadık biçimde hareket etmesi üzerine tasarlanmıştır. Önemli bilgi yalnızca görünür, yalnızca duyulur veya yalnızca dokunma yoluyla available ise, system o duyuya güvenemeyen users için unusable hâle gelebilir. Accessibility Verification, essential information ve interaction’ın alternate sensory routes üzerinden devam etmesine izin vererek access’i koruyan systems’ı belirlemek için vardır.

Amaç her olası interaction method, her assistive technology veya her specialized accommodation’ı zorunlu kılmak değildir. Amaç, görme, ses veya dokunma tek tek unavailable olduğunda essential system’ın meaningfully usable kalıp kalmadığını belirlemektir.

## Verification Ne Anlama Gelir

Bir system, bu bölümde listelenen requirements’a göre incelenip within spec bulunduğunda **CatalystUI Verified for Accessibility** olur.

Verified olmak için bir system aşağıdaki durumların her birinde makul ölçüde kullanılabilir kalmalıdır:

| Kullanılamayan Duyu | Gerekli Accessibility Behavior |
| ------------------- | ------------------------------ |
| Görme               | System ses ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır. |
| Ses                 | System görme ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır. |
| Dokunma             | System görme ve ses yoluyla makul ölçüde kullanılabilir kalmalıdır. |

Bir system’ın her sensory path üzerinde identical experiences sağlaması gerekmez. Non-visual experience, visual olandan daha yavaş olabilir. Sound-free experience captions, visual indicators veya diğer substitutions gerektirebilir. Touch-free experience alternate controls, voice interaction, keyboard navigation, pointer navigation veya diğer non-touch methods gerektirebilir.

Önemli olan, essential functionality’nin unavailable sense gerektirmeden accessible, understandable ve operable kalıp kalmadığıdır.

## Essential Functionality

Accessibility Verification için **essential functionality**, bir user’ın system’ı anlamak, navigate etmek, configure etmek ve operate etmek için makul olarak ihtiyaç duyduğu bölümleri ifade eder.

Essential functionality şunları içerebilir:

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
* normal kullanım için required olan herhangi bir interaction

Decorative, redundant, optional veya nonessential features her sensory path üzerinden eşit şekilde available değilse bir system yine within spec olabilir. Ancak user, missing sense nedeniyle essential system’ı kullanmaktan engellenmemelidir.

## Görme Kullanılamadığında

Görme unavailable olduğunda system ses ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır.

Bu spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions veya essential information’ı ileten başka bir reasonable non-visual method içerebilir.

Bir system, essential functionality’yi anlamak veya operate etmek için gerekli olan bilgide yalnızca visual position, color, shape, animation, icons veya layout’a güvenmemelidir.

## Ses Kullanılamadığında

Ses unavailable olduğunda system görme ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır.

Bu captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback veya essential information’ı ileten başka bir reasonable non-auditory method içerebilir.

Bir system, essential functionality’yi anlamak veya operate etmek için gerekli olan bilgide yalnızca sound effects, spoken instructions, alerts, alarms, music cues veya audio-only prompts’a güvenmemelidir.

## Dokunma Kullanılamadığında

Dokunma unavailable olduğunda system görme ve ses yoluyla makul ölçüde kullanılabilir kalmalıdır.

Bu voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation veya touch-based interaction ya da tactile perception gerektirmeyen başka bir reasonable method içerebilir.

Bir system, essential functionality’yi anlamak veya operate etmek için gerekli interaction’larda yalnızca touch gestures, haptic feedback, physical texture, vibration, force, pressure veya touch-only controls’a güvenmemelidir.

## Ek Sensory Domains

CatalystUI ayrıca **tat** ve **koku**yu sensory domains olarak tanır. System bunları anlamlı biçimde kullanıyorsa accessibility review sırasında dikkate alınabilirler.

Tat ve koku verification için **inclusive** kabul edilir; yani meaningful alternate access veya ek context sağladıklarında accessibility review’u güçlendirebilir veya destekleyebilirler.

Tat ve koku şu anda failure için **exclusive** değildir; yani bir system taste-based veya smell-based interaction sağlamadığı için tek başına Accessibility Verification’dan kalmaz.

CatalystUI Accessibility Verification öncelikle system’ın görme, ses veya dokunma tek tek unavailable olduğunda makul ölçüde kullanılabilir kalıp kalmadığıyla ilgilenir.

## “Within Spec” Ne Anlama Gelir

Bir system **within spec** kabul edildiğinde, CatalystUI Team’in system’ı manuel olarak incelediği ve bu verification category tarafından açıklanan accessibility requirements’ı karşıladığını makul biçimde sonuçlandırdığı anlamına gelir.

Bu, tek bir katı implementation pattern gerektirmez. Bir system accessibility requirements’ı native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration veya system’a uygun başka bir stable mechanism ile karşılayabilir.

Verification, system’ın belirli bir accessibility architecture kullanıp kullanmadığından çok, bir primary sense unavailable olduğunda users’ın essential system’a pratik olarak erişebilmesiyle ilgilenir.

## Verification Ne Anlama Gelmez

CatalystUI Verified for Accessibility, her olası disability, device, assistive technology, medical condition, legal requirement, regional standard veya specialized use case’in tamamen incelendiğini garanti etmez.

Ayrıca bu konular reviewed accessibility scope içine alınmadıkça internationalization, translation quality, typography, localization, regional compliance veya general design quality’yi otomatik olarak verify etmez.

Bir system CatalystUI’nin accessibility modeline göre makul ölçüde accessible olabilir ve yine de legal compliance, platform certification, specialized assistive technology support veya başka accessibility standards için ayrı review gerektirebilir.

## Bu Verification Neden Var

Bir user interface ancak users onu gerçekten kullanabildiğinde başarılıdır.

Birçok system accessibility’yi human-computer interaction’ın temel bir parçası yerine afterthought, checklist veya dar bir technical requirement olarak ele alır. CatalystUI daha basit ve daha doğrudan bir approach benimser: Bir system human perception’a bağlıysa, bir primary sensory path unavailable olduğunda essential meaning’i korumalıdır.

Accessibility Verification bu sorumluluğu ciddiye alan systems’ı belirlemek için vardır. Meaningful alternate access sağlayan, essential functionality’yi koruyan ve users’ı tek bir required sense arkasına hapsetmeyen systems’ı tanır.

## Verification Scope

CatalystUI Verification for Accessibility, verification verildiği anda mevcut olan reviewed system, service, framework, application, library veya implementation için geçerlidir.

Verified system, reviewed conditions altında essential functionality’si için reasonable accessibility sağlar. Bu, her future page, feature, release, plugin, extension, third-party integration, device veya platform-specific version’ın otomatik olarak within spec olduğunu garanti etmez.

Separate products, modules, services, major revisions veya platform-specific builds, istenen verification category’ye bağlı olarak kendi review sürecini gerektirebilir.

## Verification Validity

CatalystUI Verification yalnızca verification verildiği anda system’ın reviewed state’i için geçerlidir.

Bir system, verified accessibility foundation’ı koruduğu sürece sonraki updates boyunca verification’ını koruyabilir. Minor wording changes, visual refinements, performance improvements ve ordinary content updates verification’ı otomatik olarak geçersiz kılmaz.

System alternate access paths’i kaldırırsa, assistive-technology support’u bozarsa, essential navigation’ı substantial biçimde değiştirirse, required accessibility settings’i kaldırırsa veya interaction behavior’ı verified accessibility foundation’ı etkileyecek şekilde değiştirirse yeni review gerekebilir.

Başka bir deyişle, accessibility’yi iyileştirmek genellikle sorun değildir. Verified access model’ı bozmak review gerektirebilir.

## Verified Systems

Accessibility için verified olduğu bilinen systems, ilgili CatalystUI Verified page üzerinde ayrı olarak listelenir.
