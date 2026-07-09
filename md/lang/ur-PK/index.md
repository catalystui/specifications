<!-- یہ ترجمہ ChatGPT نے تیار کیا ہے اور کسی انسانی مترجم کو اس کا جائزہ لینا چاہیے۔ -->

<!-- ترجمہ تصدیق ہونے کے بعد pull request میں یہ سطریں ہٹا دیں۔ -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Accessibility کے لیے CatalystUI Verification دستاویزات میں خوش آمدید۔

**CatalystUI Verified for Accessibility** اس بات کی نشان دہی کرتا ہے کہ کسی service، framework، application، library، یا system کا CatalystUI Team نے جائزہ لیا ہے، اور اسے اس قابل پایا ہے کہ user-interface interaction میں شامل تین primary senses میں سے کوئی ایک sense انفرادی طور پر unavailable ہو تو بھی وہ معقول حد تک usable رہتا ہے۔

اس verification کے لیے CatalystUI تین primary accessibility senses کو **sight**، **sound**، اور **touch** کے طور پر شناخت کرتا ہے۔ ایک verified system کو اپنی essential functionality تک reasonable access برقرار رکھنی چاہیے جب ان میں سے کوئی بھی sense unavailable ہو، اور اسے باقی available sensory domains پر انحصار کرتے ہوئے ایسا کرنا چاہیے۔

آسان الفاظ میں، یہ verification یہ پوچھتی ہے کہ کیا کوئی user کسی system کے essential parts کو meaningful طور پر سمجھ، navigate، اور operate کر سکتا ہے اگر وہ sight، sound، یا touch میں سے کسی ایک پر انفرادی طور پر اعتماد نہ کر سکے۔

## مقصد

Accessibility اس لیے اہم ہے کیونکہ user interface کو ایک ہی sensory pathway پر مکمل طور پر depend نہیں کرنا چاہیے جب وہی essential meaning کسی دوسرے ذریعے سے reasonable طور پر communicate کیا جا سکتا ہو۔

CatalystUI systems اور human perception کے درمیان data کی faithful movement کے گرد design کیا گیا ہے۔ اگر important information صرف visible ہو، صرف audible ہو، یا صرف touch کے ذریعے available ہو، تو وہ system ان users کے لیے unusable ہو سکتا ہے جو اس sense پر rely نہیں کر سکتے۔ Accessibility Verification ایسے systems کی نشاندہی کرنے کے لیے موجود ہے جو essential information اور interaction کو alternate sensory routes کے ذریعے جاری رکھ کر access کو preserve کرتے ہیں۔

مقصد ہر ممکن interaction method، ہر assistive technology، یا ہر specialized accommodation کو require کرنا نہیں ہے۔ مقصد یہ determine کرنا ہے کہ sight، sound، یا touch individually unavailable ہونے پر بھی essential system meaningfully usable رہتا ہے یا نہیں۔

## Verification کا مطلب

کوئی system **CatalystUI Verified for Accessibility** اس وقت بنتا ہے جب اسے اس section میں listed requirements کے مطابق review کیا جائے اور اسے within spec پایا جائے۔

Verified ہونے کے لیے system کو درج ذیل ہر case میں reasonably usable رہنا چاہیے:

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System کو sound اور touch کے ذریعے reasonably usable رہنا چاہیے۔ |
| Sound             | System کو sight اور touch کے ذریعے reasonably usable رہنا چاہیے۔ |
| Touch             | System کو sight اور sound کے ذریعے reasonably usable رہنا چاہیے۔ |

System کو ہر sensory path پر identical experiences فراہم کرنے کی ضرورت نہیں۔ Non-visual experience visual experience سے slow ہو سکتا ہے۔ Sound-free experience کو captions، visual indicators، یا other substitutions کی ضرورت ہو سکتی ہے۔ Touch-free experience کو alternate controls، voice interaction، keyboard navigation، pointer navigation، یا other non-touch methods کی ضرورت ہو سکتی ہے۔

اصل بات یہ ہے کہ essential functionality accessible، understandable، اور operable رہے بغیر unavailable sense کو require کیے۔

## Essential Functionality

Accessibility Verification کے لیے **essential functionality** سے مراد system کے وہ حصے ہیں جن کی user کو system کو understand، navigate، configure، اور operate کرنے کے لیے reasonable ضرورت ہوتی ہے۔

Essential functionality میں شامل ہو سکتے ہیں:

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
* normal use کے لیے required کوئی بھی interaction

System پھر بھی within spec ہو سکتا ہے اگر decorative، redundant، optional، یا nonessential features ہر sensory path کے ذریعے برابر available نہ ہوں۔ تاہم user missing sense کی وجہ سے essential system استعمال کرنے سے blocked نہیں ہونا چاہیے۔

## Sight Unavailable

جب sight unavailable ہو، system کو sound اور touch کے ذریعے reasonably usable رہنا چاہیے۔

اس میں spoken output، screen-reader-compatible structure، meaningful focus order، tactile controls، keyboard access، haptic confirmation، audio descriptions، یا essential information communicate کرنے کا کوئی اور reasonable non-visual method شامل ہو سکتا ہے۔

System کو visual position، color، shape، animation، icons، یا layout پر exclusively rely نہیں کرنا چاہیے جب وہ information essential functionality کو understand یا operate کرنے کے لیے required ہو۔

## Sound Unavailable

جب sound unavailable ہو، system کو sight اور touch کے ذریعے reasonably usable رہنا چاہیے۔

اس میں captions، transcripts، visual alerts، text equivalents، progress indicators، visible status messages، haptic feedback، یا essential information communicate کرنے کا کوئی اور reasonable non-auditory method شامل ہو سکتا ہے۔

System کو sound effects، spoken instructions، alerts، alarms، music cues، یا audio-only prompts پر exclusively rely نہیں کرنا چاہیے جب وہ information essential functionality کو understand یا operate کرنے کے لیے required ہو۔

## Touch Unavailable

جب touch unavailable ہو، system کو sight اور sound کے ذریعے reasonably usable رہنا چاہیے۔

اس میں voice control، keyboard navigation، pointer alternatives، remote controls، gaze-compatible interaction، switch-compatible interaction، spoken prompts، visual confirmation، یا کوئی اور reasonable method شامل ہو سکتا ہے جس کے لیے touch-based interaction یا tactile perception required نہ ہو۔

System کو touch gestures، haptic feedback، physical texture، vibration، force، pressure، یا touch-only controls پر exclusively rely نہیں کرنا چاہیے جب یہ interactions essential functionality کو understand یا operate کرنے کے لیے required ہوں۔

## Additional Sensory Domains

CatalystUI **taste** اور **smell** کو بھی sensory domains کے طور پر recognize کرتا ہے۔ جب system انہیں meaningfully استعمال کرتا ہو تو accessibility review میں ان domains کو consider کیا جا سکتا ہے۔

Taste اور smell verification کے لیے **inclusive** ہیں، یعنی meaningful alternate access یا additional context فراہم کرنے پر یہ accessibility review کو strengthen یا support کر سکتے ہیں۔

Taste اور smell فی الحال failure کے لیے **exclusive** نہیں ہیں، یعنی کوئی system صرف اس وجہ سے Accessibility Verification میں fail نہیں ہوتا کہ وہ taste-based یا smell-based interaction فراہم نہیں کرتا۔

CatalystUI Accessibility Verification بنیادی طور پر یہ determine کرتی ہے کہ sight، sound، یا touch individually unavailable ہونے پر system reasonably usable رہتا ہے یا نہیں۔

## “Within Spec” کا مطلب

جب کوئی system **within spec** سمجھا جاتا ہے، تو اس کا مطلب ہے کہ CatalystUI Team نے system کو manually review کیا ہے اور اسے reasonable طور پر accessibility requirements کے مطابق پایا ہے جو اس verification category میں بیان کی گئی ہیں۔

یہ کسی rigid implementation pattern کو require نہیں کرتا۔ کوئی system native platform accessibility APIs، semantic structure، alternate input methods، alternate output methods، assistive-technology support، built-in accessibility settings، device-level integration، یا system کے لیے appropriate کسی اور stable mechanism کے ذریعے requirements پوری کر سکتا ہے۔

Verification practical ability پر focus کرتی ہے کہ users primary sense unavailable ہونے پر essential system تک access حاصل کر سکیں، نہ کہ system کسی مخصوص accessibility architecture کو استعمال کرتا ہے یا نہیں۔

## Verification کا مطلب کیا نہیں ہے

CatalystUI Verified for Accessibility یہ guarantee نہیں کرتا کہ ہر possible disability، device، assistive technology، medical condition، legal requirement، regional standard، یا specialized use case کا مکمل review ہو چکا ہے۔

یہ automatically internationalization، translation quality، typography، localization، regional compliance، یا general design quality کو verify نہیں کرتا، جب تک وہ reviewed accessibility scope میں شامل نہ ہوں۔

کوئی system CatalystUI accessibility model کے تحت reasonably accessible ہو سکتا ہے اور پھر بھی legal compliance، platform certification، specialized assistive technology support، یا other accessibility standards کے لیے separate review require کر سکتا ہے۔

## یہ Verification کیوں موجود ہے

User interface تبھی کامیاب ہوتا ہے جب users اسے واقعی استعمال کر سکیں۔

بہت سے systems accessibility کو fundamental human-computer interaction کا حصہ سمجھنے کے بجائے afterthought، checklist، یا narrow technical requirement سمجھتے ہیں۔ CatalystUI کا approach simpler اور more direct ہے: اگر کوئی system human perception پر depend کرتا ہے، تو اسے primary sensory path unavailable ہونے پر essential meaning preserve کرنا چاہیے۔

Accessibility Verification ایسے systems کو identify کرنے کے لیے موجود ہے جو اس responsibility کو serious لیتے ہیں۔ یہ ان systems کو recognize کرتی ہے جو meaningful alternate access فراہم کرتے ہیں، essential functionality preserve کرتے ہیں، اور users کو ایک required sense کے پیچھے locked نہیں کرتے۔

## Verification کا Scope

CatalystUI Verification for Accessibility reviewed system، service، framework، application، library، یا implementation پر اسی state کے مطابق apply کرتی ہے جس میں verification issue کی گئی ہو۔

Verified system reviewed conditions کے تحت اپنی essential functionality کے لیے reasonable accessibility فراہم کرتا ہے۔ یہ guarantee نہیں کرتا کہ ہر future page، feature، release، plugin، extension، third-party integration، device، یا platform-specific version automatically within spec ہے۔

Separate products، modules، services، major revisions، یا platform-specific builds کو requested verification category کے لحاظ سے اپنی review require ہو سکتی ہے۔

## Verification Validity

CatalystUI Verification صرف system کی reviewed state پر apply کرتی ہے، یعنی جس وقت verification issue کی گئی۔

System later updates میں اپنی verification retain کر سکتا ہے جب تک وہ verified accessibility foundation preserve کرتا رہے۔ Minor wording changes، visual refinements، performance improvements، اور ordinary content updates automatically verification کو invalidate نہیں کرتے۔

نئی review required ہو سکتی ہے اگر system alternate access paths remove کرے، assistive-technology support break کرے، essential navigation کو substantially change کرے، required accessibility settings remove کرے، یا interaction behavior کو اس طرح change کرے جو verified accessibility foundation کو affect کرے۔

دوسرے الفاظ میں، accessibility کو improve کرنا عموماً ٹھیک ہے۔ Verified access model کو break کرنا review require کر سکتا ہے۔

## Verified Systems

Accessibility کے لیے verified known systems مناسب CatalystUI Verified page پر separately listed ہیں۔
