<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# FDEFSPEC

<br/>

> **Especificação de Definições Fundamentais**<br/>
> Revisão 1<br/>
> 23 de março de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos os direitos reservados.<br/>
> <br/>
> As definições e os conceitos apresentados aqui descrevem construções matemáticas fundamentais e podem ser reexpressos livremente.

## Introdução

A **Foundational Definitions Specification (FDEFSPEC)** estabelece os conceitos centrais e a terminologia que sustentam o ecossistema CatalystUI. Seu propósito é fornecer um entendimento unificado desses conceitos em documentações, especificações, implementações e revisões de verificação, garantindo consistência, clareza e alinhamento.

Ao definir termos e relações-chave de forma precisa e estável, a FDEFSPEC fornece um ponto de referência comum para especificações de nível superior. Isso permite que desenvolvedores, revisores e implementadores raciocinem a partir da mesma base ao determinar se uma linguagem, serviço, framework ou sistema pode ser considerado dentro da especificação.

> [!IMPORTANT]
>
> Expressamos as definições usando uma forma derivada da notação de [teoria dos conjuntos](https://en.wikipedia.org/wiki/Set_theory). Essa abordagem fornece definições precisas e não ambíguas, mantendo clareza e concisão. Estruturamos essas definições para apoiar referência fácil, interpretação clara e uma hierarquia conceitual consistente.

## Sumário

- [FDEFSPEC](#fdefspec)
  - [Introdução](#introduction)
  - [Sumário](#table-of-contents)
  - [Numéricos](#numerics)
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
  - [Codificação de texto](#text-encoding)
    - [Codificação de texto](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
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
  - [Status de operação](#operation-status)
    - [Código de status](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Sucesso](#success)
        - [Aviso](#warning)
        - [Erro](#error)
        - [Fatal](#fatal)
    - [Código de contexto](#context-code)
      - [Context Code()](#context-code-1)
    - [Código de operação](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Código de detalhe](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Resultado](#result)
      - [Result()](#result-1)

## Numéricos

### Bit

Um bit é qualquer $b \in \{0,1\}$.

### Nibble

Um nibble é qualquer $(b_0,\dots,b_3)$ tal que, para todo $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Um byte é qualquer $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Um short é qualquer $(b_0,\dots,b_{15})$ tal que, para todo $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Um inteiro é qualquer $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Um long é qualquer $(b_0,\dots,b_{63})$ tal que, para todo $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Um single é qualquer $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

A definição a seguir está em conformidade com o padrão IEEE 754 para representação de ponto flutuante de precisão simples. Ela define como uma sequência binária de 32 bits é interpretada como número de ponto flutuante, incluindo casos especiais para zero, infinito e NaN (Não é um Número).

> Seja $s = b_0$
>
> Seja $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Seja $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Um double é qualquer $(b_0,\dots,b_{63})$ tal que, para todo $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

A definição a seguir está em conformidade com o padrão IEEE 754 para representação de ponto flutuante de precisão dupla. Ela define como uma sequência binária de 64 bits é interpretada como número de ponto flutuante, incluindo casos especiais para zero, infinito e NaN (Não é um Número).

> Seja $s = b_0$
>
> Seja $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Seja $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Um booleano é qualquer $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{em que } b \in \mathrm{Bit}$

## Codificação de texto

### Codificação de texto

Uma codificação de texto é definida como o seguinte conjunto:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Codificação de texto()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Um codepoint Unicode é qualquer $e \in \mathbb{Z}$ tal que $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Uma unidade de código ASCII é qualquer $(b_0,\dots,b_6)$ tal que, para todo $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

É comum representar uma unidade de código ASCII como um byte acrescentando um bit zero inicial, por razões de desempenho e compatibilidade. Nesses casos, a unidade de código ASCII é representada como:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Caso contrário:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

No caso deste teorema, ambas as definições são representações aceitáveis de uma unidade de código ASCII. Por consistência, usaremos a primeira definição ao representar unidades de código ASCII como bytes, e a segunda definição ao representá-las como sequências de 7 bits.

#### ASCII()

ASCII é uma tupla finita terminada em nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ é uma unidade de código ASCII
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Diz-se que a sequência é terminada em nulo.

### CP1252 Code Unit

Uma unidade de código CP1252 é qualquer $(b_0,\dots,b_7)$ tal que for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 é uma tupla finita terminada em nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ é uma unidade de código CP1252
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Diz-se que a sequência é terminada em nulo.

### UTF-8 Code Unit

Uma unidade de código UTF-8 é qualquer $(b_0,\dots,b_7)$ tal que for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 é uma tupla finita terminada em nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ é uma unidade de código UTF-8
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Diz-se que a sequência é terminada em nulo.

### UTF-16LE Code Unit

Uma unidade de código UTF-16LE é qualquer $(b_0,\dots,b_{15})$ tal que for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE é uma tupla finita terminada em nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ é uma unidade de código UTF-16LE
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Diz-se que a sequência é terminada em nulo.

## Status de operação

### Código de status

Um código de status é qualquer $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Um nível de código de status é definido como o seguinte conjunto:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Código de status()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Código de status Level()

O conjunto de valores de código de status é o intervalo $[0, 255]$, que é particionado em quatro níveis:

> Seja $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Código de status Definition()

Todos os códigos de status têm definições explícitas. Qualquer código de status não incluído na lista a seguir é reservado para uso futuro, e seu significado é indefinido. O nível de um código de status é determinado por $\mathrm{Status\ Code\ Level}(s)$.

Na lista a seguir, a entrada $s$ é representada como valor hexadecimal para facilitar a leitura. Cada código de status definido especifica seu nível, categoria, subcategoria, descrição e detalhe correspondentes, quando aplicável.

Esta lista pode ser estendida conforme novos códigos de status forem definidos. Qualquer novo código de status definido não deve entrar em conflito com códigos existentes e deve ter um significado claramente documentado.

Para transmitir informações não representadas por um código de status definido, deve-se usar o código de contexto, o código de operação ou o código de detalhe.

##### Sucesso

| Código | Nível | Categoria | Descrição | Detalhe |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | A operação foi concluída com sucesso. | |
| `0x01` | SUCCESS | NOOP | A operação foi concluída com sucesso sem executar nenhuma ação. | |

##### Aviso

| Código | Nível | Categoria | Descrição | Detalhe |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | A operação foi concluída, mas o resultado pode ser inesperado ou indesejável. | |
| `0x41` | WARNING | PARTIAL | A operação foi concluída, mas apenas parcialmente. A saída pode estar incompleta. | |
| `0x42` | WARNING | DEPRECATED | A operação foi concluída, mas usou um recurso ou comportamento obsoleto. A operação pode deixar de funcionar no futuro. | |

##### Erro

| Código | Nível | Categoria | Descrição | Detalhe |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | A operação falhou devido a um erro recuperável. | |
| `0x81` | ERROR | INVALID_ARGUMENT | A operação falhou. Um argumento era inválido ou estava fora do intervalo. | O índice do argumento inválido, começando em 0 da esquerda para a direita na assinatura da função. |
| `0x82` | ERROR | INVALID_STATE | A operação falhou. O sistema está em um estado inconsistente, corrompido ou inválido de outra forma. | |
| `0x83` | ERROR | MALFORMED_INPUT | A operação falhou. Uma entrada obrigatória estava malformada ou continha dados inválidos. | |
| `0x84` | ERROR | ACCESS_DENIED | A operação falhou porque um recurso necessário negou acesso. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | A operação falhou porque o recurso ou comportamento solicitado ainda não foi implementado. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | A operação falhou porque o sistema ou configuração de destino não oferece suporte ao recurso solicitado. | |
| `0x87` | ERROR | TIMEOUT | A operação falhou porque um timeout obrigatório ocorreu antes da conclusão. | |
| `0x88` | ERROR | NOT_FOUND | A operação falhou porque um recurso necessário não existe. | |
| `0x89` | ERROR | INTERRUPTED | A operação falhou porque um evento externo a interrompeu. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | A operação falhou porque uma dependência necessária falhou. | O valor `STATUS_CODE` da dependência. Chamadores são incentivados, mas não obrigados, a identificar a dependência que falhou por meio do campo `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | A operação falhou. Um buffer era pequeno demais para conter os dados necessários. | |
| `0x91` | ERROR | ALLOCATION_FAILED | A operação falhou. Uma solicitação de alocação de memória não foi bem-sucedida. | |
| `0xA0` | ERROR | IO_ERROR | A operação falhou. Ocorreu um erro de E/S durante a operação. | |

##### Fatal

| Código | Nível | Categoria | Descrição | Detalhe |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | A operação falhou devido a um erro irrecuperável. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | A operação falhou porque o sistema violou uma invariante fundamental, indicando um erro crítico de lógica ou corrupção de dados. | |

### Código de contexto

Um código de contexto é qualquer $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de contexto()

Um valor de código de contexto representa informações contextuais adicionais sobre uma operação concluída, conforme definido pela operação associada; ele deve ser zero quando o nível do código de status é $\mathrm{Success}$ e, caso contrário, é definido pela implementação.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Código de operação

Um código de operação é qualquer $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de operação()

Um valor de código de operação representa a operação associada a um resultado. Seu significado é definido pela operação correspondente e por sua documentação. Valores indefinidos são considerados desconhecidos.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Código de detalhe

Um código de detalhe é qualquer $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de detalhe()

Um valor de código de detalhe representa informações adicionais sobre uma operação concluída; seu significado é definido pelo status, contexto ou código de operação associado, nessa ordem, e caso contrário é desconhecido.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Resultado

> [!TIP]
>
> Um valor de resultado pode ser representado como um inteiro de 32 bits. Em ordem de bytes big-endian, o valor aparece como `0xSSCCOODD`, em que `SS`, `CC`, `OO` e `DD` correspondem ao código de status, código de contexto, código de operação e código de detalhe, respectivamente. Em ordem de bytes little-endian, o mesmo valor aparece como `0xDDOOCCSS`. Qualquer ordem de bytes pode ser usada, desde que seja aplicada de forma consistente e documentada.

Um resultado é qualquer $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Um resultado é particionado em quatro bytes ordenados:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

em que $s$, $c$, $o$ e $d$ são os componentes do resultado.

#### Resultado()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
