<!-- Bản dịch này được tạo bởi ChatGPT và nên được một biên dịch viên con người xem xét lại. -->

<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Chào mừng bạn đến với tài liệu CatalystUI Verification dành cho accessibility.

**CatalystUI Verified for Accessibility** cho biết rằng một service, framework, application, library hoặc system đã được CatalystUI Team xem xét và được xác định là vẫn có thể sử dụng hợp lý khi một trong ba giác quan chính liên quan đến user-interface interaction không khả dụng riêng lẻ.

Đối với verification này, CatalystUI xác định ba primary accessibility senses là **sight**, **sound** và **touch**. Một verified system phải duy trì quyền truy cập hợp lý vào essential functionality khi bất kỳ giác quan nào trong số này không khả dụng, bằng cách dựa vào các sensory domains còn lại.

Nói đơn giản hơn, verification này hỏi liệu user vẫn có thể hiểu, navigate và operate những phần thiết yếu của system một cách có ý nghĩa nếu họ không thể dựa vào sight, sound hoặc touch một cách riêng lẻ hay không.

## Mục đích

Accessibility quan trọng vì user interface không nên phụ thuộc hoàn toàn vào một sensory pathway khi cùng một essential meaning có thể được truyền đạt hợp lý qua một con đường khác.

CatalystUI được thiết kế quanh việc di chuyển dữ liệu một cách trung thực giữa systems và human perception. Nếu thông tin quan trọng chỉ visible, chỉ audible hoặc chỉ available through touch, thì system có thể trở nên unusable đối với users không thể dựa vào giác quan đó. Accessibility Verification tồn tại để xác định các systems duy trì access bằng cách cho phép essential information và interaction tiếp tục thông qua alternate sensory routes.

Mục tiêu không phải là yêu cầu mọi possible interaction method, mọi assistive technology hoặc mọi specialized accommodation. Mục tiêu là xác định liệu essential system có còn meaningfully usable khi sight, sound hoặc touch không khả dụng riêng lẻ hay không.

## Verification có nghĩa là gì

Một system trở thành **CatalystUI Verified for Accessibility** khi nó được review theo các requirements được liệt kê trong phần này và được xác định là within spec.

Để được verified, system phải vẫn reasonably usable trong từng trường hợp sau:

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System phải vẫn reasonably usable thông qua sound và touch. |
| Sound             | System phải vẫn reasonably usable thông qua sight và touch. |
| Touch             | System phải vẫn reasonably usable thông qua sight và sound. |

System không cần cung cấp experiences giống hệt nhau trên mọi sensory path. Non-visual experience có thể chậm hơn visual experience. Sound-free experience có thể cần captions, visual indicators hoặc các substitutions khác. Touch-free experience có thể cần alternate controls, voice interaction, keyboard navigation, pointer navigation hoặc các non-touch methods khác.

Điều quan trọng là essential functionality vẫn accessible, understandable và operable mà không requiring unavailable sense.

## Essential Functionality

Đối với Accessibility Verification, **essential functionality** là các phần của system mà user cần một cách hợp lý để understand, navigate, configure và operate system.

Essential functionality có thể bao gồm:

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
* bất kỳ interaction nào required for normal use

System vẫn có thể within spec nếu decorative, redundant, optional hoặc nonessential features không equally available qua mọi sensory path. Tuy nhiên, user vẫn phải có thể sử dụng essential system mà không bị chặn bởi missing sense.

## Sight Unavailable

Khi sight unavailable, system nên vẫn reasonably usable thông qua sound và touch.

Điều này có thể bao gồm spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions hoặc một reasonable non-visual method khác để truyền đạt essential information.

System không nên rely exclusively vào visual position, color, shape, animation, icons hoặc layout khi thông tin đó required để understand hoặc operate essential functionality.

## Sound Unavailable

Khi sound unavailable, system nên vẫn reasonably usable thông qua sight và touch.

Điều này có thể bao gồm captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback hoặc một reasonable non-auditory method khác để truyền đạt essential information.

System không nên rely exclusively vào sound effects, spoken instructions, alerts, alarms, music cues hoặc audio-only prompts khi thông tin đó required để understand hoặc operate essential functionality.

## Touch Unavailable

Khi touch unavailable, system nên vẫn reasonably usable thông qua sight và sound.

Điều này có thể bao gồm voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation hoặc một reasonable method khác không requiring touch-based interaction hoặc tactile perception.

System không nên rely exclusively vào touch gestures, haptic feedback, physical texture, vibration, force, pressure hoặc touch-only controls khi các interactions đó required để understand hoặc operate essential functionality.

## Additional Sensory Domains

CatalystUI cũng nhận diện **taste** và **smell** là sensory domains. Các domains này có thể được xem xét trong accessibility review khi system sử dụng chúng một cách meaningful.

Taste và smell là **inclusive** đối với verification, nghĩa là chúng có thể strengthen hoặc support accessibility review khi cung cấp meaningful alternate access hoặc additional context.

Taste và smell hiện không **exclusive** cho failure, nghĩa là system không fail Accessibility Verification chỉ vì không cung cấp taste-based hoặc smell-based interaction.

CatalystUI Accessibility Verification chủ yếu xác định liệu system vẫn reasonably usable khi sight, sound hoặc touch không khả dụng riêng lẻ hay không.

## “Within Spec” có nghĩa là gì

Khi một system được coi là **within spec**, điều đó nghĩa là CatalystUI Team đã manually review system và thấy hợp lý để kết luận rằng nó đáp ứng accessibility requirements được mô tả bởi verification category này.

Điều này không yêu cầu một rigid implementation pattern. System có thể đáp ứng accessibility requirements thông qua native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration hoặc một stable mechanism khác phù hợp với system.

Verification tập trung vào practical ability của users để access essential system khi một primary sense unavailable, không phải vào việc system sử dụng một accessibility architecture cụ thể nào.

## Verification không có nghĩa là gì

CatalystUI Verified for Accessibility không đảm bảo rằng mọi possible disability, device, assistive technology, medical condition, legal requirement, regional standard hoặc specialized use case đã được review đầy đủ.

Nó cũng không automatically verify internationalization, translation quality, typography, localization, regional compliance hoặc general design quality trừ khi các yếu tố đó nằm trong reviewed accessibility scope.

Một system có thể reasonably accessible theo accessibility model của CatalystUI nhưng vẫn cần separate review cho legal compliance, platform certification, specialized assistive technology support hoặc other accessibility standards.

## Vì sao verification này tồn tại

User interface chỉ thành công khi users thực sự có thể sử dụng nó.

Nhiều systems xem accessibility như afterthought, checklist hoặc narrow technical requirement thay vì một phần fundamental của human-computer interaction. Approach của CatalystUI đơn giản và trực tiếp hơn: nếu system phụ thuộc vào human perception, nó phải preserve essential meaning khi một primary sensory path unavailable.

Accessibility Verification tồn tại để xác định các systems nghiêm túc với trách nhiệm này. Nó công nhận các systems cung cấp meaningful alternate access, preserve essential functionality và tránh khóa users phía sau một required sense duy nhất.

## Verification Scope

CatalystUI Verification for Accessibility áp dụng cho reviewed system, service, framework, application, library hoặc implementation theo trạng thái của nó tại thời điểm verification được issued.

Verified system cung cấp reasonable accessibility cho essential functionality trong reviewed conditions. Điều này không đảm bảo rằng mọi future page, feature, release, plugin, extension, third-party integration, device hoặc platform-specific version đều automatically within spec.

Separate products, modules, services, major revisions hoặc platform-specific builds có thể cần review riêng tùy theo verification category được yêu cầu.

## Verification Validity

CatalystUI Verification chỉ áp dụng cho reviewed state của system tại thời điểm verification được issued.

System có thể retain verification qua later updates miễn là nó preserve verified accessibility foundation. Minor wording changes, visual refinements, performance improvements và ordinary content updates không automatically invalidate verification.

New review có thể required nếu system removes alternate access paths, breaks assistive-technology support, substantially changes essential navigation, removes required accessibility settings hoặc changes interaction behavior theo cách ảnh hưởng đến verified accessibility foundation.

Nói cách khác, improving accessibility thường là ổn. Breaking the verified access model có thể require review.

## Verified Systems

Các known systems được verified cho accessibility được listed separately trên trang CatalystUI Verified phù hợp.
