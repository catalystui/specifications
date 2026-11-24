<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagasalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request matapos mapatunayan ang salin. -->

# FRELSPEC

<br/>

> **Espesipikasyon ng mga Pundamental na Ugnayan**<br/>
> Rebisyon 2.1<br/>
> Nobyembre 24, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Nakalaan ang lahat ng karapatan.<br/>
> <br/>
> Inilalarawan ng mga depinisyon at konseptong inilahad dito ang mga pundamental na matematikal na konstruksyon at maaari itong malayang ipahayag muli.

## Panimula

Itinatatag ng **Espesipikasyon ng mga Pundamental na Ugnayan (FRELSPEC)** ang mga pangunahing estrukturang relasyonal na pundasyon ng ekosistema ng CatalystUI. Layunin nitong magbigay ng iisang pag-unawa sa mga ugnayan ng memorya, mga koleksiyon, mga operasyon, at mga komposit sa dokumentasyon, mga espesipikasyon, mga implementasyon, at mga pagsusuri sa beripikasyon, upang matiyak ang pagkakapare-pareho, kalinawan, at pagkakatugma.

Sa pamamagitan ng tumpak at matatag na pagtukoy sa mga ugnayan ng mga pundamental na konsepto, nagbibigay ang FRELSPEC ng karaniwang sanggunian para sa mga espesipikasyon sa mas mataas na antas habang pinahihintulutan ang bawat implementasyon na magtakda ng sariling mga tuntunin at pag-uugali. Dahil dito, makapagsusuri ang mga developer, tagasuri, at tagapagpatupad mula sa parehong batayan kung kayang katawanin ng isang wika, serbisyo, framework, o sistema ang mga relasyonal na konstruksyong kailangan upang umayon sa espesipikasyon.

> [!IMPORTANT]
>
> Ipinapahayag namin ang mga depinisyon gamit ang isang hinangong anyo ng notasyon ng [teorya ng mga set](https://en.wikipedia.org/wiki/Set_theory). Nagbibigay ito ng tumpak at di-malabong mga depinisyon habang pinananatili ang kalinawan at kaiklian. Inaayos namin ang mga ito upang madaling sangguniin, malinaw na bigyang-kahulugan, at magkaroon ng pare-parehong konseptuwal na hirarkiya.

## Talaan ng nilalaman

- [FRELSPEC](#frelspec)
  - [Panimula](#panimula)
  - [Talaan ng nilalaman](#talaan-ng-nilalaman)
  - [Mga rebisyon](#mga-rebisyon)
    - [Rebisyon 2.1](#rebisyon-21)
    - [Rebisyon 2](#rebisyon-2)
  - [Memorya](#memorya)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Mga koleksiyon](#mga-koleksiyon)
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
  - [Mga operasyon](#mga-operasyon)
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
  - [Mga komposit](#mga-komposit)
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

## Mga rebisyon

### Rebisyon 2.1

**Nobyembre 24, 2026**

Pinino namin ang depinisyon ng File upang itatag ang resolusyon ng data na pinamamahalaan ng metadata at muling dinepinisa ang Stream bilang independiyenteng mekanismo ng sunud-sunod na pagbuo o pagkuha ng data. Pinahihintulutan ng mga pagbabagong ito ang mga stream na kumatawan sa may hangganan o walang hangganang mga sequence nang hindi nagdaragdag ng mga limitasyon sa ibang koleksiyon.

### Rebisyon 2

**Nobyembre 21, 2026**

Natukoy namin ang mga hindi pagkakapare-pareho sa representasyon ng memorya at nakaimbak na mga value gamit ang mga byte at byte array. Itinatag namin ang Word bilang pundamental na representasyon ng memorya, pinag-iisa ang mga ugnayan sa Memorya, mga Operasyon, at mga Komposit.

Natukoy namin ang mga hindi pagkakapare-pareho sa pag-index ng array at sa mga ugnayan ng mga koleksiyon. Ginawang pamantayan ang may hangganan at magkakasunod na mga index at nilinaw ang mga ugnayan ng Array, File, at Stream.

Natukoy namin ang mga kalabisan at kalabuan sa mga ugnayan ng execution at komposisyon. Pinino namin ang mga procedure, function, dispatcher, at mga ugnayan ng object upang malutas ang mga ito habang pinananatili ang kalayaan mula sa implementasyon.

## Memorya

### Word

Ang word ay anumang sequence ng mga bit $w \in \mathrm{Bit}^n$ na nakaimbak sa memorya, na tumutupad sa $n \in \mathbb{N}^+$.

### Address

Ang address ay anumang word $a \in A$, kung saan ang $A$ ay set ng mga word, at natatanging tinutukoy ng $a$ ang isang lokasyon sa itinakdang estruktura ng memorya.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Ang pointer ay anumang function $f_p : \{a\} \to B$ kung saan ang $a \in A$ ay address at ang $B$ ay set ng mga word, at ang bawat aplikasyon ng $f_p$ ay nag-eevaluate sa word na nakaimbak sa lokasyon ng memorya na tinutukoy ng $a$.

#### Pointer()

> Ipagpalagay na ang $f_m : A \to B$ ay memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Ang variable ay anumang function $f_v : \{k\} \to B$ kung saan ang $k$ ay key at ang $B$ ay set ng mga word, at pinalalawak ng variable ang pointer sa pagbibigkis ng key sa address at pag-evaluate sa word na nakaimbak sa address na iyon.

#### Variable(k)

> Ipagpalagay na ang $f_b : \{k\} \to \{a\}$ ay binding function ng variable.
>
> Ipagpalagay na ang $f_p : \{a\} \to B$ ay pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Ang constant ay anumang variable $f_c : \{k\} \to B$ kung saan ang $k$ ay key at ang $B$ ay set ng mga word, at ang word na nauugnay sa $k$ ay hindi maaaring baguhin matapos itong maitalaga.

#### Constant(k)

> Ipagpalagay na ang $b_0 \in B$ ay word na itinalaga sa $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ matapos maitalaga ang $b_0$.

## Mga koleksiyon

### Set

Ang set ay anumang may hangganan at walang pagkakasunod-sunod na koleksiyon ng magkakaibang word.

#### Set()

> Ipagpalagay na ang $B$ ay set ng mga word.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Ang map ay anumang function $f_m : K \to V$ kung saan ang $K$ ay set ng mga key at ang $V$ ay set ng mga value, at bawat key ay nauugnay sa eksaktong isang value.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Ang array ay anumang function $f_a : I \to V$ kung saan ang $I \subseteq \mathbb{N}$ ay may hangganan at magkakasunod na set ng mga integer index at ang $V$ ay set ng mga word, at bawat index ay tumutukoy sa eksaktong isang value.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Ang file ay anumang tuple $(f_m,d)$ kung saan ang $d$ ay array ng mga word at ang $f_m : I \times \{d\} \to \mathrm{Array}$ ay metadata function na kinakatawan ng array ng mga word, at ang $I$ ay may hangganan at magkakasunod na set ng mga integer index, at tinutukoy ng $f_m$ kung paano nireresolba ang data mula sa $d$.

#### File(i)

> Ipagpalagay na ang $(f_m,d)$ ay file.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Ang stream ay anumang function $f_s$ kung saan ang bawat aplikasyon ng $f_s$ ay nagbubunga ng susunod na chunk $c$ sa may hangganan o walang hangganang sequence, at itinatatag ng $f_s$ ang mekanismo ng sunud-sunod na pagbuo o pagkuha ng data.

#### Stream()

> Ipagpalagay na ang $f_c : K \to C$ ay chunk-resolution function, kung saan ang $K \subseteq \mathbb{N}$ ay magkakasunod na set ng mga integer index at ang $C$ ay set ng mga chunk.
>
> Ipagpalagay na ang $k \in K$ ay index ng susunod na chunk.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, na isinusulong ang $k$ pagkatapos ng bawat aplikasyon.

## Mga operasyon

### Instruction

Ang instruction ay anumang word o may hangganang tuple ng mga word $i \in B$ kung saan ang $B$ ay set ng mga word o may hangganang tuple ng mga word, at bawat instruction ay kumakatawan sa isang computational operation na isasagawa.

### Procedure

Ang procedure ay anumang variable $f_{proc} : \{k\} \to B$ kung saan ang $f_{proc}(k)$ ay kumakatawan sa array ng mga instruction $f_a : I \to V$, at ang pag-execute sa procedure ay nagsasagawa ng bawat instruction ayon sa pagkakasunod-sunod ng index.

#### Procedure(k)

> Ang $\mathrm{Procedure}(k)$ ay ang execution ng bawat $f_a(i)$ sa pataas na pagkakasunod-sunod ng $i \in I$.

### Function

Ang function ay anumang procedure $f_{func} : \{k\} \to B$ na kapag in-execute ay nagbabalik ng address $a_r \in A$ na tumutukoy sa resultang word o sa unang word ng array ng mga word na kumakatawan sa resulta.

#### Function(k)

> Ipagpalagay na ang $f_m : A \to B$ ay memory map, kung saan tinutukoy ng $a_r \in A$ ang resultang word $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Threading

### Process

Ang process ay anumang may hangganang daloy ng execution na tumatanggap ng input, nag-eexecute ng isa o higit pang procedure o function, at nagbubunga ng output, kung saan ang process ay kumakatawan sa isang natatanging yunit ng transpormasyon sa loob ng sistema.

### Thread

Ang thread ay anumang daloy ng execution na nakapaloob sa process, na nagbibigay ng isang landas kung saan maaaring i-execute ang mga procedure o function na kabilang sa process na iyon.

#### Thread(p)

> Ipagpalagay na ang $p$ ay process.
>
> Ipagpalagay na ang $(w_0, \dots, w_n)$ ay may hangganang tuple ng mga procedure o function na kabilang sa $p$.
>
> Ang $\mathrm{Thread}(p)$ ay ang execution ng bawat $w_j$ sa pataas na pagkakasunod-sunod ng $j$ sa loob ng $p$.

### Dispatcher

Ang dispatcher ay anumang tuple $(t,W,f_d)$ kung saan ang $t$ ay thread, ang $W$ ay set ng mga procedure o function na tinatanggap bilang gawain, at ang $f_d$ ay dispatch rule na pumipili ng gawain mula sa $W$, at ipinapa-execute ng dispatcher ang napiling gawain sa $t$ ayon sa tuntunin.

#### Dispatcher(t)

> Ipagpalagay na ang $t$ ay thread.
>
> Ipagpalagay na ang $W$ ay set ng mga procedure o function na tinatanggap ng dispatcher, kung saan $\forall w \in W$, ang $w$ ay procedure o function.
>
> Ipagpalagay na ang $f_d : \mathcal{P}^+(W) \to W$ ay dispatch rule na pumipili ng gawain mula sa di-bakanteng subset ng tinanggap na gawain.
>
> Ang $\mathrm{Dispatcher}(t)$ ay ang execution ng bawat napiling $f_d(W')$ sa $t$, kung saan $W' \subseteq W$, $W' \neq \varnothing$, at $f_d(W') \in W'$.

## Mga komposit

### Member

Ang member ay anumang elemento $m \in M$ kung saan ang $M$ ay set ng mga elemento at ang $f_o : K \to M$ ay member map ng object, kung saan $m = f_o(k)$ para sa isang key $k \in K$.

### Object

Ang object ay anumang tuple $(a,K,f_o)$ kung saan ang $a \in A$ ay address, ang $K$ ay set ng mga key, at ang $f_o : K \to M$ ay member map, kung saan ang $M$ ay set ng mga elemento, na nagpapahintulot sa object na kumatawan sa isang addressable na komposit na ang mga member ay itinatalaga sa mga key sa pamamagitan ng $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Ang field ay anumang tuple $(o,k,m)$ kung saan ang $o = (a,K,f_o)$ ay object, ang $k \in K$ ay key, at ang $m = f_o(k)$ ay member, at ang field ay kumakatawan sa isang member na may key na nireresolba mula sa member map ng object.

#### Field(o,k)

> Ipagpalagay na ang $o = (a,K,f_o)$ ay object.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Ang method ay anumang field $(o,k,m)$ kung saan ang $m$ ay procedure o function, at ang method ay kumakatawan sa executable na member ng object na may key.

#### Method(o,k)

> Ipagpalagay na ang $(o,k,m)$ ay field.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, kung saan ang $m$ ay procedure o function.

### Property

Ang property ay anumang field $(o,k,m)$ kung saan ang $m = (X,f_a)$ ay accessor map, $X = \{\mathrm{Get}, \mathrm{Set}\}$, at iminamapa ng $f_a : X \to M$ ang bawat accessor sa isang member, kung saan ang $f_a(\mathrm{Get})$ ay function at ang $f_a(\mathrm{Set})$ ay procedure, na nagpapahintulot sa property na tukuyin ang pagkuha at pagtatalaga ng member na may key.

#### Property(o,k)

> Ipagpalagay na ang $(o,k,m)$ ay field, kung saan ang $m = (X,f_a)$ ay accessor map.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Ipagpalagay na ang $(o,k,(X,f_a))$ ay property.
>
> Ang $\mathrm{Get}(o,k)$ ay aplikasyon ng $f_a(\mathrm{Get})$.

#### Set(o,k)

> Ipagpalagay na ang $(o,k,(X,f_a))$ ay property.
>
> Ang $\mathrm{Set}(o,k)$ ay aplikasyon ng $f_a(\mathrm{Set})$.

### Structure

Ang structure (madalas pinaikli bilang `struct`) ay anumang object $s = (a,K,f_s)$ kung saan ang $K$ ay may hangganang set ng mga key at ang $f_s : K \to M$ ay member map na ang mga key ay hindi maaaring baguhin matapos maitalaga ang structure, at ang structure ay isang espesyalisadong object na may nakapirming layout ng mga member na may key.

#### Structure(s,k)

> Ipagpalagay na ang $s = (a,K,f_s)$ ay structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Ang class ay anumang object $c = (a_c,K_c,f_c)$ kung saan ang $K_c$ ay may hangganang set ng mga key at ang $f_c : K_c \to M$ ay map ng mga depinisyon ng member, at ang class ay isang espesyalisadong object na ang mga member na may key ay tumutukoy sa layout na ginagamit sa paglikha ng ibang object.

#### Class(c,a)

> Ipagpalagay na ang $c = (a_c,K_c,f_c)$ ay class.
>
> Ipagpalagay na ang $a \in A$ ay address na itinalaga sa object na ginawa mula sa $c$.
>
> Ipagpalagay na ang $f_o : K_c \to M$ ay member map na sumusunod sa mga depinisyon ng $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Ang interface ay anumang object $r = (a_r,K_r,f_r)$ kung saan ang $K_r$ ay may hangganang set ng mga key at ang $f_r : K_r \to M$ ay map ng mga requirement ng member, at ang interface ay isang espesyalisadong object na ang mga member na may key ay tumutukoy sa mga member na dapat ibigay ng ibang object.

#### Interface(r,o)

> Ipagpalagay na ang $r = (a_r,K_r,f_r)$ ay interface.
>
> Ipagpalagay na ang $o = (a,K,f_o)$ ay object.
>
> Ipagpalagay na ang $f_v : M \times M \to \{0,1\}$ ay validation rule na tumutukoy kung natutugunan ng isang member ang mga requirement ng ibang member.
>
> Ang $\mathrm{Interface}(r,o)$ ay totoo kapag $K_r \subseteq K$ at $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
