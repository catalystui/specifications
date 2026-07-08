<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da verificação

## Java

### Visão geral

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


A linguagem de programação Java foi verificada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração de boa-fé

Acreditamos de boa-fé que a linguagem de programação Java consegue representar razoavelmente uma grande parte dos conceitos e provisões definidos nas especificações a seguir, e que pode ser usada para implementar sistemas em conformidade com essas especificações.

#### Pressupostos da revisão

Esta revisão pressupõe suporte moderno da linguagem Java quando recursos dependentes de versão são observados. Recursos como inferência de variáveis locais, records e acesso a memória estrangeira podem exigir versões posteriores do Java.

### Avisos

* Java não possui suporte nativo a tipos numéricos sem sinal, o que pode exigir alargamento ou representações alternativas para certas provisões.
* Endereços diretos de memória e comportamento semelhante a ponteiros podem exigir suporte à API Foreign Function and Memory do Java 22+.
* Java não possui sintaxe nativa de propriedades, exigindo métodos getter e setter em seu lugar.

### Falhas

* Java não fornece CP1252 como charset padrão garantido, exigindo suporte específico da implementação, bibliotecas adicionais ou tratamento personalizado para conformidade total.
* Propriedades Java não fornecem um membro explícito com chave apoiado por um mapa de acessores Get/Set exigido.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Sem numérico de 1 bit; alargue.                         |
| Nibble    | ⚠️       | Sem numérico de 4 bits; alargue.                         |
| Byte      | ⚠️       | Apenas 8 bits com sinal; alargue para sem sinal.           |
| Short     | ⚠️       | Apenas 16 bits com sinal; alargue para sem sinal.          |
| Int       | ⚠️       | 32 bits com sinal; auxiliares sem sinal exigem Java 8+. |
| Long      | ⚠️       | 64 bits com sinal; auxiliares sem sinal exigem Java 8+. |
| Float     | ✅        | Ponto flutuante de 32 bits é suportado.              |
| Double    | ✅        | Ponto flutuante de 64 bits é suportado.              |
| Boolean   | ✅        | O tipo booleano é suportado.                       |

#### Codificação de texto

| Provisão | Verificado | Observações                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Suportado por `int` e `Character`. |
| ASCII     | ✅        | Charset padrão garantido.             |
| CP1252    | ❌        | Não garantido por `StandardCharsets`.    |
| UTF-8     | ✅        | Charset padrão garantido.             |
| UTF-16LE  | ✅        | Charset padrão garantido.             |

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

| Provisão | Verificado | Observações                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Suportado por `Set`.       |
| Map       | ✅        | Suportado por `Map`.       |
| Array     | ✅        | Arrays nativos são suportados.   |
| File      | ✅        | Suportado por APIs de arquivo.   |
| Stream    | ✅        | Suportado por APIs de stream. |

#### Memória

| Provisão | Verificado | Observações                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Endereços diretos exigem Java 22+ FFM.                         |
| Pointer   | ⚠️       | Acesso semelhante a ponteiro exige Java 22+ FFM.                     |
| Variable  | ✅        | Declarações e `var` são suportados; `var` exige Java 10+. |
| Constant  | ✅        | Suportado por `final`.                                     |

#### Operações

| Provisão   | Verificado | Observações                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Representado por bytecode e operações. |
| Procedure   | ✅        | Suportado por métodos `void`.            |
| Function    | ✅        | Suportado por métodos com retorno.         |

#### Encadeamento

| Provisão  | Verificado | Observações                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Suportado por APIs de aplicação e `Process`. |
| Thread     | ✅        | Suportado por `Thread`.                       |
| Dispatcher | ✅        | Suportado por APIs `Executor`.                |

#### Compostos

| Provisão | Verificado | Observações                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Membros de classe são suportados.           |
| Object    | ✅        | Objetos são suportados.                 |
| Field     | ✅        | Campos são suportados.                  |
| Method    | ✅        | Métodos são suportados.                 |
| Property  | ❌        | Sem mapa explícito de acessores.              |
| Structure | ✅        | Suportado por records; Java 16+.   |
| Class     | ✅        | Classes são suportadas.                 |
| Interface | ✅        | Interfaces são suportadas.              |
