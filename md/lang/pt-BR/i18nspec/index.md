<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->

<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# I18NSPEC

<br/>

> **Especificação de Internacionalização**<br/>
> Revisão 1<br/>
> 8 de julho de 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> As definições, os requisitos e os conceitos apresentados aqui descrevem suporte prático à internacionalização e podem ser livremente reexpressos.

<a id="introduction"></a>
## Introdução

A **Internationalization Specification (I18NSPEC)** estabelece os conceitos centrais, a terminologia e os requisitos usados para avaliar o suporte multilíngue dentro do ecossistema CatalystUI. Seu propósito é fornecer um padrão claro para determinar se um sistema, serviço, framework, aplicativo ou implementação oferece suporte de idioma suficiente para ser considerado dentro da especificação.

A internacionalização é importante porque uma interface de usuário não consegue se comunicar claramente se seu significado essencial estiver disponível em apenas um idioma. Um sistema pode funcionar tecnicamente, mas, se os usuários não conseguem entender seus rótulos, instruções, controles, configurações, avisos, erros ou fluxos de trabalho principais, então o sistema deixou de oferecer uma interface significativa para esses usuários.

Esta especificação não tenta medir qualidade perfeita de tradução, estilo literário, adaptação cultural, conformidade legal ou localização regional completa. Em vez disso, ela define a base multilíngue mínima necessária para que os usuários possam acessar e operar de forma significativa as partes essenciais de um sistema em todo o conjunto de locales exigido pela CatalystUI.

Em termos mais simples, a I18NSPEC faz três perguntas principais:

1. Os usuários conseguem acessar as partes essenciais do sistema em cada idioma exigido?
2. Os usuários conseguem selecionar razoavelmente o idioma que entendem?
3. O sistema preserva significado suficiente entre os idiomas para continuar utilizável?

> [!IMPORTANT]
>
> A I18NSPEC define requisitos de internacionalização para verificação. Ela não é uma especificação separada para cada idioma. Cada locale exigido é verificado contra a mesma especificação.

<a id="table-of-contents"></a>
## Sumário

* [I18NSPEC](#i18nspec)

  * [Introdução](#introduction)
  * [Sumário](#table-of-contents)
  * [Conformidade](#conformance)
  * [Conjunto de locales exigido](#required-locale-set)
  * [Conteúdo voltado ao usuário](#user-facing-content)

    * [Conteúdo voltado ao usuário](#user-facing-content-1)
    * [Conteúdo essencial voltado ao usuário](#essential-user-facing-content)
    * [Conteúdo crítico voltado ao usuário](#critical-user-facing-content)
    * [Conteúdo não essencial](#nonessential-content)
  * [Cobertura de tradução](#translation-coverage)

    * [Cobertura essencial de tradução](#essential-translation-coverage)
    * [Requisito de cobertura](#coverage-requirement)
    * [Requisito de conteúdo crítico](#critical-content-requirement)
  * [Seleção de idioma](#language-selection)

    * [Locale ativo](#active-locale)
    * [Locale padrão](#default-locale)
    * [Mecanismo de seleção de idioma](#language-selection-mechanism)
    * [Rótulos das opções de idioma](#language-option-labels)
  * [Fallbacks e equivalência de locale](#fallbacks-and-locale-equivalence)

    * [Locale de fallback](#fallback-locale)
    * [Comportamento de fallback](#fallback-behavior)
    * [Equivalência de locale](#locale-equivalence)
  * [Requisitos de implementação](#implementation-requirements)

    * [Mecanismo de tradução estável](#stable-translation-mechanism)
    * [Preservação do significado](#preservation-of-meaning)
    * [Idiomas sensíveis à direção](#direction-sensitive-languages)
    * [Valores sensíveis ao locale](#locale-sensitive-values)
  * [Verificação](#verification)

    * [Dentro da especificação](#within-spec)
    * [Avisos](#warnings)
    * [Falhas](#failures)
    * [Validade da verificação](#verification-validity)

<a id="conformance"></a>
## Conformidade

Um sistema é considerado conforme com a I18NSPEC quando satisfaz os requisitos definidos por este documento para cada locale no conjunto de locales exigido.

Um sistema conforme deve:

1. Oferecer suporte a cada locale do conjunto de locales exigido.
2. Fornecer conteúdo traduzido para mais de 75% do conteúdo essencial voltado ao usuário em cada locale exigido.
3. Fornecer conteúdo traduzido para todo o conteúdo crítico voltado ao usuário em cada locale exigido.
4. Fornecer um mecanismo razoável para o usuário final selecionar o locale ativo.
5. Usar um mecanismo de tradução estável e apropriado ao sistema.
6. Preservar o significado essencial do conteúdo traduzido voltado ao usuário.
7. Evitar depender de conteúdo de fallback para alegar cobertura de tradução, exceto quando a equivalência de locale for aceita durante a revisão.

Um sistema não precisa usar um único padrão específico de implementação para estar conforme com esta especificação. Ele pode usar arquivos de recursos, tabelas de tradução, roteamento sensível a locale, recursos de idioma compilados, páginas localizadas estáticas, pacotes de idioma em tempo de execução, traduções apoiadas por banco de dados ou outro mecanismo estável apropriado ao sistema.

A verificação se preocupa com acesso prático do usuário e significado essencial, não com uma única arquitetura técnica rígida.

<a id="required-locale-set"></a>
## Conjunto de locales exigido

O conjunto de locales exigido define os idiomas e variantes regionais que devem ser revisados para a CatalystUI Internationalization Verification.

O conjunto atual de locales exigido inclui os seguintes locales:

| Locale    | Idioma                   |
| --------- | ------------------------ |
| `ar-SA`   | Árabe (Arábia Saudita)   |
| `bn-BD`   | Bengali (Bangladesh)     |
| `de-DE`   | Alemão (Alemanha)        |
| `en-GB`   | Inglês (Reino Unido)     |
| `en-IN`   | Inglês (Índia)           |
| `en-US`   | Inglês (Estados Unidos)  |
| `es-ES`   | Espanhol (Espanha)       |
| `es-MX`   | Espanhol (México)        |
| `fa-IR`   | Persa (Irã)              |
| `fr-FR`   | Francês (França)         |
| `hi-IN`   | Hindi (Índia)            |
| `id-ID`   | Indonésio (Indonésia)    |
| `it-IT`   | Italiano (Itália)        |
| `ja-JP`   | Japonês (Japão)          |
| `ko-KR`   | Coreano (Coreia do Sul)  |
| `nl-NL`   | Holandês (Países Baixos) |
| `pl-PL`   | Polonês (Polônia)        |
| `pt-BR`   | Português (Brasil)       |
| `ru-RU`   | Russo (Rússia)           |
| `tl-PH`   | Tagalog (Filipinas)      |
| `tr-TR`   | Turco (Turquia)          |
| `uk-UA`   | Ucraniano (Ucrânia)      |
| `ur-PK`   | Urdu (Paquistão)         |
| `vi-VN`   | Vietnamita (Vietnã)      |
| `zh-CN`   | Chinês (China)           |
| `zh-Hans` | Chinês (Simplificado)    |

Um sistema deve fornecer suporte suficiente de tradução essencial para cada locale listado a fim de ser considerado dentro da especificação.

O conjunto de locales exigido não pretende representar todos os idiomas, dialetos, regiões ou sistemas de escrita. Em vez disso, estabelece uma base prática para ampla usabilidade internacional em muitos grupos linguísticos comuns voltados à tecnologia.

<a id="user-facing-content"></a>
## Conteúdo voltado ao usuário

<a id="user-facing-content-1"></a>
### Conteúdo voltado ao usuário

Conteúdo voltado ao usuário é qualquer conteúdo destinado a ser percebido, lido, ouvido, selecionado, entendido ou usado como base para ação por um usuário final.

Conteúdo voltado ao usuário pode incluir:

* navegação
* rótulos
* botões
* menus
* controles
* cabeçalhos
* diálogos
* configurações
* instruções
* prompts
* avisos
* erros
* confirmações
* mensagens de status
* texto de integração inicial
* texto de ajuda obrigatório
* controles de seleção de idioma
* conteúdo de fluxos de trabalho principais

Conteúdo voltado ao usuário não precisa ser visual. Ele também pode incluir conteúdo auditivo, tátil, simbólico ou multissensorial quando esse conteúdo comunica significado ao usuário.

<a id="essential-user-facing-content"></a>
### Conteúdo essencial voltado ao usuário

Conteúdo essencial voltado ao usuário é conteúdo voltado ao usuário de que uma pessoa razoavelmente precisa para entender, navegar, configurar ou operar o comportamento essencial de um sistema.

Conteúdo essencial voltado ao usuário pode incluir:

* navegação primária
* telas e visualizações principais
* configurações e preferências
* rótulos voltados ao usuário
* controles voltados ao usuário
* instruções obrigatórias
* avisos importantes
* erros importantes
* prompts essenciais
* mensagens de confirmação obrigatórias
* controles de seleção de idioma
* fluxos de trabalho principais necessários para o uso normal

Um sistema não precisa traduzir toda página opcional, mensagem oculta, rótulo interno ou texto não essencial para satisfazer a I18NSPEC. No entanto, o conteúdo exigido para o uso essencial comum deve ser traduzido de acordo com os requisitos desta especificação.

<a id="critical-user-facing-content"></a>
### Conteúdo crítico voltado ao usuário

Conteúdo crítico voltado ao usuário é conteúdo essencial voltado ao usuário em que um mal-entendido pode impedir o uso significativo, criar um erro sério ou levar o usuário a tomar uma decisão importante sem entender a consequência.

Conteúdo crítico voltado ao usuário pode incluir:

* controles de seleção de idioma
* avisos de ações destrutivas
* avisos de exclusão de conta
* confirmações de pagamento
* confirmações de compra
* escolhas de privacidade
* avisos de segurança
* prompts de consentimento
* instruções de segurança obrigatórias
* instruções de configuração obrigatórias
* mensagens de erro obrigatórias
* navegação principal necessária para acessar configurações de idioma

Conteúdo crítico voltado ao usuário deve ser traduzido para cada locale exigido.

O limite de 75% de cobertura essencial de tradução não deve ser usado para deixar conteúdo crítico sem tradução.

<a id="nonessential-content"></a>
### Conteúdo não essencial

Conteúdo não essencial é conteúdo que não é razoavelmente necessário para que um usuário entenda, navegue, configure ou opere o comportamento essencial de um sistema.

Conteúdo não essencial pode incluir:

* identificadores internos
* nomes de código-fonte
* strings apenas de depuração
* detalhes de implementação voltados a desenvolvedores
* texto diagnóstico oculto
* páginas opcionais de marketing
* páginas opcionais de suporte
* texto jurídico ou comercial não essencial fora do escopo revisado
* conteúdo de terceiros não controlado pelo sistema revisado

Conteúdo não essencial pode ser traduzido, mas não é exigido para conformidade com a I18NSPEC, a menos que se torne necessário para a compreensão ou operação essencial pelo usuário.

<a id="translation-coverage"></a>
## Cobertura de tradução

<a id="essential-translation-coverage"></a>
### Cobertura essencial de tradução

Cobertura essencial de tradução é a quantidade de conteúdo essencial voltado ao usuário traduzida para um locale específico.

A cobertura deve ser avaliada por unidades significativas de conteúdo voltado ao usuário, em vez de tamanho de arquivo, contagem de bytes, contagem de linhas, tamanho do repositório ou número de páginas.

Por exemplo, um único botão sem tradução que controla uma ação essencial pode importar mais do que um grande parágrafo opcional sem tradução que não afeta o uso comum.

A cobertura de tradução deve ser julgada por se o usuário consegue entender e operar de forma significativa o sistema essencial no locale revisado.

<a id="coverage-requirement"></a>
### Requisito de cobertura

Um sistema satisfaz o requisito de cobertura de tradução para um locale quando mais de 75% do conteúdo essencial voltado ao usuário está traduzido para esse locale.

Um sistema satisfaz o requisito de cobertura da I18NSPEC quando atende a esse limite para todos os locales do conjunto de locales exigido.

Em uma revisão prática, isso pode ser representado como:

| Locale  | Cobertura essencial de tradução | Resultado |
| ------- | ------------------------------- | --------- |
| `en-US` | 100%                            | Pass      |
| `es-ES` | 94%                             | Pass      |
| `ar-SA` | 78%                             | Pass      |
| `ja-JP` | 61%                             | Fail      |

Um locale com 75% de cobertura ou menos não satisfaz o requisito de cobertura.

Um locale com mais de 75% de cobertura ainda pode falhar se conteúdo crítico voltado ao usuário não estiver traduzido.

<a id="critical-content-requirement"></a>
### Requisito de conteúdo crítico

Todo conteúdo crítico voltado ao usuário deve ser traduzido para cada locale exigido.

Um sistema pode falhar na I18NSPEC mesmo quando satisfaz o limite geral de cobertura se um ou mais itens de conteúdo crítico voltado ao usuário estiverem ausentes, sem tradução, enganosos ou não forem significativamente compreensíveis.

Por exemplo, um sistema não deve ser considerado dentro da especificação se a interface geral estiver traduzida, mas o aviso de exclusão de conta, a confirmação de compra, o aviso de segurança ou o seletor de idioma permanecer sem tradução.

<a id="language-selection"></a>
## Seleção de idioma

<a id="active-locale"></a>
### Locale ativo

O locale ativo é o locale atualmente selecionado para a experiência do usuário.

O locale ativo determina qual conteúdo traduzido deve ser exibido, fornecido ou comunicado de outra forma ao usuário.

<a id="default-locale"></a>
### Locale padrão

O locale padrão é o locale usado quando o usuário não selecionou um locale ativo ou quando nenhuma preferência do usuário está disponível.

Um sistema deve definir um locale padrão.

O locale padrão deve estar documentado ou ser razoavelmente inferível pelo revisor.

<a id="language-selection-mechanism"></a>
### Mecanismo de seleção de idioma

Um sistema conforme deve fornecer uma maneira razoável para que o usuário final altere o locale ativo.

O mecanismo de seleção de idioma deve estar disponível sem exigir que o usuário:

* modifique código-fonte
* use ferramentas de desenvolvedor
* edite arquivos de configuração não documentados
* instale patches não oficiais
* dependa de comportamento oculto
* contate o suporte para mudanças comuns de idioma

Um mecanismo de seleção de idioma pode ser fornecido por meio de:

* configurações do aplicativo
* preferências da conta
* um seletor de idioma
* um prompt de inicialização
* configurações do navegador
* configurações do sistema operacional
* configurações do dispositivo
* outro mecanismo apropriado acessível ao usuário final

O mecanismo não precisa seguir um padrão específico de design. Ele deve permitir razoavelmente que o usuário selecione um idioma suportado.

<a id="language-option-labels"></a>
### Rótulos das opções de idioma

Ao exibir opções de idioma, um sistema deve identificar cada idioma de uma forma compreensível para usuários que falam esse idioma.

Uma opção de idioma pode incluir:

* o nome do idioma nesse idioma
* o nome do idioma no idioma ativo atual
* o código do locale
* um rótulo regional
* um rótulo de sistema de escrita

Por exemplo:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

A formatação exata pode variar.

A intenção é que os usuários consigam reconhecer seu próprio idioma, entender o nome do idioma exibido atualmente quando possível e identificar o código de locale associado.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks e equivalência de locale

<a id="fallback-locale"></a>
### Locale de fallback

Um locale de fallback é um locale usado quando o conteúdo traduzido está indisponível para o locale ativo.

Locales de fallback podem ajudar a preservar a usabilidade, mas o conteúdo de fallback não é automaticamente considerado conteúdo traduzido para o locale ativo.

Por exemplo, se um sistema estiver configurado para `es-MX`, mas exibir texto `en-US` porque a tradução em espanhol está ausente, esse texto em inglês pode ser útil como fallback, mas não deve ser contado como cobertura de tradução em espanhol.

<a id="fallback-behavior"></a>
### Comportamento de fallback

Um sistema conforme pode usar comportamento de fallback quando conteúdo localizado estiver indisponível.

O comportamento de fallback deve evitar saídas quebradas, vazias ou enganosas.

O comportamento de fallback não deve ser usado para alegar falsamente cobertura de tradução para um locale exigido.

Um sistema pode receber um aviso ou falha se o comportamento de fallback for excessivo, confuso, não documentado ou fizer com que conteúdo essencial apareça sem tradução em um locale exigido.

<a id="locale-equivalence"></a>
### Equivalência de locale

A equivalência de locale ocorre quando uma tradução pode servir razoavelmente a mais de um locale sem impedir a compreensão ou operação essencial.

Por exemplo, um sistema pode usar uma tradução em inglês para `en-US`, `en-GB` e `en-IN` se o significado essencial permanecer claro para os usuários de cada locale.

A equivalência de locale pode ser aceita durante a revisão quando as diferenças regionais são pequenas e não afetam materialmente a usabilidade essencial.

A equivalência de locale não deve ser usada quando um locale ausente criaria confusão significativa, omitiria terminologia regional importante, quebraria comportamento essencial ou impediria os usuários de entender o sistema.

Por exemplo, um sistema não deve presumir que idiomas não relacionados são equivalentes porque compartilham uma direção de escrita, região geográfica, família de escrita ou categoria cultural ampla.

A equivalência de locale é um julgamento de revisão, não uma regra automática.

<a id="implementation-requirements"></a>
## Requisitos de implementação

<a id="stable-translation-mechanism"></a>
### Mecanismo de tradução estável

Um sistema conforme deve usar um mecanismo de tradução estável apropriado ao sistema sendo revisado.

Um mecanismo de tradução estável deve permitir que o conteúdo traduzido seja mantido, atualizado, revisado e ampliado sem depender de comportamento frágil ou não documentado.

Um mecanismo de tradução estável pode incluir:

* arquivos de recursos
* tabelas de tradução
* roteamento sensível a locale
* recursos de idioma compilados
* páginas localizadas estáticas
* pacotes de idioma em tempo de execução
* traduções apoiadas por banco de dados
* outra estrutura de tradução documentada

Um sistema deve evitar codificar de forma fixa conteúdo essencial voltado ao usuário de um modo que impeça o suporte de tradução exigido.

<a id="preservation-of-meaning"></a>
### Preservação do significado

Uma tradução preserva o significado quando o usuário consegue entender razoavelmente a mesma instrução, rótulo, aviso, controle, configuração ou fluxo de trabalho essencial que os usuários do idioma de origem.

Uma tradução não precisa ser idêntica palavra por palavra ao conteúdo de origem.

Uma tradução pode alterar ordem de palavras, gramática, estrutura de frase, expressão idiomática, tom ou formulação quando isso for necessário para comunicar o mesmo significado essencial no idioma de destino.

Uma tradução pode falhar na revisão se for enganosa, incompleta, sem sentido, corrompida por máquina ou significativamente diferente do conteúdo de origem de uma forma que afete o uso essencial.

<a id="direction-sensitive-languages"></a>
### Idiomas sensíveis à direção

Alguns locales exigidos usam comumente direção de texto da direita para a esquerda.

Um sistema conforme não deve impedir que conteúdo essencial traduzido seja lido, entendido, selecionado ou usado como base para ação porque o locale ativo usa uma direção de texto diferente.

O sistema deve preservar ordenação legível, comportamento de pontuação e associação de controles para idiomas sensíveis à direção.

Polimento visual completo, qualidade tipográfica, comportamento de acessibilidade e refinamento de layout podem exigir revisão separada. No entanto, o conteúdo essencial traduzido deve permanecer significativamente utilizável.

<a id="locale-sensitive-values"></a>
### Valores sensíveis ao locale

Valores sensíveis ao locale são valores cujo significado ou legibilidade pode variar por idioma, região, sistema de escrita ou cultura.

Valores sensíveis ao locale podem incluir:

* datas
* horários
* números
* moedas
* medidas
* formas plurais
* gênero gramatical
* ordem de classificação
* formatos de endereço
* formatos de número de telefone

A I18NSPEC não exige localização completa de todo valor sensível ao locale, a menos que esse valor seja essencial para entender ou operar o sistema.

Quando valores sensíveis ao locale são essenciais, o sistema deve representá-los de uma forma que os usuários do locale ativo consigam entender razoavelmente.

<a id="verification"></a>
## Verificação

<a id="within-spec"></a>
### Dentro da especificação

Um sistema é considerado dentro da especificação quando a Equipe CatalystUI revisou o sistema e achou razoável concluir que ele satisfaz a I18NSPEC.

Um sistema pode estar dentro da especificação quando:

* cada locale exigido é suportado
* mais de 75% do conteúdo essencial voltado ao usuário está traduzido para cada locale exigido
* todo o conteúdo crítico voltado ao usuário está traduzido para cada locale exigido
* os usuários conseguem selecionar razoavelmente o locale ativo
* o comportamento de fallback não alega falsamente cobertura de tradução
* a equivalência de locale, se usada, é razoável e documentada
* o conteúdo traduzido preserva o significado essencial

Um sistema pode estar dentro da especificação mesmo que algum conteúdo não essencial permaneça sem tradução.

Um sistema pode estar dentro da especificação mesmo que as traduções não sejam perfeitas, desde que o significado essencial seja preservado e os requisitos desta especificação sejam satisfeitos.

<a id="warnings"></a>
### Avisos

Um aviso pode ser emitido quando um sistema parece satisfazer a I18NSPEC, mas contém preocupações que devem ser documentadas.

Avisos podem incluir:

* pequeno conteúdo não essencial sem tradução
* terminologia inconsistente entre locales
* traduções imperfeitas, mas compreensíveis
* equivalência de locale aceitável que deve ser documentada
* comportamento limitado de fallback
* páginas opcionais parcialmente traduzidas
* preocupações de layout sensível à direção que não impedem o uso essencial
* valores sensíveis ao locale que são compreensíveis, mas não ideais

Avisos não impedem necessariamente a verificação.

<a id="failures"></a>
### Falhas

Uma falha ocorre quando um sistema não satisfaz uma ou mais condições obrigatórias da I18NSPEC.

Falhas podem incluir:

* ausência de suporte para um locale exigido
* cobertura essencial de tradução igual ou inferior a 75% para um locale exigido
* conteúdo crítico voltado ao usuário sem tradução
* ausência de mecanismo razoável de seleção de idioma
* seleção de idioma exigindo modificação de código-fonte
* seleção de idioma exigindo ferramentas de desenvolvedor
* carregamento de tradução quebrado
* alegações enganosas de locale
* comportamento excessivo de fallback
* conteúdo de fallback contado como conteúdo traduzido sem equivalência de locale válida
* conteúdo sensível à direção ilegível ou inutilizável
* fluxos de trabalho essenciais indisponíveis em um ou mais locales exigidos

Falhas impedem a verificação até serem resolvidas.

<a id="verification-validity"></a>
### Validade da verificação

A verificação I18NSPEC se aplica apenas ao estado revisado do sistema no momento em que a verificação é emitida.

Um sistema pode manter a verificação em atualizações posteriores desde que preserve a base de internacionalização verificada.

Pequenas mudanças de redação, traduções adicionadas, traduções melhoradas e atualizações comuns de conteúdo não invalidam automaticamente a verificação.

Uma nova revisão pode ser exigida se um sistema:

* remover suporte a locales exigidos
* quebrar a seleção de idioma
* reduzir substancialmente a cobertura essencial de tradução
* deixar novos fluxos de trabalho essenciais sem tradução
* substituir conteúdo traduzido por conteúdo de fallback
* alterar sua arquitetura de tradução de uma forma que afete o comportamento verificado
* introduzir grandes mudanças voltadas ao usuário que alterem o escopo revisado

Em outras palavras, melhorar o suporte de tradução normalmente é aceitável.

Quebrar a base multilíngue verificada pode exigir revisão.
