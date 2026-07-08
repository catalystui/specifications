<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da verificação

## C++

### Visão geral

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


A linguagem de programação C++ foi verificada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração de boa-fé

Acreditamos de boa-fé que a linguagem de programação C++ consegue representar razoavelmente os conceitos e provisões definidos nas especificações a seguir, e que pode ser usada para implementar sistemas em conformidade com essas especificações.

#### Pressupostos da revisão

Esta revisão pressupõe suporte moderno ao C++ padrão quando recursos dependentes de versão são observados. O suporte a inteiros de largura exata pressupõe que os tipos correspondentes de `<cstdint>` sejam fornecidos pela implementação.

Esta revisão trata C++ como uma linguagem de programação de sistemas com suporte direto para representação de baixo nível, modelagem de objetos, controle de memória, programação genérica e execução concorrente.

### Avisos

* Tipos inteiros de largura exata dependem de suporte da implementação.
* CP1252 pode ser representado byte a byte, mas nenhum codec padrão nomeado é fornecido.
* A serialização UTF-16LE exige tratamento explícito da ordem dos bytes.
* Some concurrency and character features require modern C++ revisions.

### Falhas

* Nenhuma falha FDEFSPEC ou FRELSPEC conhecida foi encontrada durante esta verificação.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use campos de bits ou máscaras.                    |
| Nibble    | ⚠️       | Use campos de bits ou máscaras.                    |
| Byte      | ✅        | Suportado por `std::byte`.              |
| Short     | ✅        | Suportado por `int16_t` e `uint16_t`. |
| Int       | ✅        | Suportado por `int32_t` e `uint32_t`. |
| Long      | ✅        | Suportado por `int64_t` e `uint64_t`. |
| Float     | ✅        | Suportado por `float`.                  |
| Double    | ✅        | Suportado por `double`.                 |
| Boolean   | ✅        | Suportado por `bool`.                   |

#### Codificação de texto

| Provisão | Verificado | Observações                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Suportado por `char32_t`.        |
| ASCII     | ✅        | Representável como valores de byte.        |
| CP1252    | ⚠️        | Exige mapeamento explícito de bytes.      |
| UTF-8     | ✅        | Suportado por `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Exige tratamento da ordem dos bytes.        |

#### Status de operação

| Provisão | Verificado | Observações                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Pode ser representado por um enum.           |
| Context   | ✅        | Pode ser representado por um valor.           |
| Operation | ✅        | Pode ser representado por um valor.           |
| Detail    | ✅        | Pode ser representado por um valor.           |
| Result    | ✅        | Pode ser representado por uma struct ou classe. |

### Verificação FRELSPEC

#### Coleções

| Provisão | Verificado | Observações                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Suportado por `std::set`.              |
| Map       | ✅        | Suportado por `std::map`.              |
| Array     | ✅        | Suportado por arrays e `std::array`. |
| File      | ✅        | Suportado por streams de arquivo.            |
| Stream    | ✅        | Suportado por iostreams.               |

#### Memória

| Provisão | Verificado | Observações                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Endereços são suportados.                   |
| Pointer   | ✅        | Ponteiros são suportados.                    |
| Variable  | ✅        | Variáveis são suportadas.                   |
| Constant  | ✅        | Suportado por `const` e `constexpr`. |

#### Operações

| Provisão   | Verificado | Observações                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Representado por operações de máquina. |
| Procedure   | ✅        | Suportado por funções `void`.     |
| Function    | ✅        | Suportado por funções com retorno.  |

#### Encadeamento

| Provisão  | Verificado | Observações                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Suportado por execução hospedada.      |
| Thread     | ✅        | Suportado por `std::thread`; C++11+. |
| Dispatcher | ✅        | Suportado por async e escalonadores.  |

#### Compostos

| Provisão | Verificado | Observações                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Membros de classe são suportados.            |
| Object    | ✅        | Objetos são suportados.                  |
| Field     | ✅        | Campos são suportados.                   |
| Method    | ✅        | Métodos são suportados.                  |
| Property  | ✅        | Mapas Get/Set podem ser representados.        |
| Structure | ✅        | Estruturas são suportadas nativamente.      |
| Class     | ✅        | Classes são suportadas nativamente.         |
| Interface | ✅        | Pode ser representado por classes abstratas. |
