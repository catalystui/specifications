<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->

<!-- 翻訳が確認された後、pull request でこれらの行を削除してください。 -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

CatalystUI のアクセシビリティ検証ドキュメントへようこそ。

**CatalystUI Verified for Accessibility** は、サービス、framework、application、library、または system が CatalystUI Team によって審査され、user-interface interaction に関わる三つの主要な感覚のうち一つが個別に利用できない場合でも、合理的に利用可能であると判断されたことを示します。

この検証では、CatalystUI は主要な accessibility senses を **sight**、**sound**、**touch** の三つとして扱います。検証済みの system は、これらのいずれか一つが利用できない場合でも、残りの利用可能な sensory domains によって essential functionality への合理的な access を維持しなければなりません。

より簡単に言えば、この検証は、user が sight、sound、touch のいずれか一つに頼れない場合でも、system の essential parts を意味ある形で理解し、移動し、操作できるかを確認します。

## Purpose

Accessibility が重要なのは、同じ essential meaning を別の sensory pathway で合理的に伝えられる場合、user interface が一つの sensory pathway に完全に依存すべきではないからです。

CatalystUI は、systems と human perception のあいだで data が忠実に移動することを中心に設計されています。重要な information が visible だけ、audible だけ、または touch だけで利用できる場合、その sense に頼れない users にとって system は使用不能になる可能性があります。Accessibility Verification は、essential information と interaction が alternate sensory routes を通して継続できるように access を維持する systems を識別するために存在します。

目的は、あらゆる interaction method、あらゆる assistive technology、またはあらゆる specialized accommodation を要求することではありません。目的は、sight、sound、touch のいずれか一つが個別に利用できない場合でも、essential system が meaningfully usable のままであるかを判断することです。

## What Verification Means

system は、この section に記載された requirements に照らして審査され、within spec であると判断された場合に **CatalystUI Verified for Accessibility** になります。

検証されるために、system は次の各 case で合理的に利用可能でなければなりません。

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | system は sound と touch を通じて合理的に利用可能でなければなりません。 |
| Sound             | system は sight と touch を通じて合理的に利用可能でなければなりません。 |
| Touch             | system は sight と sound を通じて合理的に利用可能でなければなりません。 |

system は、すべての sensory path で同一の experience を提供する必要はありません。non-visual experience は visual experience より遅い場合があります。sound-free experience では captions、visual indicators、またはその他の substitutions が必要になる場合があります。touch-free experience では alternate controls、voice interaction、keyboard navigation、pointer navigation、またはその他の non-touch methods が必要になる場合があります。

重要なのは、essential functionality が unavailable sense を要求せずに accessible、understandable、operable のままであるかどうかです。

## Essential Functionality

Accessibility Verification において、**essential functionality** とは、user が system を理解し、移動し、設定し、操作するために合理的に必要とする部分を指します。

Essential functionality には次のようなものが含まれます。

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
* normal use に必要な interaction

装飾的、冗長、任意、または nonessential な features がすべての sensory path で同等に利用できなくても、system は within spec であり得ます。ただし、user が missing sense によって essential system の使用を妨げられてはなりません。

## Sight Unavailable

sight が利用できない場合、system は sound と touch を通じて合理的に利用可能であるべきです。

これには、spoken output、screen-reader-compatible structure、meaningful focus order、tactile controls、keyboard access、haptic confirmation、audio descriptions、または essential information を伝えるための別の合理的な non-visual method が含まれる場合があります。

essential functionality を理解または操作するために必要な information について、system は visual position、color、shape、animation、icons、layout のみに依存すべきではありません。

## Sound Unavailable

sound が利用できない場合、system は sight と touch を通じて合理的に利用可能であるべきです。

これには、captions、transcripts、visual alerts、text equivalents、progress indicators、visible status messages、haptic feedback、または essential information を伝えるための別の合理的な non-auditory method が含まれる場合があります。

essential functionality を理解または操作するために必要な information について、system は sound effects、spoken instructions、alerts、alarms、music cues、audio-only prompts のみに依存すべきではありません。

## Touch Unavailable

touch が利用できない場合、system は sight と sound を通じて合理的に利用可能であるべきです。

これには、voice control、keyboard navigation、pointer alternatives、remote controls、gaze-compatible interaction、switch-compatible interaction、spoken prompts、visual confirmation、または touch-based interaction や tactile perception を必要としない別の合理的な method が含まれる場合があります。

essential functionality を理解または操作するために必要な interactions について、system は touch gestures、haptic feedback、physical texture、vibration、force、pressure、touch-only controls のみに依存すべきではありません。

## Additional Sensory Domains

CatalystUI は **taste** と **smell** も sensory domains として認識します。これらの domains は、system が意味ある形で使用している場合、accessibility review で考慮されることがあります。

taste と smell は verification において **inclusive** です。つまり、meaningful alternate access や additional context を提供する場合、accessibility review を強化または支援できます。

taste と smell は現在、failure のために **exclusive** ではありません。つまり、system が taste-based または smell-based interaction を提供しないだけで Accessibility Verification に失敗するわけではありません。

CatalystUI Accessibility Verification は、主に sight、sound、touch のいずれか一つが個別に利用できない場合でも system が合理的に利用可能であるかに関心を置きます。

## What “Within Spec” Means

system が **within spec** と見なされるとは、CatalystUI Team が system を手動で審査し、この verification category によって説明される accessibility requirements を満たしていると合理的に結論づけたことを意味します。

これは一つの厳格な implementation pattern を要求するものではありません。system は native platform accessibility APIs、semantic structure、alternate input methods、alternate output methods、assistive-technology support、built-in accessibility settings、device-level integration、または system に適した他の stable mechanism によって accessibility requirements を満たすことができます。

verification が関心を置くのは、one primary sense が unavailable である場合に users が essential system に実際に access できるかであり、system が特定の accessibility architecture を使用しているかどうかではありません。

## What Verification Does Not Mean

CatalystUI Verified for Accessibility は、あらゆる disability、device、assistive technology、medical condition、legal requirement、regional standard、または specialized use case が完全に review されたことを保証しません。

また、reviewed accessibility scope に含まれていない限り、internationalization、translation quality、typography、localization、regional compliance、または general design quality を自動的に検証するものでもありません。

system は CatalystUI の accessibility model の下で合理的に accessible でありながら、legal compliance、platform certification、specialized assistive technology support、またはその他の accessibility standards のために別個の review を必要とする場合があります。

## Why This Verification Exists

user interface は、users が実際にそれを使えるときにのみ成功します。

多くの systems は accessibility を、human-computer interaction の fundamental part ではなく、後付け、checklist、または狭い technical requirement として扱います。CatalystUI はより単純で直接的な approach を取ります。system が human perception に依存するなら、primary sensory path の一つが unavailable であるときも essential meaning を維持すべきです。

Accessibility Verification は、この責任を真剣に受け止める systems を識別するために存在します。meaningful alternate access を提供し、essential functionality を維持し、users を一つの required sense の後ろに閉じ込めない systems を認めます。

## Verification Scope

CatalystUI Verification for Accessibility は、verification が issued された時点に存在した reviewed system、service、framework、application、library、または implementation に適用されます。

verified system は、reviewed conditions の下で essential functionality に対して reasonable accessibility を提供します。これは、将来の page、feature、release、plugin、extension、third-party integration、device、または platform-specific version が自動的に within spec になることを保証しません。

separate products、modules、services、major revisions、または platform-specific builds は、requested verification category に応じて個別の review を必要とする場合があります。

## Verification Validity

CatalystUI Verification は、verification が issued された時点の reviewed state of the system にのみ適用されます。

system は、verified accessibility foundation を維持する限り、後の updates において verification を保持できます。minor wording changes、visual refinements、performance improvements、ordinary content updates は verification を自動的に invalid にしません。

system が alternate access paths を削除したり、assistive-technology support を壊したり、essential navigation を大幅に変更したり、required accessibility settings を削除したり、verified accessibility foundation に影響する形で interaction behavior を変更したりした場合、新しい review が必要になることがあります。

言い換えれば、accessibility を改善することは通常問題ありません。verified access model を壊すことは review を必要とする場合があります。

## Verified Systems

accessibility について verified された既知の systems は、適切な CatalystUI Verified page に別途掲載されます。
