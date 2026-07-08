<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# FRELSPEC

<br/>

> **Especificação de Relações Fundamentais**<br/>
> Revisão 1<br/>
> 7 de julho de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos os direitos reservados.<br/>
> <br/>
> As definições e os conceitos apresentados aqui descrevem construções matemáticas fundamentais e podem ser reexpressos livremente.

## Introdução

A **Foundational Relations Specification (FRELSPEC)** estabelece as estruturas relacionais centrais que sustentam o ecossistema CatalystUI. Seu propósito é fornecer um entendimento unificado de como valores, memória, operações e compostos se associam em documentações, especificações, implementações e revisões de verificação, garantindo consistência, clareza e alinhamento.

Ao definir relações entre conceitos fundamentais de forma precisa e estável, a FRELSPEC fornece um ponto de referência comum para especificações de nível superior. Isso permite que desenvolvedores, revisores e implementadores raciocinem a partir da mesma base ao determinar se uma linguagem, serviço, framework ou sistema consegue representar as construções relacionais exigidas para ser considerado dentro da especificação.

> [!IMPORTANT]
>
> Expressamos as definições usando uma forma derivada da notação de [teoria dos conjuntos](https://en.wikipedia.org/wiki/Set_theory). Essa abordagem fornece definições precisas e não ambíguas, mantendo clareza e concisão. Estruturamos essas definições para apoiar referência fácil, interpretação clara e uma hierarquia conceitual consistente.

## Sumário

- [FRELSPEC](#frelspec)
  - [Introdução](#introduction)
  - [Sumário](#table-of-contents)
  - [Coleções](#collections)
    - [Conjunto](#set)
    - [Mapa](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [Arquivo](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Memória](#memory)
    - [Endereço](#address)
    - [Ponteiro](#pointer)
      - [Pointer()](#pointer-1)
    - [Variável](#variable)
      - [Variable(k)](#variablek)
    - [Constante](#constant)
      - [Constant(k)](#constantk)
  - [Operações](#operations)
    - [Instrução](#instruction)
    - [Procedimento](#procedure)
      - [Procedure(k)](#procedurek)
    - [Função](#function)
      - [Function(k)](#functionk)
  - [Encadeamento](#threading)
    - [Processo](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Compostos](#composites)
    - [Membro](#member)
    - [Objeto](#object)
      - [Object(k)](#objectk)
    - [Campo](#field)
      - [Field(k)](#fieldk)
    - [Método](#method)
      - [Method(k)](#methodk)
    - [Propriedade](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Estrutura](#structure)
      - [Structure(k)](#structurek)
    - [Classe](#class)
      - [Class(a)](#classa)
    - [Interface](#interface)
      - [Interface(o)](#interfaceo)

## Coleções

### Conjunto

Um conjunto é qualquer coleção de elementos distintos.

### Mapa

Um mapa é qualquer função $f_m : K \to V$ tal que $K$ é um conjunto de chaves e $V$ é um conjunto de valores.

#### Mapa(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Um array é qualquer função $f_a : I \to V$ tal que $I \subset \mathbb{N}$, $I$ é um conjunto finito e contíguo de inteiros, e $V$ é um conjunto de valores.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### Arquivo

Um arquivo é qualquer função $f_f : I \to B$ tal que $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ é um conjunto finito e contíguo de inteiros, e $b$ é um conjunto de bytes, em que $f_f$ se origina de um mecanismo de armazenamento persistente de dados.

#### Arquivo(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

Um stream é qualquer função $f_s$ tal que cada aplicação de $f_s$ produz o próximo bloco $f_c : I \to B$ em uma sequência de bytes, em que $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ é um conjunto finito e contíguo de inteiros, $B$ é um conjunto de bytes, e $f_s$ se origina de um mecanismo de geração ou recuperação sequencial de dados.

#### Stream()

> Seja $c_k : I_k \to B$ o bloco retornado pela $k$-th application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ na $k$-ésima aplicação.

## Memória

### Endereço

Um endereço é qualquer elemento $a \in A$ tal que $A$ é um conjunto de endereços, em que cada endereço $a$ identifica de forma única uma localização em uma estrutura de memória.

### Ponteiro

Um ponteiro é qualquer função $f_p : \{a\} \to B$ tal que $a \in A$ é um endereço e $B$ é um conjunto de arrays de bytes, em que cada aplicação de $f_p$ avalia o array de bytes armazenado na localização de memória identificada por seu endereço vinculado.

#### Ponteiro()

> Seja $f_m : A \to B$ um mapa de memória.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variável

Uma variável é qualquer função $f_v : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de arrays de bytes, em que a variável estende um ponteiro ao vincular uma chave a um endereço e avaliar o array de bytes armazenado na localização de memória identificada por esse endereço.

#### Variável(k)

> Seja $f_b : \{k\} \to \{a\}$ be a função de vínculo da variável.
>
> Seja $f_p : \{a\} \to B$ um ponteiro.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constante

Uma constante é qualquer variável $f_c : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de arrays de bytes, em que o array de bytes associado a $k$ não pode ser alterado depois de atribuído.

#### Constante(k)

> Seja $b_0 \in B$ o array de bytes atribuído a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ depois que $b_0$ é atribuído.


## Operações

### Instrução

Uma instrução é qualquer array de bytes $i \in B$ tal que $B$ é um conjunto de arrays de bytes, em que cada instrução representa uma única operação computacional a ser executada.

### Procedimento

Um procedimento é qualquer variável $f_{proc} : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de arrays de bytes, em que cada aplicação do procedimento avalia o array de bytes associado a $k$ como uma sequência finita e ordenada de instruções e executa essas instruções na ordem representada sem definir um valor retornado.

#### Procedimento(k)

> Seja $b \in B$ tal que $f_{proc}(k) = b$.
>
> Seja $(i_0,\dots,i_n)$ a sequência finita e ordenada de instruções representada por $b$, em que $\forall j \in \{0,\dots,n\}, i_j$ é uma instrução.
>
> $\mathrm{Procedure}(k)$ é a execução de cada $i_j$ em ordem crescente de $j$.

### Função

Uma função é qualquer procedimento $f_{func} : \{k\} \to B$ tal que $k$ é uma chave e $B$ é um conjunto de arrays de bytes, em que cada aplicação da função avalia o array de bytes associado a $k$ como uma sequência finita e ordenada de instruções, executa essas instruções na ordem representada e, depois que a execução é concluída, atribui um array de bytes resultante a algum endereço na memória que pode ser avaliado como o valor retornado pela função.

#### Função(k)

> Seja $b \in B$ tal que $f_{func}(k) = b$.
>
> Seja $(i_0,\dots,i_n)$ a sequência finita e ordenada de instruções representada por $b$, em que $\forall j \in \{0,\dots,n\}, i_j$ é uma instrução.
>
> Seja $a_r \in A$ um endereço atribuído depois que a execução é concluída.
>
> Seja $f_m : A \to B$ um mapa de memória.
>
> $\mathrm{Function}(k)$ é a execução de cada $i_j$ em ordem crescente de $j$, em que $\exists b_r \in B : f_m(a_r) = b_r$ depois que a execução é concluída.
>
> $\mathrm{Function}(k) = b_r$

## Encadeamento

### Processo

Um processo é qualquer fluxo de execução limitado que aceita entrada, executa uma ou mais instruções e produz saída, em que o processo representa uma unidade distinta de transformação dentro de um sistema.

### Thread

Uma thread é qualquer fluxo de execução contido em um processo, em que a thread fornece um caminho pelo qual sequências ordenadas de instruções pertencentes a esse processo podem ser executadas.

#### Thread(p)

> Seja $p$ um processo.
>
> Seja $(i_0,\dots,i_n)$ uma sequência finita e ordenada de instruções pertencente a $p$.
>
> $\mathrm{Thread}(p)$ é a execução de cada $i_j$ em ordem crescente de $j$ dentro de $p$.

### Dispatcher

Um dispatcher é qualquer tupla $(t,W,f_d)$ tal que $t$ é uma thread, $W$ é um conjunto de procedimentos ou funções aceitos como trabalho, e $f_d$ é uma regra de despacho que seleciona trabalho de $W$, em que o dispatcher faz o trabalho selecionado ser executado em $t$ de acordo com a regra de despacho.

#### Dispatcher(t)

> Seja $t$ uma thread.
>
> Seja $W$ um conjunto de procedimentos ou funções aceitos pelo dispatcher, em que $\forall w \in W$, $w$ é um procedimento ou função.
>
> Seja $f_d : \mathcal{P}(W) \to W$ uma regra de despacho que seleciona trabalho de um subconjunto não vazio de trabalho aceito.
>
> $\mathrm{Dispatcher}(t)$ é a execução de cada selected $f_d(W')$ on $t$, em que $W' \subseteq W$ and $W' \neq \varnothing$.

## Compostos

### Membro

Um membro é qualquer elemento $m \in M$ tal que $M$ é um conjunto de membros, em que um membro é um valor que pode ser atribuído a uma chave dentro do mapa de membros de um objeto.

### Objeto

Um objeto é qualquer tupla $(a,K,f_o)$ tal que $a \in A$ é um endereço, $K$ é um conjunto de chaves, e $f_o : K \to M$ é um mapa de membros, em que $M$ é um conjunto de membros, permitindo que o objeto represente um composto endereçável cujos membros são atribuídos a chaves por meio de $f_o$.

#### Objeto(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Campo

Um campo é qualquer tupla $(o,k,m)$ tal que $o = (a,K,f_o)$ é um objeto, $k \in K$ é uma chave, $m \in M$ é um membro, e $f_o(k) = m$, em que o campo representa um membro com chave resolvido a partir do mapa de membros de um objeto.

#### Campo(k)

> Seja $o = (a,K,f_o)$ um objeto.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Método

Um método é qualquer campo $(o,k,m)$ tal que $m$ é um procedimento ou função, em que o método representa um membro executável com chave de um objeto.

#### Método(k)

> Seja $o = (a,K,f_o)$ um objeto.
>
> Seja $k \in K$ uma chave.
>
> Seja $m \in M$ um membro tal que $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ quando $m$ é um procedimento ou função.

### Propriedade

Uma propriedade é qualquer campo $(o,k,m)$ tal que $m = (A,f_a)$ é um mapa de acessores, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, e $f_a : A \to M$ mapeia cada acessor para um membro, em que $f_a(\mathrm{Get})$ é uma função e $f_a(\mathrm{Set})$ é um procedimento, permitindo que a propriedade defina tanto o comportamento de recuperação quanto o de atribuição de um membro com chave.

#### Propriedade(k)

> Seja $(o,k,m)$ um campo.
>
> Seja $m = (A,f_a)$ um mapa de acessores.
>
> Seja $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, em que $g$ é uma função.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, em que $s$ é um procedimento.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Seja $(o,k,(A,f_a))$ uma propriedade.
>
> Seja $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ é a aplicação de $g$.

#### Conjunto(k)

> Seja $(o,k,(A,f_a))$ uma propriedade.
>
> Seja $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ é a aplicação de $s$.

### Estrutura

Uma estrutura (frequentemente abreviada como `struct`) é qualquer objeto $s = (a,K,f_s)$ tal que $K$ é um conjunto finito de chaves e $f_s : K \to M$ é um mapa de membros que não pode ser alterado depois que a struct é atribuída, em que a struct é um objeto especializado cujo layout de membros com chave é fixo.

#### Estrutura(k)

> Seja $s = (a,K,f_s)$ uma estrutura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Classe

Uma classe é qualquer objeto $c = (a_c,K_c,f_c)$ tal que $K_c$ é um conjunto finito de chaves e $f_c : K_c \to M$ é um mapa de definição de membros, em que a classe é um objeto especializado cujos membros com chave definem o layout de membros usado para produzir outros objetos.

#### Classe(a)

> Seja $c = (a_c,K_c,f_c)$ uma classe.
>
> Seja $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

Uma interface é qualquer objeto $r = (a_r,K_r,f_r)$ tal que $K_r$ é um conjunto finito de chaves e $f_r : K_r \to M$ é um mapa de requisitos de membros, em que a interface é um objeto especializado cujos membros com chave definem os membros que devem ser fornecidos por outro objeto.

#### Interface(o)

> Seja $r = (a_r,K_r,f_r)$ uma interface.
>
> Seja $o = (a,K,f_o)$ um objeto.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
