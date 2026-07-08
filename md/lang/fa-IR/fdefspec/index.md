<!-- این ترجمه توسط ChatGPT تولید شده و باید توسط مترجم انسانی بررسی شود. -->
<!-- پس از تأیید ترجمه، این خطوط را در یک pull request حذف کنید. -->

# FDEFSPEC

<br/>

> **مشخصات تعاریف بنیادی**<br/>
> بازنگری ۱<br/>
> ۲۳ مارس ۲۰۲۶<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> کلیه حقوق محفوظ است.<br/>
> <br/>
> تعاریف و مفاهیم ارائه‌شده در این سند سازه‌های ریاضی بنیادی را توصیف می‌کنند و می‌توانند آزادانه بازبیان شوند.

## مقدمه

**مشخصات تعاریف بنیادی (FDEFSPEC)** مفاهیم اصلی و اصطلاحاتی را تعیین می‌کند که زیربنای اکوسیستم CatalystUI هستند. هدف آن فراهم‌کردن فهمی یکپارچه از این مفاهیم در مستندات، مشخصات، پیاده‌سازی‌ها و بازبینی‌های تأیید است تا سازگاری، شفافیت و هم‌راستایی حفظ شود.

FDEFSPEC با تعریف اصطلاحات کلیدی و رابطه‌ها در قالبی دقیق و پایدار، یک نقطهٔ مرجع مشترک برای مشخصات سطح بالاتر فراهم می‌کند. این کار به توسعه‌دهندگان، بازبینان و پیاده‌سازان اجازه می‌دهد هنگام تعیین این‌که آیا یک زبان، سرویس، فریم‌ورک یا سیستم را می‌توان درون مشخصات دانست، از یک بنیاد مشترک استدلال کنند.

> [!IMPORTANT]
>
> ما تعاریف را با شکلی مشتق‌شده از نمادگذاری [نظریهٔ مجموعه‌ها](https://en.wikipedia.org/wiki/Set_theory) بیان می‌کنیم. این رویکرد تعاریفی دقیق و بدون ابهام فراهم می‌کند، در حالی که شفافیت و اختصار را حفظ می‌کند. این تعاریف برای پشتیبانی از ارجاع آسان، تفسیر روشن و یک سلسله‌مراتب مفهومی سازگار ساختار یافته‌اند.

## فهرست مطالب

- [FDEFSPEC](#fdefspec)
  - [مقدمه](#مقدمه)
  - [فهرست مطالب](#فهرست-مطالب)
  - [اعداد](#اعداد)
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
  - [رمزگذاری متن](#رمزگذاری-متن)
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
  - [وضعیت عملیات](#وضعیت-عملیات)
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

## اعداد

### Bit

یک bit هر $b \in \{0,1\}$ است.

### Nibble

یک nibble هر $(b_0,\dots,b_3)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,3\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

یک byte هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

یک short هر $(b_0,\dots,b_{15})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,15\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

یک integer هر $(b_0,\dots,b_{31})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,31\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

یک long هر $(b_0,\dots,b_{63})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,63\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

یک single هر $(b_0,\dots,b_{31})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,31\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Single()

تعریف زیر با استاندارد IEEE 754 برای نمایش ممیز شناور تک‌دقتی سازگار است. این تعریف مشخص می‌کند که یک دنبالهٔ دودویی ۳۲ بیتی چگونه به عنوان عدد ممیز شناور تفسیر می‌شود؛ از جمله حالت‌های ویژهٔ صفر، بی‌نهایت و NaN (عدد نیست).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

یک double هر $(b_0,\dots,b_{63})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,63\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Double()

تعریف زیر با استاندارد IEEE 754 برای نمایش ممیز شناور دودقتی سازگار است. این تعریف مشخص می‌کند که یک دنبالهٔ دودویی ۶۴ بیتی چگونه به عنوان عدد ممیز شناور تفسیر می‌شود؛ از جمله حالت‌های ویژهٔ صفر، بی‌نهایت و NaN (عدد نیست).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

یک boolean هر $b \in \{0,1\}$ است.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## رمزگذاری متن

### Text Encoding

یک رمزگذاری متن به صورت مجموعهٔ زیر تعریف می‌شود:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

یک codepoint یونیکد هر $e \in \mathbb{Z}$ است به‌گونه‌ای که $0 \leq e \leq 0x10FFFF$ باشد.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

یک ASCII code unit هر $(b_0,\dots,b_6)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,6\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### ASCII Code Unit()

برای کارایی و سازگاری، رایج است که یک ASCII code unit با افزودن یک بیت صفر پیشرو به صورت یک byte نمایش داده شود. در چنین حالت‌هایی، ASCII code unit به این صورت نمایش داده می‌شود:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

در غیر این صورت:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

در مورد این قضیه، هر دو تعریف نمایش‌های پذیرفتنی یک ASCII code unit هستند. برای سازگاری، هنگام نمایش ASCII code unitها به صورت byte از تعریف اول، و هنگام نمایش آن‌ها به صورت دنباله‌های ۷ بیتی از تعریف دوم استفاده خواهیم کرد.

#### ASCII()

ASCII یک چندتایی متناهی پایان‌یافته با null به صورت $(u_0, \dots, u_k, u_{k+1})$ است به‌گونه‌ای که:

- $\forall i \in \{0,\dots,k+1\}$، $u_i$ یک ASCII code unit است
- $\forall i \in \{0,\dots,k\}$، $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

به این دنباله null-terminated گفته می‌شود.

### CP1252 Code Unit

یک CP1252 code unit هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 یک چندتایی متناهی پایان‌یافته با null به صورت $(u_0, \dots, u_k, u_{k+1})$ است به‌گونه‌ای که:

- $\forall i \in \{0,\dots,k+1\}$، $u_i$ یک CP1252 code unit است
- $\forall i \in \{0,\dots,k\}$، $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

به این دنباله null-terminated گفته می‌شود.

### UTF-8 Code Unit

یک UTF-8 code unit هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 یک چندتایی متناهی پایان‌یافته با null به صورت $(u_0, \dots, u_k, u_{k+1})$ است به‌گونه‌ای که:

- $\forall i \in \{0,\dots,k+1\}$، $u_i$ یک UTF-8 code unit است
- $\forall i \in \{0,\dots,k\}$، $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

به این دنباله null-terminated گفته می‌شود.

### UTF-16LE Code Unit

یک UTF-16LE code unit هر $(b_0,\dots,b_{15})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,15\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE یک چندتایی متناهی پایان‌یافته با null به صورت $(u_0, \dots, u_k, u_{k+1})$ است به‌گونه‌ای که:

- $\forall i \in \{0,\dots,k+1\}$، $u_i$ یک UTF-16LE code unit است
- $\forall i \in \{0,\dots,k\}$، $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

به این دنباله null-terminated گفته می‌شود.

## وضعیت عملیات

### Status Code

یک status code هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

یک سطح status code به صورت مجموعهٔ زیر تعریف می‌شود:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

مجموعهٔ مقدارهای status code بازهٔ $[0, 255]$ است که به چهار سطح تقسیم می‌شود:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

همهٔ status codeها تعریف‌های صریح دارند. هر status code که در فهرست زیر نیامده باشد برای استفادهٔ آینده رزرو شده است و معنای آن تعریف نشده است. سطح یک status code با $\mathrm{Status\ Code\ Level}(s)$ تعیین می‌شود.

در فهرست زیر، ورودی $s$ برای خوانایی به صورت مقدار هگزادسیمال نمایش داده شده است. هر status code تعریف‌شده سطح، دسته، زیر‌دسته، توضیح و جزئیات متناظر خود را، در صورت وجود، مشخص می‌کند.

این فهرست می‌تواند با تعریف status codeهای جدید گسترش یابد. هر status code تازه‌تعریف‌شده نباید با کدهای موجود تعارض داشته باشد و باید معنایی روشن و مستند داشته باشد.

برای رساندن اطلاعاتی که در یک status code تعریف‌شده نمایش داده نشده‌اند، باید از context code، operation code یا detail code استفاده شود.

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | عملیات با موفقیت کامل شد. | |
| `0x01` | SUCCESS | NOOP | عملیات بدون انجام هیچ اقدامی با موفقیت کامل شد. | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | عملیات کامل شد، اما نتیجه ممکن است غیرمنتظره یا نامطلوب باشد. | |
| `0x41` | WARNING | PARTIAL | عملیات کامل شد، اما فقط به‌صورت جزئی. خروجی ممکن است ناقص باشد. | |
| `0x42` | WARNING | DEPRECATED | عملیات کامل شد، اما از قابلیت یا رفتاری منسوخ استفاده کرد. ممکن است این عملیات در آینده دیگر کار نکند. | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | عملیات به دلیل خطایی قابل‌بازیابی ناموفق بود. | |
| `0x81` | ERROR | INVALID_ARGUMENT | عملیات ناموفق بود. یک آرگومان نامعتبر یا خارج از محدوده بود. | اندیس آرگومان نامعتبر، از ۰ و از چپ به راست در امضای تابع. |
| `0x82` | ERROR | INVALID_STATE | عملیات ناموفق بود. سیستم در وضعیتی ناسازگار، خراب یا به شکلی دیگر نامعتبر قرار دارد. | |
| `0x83` | ERROR | MALFORMED_INPUT | عملیات ناموفق بود. یک ورودی لازم بدشکل بود یا دادهٔ نامعتبر داشت. | |
| `0x84` | ERROR | ACCESS_DENIED | عملیات ناموفق بود زیرا یک منبع لازم دسترسی را رد کرد. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | عملیات ناموفق بود زیرا قابلیت یا رفتار درخواست‌شده هنوز پیاده‌سازی نشده است. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | عملیات ناموفق بود زیرا سیستم یا پیکربندی هدف از قابلیت درخواست‌شده پشتیبانی نمی‌کند. | |
| `0x87` | ERROR | TIMEOUT | عملیات ناموفق بود زیرا یک مهلت زمانی لازم پیش از تکمیل رخ داد. | |
| `0x88` | ERROR | NOT_FOUND | عملیات ناموفق بود زیرا یک منبع لازم وجود ندارد. | |
| `0x89` | ERROR | INTERRUPTED | عملیات ناموفق بود زیرا یک رویداد خارجی آن را قطع کرد. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | عملیات ناموفق بود زیرا یک وابستگی لازم شکست خورد. | مقدار `STATUS_CODE` مربوط به آن وابستگی. فراخواننده‌ها تشویق می‌شوند، اما ملزم نیستند، وابستگی شکست‌خورده را از طریق فیلد `OP_CODE` شناسایی کنند. |
| `0x90` | ERROR | BUFFER_OVERFLOW | عملیات ناموفق بود. یک بافر برای نگهداری دادهٔ لازم بیش از حد کوچک بود. | |
| `0x91` | ERROR | ALLOCATION_FAILED | عملیات ناموفق بود. یک درخواست تخصیص حافظه موفق نبود. | |
| `0xA0` | ERROR | IO_ERROR | عملیات ناموفق بود. هنگام عملیات یک خطای I/O رخ داد. | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | عملیات به دلیل خطایی غیرقابل‌بازیابی ناموفق بود. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | عملیات ناموفق بود زیرا سیستم یک ناوردای بنیادی را نقض کرد، که نشان‌دهندهٔ خطای منطقی بحرانی یا خرابی داده است. | |

### Context Code

یک context code هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Context Code()

یک مقدار context code اطلاعات زمینه‌ای بیشتری دربارهٔ یک عملیات کامل‌شده ارائه می‌کند، همان‌گونه که توسط عملیات وابسته تعریف شده است؛ این مقدار وقتی سطح status code برابر $\mathrm{Success}$ است باید صفر باشد، و در غیر این صورت وابسته به پیاده‌سازی است.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

یک operation code هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Operation Code()

یک مقدار operation code عملیاتی را که با یک result مرتبط است نشان می‌دهد. معنای آن توسط عملیات متناظر و مستندات آن تعریف می‌شود. مقدارهای تعریف‌نشده unknown در نظر گرفته می‌شوند.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

یک detail code هر $(b_0,\dots,b_7)$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,7\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

#### Detail Code()

یک مقدار detail code اطلاعات بیشتری دربارهٔ یک عملیات کامل‌شده نشان می‌دهد؛ معنای آن توسط status، context یا operation code وابسته، به همین ترتیب، تعریف می‌شود و در غیر این صورت unknown است.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> یک مقدار result می‌تواند به صورت یک integer ۳۲ بیتی نمایش داده شود. در ترتیب بایت big-endian، مقدار به صورت `0xSSCCOODD` ظاهر می‌شود، که در آن `SS`، `CC`، `OO` و `DD` به ترتیب متناظر با status code، context code، operation code و detail code هستند. در ترتیب بایت little-endian، همان مقدار به صورت `0xDDOOCCSS` ظاهر می‌شود. هر کدام از ترتیب‌های بایت می‌تواند استفاده شود، مشروط بر آن‌که به‌صورت سازگار اعمال و مستند شود.

یک result هر $(b_0,\dots,b_{31})$ است به‌گونه‌ای که برای همهٔ $i \in \{0,\dots,31\}$، مقدار $b_i \in \mathrm{Bit}$ باشد.

یک result به چهار byte مرتب تقسیم می‌شود:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

که در آن $s$، $c$، $o$ و $d$ مؤلفه‌های result هستند.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
