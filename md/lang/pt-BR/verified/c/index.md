<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# Detalhes da verificação

## C

### Visão geral

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


A linguagem de programação C foi verificada em relação às especificações FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) em 7 de julho de 2026.

#### Declaração de boa-fé

Acreditamos de boa-fé que a linguagem de programação C consegue representar razoavelmente os conceitos e provisões definidos nas especificações a seguir, e que pode ser usada para implementar sistemas em conformidade com essas especificações.

#### Declaração da revisão

C fornece forte suporte de baixo nível para representação de dados fundamentais, acesso à memória, arquivos, streams, procedimentos, funções, estruturas e implementação direta orientada ao sistema.

Embora C não forneça nativamente várias construções compostas orientadas a objetos, essas limitações são isoladas a provisões compostas específicas da FRELSPEC e estão documentadas abaixo. Essas falhas não impedem que C seja considerado dentro da especificação como um todo, mas devem ser compreendidas ao usar C para implementações compatíveis com CatalystUI.

#### Pressupostos da revisão

Esta revisão pressupõe suporte moderno ao C padrão quando recursos dependentes de versão são observados. O suporte a inteiros de largura exata pressupõe que os tipos correspondentes de `<stdint.h>` sejam fornecidos pela implementação.

Esta revisão trata C como uma linguagem de representação de baixo nível. Codificações exatas por byte podem ser representadas diretamente por arrays de bytes, tabelas de consulta e lógica explícita de parsing quando nenhum codec padrão nomeado é fornecido.

### Avisos

* Tipos inteiros de largura exata dependem de suporte da implementação.
* CP1252 pode ser representado byte a byte, mas nenhum codec padrão nomeado é fornecido.
* A serialização UTF-16LE exige tratamento explícito da ordem dos bytes.
* Threads padrão podem ser omitidas por algumas implementações de C.
* Padrões orientados a objetos podem ser emulados manualmente, mas não são construções nativas da linguagem.

### Falhas

* C não fornece membros de método nativos.
* C não fornece propriedades nativas.
* C não fornece classes nativas.
* C não fornece interfaces nativas.

### Verificação FDEFSPEC

#### Numéricos

| Provisão | Verificado | Observações                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use campos de bits ou máscaras.                    |
| Nibble    | ⚠️       | Use campos de bits ou máscaras.                    |
| Byte      | ✅        | Suportado por `unsigned char`.          |
| Short     | ✅        | Suportado por `int16_t` e `uint16_t`. |
| Int       | ✅        | Suportado por `int32_t` e `uint32_t`. |
| Long      | ✅        | Suportado por `int64_t` e `uint64_t`. |
| Float     | ✅        | Suportado por `float`.                  |
| Double    | ✅        | Suportado por `double`.                 |
| Boolean   | ✅        | Suportado por `bool`; C99+.             |

#### Codificação de texto

| Provisão | Verificado | Observações                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Suportado por `char32_t`; C11+.     |
| ASCII     | ✅        | Representável como valores de byte.           |
| CP1252    | ⚠️        | Exige mapeamento explícito de bytes.         |
| UTF-8     | ✅        | Suportado por literais UTF-8; C11+. |
| UTF-16LE  | ⚠️        | Exige tratamento da ordem dos bytes.           |

#### Status de operação

| Provisão | Verificado | Observações                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Pode ser representado por um enum.  |
| Context   | ✅        | Pode ser representado por um valor.  |
| Operation | ✅        | Pode ser representado por um valor.  |
| Detail    | ✅        | Pode ser representado por um valor.  |
| Result    | ✅        | Pode ser representado por uma struct. |

### Verificação FRELSPEC

#### Coleções

| Provisão | Verificado | Observações                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Pode ser representado por structs. |
| Map       | ✅        | Pode ser representado por structs. |
| Array     | ✅        | Arrays nativos são suportados.   |
| File      | ✅        | Suportado por APIs de arquivo.   |
| Stream    | ✅        | Suportado por APIs de stream. |

#### Memória

| Provisão | Verificado | Observações                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Endereços são suportados.   |
| Pointer   | ✅        | Ponteiros são suportados.    |
| Variable  | ✅        | Variáveis são suportadas.   |
| Constant  | ✅        | Suportado por `const`. |

#### Operações

| Provisão   | Verificado | Observações                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Representado por operações de máquina. |
| Procedure   | ✅        | Suportado por funções `void`.     |
| Function    | ✅        | Suportado por funções com retorno.  |

#### Encadeamento

| Provisão  | Verificado | Observações                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Suportado por ambientes hospedados. |
| Thread     | ⚠️        | Suportado por `<threads.h>`; C11+. |
| Dispatcher | ✅        | Pode ser representado diretamente.           |

#### Compostos

| Provisão | Verificado | Observações                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Membros de struct são suportados.            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | Campos de struct são suportados.             |
| Method    | ❌        | Sem membros de método nativos.                |
| Property  | ❌        | Sem mapa explícito de acessores Get/Set.        |
| Structure | ✅        | Estruturas são suportadas nativamente.       |
| Class     | ❌        | Sem construção nativa de classe.               |
| Interface | ❌        | Sem construção nativa de interface.           |
