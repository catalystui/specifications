<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# FRELSPEC

<br/>

> **Especificação de Relações Fundamentais**<br/>
> Revisão 2.1<br/>
> 24 de novembro de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos os direitos reservados.<br/>
> <br/>
> As definições e os conceitos apresentados aqui descrevem construções matemáticas fundamentais e podem ser reformulados livremente.

## Introdução

A **Especificação de Relações Fundamentais (FRELSPEC)** estabelece as estruturas relacionais centrais que sustentam o ecossistema CatalystUI. Seu propósito é fornecer uma compreensão unificada das relações entre memória, coleções, operações e compostos na documentação, nas especificações, nas implementações e nas revisões de verificação, garantindo consistência, clareza e alinhamento.

Ao definir relações entre conceitos fundamentais de forma precisa e estável, a FRELSPEC fornece um ponto de referência comum para especificações de nível superior, permitindo que cada implementação estabeleça suas próprias regras e comportamentos. Assim, desenvolvedores, revisores e implementadores podem raciocinar a partir da mesma base para determinar se uma linguagem, serviço, framework ou sistema consegue representar as construções relacionais necessárias à conformidade com a especificação.

> [!IMPORTANT]
>
> Expressamos as definições usando uma forma derivada da notação da [teoria dos conjuntos](https://en.wikipedia.org/wiki/Set_theory). Essa abordagem fornece definições precisas e inequívocas, preservando clareza e concisão. Estruturamos as definições para facilitar a consulta, a interpretação clara e uma hierarquia conceitual consistente.

## Sumário

- [FRELSPEC](#frelspec)
  - [Introdução](#introdução)
  - [Sumário](#sumário)
  - [Revisões](#revisões)
    - [Revisão 2.1](#revisão-21)
    - [Revisão 2](#revisão-2)
  - [Memória](#memória)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Coleções](#coleções)
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
  - [Operações](#operações)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Encadeamento](#encadeamento)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Compostos](#compostos)
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

## Revisões

### Revisão 2.1

**24 de novembro de 2026**

Refinamos a definição de File para estabelecer a resolução de dados regida por metadados e redefinimos Stream como um mecanismo independente de geração ou recuperação sequencial de dados. Essas mudanças permitem que fluxos representem sequências finitas ou infinitas sem impor restrições adicionais às demais coleções.

### Revisão 2

**21 de novembro de 2026**

Identificamos inconsistências na representação da memória e dos valores armazenados por bytes e arrays de bytes. Estabelecemos Word como representação fundamental da memória, unificando as relações entre Memória, Operações e Compostos.

Identificamos inconsistências na indexação de arrays e nas relações entre coleções. Padronizamos índices finitos e contíguos e esclarecemos as relações entre Array, File e Stream.

Identificamos redundâncias e ambiguidades nas relações de execução e composição. Refinamos procedimentos, funções, despachantes e relações entre objetos para resolver esses problemas, preservando a independência de implementação.

## Memória

### Word

Uma palavra é qualquer sequência de bits $w \in \mathrm{Bit}^n$ armazenada na memória, tal que $n \in \mathbb{N}^+$.

### Address

Um endereço é qualquer palavra $a \in A$, em que $A$ é um conjunto de palavras, tal que $a$ identifica unicamente uma localização em uma estrutura de memória especificada.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Um ponteiro é qualquer função $f_p : \{a\} \to B$ tal que $a \in A$ é um endereço e $B$ é um conjunto de palavras, em que cada aplicação de $f_p$ avalia a palavra armazenada na localização de memória identificada por $a$.

#### Pointer()

> Seja $f_m : A \to B$ um mapa de memória.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Uma variável é qualquer função $f_v : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de palavras, em que a variável estende um ponteiro vinculando uma chave a um endereço e avaliando a palavra armazenada nesse endereço.

#### Variable(k)

> Seja $f_b : \{k\} \to \{a\}$ a função de vinculação da variável.
>
> Seja $f_p : \{a\} \to B$ um ponteiro.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Uma constante é qualquer variável $f_c : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de palavras, em que a palavra associada a $k$ não pode ser alterada depois de atribuída.

#### Constant(k)

> Seja $b_0 \in B$ a palavra atribuída a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ após a atribuição de $b_0$.

## Coleções

### Set

Um conjunto é qualquer coleção finita e não ordenada de palavras distintas.

#### Set()

> Seja $B$ um conjunto de palavras.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Um mapa é qualquer função $f_m : K \to V$ tal que $K$ é um conjunto de chaves e $V$ é um conjunto de valores, em que cada chave é associada a exatamente um valor.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Um array é qualquer função $f_a : I \to V$ tal que $I \subseteq \mathbb{N}$ é um conjunto finito e contíguo de índices inteiros e $V$ é um conjunto de palavras, em que cada índice identifica exatamente um valor.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Um arquivo é qualquer tupla $(f_m,d)$ tal que $d$ é um array de palavras e $f_m : I \times \{d\} \to \mathrm{Array}$ é uma função de metadados representada por um array de palavras, em que $I$ é um conjunto finito e contíguo de índices inteiros e $f_m$ determina como os dados são resolvidos a partir de $d$.

#### File(i)

> Seja $(f_m,d)$ um arquivo.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Um fluxo é qualquer função $f_s$ tal que cada aplicação de $f_s$ produz o próximo fragmento $c$ em uma sequência finita ou infinita, em que $f_s$ estabelece um mecanismo de geração ou recuperação sequencial de dados.

#### Stream()

> Seja $f_c : K \to C$ uma função de resolução de fragmentos, em que $K \subseteq \mathbb{N}$ é um conjunto contíguo de índices inteiros e $C$ é um conjunto de fragmentos.
>
> Seja $k \in K$ o índice do próximo fragmento.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, avançando $k$ após cada aplicação.

## Operações

### Instruction

Uma instrução é qualquer palavra ou tupla finita de palavras $i \in B$ tal que $B$ é um conjunto de palavras ou tuplas finitas de palavras, em que cada instrução representa uma única operação computacional a ser realizada.

### Procedure

Um procedimento é qualquer variável $f_{proc} : \{k\} \to B$ tal que $f_{proc}(k)$ representa um array de instruções $f_a : I \to V$, em que a execução do procedimento realiza cada instrução na ordem dos índices.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ é a execução de cada $f_a(i)$ em ordem crescente de $i \in I$.

### Function

Uma função é qualquer procedimento $f_{func} : \{k\} \to B$ tal que sua execução retorna um endereço $a_r \in A$ que identifica a palavra resultante ou a primeira palavra de um array de palavras que representa o resultado.

#### Function(k)

> Seja $f_m : A \to B$ um mapa de memória, em que $a_r \in A$ identifica a palavra resultante $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Encadeamento

### Process

Um processo é qualquer fluxo de execução delimitado que recebe entrada, executa um ou mais procedimentos ou funções e produz saída, representando uma unidade distinta de transformação dentro de um sistema.

### Thread

Uma thread é qualquer fluxo de execução contido em um processo, fornecendo um caminho pelo qual os procedimentos ou funções desse processo podem ser executados.

#### Thread(p)

> Seja $p$ um processo.
>
> Seja $(w_0, \dots, w_n)$ uma tupla finita de procedimentos ou funções pertencentes a $p$.
>
> $\mathrm{Thread}(p)$ é a execução de cada $w_j$ em ordem crescente de $j$ dentro de $p$.

### Dispatcher

Um despachante é qualquer tupla $(t,W,f_d)$ tal que $t$ é uma thread, $W$ é um conjunto de procedimentos ou funções aceitos como trabalho e $f_d$ é uma regra de despacho que seleciona trabalho de $W$, em que o despachante faz o trabalho selecionado ser executado em $t$ de acordo com essa regra.

#### Dispatcher(t)

> Seja $t$ uma thread.
>
> Seja $W$ um conjunto de procedimentos ou funções aceitos pelo despachante, em que $\forall w \in W$, $w$ é um procedimento ou função.
>
> Seja $f_d : \mathcal{P}^+(W) \to W$ uma regra de despacho que seleciona trabalho de um subconjunto não vazio do trabalho aceito.
>
> $\mathrm{Dispatcher}(t)$ é a execução de cada $f_d(W')$ selecionado em $t$, em que $W' \subseteq W$, $W' \neq \varnothing$ e $f_d(W') \in W'$.

## Compostos

### Member

Um membro é qualquer elemento $m \in M$ tal que $M$ é um conjunto de elementos e $f_o : K \to M$ é o mapa de membros de um objeto, em que $m = f_o(k)$ para alguma chave $k \in K$.

### Object

Um objeto é qualquer tupla $(a,K,f_o)$ tal que $a \in A$ é um endereço, $K$ é um conjunto de chaves e $f_o : K \to M$ é um mapa de membros, em que $M$ é um conjunto de elementos, permitindo que o objeto represente um composto endereçável cujos membros são atribuídos a chaves por meio de $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Um campo é qualquer tupla $(o,k,m)$ tal que $o = (a,K,f_o)$ é um objeto, $k \in K$ é uma chave e $m = f_o(k)$ é um membro, em que o campo representa um membro identificado por chave e resolvido a partir do mapa de membros do objeto.

#### Field(o,k)

> Seja $o = (a,K,f_o)$ um objeto.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Um método é qualquer campo $(o,k,m)$ tal que $m$ é um procedimento ou função, em que o método representa um membro executável de um objeto identificado por chave.

#### Method(o,k)

> Seja $(o,k,m)$ um campo.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, em que $m$ é um procedimento ou função.

### Property

Uma propriedade é qualquer campo $(o,k,m)$ tal que $m = (X,f_a)$ é um mapa de acessores, $X = \{\mathrm{Get}, \mathrm{Set}\}$, e $f_a : X \to M$ mapeia cada acessor a um membro, em que $f_a(\mathrm{Get})$ é uma função e $f_a(\mathrm{Set})$ é um procedimento, permitindo à propriedade definir tanto o comportamento de recuperação quanto o de atribuição de um membro identificado por chave.

#### Property(o,k)

> Seja $(o,k,m)$ um campo, em que $m = (X,f_a)$ é um mapa de acessores.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Seja $(o,k,(X,f_a))$ uma propriedade.
>
> $\mathrm{Get}(o,k)$ é a aplicação de $f_a(\mathrm{Get})$.

#### Set(o,k)

> Seja $(o,k,(X,f_a))$ uma propriedade.
>
> $\mathrm{Set}(o,k)$ é a aplicação de $f_a(\mathrm{Set})$.

### Structure

Uma estrutura (frequentemente abreviada como `struct`) é qualquer objeto $s = (a,K,f_s)$ tal que $K$ é um conjunto finito de chaves e $f_s : K \to M$ é um mapa de membros cujas chaves não podem ser alteradas após a atribuição da estrutura, que é um objeto especializado com disposição fixa de membros identificados por chave.

#### Structure(s,k)

> Seja $s = (a,K,f_s)$ uma estrutura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Uma classe é qualquer objeto $c = (a_c,K_c,f_c)$ tal que $K_c$ é um conjunto finito de chaves e $f_c : K_c \to M$ é um mapa de definições de membros, em que a classe é um objeto especializado cujos membros identificados por chave definem a disposição de membros usada para produzir outros objetos.

#### Class(c,a)

> Seja $c = (a_c,K_c,f_c)$ uma classe.
>
> Seja $a \in A$ um endereço atribuído a um objeto produzido a partir de $c$.
>
> Seja $f_o : K_c \to M$ um mapa de membros que segue as definições de $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Uma interface é qualquer objeto $r = (a_r,K_r,f_r)$ tal que $K_r$ é um conjunto finito de chaves e $f_r : K_r \to M$ é um mapa de requisitos de membros, em que a interface é um objeto especializado cujos membros identificados por chave definem os membros que outro objeto deve fornecer.

#### Interface(r,o)

> Seja $r = (a_r,K_r,f_r)$ uma interface.
>
> Seja $o = (a,K,f_o)$ um objeto.
>
> Seja $f_v : M \times M \to \{0,1\}$ uma regra de validação que determina se um membro satisfaz os requisitos de outro membro.
>
> $\mathrm{Interface}(r,o)$ é válido quando $K_r \subseteq K$ e $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
