<!-- تم إنشاء هذه الترجمة بواسطة ChatGPT ويجب أن يراجعها مترجم بشري. -->
<!-- أزل هذه الأسطر في طلب سحب بعد التحقق من الترجمة. -->

# FDEFSPEC

<br/>

> **مواصفة التعريفات التأسيسية**<br/>
> المراجعة 1<br/>
> 23 مارس 2026<br/>
> <br/>
> حقوق النشر © 2026 CatalystUI LLC. <br/>
> جميع الحقوق محفوظة.<br/>
> <br/>
> تصف التعريفات والمفاهيم المعروضة هنا بُنى رياضية تأسيسية، ويجوز إعادة التعبير عنها بحرية.

## المقدمة

تؤسس **مواصفة التعريفات التأسيسية (FDEFSPEC)** المفاهيم والمصطلحات الأساسية التي يقوم عليها نظام CatalystUI البيئي. والغرض منها هو توفير فهم موحَّد لهذه المفاهيم عبر الوثائق والمواصفات والتنفيذات ومراجعات التحقق، بما يضمن الاتساق والوضوح والمحاذاة.

ومن خلال تعريف المصطلحات والعلاقات الأساسية بصيغة دقيقة ومستقرة، توفر FDEFSPEC نقطة مرجعية مشتركة للمواصفات الأعلى مستوى. وهذا يتيح للمطورين والمراجعين والمنفذين أن يستدلوا من الأساس نفسه عند تحديد ما إذا كانت لغة أو خدمة أو إطار عمل أو نظام يمكن اعتباره ضمن المواصفة.

> [!IMPORTANT]
>
> نعبّر عن التعريفات باستخدام صيغة مشتقة من ترميز [نظرية المجموعات](https://en.wikipedia.org/wiki/Set_theory). يوفر هذا الأسلوب تعريفات دقيقة وغير ملتبسة مع الحفاظ على الوضوح والإيجاز. وننظم هذه التعريفات لدعم سهولة الرجوع إليها، ووضوح تفسيرها، وتسلسلها المفاهيمي المتسق.

## جدول المحتويات

- [FDEFSPEC](#fdefspec)
  - [المقدمة](#المقدمة)
  - [جدول المحتويات](#جدول-المحتويات)
  - [الأعداد](#الأعداد)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [ترميز النص](#ترميز-النص)
    - [Text Encoding](#text-encoding)
      - [Text Encoding()](#text-encoding-1)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [حالة العملية](#حالة-العملية)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## الأعداد

### Bit

البت هو أي $b \in \{0,1\}$.

### Nibble

النبل هو أي $(b_0,\dots,b_3)$ بحيث يكون، لكل $i \in \{0,\dots,3\}$، فإن $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

البايت هو أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

الـ short هو أي $(b_0,\dots,b_{15})$ بحيث يكون، لكل $i \in \{0,\dots,15\}$، فإن $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

العدد الصحيح هو أي $(b_0,\dots,b_{31})$ بحيث يكون، لكل $i \in \{0,\dots,31\}$، فإن $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

الـ long هو أي $(b_0,\dots,b_{63})$ بحيث يكون، لكل $i \in \{0,\dots,63\}$، فإن $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

الـ single هو أي $(b_0,\dots,b_{31})$ بحيث يكون، لكل $i \in \{0,\dots,31\}$، فإن $b_i \in \mathrm{Bit}$.

#### Single()

يتوافق التعريف الآتي مع معيار IEEE 754 لتمثيل أعداد الفاصلة العائمة أحادية الدقة. وهو يحدد كيف تُفسَّر سلسلة ثنائية من 32 بت بوصفها عددًا ذا فاصلة عائمة، بما في ذلك الحالات الخاصة للصفر واللانهاية و NaN (ليس رقمًا).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

الـ double هو أي $(b_0,\dots,b_{63})$ بحيث يكون، لكل $i \in \{0,\dots,63\}$، فإن $b_i \in \mathrm{Bit}$.

#### Double()

يتوافق التعريف الآتي مع معيار IEEE 754 لتمثيل أعداد الفاصلة العائمة مزدوجة الدقة. وهو يحدد كيف تُفسَّر سلسلة ثنائية من 64 بت بوصفها عددًا ذا فاصلة عائمة، بما في ذلك الحالات الخاصة للصفر واللانهاية و NaN (ليس رقمًا).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

القيمة المنطقية هي أي $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## ترميز النص

### Text Encoding

يُعرَّف ترميز النص على أنه المجموعة الآتية:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

نقطة ترميز Unicode هي أي $e \in \mathbb{Z}$ بحيث يكون $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

وحدة ترميز ASCII هي أي $(b_0,\dots,b_6)$ بحيث يكون، لكل $i \in \{0,\dots,6\}$، فإن $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

من الشائع تمثيل وحدة ترميز ASCII كبايت عن طريق إلحاق بت صفري بادئ، وذلك لأسباب تتعلق بالأداء والتوافق. في مثل هذه الحالات، تُمثَّل وحدة ترميز ASCII كما يلي:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

وإلا:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

في حالة هذه النظرية، يُعد كلا التعريفين تمثيلين مقبولين لوحدة ترميز ASCII. ولأجل الاتساق، سنستخدم التعريف الأول عند تمثيل وحدات ترميز ASCII كبايتات، والتعريف الثاني عند تمثيلها كتسلسلات من 7 بت.

#### ASCII()

ASCII هو tuple محدود منتهٍ بصفر $(u_0, \dots, u_k, u_{k+1})$ بحيث:

- $\forall i \in \{0,\dots,k+1\}$، يكون $u_i$ وحدة ترميز ASCII
- $\forall i \in \{0,\dots,k\}$، يكون $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

يُقال إن التسلسل منتهٍ بصفر.

### CP1252 Code Unit

وحدة ترميز CP1252 هي أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 هو tuple محدود منتهٍ بصفر $(u_0, \dots, u_k, u_{k+1})$ بحيث:

- $\forall i \in \{0,\dots,k+1\}$، يكون $u_i$ وحدة ترميز CP1252
- $\forall i \in \{0,\dots,k\}$، يكون $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

يُقال إن التسلسل منتهٍ بصفر.

### UTF-8 Code Unit

وحدة ترميز UTF-8 هي أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 هو tuple محدود منتهٍ بصفر $(u_0, \dots, u_k, u_{k+1})$ بحيث:

- $\forall i \in \{0,\dots,k+1\}$، يكون $u_i$ وحدة ترميز UTF-8
- $\forall i \in \{0,\dots,k\}$، يكون $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

يُقال إن التسلسل منتهٍ بصفر.

### UTF-16LE Code Unit

وحدة ترميز UTF-16LE هي أي $(b_0,\dots,b_{15})$ بحيث يكون، لكل $i \in \{0,\dots,15\}$، فإن $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE هو tuple محدود منتهٍ بصفر $(u_0, \dots, u_k, u_{k+1})$ بحيث:

- $\forall i \in \{0,\dots,k+1\}$، يكون $u_i$ وحدة ترميز UTF-16LE
- $\forall i \in \{0,\dots,k\}$، يكون $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

يُقال إن التسلسل منتهٍ بصفر.

## حالة العملية

### Status Code

رمز الحالة هو أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

يُعرَّف مستوى رمز الحالة على أنه المجموعة الآتية:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

مجموعة قيم رموز الحالة هي النطاق $[0, 255]$، وهي مقسمة إلى أربعة مستويات:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

لكل رموز الحالة تعريفات صريحة. وأي رمز حالة غير مدرج في القائمة التالية محجوز للاستخدام المستقبلي، ومعناه غير معرّف. ويُحدد مستوى رمز الحالة بواسطة $\mathrm{Status\ Code\ Level}(s)$.

في القائمة التالية، يُمثَّل المُدخل $s$ كقيمة ست عشرية لسهولة القراءة. ويحدد كل رمز حالة معرّف مستواه وفئته وفئته الفرعية ووصفه وتفاصيله، عند انطباق ذلك.

قد تُوسَّع هذه القائمة مع تعريف رموز حالة جديدة. ويجب ألا يتعارض أي رمز حالة جديد مع الرموز الموجودة، وأن يكون له معنى موثق بوضوح.

لإيصال معلومات لا يمثلها رمز حالة معرّف، ينبغي استخدام رمز السياق أو رمز العملية أو رمز التفاصيل.

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | اكتملت العملية بنجاح. | |
| `0x01` | SUCCESS | NOOP | اكتملت العملية بنجاح دون تنفيذ أي إجراء. | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | اكتملت العملية، لكن النتيجة قد تكون غير متوقعة أو غير مرغوبة. | |
| `0x41` | WARNING | PARTIAL | اكتملت العملية، ولكن جزئيًا فقط. قد يكون الناتج غير مكتمل. | |
| `0x42` | WARNING | DEPRECATED | اكتملت العملية، لكنها استخدمت ميزة أو سلوكًا مهمَلًا. قد لا تعمل العملية في المستقبل. | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | فشلت العملية بسبب خطأ قابل للاسترداد. | |
| `0x81` | ERROR | INVALID_ARGUMENT | فشلت العملية. كانت إحدى الوسائط غير صالحة أو خارج النطاق. | فهرس الوسيطة غير الصالحة، بدءًا من 0 من اليسار إلى اليمين في توقيع الدالة. |
| `0x82` | ERROR | INVALID_STATE | فشلت العملية. النظام في حالة غير متسقة أو تالفة أو غير صالحة بطريقة أخرى. | |
| `0x83` | ERROR | MALFORMED_INPUT | فشلت العملية. كان مُدخل مطلوب مشوّهًا أو يحتوي على بيانات غير صالحة. | |
| `0x84` | ERROR | ACCESS_DENIED | فشلت العملية لأن موردًا مطلوبًا رفض الوصول. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | فشلت العملية لأن الميزة أو السلوك المطلوب لم يُنفذ بعد. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | فشلت العملية لأن النظام الهدف أو التهيئة لا يدعمان الميزة المطلوبة. | |
| `0x87` | ERROR | TIMEOUT | فشلت العملية لأن مهلة مطلوبة انتهت قبل الإكمال. | |
| `0x88` | ERROR | NOT_FOUND | فشلت العملية لأن موردًا مطلوبًا غير موجود. | |
| `0x89` | ERROR | INTERRUPTED | فشلت العملية لأن حدثًا خارجيًا قاطعها. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | فشلت العملية لأن تبعية مطلوبة فشلت. | قيمة `STATUS_CODE` الخاصة بالتبعية. يُشجَّع المستدعون، دون إلزام، على تحديد التبعية الفاشلة عبر حقل `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | فشلت العملية. كان المخزن المؤقت أصغر من أن يحتوي البيانات المطلوبة. | |
| `0x91` | ERROR | ALLOCATION_FAILED | فشلت العملية. لم ينجح طلب تخصيص الذاكرة. | |
| `0xA0` | ERROR | IO_ERROR | فشلت العملية. حدث خطأ I/O أثناء العملية. | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | فشلت العملية بسبب خطأ غير قابل للاسترداد. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | فشلت العملية لأن النظام خالف ثابتًا أساسيًا، مما يشير إلى خطأ منطقي حرج أو تلف في البيانات. | |

### Context Code

رمز السياق هو أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### Context Code()

تمثل قيمة رمز السياق معلومات سياقية إضافية عن عملية مكتملة، كما تحددها العملية المرتبطة؛ ويجب أن تكون صفرًا عندما يكون مستوى رمز الحالة هو $\mathrm{Success}$، وإلا فهي معرّفة بحسب التنفيذ.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

رمز العملية هو أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### Operation Code()

تمثل قيمة رمز العملية العملية المرتبطة بنتيجة. ويُعرَّف معناها بواسطة العملية المقابلة ووثائقها. وتُعد القيم غير المعرّفة مجهولة.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

رمز التفاصيل هو أي $(b_0,\dots,b_7)$ بحيث يكون، لكل $i \in \{0,\dots,7\}$، فإن $b_i \in \mathrm{Bit}$.

#### Detail Code()

تمثل قيمة رمز التفاصيل معلومات إضافية عن عملية مكتملة؛ ويُعرَّف معناها بواسطة رمز الحالة أو رمز السياق أو رمز العملية المرتبط، بهذا الترتيب، وإلا فهي مجهولة.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> يمكن تمثيل قيمة النتيجة كعدد صحيح من 32 بت. في ترتيب البايتات big-endian، تظهر القيمة على صورة `0xSSCCOODD`، حيث تقابل `SS` و `CC` و `OO` و `DD` رمز الحالة ورمز السياق ورمز العملية ورمز التفاصيل، على التوالي. وفي ترتيب البايتات little-endian، تظهر القيمة نفسها على صورة `0xDDOOCCSS`. يمكن استخدام أي من ترتيبي البايتات، بشرط تطبيقه باستمرار وتوثيقه.

النتيجة هي أي $(b_0,\dots,b_{31})$ بحيث يكون، لكل $i \in \{0,\dots,31\}$، فإن $b_i \in \mathrm{Bit}$.

تُقسَّم النتيجة إلى أربعة بايتات مرتبة:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

حيث تكون $s$ و $c$ و $o$ و $d$ مكونات النتيجة.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
