<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->

<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified para Internacionalização

Bem-vindo à documentação da CatalystUI Verification para internacionalização.

**CatalystUI Verified para Internacionalização** indica que um sistema, serviço, framework, aplicativo ou implementação foi revisado pela Equipe CatalystUI e considerado capaz de fornecer suporte multilíngue suficiente para o conjunto de idiomas exigido pela internacionalização da CatalystUI.

Esta verificação não é uma classificação geral de qualidade de tradução, estilo de escrita, profundidade de localização ou adaptação cultural. Em vez disso, ela identifica se o sistema revisado fornece uma base estável e prática para que os usuários acessem sua funcionalidade essencial nos idiomas suportados exigidos.

Em termos mais simples, esta verificação pergunta se os usuários conseguem usar significativamente as partes essenciais de um sistema nos idiomas exigidos e se recebem uma forma razoável de escolher o idioma que entendem.

<a id="purpose"></a>
## Propósito

A internacionalização importa porque um sistema não pode ser considerado amplamente acessível se seu significado essencial estiver preso a um único idioma.

A CatalystUI foi projetada em torno de clareza, consistência e representação fiel da interação humano-computador. O idioma faz parte dessa interação. Se um usuário não consegue entender os rótulos, instruções, avisos, controles, configurações ou conteúdo essencial de um sistema, então o sistema falhou em comunicar claramente, mesmo que a funcionalidade subjacente funcione tecnicamente.

A Internationalization Verification existe para identificar sistemas que oferecem suporte traduzido suficiente para usuários em todo o conjunto de idiomas exigido pela CatalystUI. O objetivo não é exigir tradução perfeita de toda palavra opcional, mensagem oculta para desenvolvedor ou página não essencial. O objetivo é determinar se as partes essenciais do sistema podem ser entendidas e usadas por pessoas em cada idioma exigido.

<a id="what-verification-means"></a>
## O que a verificação significa

Um sistema se torna **CatalystUI Verified para Internacionalização** quando é revisado contra os requisitos listados nesta seção e considerado dentro da especificação.

Para ser verificado, um sistema deve fornecer traduções para mais de 75% das partes essenciais voltadas ao usuário do sistema em cada idioma exigido. Ele também deve fornecer um mecanismo razoável para que o usuário final altere o idioma ativo.

Um sistema não precisa traduzir todo identificador interno, detalhe de implementação voltado ao desenvolvedor, string de depuração, página opcional de marketing ou texto de suporte não essencial. No entanto, as partes voltadas ao usuário necessárias para entender e operar o sistema essencial devem estar disponíveis em cada idioma exigido.

<a id="required-languages"></a>
## Idiomas exigidos

O conjunto atual de idiomas de internacionalização da CatalystUI foi selecionado a partir de uma revisão prática de idiomas comumente necessários em contextos de tecnologia, incluindo alcance global de falantes, uso comum online, expectativas de software multilíngue e necessidades amplas de acessibilidade regional.

Esse conjunto de idiomas não pretende representar todos os idiomas, todos os dialetos ou todas as variantes regionais. Em vez disso, ele estabelece uma base prática para sistemas que buscam ampla usabilidade internacional em muitos dos grupos linguísticos mais comuns do mundo voltados à tecnologia.

O conjunto atual de idiomas de internacionalização da CatalystUI inclui os seguintes locales:

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

Um sistema deve fornecer cobertura essencial de tradução suficiente para cada grupo linguístico listado a fim de ser considerado dentro da especificação.

No entanto, variantes regionais podem ser revisadas com flexibilidade razoável quando as diferenças entre variantes são pequenas e não afetam materialmente a capacidade do usuário de entender ou operar o sistema. Por exemplo, um sistema ainda pode ser elegível para verificação se fornecer uma tradução forte em inglês, mas não traduzir separadamente cada variante regional do inglês, desde que o significado essencial, a navegação, as instruções, os avisos e os controles permaneçam claros para usuários das variantes ausentes.

Essa flexibilidade não se aplica quando uma variante ausente criaria confusão significativa, omitiria terminologia regional importante, quebraria comportamento sensível ao locale ou impediria os usuários de entender partes essenciais do sistema.

<a id="essential-translation-coverage"></a>
## Cobertura essencial de tradução

Para a Internationalization Verification, **cobertura essencial de tradução** refere-se às partes de um sistema de que um usuário razoavelmente precisa para entender, navegar, configurar e operar o sistema.

Partes essenciais podem incluir:

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

Um sistema é considerado como atendendo ao requisito de cobertura de tradução quando mais de 75% de seu conteúdo essencial voltado ao usuário está disponível em cada idioma exigido.

Esse limite existe porque o trabalho de internacionalização pode ser grande, contínuo e dependente de contexto. Um sistema ainda pode estar dentro da especificação mesmo que algum conteúdo não essencial ou de menor prioridade permaneça sem tradução. No entanto, a experiência essencial deve estar significativamente disponível em todos os idiomas exigidos.

<a id="language-selection"></a>
## Seleção de idioma

Um sistema verificado deve fornecer uma forma razoável para que o usuário final altere o idioma ativo.

O mecanismo de seleção de idioma deve ser fácil de encontrar, compreensível e disponível sem exigir conhecimento técnico. Os usuários não devem precisar editar arquivos de configuração, modificar código-fonte, instalar ferramentas de desenvolvedor ou depender de comportamento não documentado apenas para mudar o idioma.

Ao exibir opções de idioma, o sistema deve identificar cada idioma de uma forma compreensível tanto para usuários que falam esse idioma quanto para usuários que estão usando outro idioma selecionado.

Por exemplo, uma opção de idioma pode ser exibida usando:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

A formatação exata pode variar, mas a intenção deve permanecer a mesma: os usuários devem conseguir reconhecer seu próprio idioma, entender o nome do idioma exibido atualmente quando possível e identificar o código de locale associado.

<a id="what-within-spec-means"></a>
## O que “dentro da especificação” significa

Quando um sistema é considerado **dentro da especificação**, isso significa que a Equipe CatalystUI revisou manualmente o sistema e achou razoável concluir que ele satisfaz os requisitos de internacionalização descritos por esta categoria de verificação.

Isso não exige um padrão rígido único de implementação. Um sistema pode satisfazer o requisito por meio de arquivos de recursos, tabelas de tradução, roteamento sensível a locale, recursos de idioma compilados, traduções apoiadas por banco de dados, pacotes de idioma em tempo de execução ou outro mecanismo estável apropriado ao sistema.

A verificação se preocupa com a capacidade prática dos usuários de acessar o sistema essencial nos idiomas exigidos, não com o uso de uma arquitetura específica de tradução.

<a id="what-verification-does-not-mean"></a>
## O que a verificação não significa

CatalystUI Verified para Internacionalização não garante que toda tradução seja perfeita, literária, idiomática, culturalmente completa ou legalmente suficiente para todas as regiões.

Ela também não verifica automaticamente acessibilidade, tipografia, layout da direita para a esquerda, formatação específica de locale, formatação de moeda, formatação de data, conformidade legal ou requisitos comerciais regionais, a menos que essas preocupações estejam incluídas no escopo de internacionalização revisado.

Um sistema pode fornecer forte cobertura de tradução e ainda exigir revisão separada para acessibilidade, qualidade de localização, conformidade regional ou outras preocupações especializadas.

<a id="why-this-verification-exists"></a>
## Por que esta verificação existe

Uma interface de usuário só é útil quando o usuário consegue entender o que ela está comunicando.

Muitos sistemas afirmam oferecer suporte a idiomas enquanto traduzem apenas uma pequena parte da experiência, escondem a seleção de idioma, omitem mensagens importantes ou deixam fluxos de trabalho essenciais parcialmente sem tradução. Isso cria confusão e impede que os usuários confiem no sistema.

A Internationalization Verification existe para definir um padrão mais claro. Ela identifica sistemas que fazem um esforço sério e prático para apoiar usuários em todo o conjunto de idiomas exigido pela CatalystUI e que fornecem uma maneira razoável para os usuários selecionarem o idioma de que precisam.

<a id="verification-scope"></a>
## Escopo da verificação

A CatalystUI Verification para Internacionalização se aplica ao sistema, serviço, framework, aplicativo ou implementação revisado como existia no momento em que a verificação foi emitida.

Um sistema verificado fornece cobertura essencial de tradução suficiente para os idiomas exigidos. Ele não garante que toda página, recurso, lançamento, plugin, extensão ou integração de terceiros futura esteja automaticamente dentro da especificação.

Produtos, módulos, serviços, pacotes de idioma ou revisões principais separados podem exigir sua própria revisão, dependendo da categoria de verificação solicitada.

<a id="verification-validity"></a>
## Validade da verificação

A CatalystUI Verification se aplica apenas ao estado revisado do sistema no momento em que a verificação é emitida.

Um sistema pode manter sua verificação em atualizações posteriores desde que preserve a base de internacionalização verificada. Pequenas mudanças de redação, traduções adicionadas e atualizações comuns de conteúdo não invalidam automaticamente a verificação.

Uma nova revisão pode ser exigida se um sistema remover suporte a idiomas exigidos, quebrar a seleção de idioma, reduzir substancialmente a cobertura essencial de tradução ou alterar sua arquitetura de internacionalização de uma forma que afete o comportamento verificado.

Em outras palavras, melhorar o suporte de tradução normalmente é aceitável. Quebrar a base multilíngue verificada pode exigir revisão.

<a id="verified-systems"></a>
## Sistemas verificados

Sistemas conhecidos verificados para internacionalização são listados separadamente na página apropriada da CatalystUI Verified.
