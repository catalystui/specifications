<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->

<!-- Remova estas linhas em um pull request depois que a tradução for verificada. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> As definições, requisitos e conceitos apresentados aqui descrevem suporte prático de acessibilidade e podem ser livremente reexpressos.

<a id="introduction"></a>

## Introdução

A **Accessibility Specification (A11YSPEC)** estabelece os core concepts, terminology e requirements usados para avaliar accessibility support no ecossistema CatalystUI. Sua finalidade é fornecer um standard claro para determinar se um system, service, framework, application, library ou implementation permanece meaningfully usable quando uma primary sensory pathway está indisponível.

Acessibilidade importa porque uma user interface não deve depender inteiramente de um único sentido quando o mesmo essential meaning pode ser comunicado razoavelmente por outro. Um sistema pode ser technically functional, mas se um usuário não consegue compreender, navegar, configurar ou operar seu essential behavior sem visão, som ou toque individualmente, então o sistema falhou em fornecer reasonable access para essa condition.

Esta specification não tenta verificar toda disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard ou specialized use case possível. Em vez disso, define a accessibility foundation mínima necessária para que usuários acessem e operem de modo significativo as essential portions de um sistema quando um dos três primary accessibility senses está indisponível.

Em termos mais simples, A11YSPEC faz três perguntas principais:

1. Os usuários conseguem compreender o essential system sem depender da visão?
2. Os usuários conseguem compreender o essential system sem depender do som?
3. Os usuários conseguem operar o essential system sem depender do toque?

> [!IMPORTANT]
>
> A11YSPEC define accessibility requirements para verification. Ela não substitui legal accessibility standards, platform certification requirements nem specialized assistive-technology review. Um sistema pode estar within A11YSPEC e ainda exigir additional review para outros accessibility standards.

<a id="table-of-contents"></a>

## Sumário

- [A11YSPEC](#a11yspec)
  - [Introdução](#introduction)
  - [Sumário](#table-of-contents)
  - [Conformidade](#conformance)
  - [Sentidos primários de acessibilidade](#primary-accessibility-senses)
    - [Visão](#sight)
    - [Som](#sound)
    - [Toque](#touch)
    - [Domínios sensoriais adicionais](#additional-sensory-domains)
  - [Casos de acessibilidade exigidos](#required-accessibility-cases)
  - [Essential Functionality](#essential-functionality)
    - [Essential Functionality](#essential-functionality-1)
    - [Critical Functionality](#critical-functionality)
    - [Nonessential Functionality](#nonessential-functionality)
  - [Requisitos de acessibilidade](#accessibility-requirements)
    - [Requisito de essential access](#essential-access-requirement)
    - [Requisito de critical access](#critical-access-requirement)
    - [Requisito de alternate access](#alternate-access-requirement)
    - [Sem dependência de um único sentido](#no-single-sense-dependency)
  - [Visão indisponível](#sight-unavailable)
  - [Som indisponível](#sound-unavailable)
  - [Toque indisponível](#touch-unavailable)
  - [Requisitos de implementação](#implementation-requirements)
    - [Mecanismo estável de acessibilidade](#stable-accessibility-mechanism)
    - [Estrutura semântica](#semantic-structure)
    - [Alternate Output](#alternate-output)
    - [Alternate Input](#alternate-input)
    - [Accessible Feedback](#accessible-feedback)
    - [Accessible Configuration](#accessible-configuration)
  - [Verificação](#verification)
    - [Within Spec](#within-spec)
    - [Avisos](#warnings)
    - [Falhas](#failures)
    - [Validade da verificação](#verification-validity)

<a id="conformance"></a>

## Conformidade

Um sistema é considerado conforme com A11YSPEC quando satisfaz os requirements definidos por este documento para cada required accessibility case.

Um sistema conforme deve:

1. Permanecer razoavelmente utilizável quando a visão estiver indisponível.
2. Permanecer razoavelmente utilizável quando o som estiver indisponível.
3. Permanecer razoavelmente utilizável quando o toque estiver indisponível.
4. Preservar acesso à essential functionality em cada required accessibility case.
5. Preservar acesso a toda critical functionality em cada required accessibility case.
6. Fornecer alternate access paths razoáveis quando essential meaning ou operation dependeria de outro modo do sentido indisponível.
7. Usar um stable accessibility mechanism apropriado ao reviewed system.
8. Evitar depender exclusivamente de um primary sense para essential functionality.

Um sistema não precisa fornecer experiências idênticas em todos os sensory paths. Uma experiência non-visual pode ser mais lenta que uma visual. Uma experiência sound-free pode exigir captions, visual indicators ou haptic confirmation. Uma experiência touch-free pode exigir keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction ou outro método non-touch.

Verification se preocupa com acesso prático à essential functionality, não com apresentação idêntica.

<a id="primary-accessibility-senses"></a>

## Sentidos primários de acessibilidade

Para A11YSPEC, os três primary accessibility senses são **visão**, **som** e **toque**.

Esses sentidos são primários porque são as sensory pathways mais comuns envolvidas em user-interface interaction. Um sistema pode fornecer output por visão, som ou toque, e pode receber interaction por toque, movimento, voz, keyboard input, pointer input, switch input ou outro input path disponível.

<a id="sight"></a>

### Visão

Visão é a visual sensory pathway pela qual um usuário percebe visual output.

A visão pode estar envolvida na percepção de:

* texto
* cor
* forma
* posição
* layout
* animation
* icons
* images
* video
* visual warnings
* visual status indicators
* visible controls

Um sistema depende da visão quando essential meaning ou operation exige que o usuário perceba visualmente a informação.

<a id="sound"></a>

### Som

Som é a auditory sensory pathway pela qual um usuário percebe audio output.

O som pode estar envolvido na percepção de:

* spoken instructions
* alerts
* alarms
* music cues
* sound effects
* audio prompts
* audio descriptions
* auditory status indicators
* spoken confirmation
* spoken navigation

Um sistema depende do som quando essential meaning ou operation exige que o usuário ouça a informação.

<a id="touch"></a>

### Toque

Toque é a tactile sensory pathway pela qual um usuário percebe physical ou haptic output, e a physical interaction pathway pela qual um usuário pode operar controls por contato direto, pressão, gesture ou movimento.

O toque pode estar envolvido em perceber ou realizar:

* touch gestures
* haptic feedback
* vibration
* physical texture
* force
* pressure
* touch-only controls
* physical buttons
* direct manipulation
* touchscreen interaction
* drag actions
* swipe actions

Um sistema depende do toque quando essential meaning ou operation exige tactile perception ou touch-based interaction sem uma alternate input or output path razoável.

<a id="additional-sensory-domains"></a>

### Domínios sensoriais adicionais

A CatalystUI também reconhece **paladar** e **olfato** como sensory domains.

Paladar e olfato podem ser considerados durante accessibility review quando forem usados de modo significativo pelo sistema. Esses sentidos são inclusive para verification, o que significa que podem fortalecer ou apoiar uma accessibility review quando fornecem meaningful alternate access ou contexto adicional.

Paladar e olfato atualmente não são exclusive para failure. Um sistema não falha em A11YSPEC simplesmente por não fornecer taste-based ou smell-based interaction.

A11YSPEC está principalmente preocupada em saber se o sistema permanece razoavelmente utilizável quando visão, som ou toque está individualmente indisponível.

<a id="required-accessibility-cases"></a>

## Casos de acessibilidade exigidos

Um sistema conforme deve ser revisado contra cada required accessibility case.

| Sentido indisponível | Comportamento de acessibilidade exigido |
| -------------------- | ----------------------------------------------------------------- |
| Visão                | O sistema deve permanecer razoavelmente utilizável por som e toque. |
| Som                  | O sistema deve permanecer razoavelmente utilizável por visão e toque. |
| Toque                | O sistema deve permanecer razoavelmente utilizável por visão e som. |

Cada caso é revisado individualmente.

Um sistema não é obrigado a permanecer totalmente utilizável quando vários primary senses estão indisponíveis ao mesmo tempo, a menos que essa condition esteja incluída no reviewed scope.

Um sistema não é obrigado a fornecer every possible accommodation. Ele deve fornecer reasonable access à essential functionality em cada required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality é qualquer behavior, content, control, output, input, workflow ou configuration de que um usuário razoavelmente precise para compreender, navegar, configurar ou operar o essential behavior de um sistema.

Essential functionality pode incluir:

* primary navigation
* core workflows
* required controls
* avisos importantes
* erros importantes
* required confirmation messages
* account or session access
* settings and preferences
* language configuration
* accessibility configuration
* essential instructions
* user-facing status information
* any interaction required for normal use

Um sistema não precisa tornar todo recurso decorative, optional, redundant ou nonessential igualmente disponível por todo sensory path. Porém, o usuário não deve ser bloqueado de usar o essential system pelo unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality é essential functionality cuja perda de acesso pode impedir meaningful use, criar um serious error ou fazer o usuário tomar uma decisão importante sem compreender a consequence.

Critical functionality pode incluir:

* accessibility settings
* language settings
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
* session access
* emergency stop or cancel behavior
* core navigation required to reach accessibility settings

Critical functionality deve permanecer acessível em cada required accessibility case.

Um sistema pode falhar em A11YSPEC se critical functionality depender exclusivamente do unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality é functionality que não é razoavelmente exigida para que um usuário compreenda, navegue, configure ou opere o essential behavior de um sistema.

Nonessential functionality pode incluir:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features outside the reviewed scope

Nonessential functionality pode ficar inaccessible em um ou mais accessibility cases sem causar failure automaticamente. Porém, nonessential functionality não deve ser confundida com essential functionality apenas porque é inconveniente oferecer suporte.

<a id="accessibility-requirements"></a>

## Requisitos de acessibilidade

<a id="essential-access-requirement"></a>

### Requisito de essential access

Um sistema satisfaz o essential access requirement quando essential functionality permanece razoavelmente understandable, navigable, configurable e operable em cada required accessibility case.

A essential experience não precisa ser idêntica em todos os sentidos.

A essential experience deve permanecer meaningfully usable.

<a id="critical-access-requirement"></a>

### Requisito de critical access

Um sistema satisfaz o critical access requirement quando toda critical functionality permanece accessible em cada required accessibility case.

Critical functionality não deve ficar escondida atrás de uma sensory pathway exigida.

Por exemplo, um sistema não deve fornecer uma accessible interface para uso comum enquanto deixa account deletion warnings, payment confirmations, privacy decisions ou accessibility settings dependentes apenas de visão, som ou toque.

<a id="alternate-access-requirement"></a>

### Requisito de alternate access

Um sistema satisfaz o alternate access requirement quando essential meaning ou operation fornecido por um primary sense também está razoavelmente disponível por outro sensory or interaction path quando esse sentido está indisponível.

Alternate access pode ser fornecido por:

* text alternatives
* captions
* transcripts
* spoken output
* screen-reader-compatible structure
* keyboard navigation
* pointer alternatives
* switch-compatible interaction
* voice control
* visual alerts
* haptic feedback
* focus indicators
* semantic structure
* accessible platform APIs
* device-level accessibility integration
* another stable mechanism appropriate to the system

O alternate path não precisa corresponder perfeitamente ao original path. Ele deve preservar essential meaning e operation.

<a id="no-single-sense-dependency"></a>

### Sem dependência de um único sentido

Um sistema não deve exigir um primary sense como único caminho para essential functionality.

Um sistema pode usar visão, som ou toque como primary experience. Porém, quando esse sentido estiver unavailable, o usuário ainda deve ter uma forma razoável de compreender e operar o essential system pelos sensory paths restantes.

Um sistema pode falhar em review quando essential information ou interaction está disponível apenas por:

* visual-only meaning
* audio-only meaning
* touch-only meaning
* gesture-only operation
* haptic-only confirmation
* color-only status
* sound-only alerts
* layout-only instructions
* physical texture-only guidance

<a id="sight-unavailable"></a>

## Visão indisponível

Quando a visão está indisponível, o sistema deve permanecer razoavelmente utilizável por som e toque.

Isso significa que essential visual information deve ter uma meaningful non-visual access path.

Um sistema pode satisfazer esse requisito por:

* spoken output
* screen-reader-compatible structure
* meaningful focus order
* keyboard access
* tactile controls
* haptic confirmation
* audio descriptions
* text-to-speech support
* semantic labels
* accessible names
* accessible roles
* accessible state information
* another reasonable non-visual mechanism

Um sistema não deve depender exclusivamente de:

* visual position
* color
* shape
* animation
* icons
* layout
* images
* video
* visual-only warnings
* visual-only status indicators

quando essa informação é necessária para compreender ou operar essential functionality.

Um sistema pode falhar neste case se um usuário não conseguir razoavelmente navegar, compreender ou operar o essential system sem visão.

<a id="sound-unavailable"></a>

## Som indisponível

Quando o som está indisponível, o sistema deve permanecer razoavelmente utilizável por visão e toque.

Isso significa que essential auditory information deve ter uma meaningful non-auditory access path.

Um sistema pode satisfazer esse requisito por:

* captions
* transcripts
* visual alerts
* text equivalents
* progress indicators
* visible status messages
* haptic feedback
* visual confirmation
* written instructions
* symbolic indicators
* another reasonable non-auditory mechanism

Um sistema não deve depender exclusivamente de:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

quando essa informação é necessária para compreender ou operar essential functionality.

Um sistema pode falhar neste case se um usuário não conseguir razoavelmente navegar, compreender ou operar o essential system sem som.

<a id="touch-unavailable"></a>

## Toque indisponível

Quando o toque está indisponível, o sistema deve permanecer razoavelmente utilizável por visão e som.

Isso significa que essential tactile information e touch-based operation devem ter uma meaningful non-touch access path.

Um sistema pode satisfazer esse requisito por:

* keyboard navigation
* pointer alternatives
* voice control
* remote controls
* gaze-compatible interaction
* switch-compatible interaction
* spoken prompts
* visual confirmation
* accessible shortcut systems
* command palettes
* focus-based interaction
* another reasonable non-touch mechanism

Um sistema não deve depender exclusivamente de:

* touch gestures
* haptic feedback
* physical texture
* vibration
* force
* pressure
* touch-only controls
* drag-only behavior
* swipe-only behavior
* pinch-only behavior
* direct manipulation without alternatives

quando essa interaction é necessária para compreender ou operar essential functionality.

Um sistema pode falhar neste case se um usuário não conseguir razoavelmente navegar, compreender ou operar o essential system sem toque.

<a id="implementation-requirements"></a>

## Requisitos de implementação

<a id="stable-accessibility-mechanism"></a>

### Mecanismo estável de acessibilidade

Um sistema conforme deve usar um stable accessibility mechanism apropriado ao sistema sendo revisado.

Um stable accessibility mechanism deve permitir que accessibility behavior seja mantido, atualizado, revisado e estendido sem depender de fragile ou undocumented behavior.

Um stable accessibility mechanism pode incluir:

* native platform accessibility APIs
* semantic structure
* alternate input methods
* alternate output methods
* assistive-technology support
* built-in accessibility settings
* device-level integration
* documented keyboard interaction
* documented voice interaction
* documented non-visual interaction
* another stable structure appropriate to the system

Um sistema deve evitar implementar essential functionality de modo que impeça reasonable alternate access.

<a id="semantic-structure"></a>

### Estrutura semântica

Um sistema conforme deve fornecer semantic structure quando apresenta meaningful content ou controls.

Semantic structure pode incluir:

* names
* roles
* states
* relationships
* ordering
* grouping
* labels
* descriptions
* focus behavior
* control purpose
* content hierarchy

Semantic structure é especialmente importante quando a visão está indisponível, porque assistive technologies frequentemente dependem de semantic information para comunicar visual interfaces por non-visual output.

Um sistema pode falhar em review se essential controls ou content não puderem ser compreendidos porque sua structure, labels ou relationships estão indisponíveis por alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Um sistema conforme deve fornecer reasonable alternate output quando essential meaning dependeria de outro modo do unavailable sense.

Alternate output pode incluir:

* visual output for auditory information
* auditory output for visual information
* tactile output for visual or auditory information
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output deve preservar essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Um sistema conforme deve fornecer reasonable alternate input quando essential operation dependeria de outro modo apenas de toque.

Alternate input pode incluir:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input não precisa ser o método de input mais rápido ou conveniente. Ele deve ser suficiente para essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Um sistema conforme deve fornecer accessible feedback para essential actions.

Accessible feedback pode incluir:

* confirmation that an action occurred
* indication that an action failed
* progress information
* validation messages
* warning messages
* error messages
* completion status
* current selection
* current focus
* current mode
* current system state

Feedback não deve depender exclusivamente do unavailable sense no accessibility case relacionado.

Por exemplo, um sound-only success chime não é suficiente quando o som está indisponível. Um color-only error state não é suficiente quando a visão está indisponível. Uma vibration-only confirmation não é suficiente quando o toque está indisponível.

<a id="accessible-configuration"></a>

### Accessible Configuration

Um sistema conforme deve permitir que usuários alcancem e usem required accessibility settings pelos mesmos accessibility requirements definidos por esta specification.

Accessibility settings não devem ficar escondidas atrás de uma inaccessible path.

Por exemplo, um screen-reader-compatible mode não é suficiente se o usuário primeiro precisar navegar por um menu visual-only sem rótulos para ativá-lo.

Um sistema pode falhar em review se sua accessibility configuration não puder ser alcançada ou operada na condition que ela pretende apoiar.

<a id="verification"></a>

## Verificação

<a id="within-spec"></a>

### Within Spec

Um sistema é considerado within spec quando a CatalystUI Team revisou o sistema e considerou razoável concluir que ele satisfaz A11YSPEC.

Um sistema pode estar within spec quando:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

Um sistema pode estar within spec mesmo que as experiências não sejam idênticas em todos os sensory paths.

Um sistema pode estar within spec mesmo que alguma nonessential functionality não esteja igualmente disponível em todo required accessibility case.

<a id="warnings"></a>

### Avisos

Um warning pode ser emitido quando um sistema parece satisfazer A11YSPEC, mas contém concerns que devem ser documentadas.

Warnings podem incluir:

* minor nonessential content unavailable in one accessibility case
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* minor focus-order concerns that do not block essential use
* redundant visual, auditory, or tactile cues missing from one path
* accessibility settings that are usable but difficult to find
* assistive-technology support that works but could be clearer
* optional workflows that are not equally accessible

Warnings não impedem necessariamente verification.

<a id="failures"></a>

### Falhas

Uma failure ocorre quando um sistema não satisfaz uma ou mais condições exigidas por A11YSPEC.

Failures podem incluir:

* essential functionality unavailable when sight is unavailable
* essential functionality unavailable when sound is unavailable
* essential functionality unavailable when touch is unavailable
* critical functionality unavailable in any required accessibility case
* no reasonable alternate access path for essential visual information
* no reasonable alternate access path for essential auditory information
* no reasonable alternate access path for essential touch-based operation
* accessibility settings unreachable under the condition they are meant to support
* controls without meaningful labels or structure when required for non-visual use
* sound-only warnings with no visual, tactile, or text equivalent
* color-only status with no non-visual equivalent
* gesture-only operation with no keyboard, pointer, voice, switch, or other alternative
* haptic-only confirmation with no visual or auditory equivalent
* broken assistive-technology support for essential workflows
* major navigation traps
* essential workflows that cannot be completed without the unavailable sense

Failures impedem verification até serem resolvidas.

<a id="verification-validity"></a>

### Validade da verificação

A11YSPEC verification se aplica apenas ao reviewed state do sistema no momento em que a verification é emitida.

Um sistema pode manter verification em updates posteriores desde que preserve a verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features e ordinary content updates não invalidam automaticamente verification.

Uma nova review pode ser necessária se um sistema:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Em outras palavras, melhorar accessibility geralmente é aceitável.

Quebrar o verified access model pode exigir review.
