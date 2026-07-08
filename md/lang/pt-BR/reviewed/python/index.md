<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da revisão

## Python

### Visão geral

A linguagem de programação Python foi revisada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração da revisão

Embora Python possa representar muitos conceitos exigidos por meio de tipos integrados, objetos, funções, classes, módulos da biblioteca padrão e validação personalizada, esses mecanismos não são suficientes para satisfazer as especificações CatalystUI aplicáveis no nível da linguagem.

Python fornece forte suporte a codificação de texto, arquivos, streams, objetos, funções, classes, propriedades, processos, threads e execução despachada por meio de seu comportamento integrado e da biblioteca padrão. No entanto, Python não fornece os tipos numéricos escalares de largura fixa exigidos, não define constantes verdadeiras e depende de comportamento dinâmico em runtime para várias construções que outras linguagens verificadas conseguem expressar de forma mais direta.

Por causa disso, não acreditamos que Python forneça uma base estável o suficiente para uma implementação compatível com CatalystUI sem infraestrutura adicional significativa.

Como resultado, Python não recebeu o status CatalystUI Verified para Linguagens de Programação.

#### Pressupostos da revisão

Esta revisão avalia o próprio Python e sua biblioteca padrão incluída.

Pacotes de terceiros, extensões específicas de implementação, módulos nativos opcionais, verificadores de tipos externos, transpiladores e frameworks personalizados de runtime não são tratados como suporte no nível da linguagem.

### Avisos

* Python fornece inteiros de precisão ilimitada, não primitivas inteiras de largura fixa.
* O `float` do Python geralmente tem precisão dupla, mas não é uma família distinta de largura fixa.
* Alguns comportamentos de memória de baixo nível podem exigir `ctypes` ou comportamento específico da implementação.
* Anotações de tipo do Python não são impostas em runtime.
* Python oferece suporte a propriedades, mas o comportamento de setter pode ser omitido.
* Python consegue modelar várias estruturas por meio de recursos da biblioteca padrão, mas não como um tipo de estrutura nativo.

### Falhas

* Python não fornece a maioria dos tipos numéricos escalares de largura fixa exigidos.
* Python não fornece um tipo escalar dedicado de ponto flutuante de 32 bits.
* Python não fornece constantes verdadeiras no nível da linguagem.
* Python não define procedimentos separadamente de funções.
* Python não fornece suporte nativo a ponteiros.
* Python não fornece suporte nativo a interfaces.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Sem tipo numérico de 1 bit.               |
| Nibble    | ❌        | Sem tipo numérico de 4 bits.               |
| Byte      | ❌        | Sem tipo inteiro escalar de 8 bits.        |
| Short     | ❌        | Sem tipo inteiro escalar de 16 bits.       |
| Int       | ❌        | Sem tipo inteiro escalar de 32 bits.       |
| Long      | ❌        | Sem tipo inteiro escalar de 64 bits.       |
| Float     | ❌        | Sem tipo float escalar de 32 bits.         |
| Double    | ⚠️       | `float` geralmente tem precisão dupla. |
| Boolean   | ✅        | Suportado por `bool`.            |

#### Codificação de texto

| Provisão | Verificado | Observações                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings usam codepoints Unicode. |
| ASCII     | ✅        | Codec suportado.                 |
| CP1252    | ✅        | Codec suportado.                 |
| UTF-8     | ✅        | Codec suportado.                 |
| UTF-16LE  | ✅        | Codec suportado.                 |

#### Status de operação

| Provisão | Verificado | Observações                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Exige validação personalizada. |
| Context   | ⚠️       | Exige validação personalizada. |
| Operation | ⚠️       | Exige validação personalizada. |
| Detail    | ⚠️       | Exige validação personalizada. |
| Result    | ⚠️       | Exige validação personalizada. |

### Verificação FRELSPEC

#### Coleções

| Provisão | Verificado | Observações                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Suportado por `set`.       |
| Map       | ✅        | Suportado por `dict`.      |
| Array     | ✅        | Suportado por sequências.   |
| File      | ✅        | Suportado por APIs de arquivo.   |
| Stream    | ✅        | Suportado por APIs de stream. |

#### Memória

| Provisão | Verificado | Observações                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Apenas identidade de objeto.        |
| Pointer   | ❌        | Sem suporte nativo a ponteiros.   |
| Variable  | ✅        | Vínculos de nomes são suportados. |
| Constant  | ❌        | Sem constantes verdadeiras.           |

#### Operações

| Provisão   | Verificado | Observações                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode é de nível de implementação. |
| Procedure   | ❌        | Funções retornam `None`.          |
| Function    | ✅        | Funções são suportadas.          |

#### Encadeamento

| Provisão  | Verificado | Observações                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Suportado por APIs de processo.  |
| Thread     | ✅        | Suportado por `threading`.   |
| Dispatcher | ✅        | Suportado por APIs de executores. |

#### Compostos

| Provisão | Verificado | Observações                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Membros de objeto são suportados.    |
| Object    | ✅        | Objetos são suportados.           |
| Field     | ✅        | Atributos podem representar campos. |
| Method    | ✅        | Métodos são suportados.           |
| Property  | ⚠️       | Existe suporte a getter/setter.    |
| Structure | ⚠️       | Apenas modelos da biblioteca padrão.    |
| Class     | ✅        | Classes são suportadas.           |
| Interface | ❌        | Sem suporte nativo a interfaces.     |
