<!-- تم إنشاء هذه الترجمة بواسطة ChatGPT ويجب أن يراجعها مترجم بشري. -->
<!-- أزل هذه الأسطر في طلب سحب بعد التحقق من الترجمة. -->

# FRELSPEC

<br/>

> **مواصفة العلاقات التأسيسية**<br/>
> المراجعة 1<br/>
> 7 يوليو 2026<br/>
> <br/>
> حقوق النشر © 2026 CatalystUI LLC. <br/>
> جميع الحقوق محفوظة.<br/>
> <br/>
> تصف التعريفات والمفاهيم المعروضة هنا بُنى رياضية تأسيسية، ويجوز إعادة التعبير عنها بحرية.

## المقدمة

تؤسس **مواصفة العلاقات التأسيسية (FRELSPEC)** البنى العلائقية الأساسية التي يقوم عليها نظام CatalystUI البيئي. والغرض منها هو توفير فهم موحَّد لكيفية ارتباط القيم والذاكرة والعمليات والمركبات عبر الوثائق والمواصفات والتنفيذات ومراجعات التحقق، بما يضمن الاتساق والوضوح والمحاذاة.

ومن خلال تعريف العلاقات بين المفاهيم التأسيسية بصيغة دقيقة ومستقرة، توفر FRELSPEC نقطة مرجعية مشتركة للمواصفات الأعلى مستوى. وهذا يتيح للمطورين والمراجعين والمنفذين أن يستدلوا من الأساس نفسه عند تحديد ما إذا كانت لغة أو خدمة أو إطار عمل أو نظام قادرًا على تمثيل البنى العلائقية المطلوبة ليُعد ضمن المواصفة.

> [!IMPORTANT]
>
> نعبّر عن التعريفات باستخدام صيغة مشتقة من ترميز [نظرية المجموعات](https://en.wikipedia.org/wiki/Set_theory). يوفر هذا الأسلوب تعريفات دقيقة وغير ملتبسة مع الحفاظ على الوضوح والإيجاز. وننظم هذه التعريفات لدعم سهولة الرجوع إليها، ووضوح تفسيرها، وتسلسلها المفاهيمي المتسق.

## جدول المحتويات

- [FRELSPEC](#frelspec)
  - [المقدمة](#المقدمة)
  - [جدول المحتويات](#جدول-المحتويات)
  - [المجموعات](#المجموعات)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [الذاكرة](#الذاكرة)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [العمليات](#العمليات)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [الخيوط التنفيذية](#الخيوط-التنفيذية)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [المركبات](#المركبات)
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

## المجموعات

### Set

المجموعة هي أي تجمّع من عناصر مميزة.

### Map

الخريطة هي أي دالة $f_m : K \to V$ بحيث تكون $K$ مجموعة من المفاتيح وتكون $V$ مجموعة من القيم.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

المصفوفة هي أي دالة $f_a : I \to V$ بحيث يكون $I \subset \mathbb{N}$، وتكون $I$ مجموعة محدودة ومتجاورة من الأعداد الصحيحة، وتكون $V$ مجموعة من القيم.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

الملف هو أي دالة $f_f : I \to B$ بحيث تكون $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ مجموعة محدودة ومتجاورة من الأعداد الصحيحة، وتكون $b$ مجموعة من البايتات، حيث تنشأ $f_f$ من آلية لتخزين بيانات مستمر.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

الدفق هو أي دالة $f_s$ بحيث ينتج كل تطبيق لـ $f_s$ القطعة التالية $f_c : I \to B$ في تسلسل بايتات، حيث تكون $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ مجموعة محدودة ومتجاورة من الأعداد الصحيحة، وتكون $B$ مجموعة من البايتات، وتنشأ $f_s$ من آلية لتوليد البيانات أو استرجاعها تسلسليًا.

#### Stream()

> Let $c_k : I_k \to B$ be the chunk returned by the $k$-th application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k$-th application.

## الذاكرة

### Address

العنوان هو أي عنصر $a \in A$ بحيث تكون $A$ مجموعة من العناوين، حيث يعرّف كل عنوان $a$ موقعًا فريدًا في بنية ذاكرة.

### Pointer

المؤشر هو أي دالة $f_p : \{a\} \to B$ بحيث يكون $a \in A$ عنوانًا، وتكون $B$ مجموعة من مصفوفات البايتات، حيث يقيّم كل تطبيق لـ $f_p$ مصفوفة البايتات المخزنة في موقع الذاكرة الذي يحدده عنوانه المرتبط.

#### Pointer()

> Let $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

المتغير هو أي دالة $f_v : \{k\} \to B$ بحيث يكون $k$ مفتاحًا وتكون $B$ مجموعة من مصفوفات البايتات، حيث يوسّع المتغير المؤشر من خلال ربط مفتاح واحد بعنوان واحد وتقييم مصفوفة البايتات المخزنة في موقع الذاكرة الذي يحدده ذلك العنوان.

#### Variable(k)

> Let $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Let $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

الثابت هو أي متغير $f_c : \{k\} \to B$ بحيث يكون $k$ مفتاحًا وتكون $B$ مجموعة من مصفوفات البايتات، حيث لا يمكن تغيير مصفوفة البايتات المرتبطة بـ $k$ بعد إسنادها.

#### Constant(k)

> Let $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## العمليات

### Instruction

التعليمة هي أي مصفوفة بايتات $i \in B$ بحيث تكون $B$ مجموعة من مصفوفات البايتات، حيث تمثل كل تعليمة عملية حسابية واحدة يجب تنفيذها.

### Procedure

الإجراء هو أي متغير $f_{proc} : \{k\} \to B$ بحيث يكون $k$ مفتاحًا وتكون $B$ مجموعة من مصفوفات البايتات، حيث يقيّم كل تطبيق للإجراء مصفوفة البايتات المرتبطة بـ $k$ بوصفها تسلسلًا مرتبًا محدودًا من التعليمات وينفذ تلك التعليمات بترتيبها الممثَّل دون تعريف قيمة مُعادة.

#### Procedure(k)

> Let $b \in B$ such that $f_{proc}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Function

الدالة هي أي إجراء $f_{func} : \{k\} \to B$ بحيث يكون $k$ مفتاحًا وتكون $B$ مجموعة من مصفوفات البايتات، حيث يقيّم كل تطبيق للدالة مصفوفة البايتات المرتبطة بـ $k$ بوصفها تسلسلًا مرتبًا محدودًا من التعليمات، وينفذ تلك التعليمات بترتيبها الممثَّل، وبعد اكتمال التنفيذ، يسند مصفوفة بايتات ناتجة إلى عنوان ما في الذاكرة يمكن تقييمه بوصفه القيمة المُعادة من الدالة.

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

## الخيوط التنفيذية

### Process

العملية هي أي تدفق تنفيذ محدود يقبل مُدخلًا، وينفذ تعليمة واحدة أو أكثر، وينتج مُخرجًا، حيث تمثل العملية وحدة تحويل مميزة داخل نظام.

### Thread

الخيط التنفيذي هو أي تدفق تنفيذ موجود داخل عملية، حيث يوفر الخيط مسارًا واحدًا يمكن من خلاله تنفيذ تسلسلات التعليمات المرتبة التابعة لتلك العملية.

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

الموزّع هو أي tuple $(t,W,f_d)$ بحيث يكون $t$ خيطًا تنفيذيًا، وتكون $W$ مجموعة من الإجراءات أو الدوال المقبولة كعمل، وتكون $f_d$ قاعدة توزيع تختار عملًا من $W$، حيث يجعل الموزّع العمل المحدد يُنفذ على $t$ وفقًا لقاعدة التوزيع.

#### Dispatcher(t)

> Let $t$ be a thread.
>
> Let $W$ be a set of procedures or functions accepted by the dispatcher, where $\forall w \in W$, $w$ is a procedure or function.
>
> Let $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, where $W' \subseteq W$ and $W' \neq \varnothing$.

## المركبات

### Member

العضو هو أي عنصر $m \in M$ بحيث تكون $M$ مجموعة من الأعضاء، حيث يكون العضو قيمة يمكن إسنادها إلى مفتاح داخل خريطة أعضاء كائن.

### Object

الكائن هو أي tuple $(a,K,f_o)$ بحيث يكون $a \in A$ عنوانًا، وتكون $K$ مجموعة من المفاتيح، وتكون $f_o : K \to M$ خريطة أعضاء، حيث تكون $M$ مجموعة من الأعضاء، مما يسمح للكائن بتمثيل مركب قابل للعنونة تُسند أعضاؤه إلى المفاتيح عبر $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

الحقل هو أي tuple $(o,k,m)$ بحيث يكون $o = (a,K,f_o)$ كائنًا، ويكون $k \in K$ مفتاحًا، ويكون $m \in M$ عضوًا، وتكون $f_o(k) = m$، حيث يمثل الحقل عضوًا واحدًا ذا مفتاح، محلولًا من خريطة أعضاء كائن.

#### Field(k)

> Let $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

الطريقة هي أي حقل $(o,k,m)$ بحيث يكون $m$ إجراءً أو دالة، حيث تمثل الطريقة عضوًا تنفيذيًا ذا مفتاح في كائن.

#### Method(k)

> Let $o = (a,K,f_o)$ be an object.
>
> Let $k \in K$ be a key.
>
> Let $m \in M$ be a member such that $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

الخاصية هي أي حقل $(o,k,m)$ بحيث يكون $m = (A,f_a)$ خريطة موصلات، وتكون $A = \{ \mathrm{Get}, \mathrm{Set} \}$، وتربط $f_a : A \to M$ كل موصل بعضو، حيث تكون $f_a(\mathrm{Get})$ دالة وتكون $f_a(\mathrm{Set})$ إجراءً، مما يسمح للخاصية بتعريف سلوك الاسترجاع والإسناد لعضو ذي مفتاح.

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

البنية، وغالبًا ما تُختصر إلى `struct`، هي أي كائن $s = (a,K,f_s)$ بحيث تكون $K$ مجموعة محدودة من المفاتيح وتكون $f_s : K \to M$ خريطة أعضاء لا يمكن تغييرها بعد إسناد الـ struct، حيث تكون الـ struct كائنًا متخصصًا ذا تخطيط أعضاء بمفاتيح ثابت.

#### Structure(k)

> Let $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

الصنف هو أي كائن $c = (a_c,K_c,f_c)$ بحيث تكون $K_c$ مجموعة محدودة من المفاتيح وتكون $f_c : K_c \to M$ خريطة تعريف أعضاء، حيث يكون الصنف كائنًا متخصصًا تحدد أعضاؤه ذات المفاتيح تخطيط الأعضاء المستخدم لإنتاج كائنات أخرى.

#### Class(a)

> Let $c = (a_c,K_c,f_c)$ be a class.
>
> Let $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

الواجهة هي أي كائن $r = (a_r,K_r,f_r)$ بحيث تكون $K_r$ مجموعة محدودة من المفاتيح وتكون $f_r : K_r \to M$ خريطة متطلبات أعضاء، حيث تكون الواجهة كائنًا متخصصًا تحدد أعضاؤه ذات المفاتيح الأعضاء المطلوب توفيرها من كائن آخر.

#### Interface(o)

> Let $r = (a_r,K_r,f_r)$ be an interface.
>
> Let $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
