<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->

<!-- Remova estas linhas em um pull request depois que a tradução for verificada. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Bem-vindo à documentação de CatalystUI Verification para acessibilidade.

**CatalystUI Verified for Accessibility** indica que um service, framework, application, library ou system foi revisado pela CatalystUI Team e considerado razoavelmente utilizável quando um dos três sentidos primários envolvidos em user-interface interaction está individualmente indisponível.

Para esta verificação, a CatalystUI identifica os três primary accessibility senses como **visão**, **som** e **toque**. Um sistema verificado deve preservar acesso razoável à sua essential functionality quando qualquer um desses sentidos estiver indisponível, recorrendo aos sensory domains restantes disponíveis.

Em termos mais simples, esta verificação pergunta se um usuário ainda consegue compreender, navegar e operar de forma significativa as essential parts de um sistema quando não pode depender individualmente de visão, som ou toque.

## Finalidade

Acessibilidade importa porque uma user interface não deve depender inteiramente de uma única sensory pathway quando o mesmo essential meaning pode ser comunicado razoavelmente por outra.

A CatalystUI é projetada em torno do movimento fiel de data entre sistemas e percepção humana. Se informações importantes estão somente visíveis, somente audíveis ou somente disponíveis por toque, o sistema pode se tornar inutilizável para usuários que não podem depender desse sentido. Accessibility Verification existe para identificar sistemas que preservam acesso permitindo que essential information e interaction continuem por alternate sensory routes.

O objetivo não é exigir todo método possível de interação, toda assistive technology ou toda acomodação especializada. O objetivo é determinar se o essential system permanece meaningfully usable quando visão, som ou toque está individualmente indisponível.

## O que a verificação significa

Um sistema se torna **CatalystUI Verified for Accessibility** quando é revisado segundo os requirements listados nesta seção e considerado within spec.

Para ser verificado, um sistema deve permanecer razoavelmente utilizável em cada um dos casos abaixo:

| Sentido indisponível | Comportamento de acessibilidade exigido |
| -------------------- | ----------------------------------------------------------------- |
| Visão                | O sistema deve permanecer razoavelmente utilizável por som e toque. |
| Som                  | O sistema deve permanecer razoavelmente utilizável por visão e toque. |
| Toque                | O sistema deve permanecer razoavelmente utilizável por visão e som. |

Um sistema não precisa oferecer experiências idênticas em todo sensory path. Uma experiência non-visual pode ser mais lenta que uma visual. Uma experiência sound-free pode exigir captions, visual indicators ou outras substitutions. Uma experiência touch-free pode exigir alternate controls, voice interaction, keyboard navigation, pointer navigation ou outros non-touch methods.

O que importa é se a essential functionality permanece accessible, understandable e operable sem exigir o sentido indisponível.

## Essential Functionality

Para Accessibility Verification, **essential functionality** se refere às partes de um sistema que um usuário razoavelmente precisa para compreender, navegar, configurar e operar o sistema.

Essential functionality pode incluir:

* primary navigation
* core workflows
* required controls
* avisos importantes
* erros importantes
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* qualquer interação exigida para uso normal

Um sistema ainda pode estar within spec se recursos decorativos, redundantes, opcionais ou nonessential não estiverem igualmente disponíveis por todo sensory path. Porém, o usuário ainda deve conseguir usar o essential system sem ser bloqueado pelo sentido ausente.

## Visão indisponível

Quando a visão está indisponível, o sistema deve permanecer razoavelmente utilizável por som e toque.

Isso pode incluir spoken output, estrutura compatível com screen reader, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions ou outro método non-visual razoável para comunicar essential information.

Um sistema não deve depender exclusivamente de visual position, color, shape, animation, icons ou layout quando essas informações são necessárias para compreender ou operar essential functionality.

## Som indisponível

Quando o som está indisponível, o sistema deve permanecer razoavelmente utilizável por visão e toque.

Isso pode incluir captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback ou outro método non-auditory razoável para comunicar essential information.

Um sistema não deve depender exclusivamente de sound effects, spoken instructions, alerts, alarms, music cues ou audio-only prompts quando essas informações são necessárias para compreender ou operar essential functionality.

## Toque indisponível

Quando o toque está indisponível, o sistema deve permanecer razoavelmente utilizável por visão e som.

Isso pode incluir voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation ou outro método razoável que não exija touch-based interaction nem tactile perception.

Um sistema não deve depender exclusivamente de touch gestures, haptic feedback, physical texture, vibration, force, pressure ou touch-only controls quando essas interações são necessárias para compreender ou operar essential functionality.

## Domínios sensoriais adicionais

A CatalystUI também reconhece **paladar** e **olfato** como sensory domains. Esses domínios podem ser considerados durante accessibility review quando forem usados de forma significativa pelo sistema.

Paladar e olfato são **inclusive** para verification, ou seja, podem fortalecer ou apoiar uma accessibility review quando fornecem meaningful alternate access ou contexto adicional.

Paladar e olfato atualmente não são **exclusive** para failure, ou seja, um sistema não falha na Accessibility Verification apenas por não fornecer taste-based ou smell-based interaction.

A CatalystUI Accessibility Verification está principalmente preocupada em saber se o sistema permanece razoavelmente utilizável quando visão, som ou toque está individualmente indisponível.

## O que “Within Spec” significa

Quando um sistema é considerado **within spec**, isso significa que a CatalystUI Team revisou manualmente o sistema e considerou razoável concluir que ele satisfaz os accessibility requirements descritos por esta verification category.

Isso não exige um único implementation pattern rígido. Um sistema pode satisfazer accessibility requirements por native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration ou outro stable mechanism apropriado ao sistema.

A verificação se preocupa com a capacidade prática dos usuários acessarem o essential system quando um primary sense está indisponível, não com o uso de uma accessibility architecture específica.

## O que a verificação não significa

CatalystUI Verified for Accessibility não garante que toda possível disability, device, assistive technology, medical condition, legal requirement, regional standard ou specialized use case tenha sido totalmente revisada.

Ela também não verifica automaticamente internationalization, translation quality, typography, localization, regional compliance ou general design quality, a menos que essas questões estejam incluídas no reviewed accessibility scope.

Um sistema pode ser razoavelmente accessible no modelo de acessibilidade da CatalystUI e ainda exigir revisão separada para legal compliance, platform certification, specialized assistive technology support ou outros accessibility standards.

## Por que esta verificação existe

Uma user interface só tem sucesso quando os usuários realmente conseguem usá-la.

Muitos sistemas tratam accessibility como algo posterior, uma checklist ou um technical requirement estreito, em vez de uma parte fundamental de human-computer interaction. A CatalystUI adota uma abordagem mais simples e direta: se um sistema depende da percepção humana, então ele deve preservar essential meaning quando uma primary sensory path estiver indisponível.

Accessibility Verification existe para identificar sistemas que levam essa responsabilidade a sério. Ela reconhece sistemas que fornecem meaningful alternate access, preservam essential functionality e evitam prender usuários atrás de um único sentido exigido.

## Escopo da verificação

CatalystUI Verification for Accessibility se aplica ao reviewed system, service, framework, application, library ou implementation conforme existia no momento em que a verification foi emitida.

Um sistema verificado fornece reasonable accessibility para sua essential functionality nas reviewed conditions. Isso não garante que toda page, feature, release, plugin, extension, third-party integration, device ou platform-specific version futura esteja automaticamente within spec.

Products, modules, services, major revisions ou platform-specific builds separados podem exigir sua própria review, dependendo da verification category solicitada.

## Validade da verificação

CatalystUI Verification se aplica apenas ao reviewed state do sistema no momento em que a verification é emitida.

Um sistema pode manter sua verification em updates posteriores desde que preserve a verified accessibility foundation. Minor wording changes, visual refinements, performance improvements e ordinary content updates não invalidam automaticamente a verification.

Uma nova review pode ser necessária se um sistema remover alternate access paths, quebrar assistive-technology support, alterar substancialmente a essential navigation, remover required accessibility settings ou alterar interaction behavior de modo que afete a verified accessibility foundation.

Em outras palavras, melhorar accessibility geralmente é aceitável. Quebrar o verified access model pode exigir review.

## Sistemas verificados

Sistemas conhecidos verificados para acessibilidade são listados separadamente na página CatalystUI Verified apropriada.
