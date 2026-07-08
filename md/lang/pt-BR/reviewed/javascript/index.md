<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da revisão

## JavaScript

### Visão geral

A linguagem de programação JavaScript foi revisada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração da revisão

Embora JavaScript possa representar alguns conceitos exigidos por meio de objetos, funções, arrays e comportamento integrado da linguagem, esses mecanismos não são suficientes para satisfazer as especificações CatalystUI aplicáveis no nível da linguagem.

Esta revisão avalia o JavaScript em si, não o ecossistema JavaScript ao redor. APIs de navegador, APIs do Node.js, APIs do Deno, APIs do Bun, Web APIs, TypeScript, WebAssembly, bibliotecas externas e validação personalizada não são tratados como suporte no nível da linguagem.

Como JavaScript carece de muitos tipos numéricos escalares de largura fixa exigidos, não fornece as codificações de texto exigidas como recursos da linguagem e não define várias construções exigidas de sistema, memória, encadeamento e compostos, não acreditamos que JavaScript forneça uma base estável o suficiente para uma implementação compatível com CatalystUI sem infraestrutura adicional significativa.

Como resultado, JavaScript não recebeu o status CatalystUI Verified para Linguagens de Programação.

#### Pressupostos da revisão

Esta revisão aplica um padrão estrito no nível da linguagem. Se uma provisão não for explicitamente suportada pelo próprio JavaScript, ela é marcada como não verificada.

APIs fornecidas pelo host, comportamento específico da implementação, bibliotecas externas, transpiladores, sistemas de tipos e validação personalizada em runtime são excluídos da verificação.

### Avisos

* JavaScript consegue representar muitos valores numéricos por meio de `Number`, mas `Number` é um tipo numérico de ponto flutuante de 64 bits.
* JavaScript fornece `BigInt`, mas `BigInt` tem largura arbitrária.
* Arrays tipados fornecem visões de armazenamento binário, não tipos escalares da linguagem.
* Strings JavaScript usam unidades de código UTF-16, não valores explícitos de codificação de texto.
* `const` protege vínculos, não valores de objetos.

### Falhas

* JavaScript não fornece a maioria dos tipos numéricos escalares de largura fixa exigidos.
* JavaScript não fornece um tipo escalar dedicado de ponto flutuante de 32 bits.
* JavaScript não fornece ASCII, CP1252, UTF-8 ou UTF-16LE como codificações de texto no nível da linguagem.
* JavaScript não fornece construções de arquivo ou stream no nível da linguagem.
* JavaScript não fornece construções de endereço ou ponteiro no nível da linguagem.
* JavaScript não fornece construções de processo, thread ou dispatcher no nível da linguagem.
* Propriedades JavaScript não fornecem um membro explícito com chave apoiado por um mapa de acessores Get/Set exigido.
* JavaScript não fornece estruturas nem interfaces.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Sem tipo numérico de 1 bit.         |
| Nibble    | ❌        | Sem tipo numérico de 4 bits.         |
| Byte      | ❌        | Sem tipo inteiro escalar de 8 bits.  |
| Short     | ❌        | Sem tipo inteiro escalar de 16 bits. |
| Int       | ❌        | Sem tipo inteiro escalar de 32 bits. |
| Long      | ❌        | Sem tipo inteiro escalar de 64 bits. |
| Float     | ❌        | Sem tipo float escalar de 32 bits.   |
| Double    | ✅        | Suportado por `Number`.    |
| Boolean   | ✅        | Suportado por `boolean`.   |

#### Codificação de texto

| Provisão | Verificado | Observações                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Sem tipo dedicado de codepoint. |
| ASCII     | ❌        | Não é de nível da linguagem.          |
| CP1252    | ❌        | Não é de nível da linguagem.          |
| UTF-8     | ❌        | Não é de nível da linguagem.          |
| UTF-16LE  | ❌        | Não é de nível da linguagem.          |

#### Status de operação

| Provisão | Verificado | Observações                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Representável, não imponível. |
| Context   | ⚠️       | Representável, não imponível. |
| Operation | ⚠️       | Representável, não imponível. |
| Detail    | ⚠️       | Representável, não imponível. |
| Result    | ⚠️       | Exige validação em runtime.    |

### Verificação FRELSPEC

#### Coleções

| Provisão | Verificado | Observações                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Suportado por `Set`. |
| Map       | ✅        | Suportado por `Map`. |
| Array     | ✅        | Arrays são suportados.    |
| File      | ❌        | Não é de nível da linguagem.      |
| Stream    | ❌        | Não é de nível da linguagem.      |

#### Memória

| Provisão | Verificado | Observações                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Sem suporte a endereços.             |
| Pointer   | ❌        | Sem suporte a ponteiros.             |
| Variable  | ✅        | Variáveis são suportadas.        |
| Constant  | ⚠️       | `const` protege apenas vínculos. |

#### Operações

| Provisão   | Verificado | Observações                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Sem tipo de instrução definido.     |
| Procedure   | ❌        | Funções sempre retornam um valor. |
| Function    | ✅        | Funções são suportadas.         |

#### Encadeamento

| Provisão  | Verificado | Observações                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Não é de nível da linguagem.         |
| Thread     | ⚠️        | Representado por agentes. |
| Dispatcher | ❌        | Exige escalonamento do host.   |


#### Compostos

| Provisão | Verificado | Observações                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Membros de objeto são suportados.         |
| Object    | ✅        | Objetos são suportados.                |
| Field     | ✅        | Propriedades de dados podem representar campos. |
| Method    | ✅        | Métodos são suportados.                |
| Property  | ❌        | Sem mapa explícito de acessores.             |
| Structure | ❌        | Sem suporte a estruturas.                 |
| Class     | ✅        | A sintaxe de classes é suportada.            |
| Interface | ❌        | Sem suporte a interfaces.                 |
