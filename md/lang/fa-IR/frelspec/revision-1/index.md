<!-- این ترجمه توسط ChatGPT تولید شده و باید توسط مترجم انسانی بررسی شود. -->
<!-- پس از تأیید ترجمه، این خطوط را در یک pull request حذف کنید. -->

# FRELSPEC

<br/>

> **مشخصات رابطه‌های بنیادی**<br/>
> بازنگری ۱<br/>
> ۷ ژوئیهٔ ۲۰۲۶<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> کلیه حقوق محفوظ است.<br/>
> <br/>
> تعاریف و مفاهیم ارائه‌شده در این سند سازه‌های ریاضی بنیادی را توصیف می‌کنند و می‌توانند آزادانه بازبیان شوند.

## مقدمه

**مشخصات رابطه‌های بنیادی (FRELSPEC)** ساختارهای رابطه‌ای اصلی را تعیین می‌کند که زیربنای اکوسیستم CatalystUI هستند. هدف آن فراهم‌کردن فهمی یکپارچه از این است که مقدارها، حافظه، عملیات و ترکیب‌ها چگونه در مستندات، مشخصات، پیاده‌سازی‌ها و بازبینی‌های تأیید به هم وابسته می‌شوند، تا سازگاری، شفافیت و هم‌راستایی حفظ شود.

FRELSPEC با تعریف رابطه‌های میان مفاهیم بنیادی در قالبی دقیق و پایدار، یک نقطهٔ مرجع مشترک برای مشخصات سطح بالاتر فراهم می‌کند. این کار به توسعه‌دهندگان، بازبینان و پیاده‌سازان اجازه می‌دهد هنگام تعیین این‌که آیا یک زبان، سرویس، فریم‌ورک یا سیستم می‌تواند سازه‌های رابطه‌ای لازم برای قرارگرفتن درون مشخصات را نمایش دهد، از یک بنیاد مشترک استدلال کنند.

> [!IMPORTANT]
>
> ما تعاریف را با شکلی مشتق‌شده از نمادگذاری [نظریهٔ مجموعه‌ها](https://en.wikipedia.org/wiki/Set_theory) بیان می‌کنیم. این رویکرد تعاریفی دقیق و بدون ابهام فراهم می‌کند، در حالی که شفافیت و اختصار را حفظ می‌کند. این تعاریف برای پشتیبانی از ارجاع آسان، تفسیر روشن و یک سلسله‌مراتب مفهومی سازگار ساختار یافته‌اند.

## فهرست مطالب

- [FRELSPEC](#frelspec)
  - [مقدمه](#مقدمه)
  - [فهرست مطالب](#فهرست-مطالب)
  - [مجموعه‌ها](#مجموعهها)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [حافظه](#حافظه)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [عملیات](#عملیات)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Threading](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [ترکیب‌ها](#ترکیبها)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(k)](#fieldk)
    - [Method](#method)
      - [Method(k)](#methodk)
    - [Property](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Structure](#structure)
      - [Structure(k)](#structurek)
    - [Class](#class)
      - [Class(a)](#classa)
    - [Interface](#interface)
      - [Interface(o)](#interfaceo)

## مجموعه‌ها

### Set

یک set هر مجموعه‌ای از عناصر متمایز است.

### Map

یک map هر تابع $f_m : K \to V$ است به‌گونه‌ای که $K$ مجموعه‌ای از کلیدها و $V$ مجموعه‌ای از مقدارها باشد.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

یک array هر تابع $f_a : I \to V$ است به‌گونه‌ای که $I \subset \mathbb{N}$ باشد، $I$ یک مجموعهٔ متناهی و پیوسته از integerها باشد، و $V$ مجموعه‌ای از مقدارها باشد.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

یک file هر تابع $f_f : I \to B$ است به‌گونه‌ای که $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ یک مجموعهٔ متناهی و پیوسته از integerها باشد و $b$ مجموعه‌ای از byteها باشد، جایی که $f_f$ از سازوکاری برای ذخیره‌سازی پایدار داده سرچشمه می‌گیرد.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

یک stream هر تابع $f_s$ است به‌گونه‌ای که هر بار اعمال $f_s$، قطعهٔ بعدی $f_c : I \to B$ را در یک دنبالهٔ byteها تولید کند، جایی که $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ یک مجموعهٔ متناهی و پیوسته از integerها است، $B$ مجموعه‌ای از byteها است، و $f_s$ از سازوکاری برای تولید یا بازیابی ترتیبی داده سرچشمه می‌گیرد.

#### Stream()

> Let $c_k : I_k \to B$ be the chunk returned by the $k\text{-th}$ application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k\text{-th}$ application.

## حافظه

### Address

یک address هر عنصر $a \in A$ است به‌گونه‌ای که $A$ مجموعه‌ای از addressها باشد، جایی که هر address $a$ یک مکان را در یک ساختار حافظه به‌صورت یکتا شناسایی می‌کند.

### Pointer

یک pointer هر تابع $f_p : \{a\} \to B$ است به‌گونه‌ای که $a \in A$ یک address و $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که هر بار اعمال $f_p$ آرایهٔ byte ذخیره‌شده در مکان حافظه‌ای را ارزیابی می‌کند که توسط address مقید آن شناسایی شده است.

#### Pointer()

> Let $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

یک variable هر تابع $f_v : \{k\} \to B$ است به‌گونه‌ای که $k$ یک کلید و $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که variable با مقیدکردن یک کلید به یک address و ارزیابی آرایهٔ byte ذخیره‌شده در مکان حافظه‌ای شناسایی‌شده توسط آن address، یک pointer را گسترش می‌دهد.

#### Variable(k)

> Let $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Let $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

یک constant هر variable $f_c : \{k\} \to B$ است به‌گونه‌ای که $k$ یک کلید و $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که آرایهٔ byte وابسته به $k$ پس از انتساب نمی‌تواند تغییر کند.

#### Constant(k)

> Let $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## عملیات

### Instruction

یک instruction هر آرایه‌ای از byteها $i \in B$ است به‌گونه‌ای که $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که هر instruction یک عملیات محاسباتی منفرد را که باید انجام شود نمایش می‌دهد.

### Procedure

یک procedure هر variable $f_{proc} : \{k\} \to B$ است به‌گونه‌ای که $k$ یک کلید و $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که هر بار اعمال procedure، آرایهٔ byte وابسته به $k$ را به عنوان دنباله‌ای متناهی و مرتب از instructionها ارزیابی و آن instructionها را به ترتیب نمایش‌داده‌شده اجرا می‌کند، بدون آن‌که مقدار بازگشتی تعریف کند.

#### Procedure(k)

> Let $b \in B$ such that $f_{proc}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Function

یک function هر procedure $f_{func} : \{k\} \to B$ است به‌گونه‌ای که $k$ یک کلید و $B$ مجموعه‌ای از آرایه‌های byte باشد، جایی که هر بار اعمال function، آرایهٔ byte وابسته به $k$ را به عنوان دنباله‌ای متناهی و مرتب از instructionها ارزیابی می‌کند، آن instructionها را به ترتیب نمایش‌داده‌شده اجرا می‌کند، و پس از کامل‌شدن اجرا، یک آرایهٔ byte نتیجه را به یک address در حافظه نسبت می‌دهد که می‌تواند به عنوان مقدار بازگشتی function ارزیابی شود.

#### Function(k)

> Let $b \in B$ such that $f_{func}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> Let $a_r \in A$ be an address assigned after execution is completed.
>
> Let $f_m : A \to B$ be a memory map.
>
> $\mathrm{Function}(k)$ is the execution of each $i_j$ in ascending order of $j$, where $\exists b_r \in B : f_m(a_r) = b_r$ after execution is completed.
>
> $\mathrm{Function}(k) = b_r$

## Threading

### Process

یک process هر جریان محدود اجراست که ورودی را می‌پذیرد، یک یا چند instruction را اجرا می‌کند و خروجی تولید می‌کند، جایی که process یک واحد متمایز از تبدیل را درون یک سیستم نمایش می‌دهد.

### Thread

یک thread هر جریان اجرایی است که درون یک process قرار دارد، جایی که thread یک مسیر فراهم می‌کند که از طریق آن دنباله‌های مرتب instructionهای متعلق به آن process می‌توانند اجرا شوند.

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

یک dispatcher هر چندتایی $(t,W,f_d)$ است به‌گونه‌ای که $t$ یک thread باشد، $W$ مجموعه‌ای از procedureها یا functionهای پذیرفته‌شده به عنوان کار باشد، و $f_d$ یک قاعدهٔ dispatch باشد که کاری را از $W$ انتخاب می‌کند، جایی که dispatcher باعث می‌شود کار انتخاب‌شده بر اساس قاعدهٔ dispatch روی $t$ اجرا شود.

#### Dispatcher(t)

> Let $t$ be a thread.
>
> Let $W$ be a set of procedures or functions accepted by the dispatcher, where $\forall w \in W$, $w$ is a procedure or function.
>
> Let $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, where $W' \subseteq W$ and $W' \neq \varnothing$.

## ترکیب‌ها

### Member

یک member هر عنصر $m \in M$ است به‌گونه‌ای که $M$ مجموعه‌ای از memberها باشد، جایی که member مقداری است که می‌تواند درون member map یک object به یک کلید نسبت داده شود.

### Object

یک object هر چندتایی $(a,K,f_o)$ است به‌گونه‌ای که $a \in A$ یک address، $K$ مجموعه‌ای از کلیدها، و $f_o : K \to M$ یک member map باشد، جایی که $M$ مجموعه‌ای از memberها است و object را قادر می‌سازد یک ترکیب آدرس‌پذیر را نمایش دهد که memberهای آن از طریق $f_o$ به کلیدها نسبت داده شده‌اند.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

یک field هر چندتایی $(o,k,m)$ است به‌گونه‌ای که $o = (a,K,f_o)$ یک object باشد، $k \in K$ یک کلید باشد، $m \in M$ یک member باشد، و $f_o(k) = m$ باشد، جایی که field یک member کلیددار را نمایش می‌دهد که از member map یک object حل شده است.

#### Field(k)

> Let $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

یک method هر field $(o,k,m)$ است به‌گونه‌ای که $m$ یک procedure یا function باشد، جایی که method یک member اجرایی کلیددار از یک object را نمایش می‌دهد.

#### Method(k)

> Let $o = (a,K,f_o)$ be an object.
>
> Let $k \in K$ be a key.
>
> Let $m \in M$ be a member such that $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

یک property هر field $(o,k,m)$ است به‌گونه‌ای که $m = (A,f_a)$ یک accessor map باشد، $A = \{ \mathrm{Get}, \mathrm{Set} \}$، و $f_a : A \to M$ هر accessor را به یک member نگاشت کند، جایی که $f_a(\mathrm{Get})$ یک function و $f_a(\mathrm{Set})$ یک procedure است و property را قادر می‌سازد هم رفتار بازیابی و هم رفتار انتساب یک member کلیددار را تعریف کند.

#### Property(k)

> Let $(o,k,m)$ be a field.
>
> Let $m = (A,f_a)$ be an accessor map.
>
> Let $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, where $g$ is a function.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, where $s$ is a procedure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Let $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ is the application of $g$.

#### Set(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Let $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ is the application of $s$.

### Structure

یک structure که اغلب به صورت `struct` کوتاه می‌شود، هر object $s = (a,K,f_s)$ است به‌گونه‌ای که $K$ مجموعه‌ای متناهی از کلیدها و $f_s : K \to M$ یک member map باشد که پس از انتساب struct نمی‌تواند تغییر کند، جایی که struct یک object تخصصی است که چینش memberهای کلیددار آن ثابت است.

#### Structure(k)

> Let $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

یک class هر object $c = (a_c,K_c,f_c)$ است به‌گونه‌ای که $K_c$ مجموعه‌ای متناهی از کلیدها و $f_c : K_c \to M$ یک member-definition map باشد، جایی که class یک object تخصصی است که memberهای کلیددار آن چینش member مورد استفاده برای تولید objectهای دیگر را تعریف می‌کنند.

#### Class(a)

> Let $c = (a_c,K_c,f_c)$ be a class.
>
> Let $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

یک interface هر object $r = (a_r,K_r,f_r)$ است به‌گونه‌ای که $K_r$ مجموعه‌ای متناهی از کلیدها و $f_r : K_r \to M$ یک member-requirement map باشد، جایی که interface یک object تخصصی است که memberهای کلیددار آن memberهایی را تعریف می‌کنند که باید توسط object دیگری فراهم شوند.

#### Interface(o)

> Let $r = (a_r,K_r,f_r)$ be an interface.
>
> Let $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
