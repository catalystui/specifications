<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request ile kaldırın. -->

# FRELSPEC

<br/>

> **Temel İlişkiler Spesifikasyonu**<br/>
> Revizyon 2.1<br/>
> 24 Kasım 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tüm hakları saklıdır.<br/>
> <br/>
> Burada sunulan tanımlar ve kavramlar temel matematiksel yapıları açıklar ve serbestçe yeniden ifade edilebilir.

## Giriş

**Temel İlişkiler Spesifikasyonu (FRELSPEC)** CatalystUI ekosisteminin temelini oluşturan çekirdek ilişkisel yapıları belirler. Amacı, bellek, koleksiyonlar, işlemler ve bileşik yapıların dokümantasyon, spesifikasyonlar, uygulamalar ve doğrulama incelemeleri boyunca nasıl ilişkili olduğuna dair ortak bir anlayış sağlamak ve tutarlılığı, açıklığı ve uyumu güvence altına almaktır.

FRELSPEC, temel kavramlar arasındaki ilişkileri kesin ve istikrarlı bir biçimde tanımlayarak üst düzey spesifikasyonlar için ortak bir referans noktası sağlar ve ayrı uygulamaların kendi kural ve davranışlarını belirlemesine olanak tanır. Böylece geliştiriciler, inceleyenler ve uygulayıcılar bir dilin, hizmetin, çerçevenin veya sistemin spesifikasyona uygunluk için gerekli ilişkisel yapıları temsil edip edemediğini aynı temelden değerlendirebilir.

> [!IMPORTANT]
>
> Tanımları [küme teorisi](https://en.wikipedia.org/wiki/Set_theory) gösteriminden türetilmiş bir biçimle ifade ediyoruz. Bu yaklaşım açıklığı ve özlülüğü koruyarak kesin ve belirsizlik içermeyen tanımlar sağlar. Tanımları kolay başvuru, açık yorumlama ve tutarlı kavramsal hiyerarşi için yapılandırıyoruz.

## İçindekiler

- [FRELSPEC](#frelspec)
  - [Giriş](#giriş)
  - [İçindekiler](#i̇çindekiler)
  - [Revizyonlar](#revizyonlar)
    - [Revizyon 2.1](#revizyon-21)
    - [Revizyon 2](#revizyon-2)
  - [Bellek](#bellek)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Koleksiyonlar](#koleksiyonlar)
    - [Set](#set)
      - [Set()](#set-1)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [İşlemler](#i̇şlemler)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [İş parçacıkları](#i̇ş-parçacıkları)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Bileşik yapılar](#bileşik-yapılar)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(o,k)](#fieldok)
    - [Method](#method)
      - [Method(o,k)](#methodok)
    - [Property](#property)
      - [Property(o,k)](#propertyok)
      - [Get(o,k)](#getok)
      - [Set(o,k)](#setok)
    - [Structure](#structure)
      - [Structure(s,k)](#structuresk)
    - [Class](#class)
      - [Class(c,a)](#classca)
    - [Interface](#interface)
      - [Interface(r,o)](#interfacero)

## Revizyonlar

### Revizyon 2.1

**24 Kasım 2026**

File tanımını üstveriler tarafından yönetilen veri çözümlemesini belirleyecek şekilde geliştirdik ve Stream'i bağımsız bir sıralı veri üretme veya alma mekanizması olarak yeniden tanımladık. Bu değişiklikler akışların diğer koleksiyonlara ek kısıtlamalar getirmeden sonlu veya sonsuz dizileri temsil etmesini sağlar.

### Revizyon 2

**21 Kasım 2026**

Belleğin ve saklanan değerlerin baytlar ve bayt dizileriyle temsilinde tutarsızlıklar belirledik. Word'ü temel bellek temsili olarak belirleyerek Bellek, İşlemler ve Bileşik yapılar arasındaki ilişkileri birleştirdik.

Dizi indeksleme ve koleksiyonlar arasındaki ilişkilerde tutarsızlıklar belirledik. Sonlu, bitişik indeksleri standartlaştırdık ve Array, File ve Stream arasındaki ilişkileri açıklığa kavuşturduk.

Yürütme ve bileşim ilişkilerinde fazlalıklar ve belirsizlikler belirledik. Uygulama bağımsızlığını koruyarak bu sorunları çözmek için prosedürleri, fonksiyonları, dağıtıcıları ve nesne ilişkilerini geliştirdik.

## Bellek

### Word

Sözcük, bellekte saklanan herhangi bir bit dizisi $w \in \mathrm{Bit}^n$ olup $n \in \mathbb{N}^+$ koşulunu sağlar.

### Address

Adres, herhangi bir sözcük $a \in A$ olup $A$ bir sözcük kümesidir ve $a$ belirtilen bir bellek yapısı içindeki konumu benzersiz olarak tanımlar.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

İşaretçi, herhangi bir fonksiyon $f_p : \{a\} \to B$ olup $a \in A$ bir adres ve $B$ bir sözcük kümesidir; $f_p$ fonksiyonunun her uygulanması $a$ tarafından tanımlanan bellek konumunda saklanan sözcüğü değerlendirir.

#### Pointer()

> $f_m : A \to B$ bir bellek eşlemesi olsun.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Değişken, herhangi bir fonksiyon $f_v : \{k\} \to B$ olup $k$ bir anahtar ve $B$ bir sözcük kümesidir; değişken anahtarı adrese bağlayıp o adreste saklanan sözcüğü değerlendirerek işaretçiyi genişletir.

#### Variable(k)

> $f_b : \{k\} \to \{a\}$ değişkenin bağlama fonksiyonu olsun.
>
> $f_p : \{a\} \to B$ bir işaretçi olsun.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Sabit, herhangi bir değişken $f_c : \{k\} \to B$ olup $k$ bir anahtar ve $B$ bir sözcük kümesidir; $k$ ile ilişkili sözcük atandıktan sonra değiştirilemez.

#### Constant(k)

> $b_0 \in B$, $k$ anahtarına atanan sözcük olsun.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$, $b_0$ atandıktan sonra.

## Koleksiyonlar

### Set

Küme, farklı sözcüklerden oluşan herhangi bir sonlu ve sırasız koleksiyondur.

#### Set()

> $B$ bir sözcük kümesi olsun.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Eşleme, herhangi bir fonksiyon $f_m : K \to V$ olup $K$ bir anahtar kümesi ve $V$ bir değer kümesidir; her anahtar tam olarak bir değerle ilişkilendirilir.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Dizi, herhangi bir fonksiyon $f_a : I \to V$ olup $I \subseteq \mathbb{N}$ sonlu, bitişik bir tamsayı indeksleri kümesi ve $V$ bir sözcük kümesidir; her indeks tam olarak bir değeri tanımlar.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Dosya, herhangi bir demet $(f_m,d)$ olup $d$ bir sözcük dizisi ve $f_m : I \times \{d\} \to \mathrm{Array}$ bir sözcük dizisiyle temsil edilen üstveri fonksiyonudur; $I$ sonlu, bitişik bir tamsayı indeksleri kümesidir ve $f_m$ verilerin $d$ üzerinden nasıl çözümlendiğini belirler.

#### File(i)

> $(f_m,d)$ bir dosya olsun.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Akış, herhangi bir fonksiyon $f_s$ olup $f_s$ fonksiyonunun her uygulanması sonlu veya sonsuz bir dizideki bir sonraki parçayı $c$ üretir ve $f_s$ sıralı veri üretme veya alma mekanizmasını belirler.

#### Stream()

> $f_c : K \to C$ bir parça çözümleme fonksiyonu olsun; $K \subseteq \mathbb{N}$ bitişik bir tamsayı indeksleri kümesi ve $C$ bir parça kümesidir.
>
> $k \in K$ bir sonraki parçanın indeksi olsun.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, her uygulamadan sonra $k$ ilerletilir.

## İşlemler

### Instruction

Komut, herhangi bir sözcük veya sonlu sözcük demeti $i \in B$ olup $B$ bir sözcükler veya sonlu sözcük demetleri kümesidir; her komut gerçekleştirilecek tek bir hesaplama işlemini temsil eder.

### Procedure

Prosedür, herhangi bir değişken $f_{proc} : \{k\} \to B$ olup $f_{proc}(k)$ bir komut dizisini $f_a : I \to V$ temsil eder; prosedür yürütüldüğünde her komut indeks sırasına göre gerçekleştirilir.

#### Procedure(k)

> $\mathrm{Procedure}(k)$, her $f_a(i)$ öğesinin $i \in I$ artan sırasında yürütülmesidir.

### Function

Fonksiyon, herhangi bir prosedür $f_{func} : \{k\} \to B$ olup yürütülmesi sonuç sözcüğünü veya sonucu temsil eden sözcük dizisinin ilk sözcüğünü tanımlayan bir adres $a_r \in A$ döndürür.

#### Function(k)

> $f_m : A \to B$ bir bellek eşlemesi olsun; $a_r \in A$ sonuç sözcüğünü $r \in B$ tanımlar.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## İş parçacıkları

### Process

Süreç, girdi alan, bir veya daha fazla prosedür veya fonksiyon yürüten ve çıktı üreten herhangi bir sınırlı yürütme akışıdır; süreç bir sistem içindeki ayrı bir dönüştürme birimini temsil eder.

### Thread

İş parçacığı, bir süreç içinde bulunan herhangi bir yürütme akışıdır ve o sürece ait prosedürlerin veya fonksiyonların yürütülebileceği bir yol sağlar.

#### Thread(p)

> $p$ bir süreç olsun.
>
> $(w_0, \dots, w_n)$, $p$ sürecine ait prosedür veya fonksiyonların sonlu bir demeti olsun.
>
> $\mathrm{Thread}(p)$, her $w_j$ öğesinin $j$ artan sırasında $p$ içinde yürütülmesidir.

### Dispatcher

Dağıtıcı, herhangi bir demet $(t,W,f_d)$ olup $t$ bir iş parçacığı, $W$ iş olarak kabul edilen prosedür veya fonksiyonların kümesi ve $f_d$, $W$ kümesinden iş seçen bir dağıtım kuralıdır; dağıtıcı seçilen işin kurala göre $t$ üzerinde yürütülmesini sağlar.

#### Dispatcher(t)

> $t$ bir iş parçacığı olsun.
>
> $W$ dağıtıcının kabul ettiği prosedür veya fonksiyonların kümesi olsun; $\forall w \in W$ için $w$ bir prosedür veya fonksiyondur.
>
> $f_d : \mathcal{P}^+(W) \to W$ kabul edilen işlerin boş olmayan bir alt kümesinden iş seçen bir dağıtım kuralı olsun.
>
> $\mathrm{Dispatcher}(t)$, seçilen her $f_d(W')$ öğesinin $t$ üzerinde yürütülmesidir; $W' \subseteq W$, $W' \neq \varnothing$ ve $f_d(W') \in W'$ koşulları geçerlidir.

## Bileşik yapılar

### Member

Üye, herhangi bir öğe $m \in M$ olup $M$ bir öğe kümesi ve $f_o : K \to M$ bir nesnenin üye eşlemesidir; $m = f_o(k)$ bir $k \in K$ anahtarı için geçerlidir.

### Object

Nesne, herhangi bir demet $(a,K,f_o)$ olup $a \in A$ bir adres, $K$ bir anahtar kümesi ve $f_o : K \to M$ bir üye eşlemesidir; $M$ bir öğe kümesidir ve nesne üyeleri $f_o$ aracılığıyla anahtarlara atanan adreslenebilir bir bileşik yapıyı temsil edebilir.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Alan, herhangi bir demet $(o,k,m)$ olup $o = (a,K,f_o)$ bir nesne, $k \in K$ bir anahtar ve $m = f_o(k)$ bir üyedir; alan nesnenin üye eşlemesinden çözümlenen anahtarlı bir üyeyi temsil eder.

#### Field(o,k)

> $o = (a,K,f_o)$ bir nesne olsun.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Metot, herhangi bir alan $(o,k,m)$ olup $m$ bir prosedür veya fonksiyondur; metot bir nesnenin anahtarlı, yürütülebilir üyesini temsil eder.

#### Method(o,k)

> $(o,k,m)$ bir alan olsun.
>
> $\mathrm{Method}(o,k) = (o,k,m)$; $m$ bir prosedür veya fonksiyondur.

### Property

Özellik, herhangi bir alan $(o,k,m)$ olup $m = (X,f_a)$ bir erişimci eşlemesidir, $X = \{\mathrm{Get}, \mathrm{Set}\}$ ve $f_a : X \to M$ her erişimciyi bir üyeye eşler; $f_a(\mathrm{Get})$ bir fonksiyon ve $f_a(\mathrm{Set})$ bir prosedürdür, böylece özellik anahtarlı üyenin hem alma hem atama davranışını tanımlayabilir.

#### Property(o,k)

> $(o,k,m)$ bir alan olsun; $m = (X,f_a)$ bir erişimci eşlemesidir.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> $(o,k,(X,f_a))$ bir özellik olsun.
>
> $\mathrm{Get}(o,k)$, $f_a(\mathrm{Get})$ fonksiyonunun uygulanmasıdır.

#### Set(o,k)

> $(o,k,(X,f_a))$ bir özellik olsun.
>
> $\mathrm{Set}(o,k)$, $f_a(\mathrm{Set})$ prosedürünün uygulanmasıdır.

### Structure

Yapı (genellikle `struct` olarak kısaltılır), herhangi bir nesne $s = (a,K,f_s)$ olup $K$ sonlu bir anahtar kümesi ve $f_s : K \to M$ yapı atandıktan sonra anahtarları değiştirilemeyen üye eşlemesidir; yapı anahtarlı üyelerinin yerleşimi sabit olan özel bir nesnedir.

#### Structure(s,k)

> $s = (a,K,f_s)$ bir yapı olsun.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Sınıf, herhangi bir nesne $c = (a_c,K_c,f_c)$ olup $K_c$ sonlu bir anahtar kümesi ve $f_c : K_c \to M$ bir üye tanımları eşlemesidir; sınıf, anahtarlı üyeleri diğer nesneleri üretmek için kullanılan üye yerleşimini tanımlayan özel bir nesnedir.

#### Class(c,a)

> $c = (a_c,K_c,f_c)$ bir sınıf olsun.
>
> $a \in A$, $c$ sınıfından üretilen nesneye atanmış adres olsun.
>
> $f_o : K_c \to M$, $f_c$ tanımlarına uyan bir üye eşlemesi olsun.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Arayüz, herhangi bir nesne $r = (a_r,K_r,f_r)$ olup $K_r$ sonlu bir anahtar kümesi ve $f_r : K_r \to M$ bir üye gereksinimleri eşlemesidir; arayüz, anahtarlı üyeleri başka bir nesnenin sağlaması gereken üyeleri tanımlayan özel bir nesnedir.

#### Interface(r,o)

> $r = (a_r,K_r,f_r)$ bir arayüz olsun.
>
> $o = (a,K,f_o)$ bir nesne olsun.
>
> $f_v : M \times M \to \{0,1\}$ bir üyenin başka bir üyenin gereksinimlerini karşılayıp karşılamadığını belirleyen doğrulama kuralı olsun.
>
> $\mathrm{Interface}(r,o)$, $K_r \subseteq K$ ve $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$ olduğunda geçerlidir.
