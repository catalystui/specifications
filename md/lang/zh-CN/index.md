<!-- 此翻译由 ChatGPT 生成，应由人工译者审阅。 -->

<!-- 翻译经过验证后，请在 pull request 中移除这些行。 -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

欢迎阅读 CatalystUI Verification 的 accessibility 文档。

**CatalystUI Verified for Accessibility** 表示某个 service、framework、application、library 或 system 已由 CatalystUI Team 审核，并被认为在 user-interface interaction 所涉及的三个 primary senses 中任意一个单独 unavailable 时，仍能保持合理可用。

在此 verification 中，CatalystUI 将三个 primary accessibility senses 定义为 **sight**、**sound** 和 **touch**。经过 verified 的 system 必须在其中任一 sense unavailable 时，通过依靠剩余可用的 sensory domains，保持对其 essential functionality 的合理访问。

简单来说，此 verification 询问的是：如果 user 不能分别依赖 sight、sound 或 touch，是否仍能 meaningful 地理解、navigate 并 operate system 的 essential parts。

## 目的

Accessibility 很重要，因为当同样的 essential meaning 可以通过另一条路径合理传达时，user interface 不应完全依赖单一 sensory pathway。

CatalystUI 围绕 systems 与 human perception 之间 data 的 faithful movement 而设计。如果 important information 只能被看见、只能被听见，或只能通过 touch 获得，那么对无法依赖该 sense 的 users 来说，system 可能变得 unusable。Accessibility Verification 的存在，是为了识别那些通过 alternate sensory routes 保持 essential information 和 interaction 继续可用的 systems。

目标不是要求每一种 possible interaction method、每一种 assistive technology 或每一种 specialized accommodation。目标是确定当 sight、sound 或 touch 分别 unavailable 时，essential system 是否仍然 meaningfully usable。

## Verification 的含义

当 system 根据本节 listed requirements 进行 review 并被认定为 within spec 时，它就成为 **CatalystUI Verified for Accessibility**。

要获得 verified，system 必须在以下每种情况中保持 reasonably usable：

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System 必须通过 sound 和 touch 保持 reasonably usable。 |
| Sound             | System 必须通过 sight 和 touch 保持 reasonably usable。 |
| Touch             | System 必须通过 sight 和 sound 保持 reasonably usable。 |

System 不需要在每条 sensory path 上提供完全相同的 experiences。Non-visual experience 可能比 visual one 更慢。Sound-free experience 可能需要 captions、visual indicators 或其他 substitutions。Touch-free experience 可能需要 alternate controls、voice interaction、keyboard navigation、pointer navigation 或其他 non-touch methods。

关键是 essential functionality 在不 require unavailable sense 的情况下仍然 accessible、understandable 且 operable。

## Essential Functionality

对于 Accessibility Verification，**essential functionality** 指 user 为了 understand、navigate、configure 和 operate system 而合理需要的部分。

Essential functionality 可以包括：

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
* normal use 所 required 的任何 interaction

如果 decorative、redundant、optional 或 nonessential features 没有通过每条 sensory path 同等 available，system 仍可能 within spec。但是，user 不得因为 missing sense 而被阻止使用 essential system。

## Sight Unavailable

当 sight unavailable 时，system 应通过 sound 和 touch 保持 reasonably usable。

这可能包括 spoken output、screen-reader-compatible structure、meaningful focus order、tactile controls、keyboard access、haptic confirmation、audio descriptions，或另一种传达 essential information 的合理 non-visual method。

当某些 information 对 understand 或 operate essential functionality 是 required 时，system 不应 exclusively rely on visual position、color、shape、animation、icons 或 layout。

## Sound Unavailable

当 sound unavailable 时，system 应通过 sight 和 touch 保持 reasonably usable。

这可能包括 captions、transcripts、visual alerts、text equivalents、progress indicators、visible status messages、haptic feedback，或另一种传达 essential information 的合理 non-auditory method。

当某些 information 对 understand 或 operate essential functionality 是 required 时，system 不应 exclusively rely on sound effects、spoken instructions、alerts、alarms、music cues 或 audio-only prompts。

## Touch Unavailable

当 touch unavailable 时，system 应通过 sight 和 sound 保持 reasonably usable。

这可能包括 voice control、keyboard navigation、pointer alternatives、remote controls、gaze-compatible interaction、switch-compatible interaction、spoken prompts、visual confirmation，或另一种不 require touch-based interaction 或 tactile perception 的 reasonable method。

当这些 interactions 对 understand 或 operate essential functionality 是 required 时，system 不应 exclusively rely on touch gestures、haptic feedback、physical texture、vibration、force、pressure 或 touch-only controls。

## Additional Sensory Domains

CatalystUI 也将 **taste** 和 **smell** 识别为 sensory domains。当 system meaningful 地使用它们时，这些 domains 可在 accessibility review 中被考虑。

Taste 和 smell 对 verification 是 **inclusive** 的，这意味着当它们提供 meaningful alternate access 或 additional context 时，可以 strengthen 或 support accessibility review。

Taste 和 smell 当前并不是 failure 的 **exclusive** 条件，也就是说，system 不会仅仅因为没有提供 taste-based 或 smell-based interaction 而 fail Accessibility Verification。

CatalystUI Accessibility Verification 主要判断 system 在 sight、sound 或 touch individually unavailable 时是否仍然 reasonably usable。

## “Within Spec” 的含义

当 system 被认为 **within spec** 时，意味着 CatalystUI Team 已经 manually review system，并认为可以合理推断它满足此 verification category 所描述的 accessibility requirements。

这并不 require 某种 rigid implementation pattern。System 可以通过 native platform accessibility APIs、semantic structure、alternate input methods、alternate output methods、assistive-technology support、built-in accessibility settings、device-level integration，或其他适合 system 的 stable mechanism 来满足 accessibility requirements。

Verification 关注的是当一个 primary sense unavailable 时，users 是否能够 practical 地 access essential system，而不是 system 是否使用某一种特定 accessibility architecture。

## Verification 不意味着什么

CatalystUI Verified for Accessibility 不保证每一种 possible disability、device、assistive technology、medical condition、legal requirement、regional standard 或 specialized use case 都已被完整 review。

它也不会 automatically verify internationalization、translation quality、typography、localization、regional compliance 或 general design quality，除非这些内容包含在 reviewed accessibility scope 中。

System 可以在 CatalystUI accessibility model 下 reasonably accessible，但仍需要针对 legal compliance、platform certification、specialized assistive technology support 或 other accessibility standards 进行 separate review。

## 此 Verification 存在的原因

User interface 只有在 users 真正能够使用时才算成功。

许多 systems 将 accessibility 视为 afterthought、checklist 或 narrow technical requirement，而不是 human-computer interaction 的 fundamental 部分。CatalystUI 的 approach 更简单、更直接：如果 system 依赖 human perception，它就必须在 primary sensory path unavailable 时 preserve essential meaning。

Accessibility Verification 的存在，是为了识别认真对待这项 responsibility 的 systems。它认可那些提供 meaningful alternate access、preserve essential functionality，并避免将 users 锁在一个 required sense 之后的 systems。

## Verification Scope

CatalystUI Verification for Accessibility 适用于 reviewed system、service、framework、application、library 或 implementation 在 verification issued 时的状态。

Verified system 在 reviewed conditions 下为其 essential functionality 提供 reasonable accessibility。这并不保证每个 future page、feature、release、plugin、extension、third-party integration、device 或 platform-specific version 都 automatically within spec。

Separate products、modules、services、major revisions 或 platform-specific builds 可能需要自己的 review，具体取决于 requested verification category。

## Verification Validity

CatalystUI Verification 只适用于 verification issued 时 system 的 reviewed state。

只要 system preserves verified accessibility foundation，它可以在 later updates 中 retain verification。Minor wording changes、visual refinements、performance improvements 和 ordinary content updates 不会 automatically invalidate verification。

如果 system removes alternate access paths、breaks assistive-technology support、substantially changes essential navigation、removes required accessibility settings，或 changes interaction behavior 以至于 affects verified accessibility foundation，则可能需要 new review。

换句话说，improving accessibility 通常没有问题。Breaking the verified access model 可能 require review。

## Verified Systems

已知通过 accessibility verified 的 systems 会 separately listed 在相应的 CatalystUI Verified page 上。
