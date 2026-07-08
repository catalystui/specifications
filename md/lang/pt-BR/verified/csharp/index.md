<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da verificação

## C#

### Visão geral

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


A linguagem de programação C# foi verificada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração de boa-fé

Acreditamos de boa-fé que a linguagem de programação C# consegue representar razoavelmente os conceitos e provisões definidos nas especificações a seguir, e que pode ser usada para implementar sistemas em conformidade com essas especificações.

#### Pressupostos da revisão

Esta revisão pressupõe suporte moderno a C# e .NET quando recursos dependentes de versão são observados.

### Avisos

* O suporte a CP1252 está disponível por meio do provedor oficial de páginas de código do .NET, mas pode exigir registro do provedor ou um pacote adicional, dependendo do runtime de destino.
* Comportamento de ponteiro unsafe pode exigir autorização unsafe explícita.

### Falhas

* Nenhuma falha FDEFSPEC ou FRELSPEC conhecida foi encontrada durante esta verificação.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Sem numérico de 1 bit; alargue.                |
| Nibble    | ⚠️       | Sem numérico de 4 bits; alargue.                |
| Byte      | ✅        | Suportado por `byte` e `sbyte`.   |
| Short     | ✅        | Suportado por `short` e `ushort`. |
| Int       | ✅        | Suportado por `int` e `uint`.     |
| Long      | ✅        | Suportado por `long` e `ulong`.   |
| Float     | ✅        | Suportado por `float`.              |
| Double    | ✅        | Suportado por `double`.             |
| Boolean   | ✅        | Suportado por `bool`.               |

#### Codificação de texto

| Provisão | Verificado | Observações                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Suportado por numéricos e `Rune`. |
| ASCII     | ✅        | Suportado por `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Exige provedor de páginas de código.          |
| UTF-8     | ✅        | Suportado por `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Suportado por `Encoding.Unicode`.  |

#### Status de operação

| Provisão | Verificado | Observações                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Pode ser representado por um tipo personalizado.        |
| Context   | ✅        | Pode ser representado por um valor personalizado.       |
| Operation | ✅        | Pode ser representado por um valor personalizado.       |
| Detail    | ✅        | Pode ser representado por um valor personalizado.       |
| Result    | ✅        | Pode ser representado por um tipo de retorno personalizado. |

### Verificação FRELSPEC

#### Coleções

| Provisão | Verificado | Observações                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Suportado por `HashSet<T>`.              |
| Map       | ✅        | Suportado por `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Arrays nativos são suportados.                 |
| File      | ✅        | Suportado por APIs de arquivo.                 |
| Stream    | ✅        | Suportado por `Stream`.                  |

#### Memória

| Provisão | Verificado | Observações                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Suportado por referências e ponteiros. |
| Pointer   | ✅        | Suportado por ponteiros unsafe.         |
| Variable  | ✅        | Variáveis são suportadas.                   |
| Constant  | ✅        | Suportado por `const` e `readonly`.  |

#### Operações

| Provisão   | Verificado | Observações                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Representado por IL e operações. |
| Procedure   | ✅        | Suportado por métodos `void`.      |
| Function    | ✅        | Suportado por métodos com retorno.   |

#### Encadeamento

| Provisão  | Verificado | Observações                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Suportado por APIs de aplicação e `Process`. |
| Thread     | ✅        | Suportado por `Thread`.                       |
| Dispatcher | ✅        | Suportado por tasks e escalonadores.           |

#### Compostos

| Provisão | Verificado | Observações                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Membros de tipo são suportados.        |
| Object    | ✅        | Objetos são suportados.             |
| Field     | ✅        | Campos são suportados.              |
| Method    | ✅        | Métodos são suportados.             |
| Property  | ✅        | Propriedades são suportadas nativamente. |
| Structure | ✅        | Estruturas são suportadas nativamente. |
| Class     | ✅        | Classes são suportadas.             |
| Interface | ✅        | Interfaces são suportadas.          |
