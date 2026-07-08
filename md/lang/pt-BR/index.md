<!-- Esta tradução foi gerada pelo ChatGPT e deve ser revisada por um tradutor humano. -->
<!-- Remova estas linhas em um pull request depois que a tradução tiver sido verificada. -->

# CatalystUI Verified para linguagens de programação

Bem-vindo à documentação de Verificação da CatalystUI para linguagens de programação.

**CatalystUI Verified para linguagens de programação** indica que uma linguagem de programação foi revisada pela Equipe CatalystUI e considerada capaz de fornecer as representações de dados fundamentais e as estruturas relacionais necessárias para expressar sistemas compatíveis com CatalystUI.

Esta verificação não é uma classificação geral de linguagens de programação. Ela não decide se uma linguagem é melhor, mais rápida, mais fácil, mais nova, mais popular ou mais agradável que outra. Em vez disso, identifica se a linguagem fornece uma base estável e prática para as especificações exigidas pela Verificação da CatalystUI.

Em termos mais simples, esta verificação pergunta se uma linguagem de programação consegue representar fielmente os dados básicos e as relações das quais a CatalystUI depende.

## Propósito

As linguagens de programação formam a base representacional sob toda implementação da CatalystUI. Antes que um framework, biblioteca, runtime, aplicação ou serviço possa seguir a Pilha da CatalystUI, a linguagem usada para construí-lo deve ser capaz de expressar os conceitos fundamentais dos quais o modelo depende.

Para linguagens de programação, isso significa principalmente duas coisas:

1. A linguagem deve ser capaz de representar dados fundamentais.
2. A linguagem deve ser capaz de representar relações fundamentais entre dados.

Essas questões são definidas pelas especificações fundamentais da CatalystUI. A FDEFSPEC define as representações de dados fundamentais esperadas. A FRELSPEC define as relações fundamentais esperadas entre essas representações, incluindo coleções, relações de memória, operações, relações de encadeamento e compostos.

Uma linguagem de programação verificada oferece aos desenvolvedores clareza e controle suficientes para criar sistemas compatíveis com CatalystUI sem depender de soluções alternativas frágeis, pouco claras ou instáveis para os conceitos básicos exigidos pela CatalystUI.

## O que a verificação significa

Uma linguagem de programação se torna **CatalystUI Verified** quando é revisada em relação às especificações listadas nesta seção e considerada dentro da especificação.

Para a Verificação de Linguagens de Programação, a revisão se concentra em saber se a linguagem consegue expressar os requisitos fundamentais definidos pelas especificações aplicáveis. Isso não significa que a própria linguagem seja uma implementação da CatalystUI. Significa que a linguagem fornece uma base adequada a partir da qual implementações compatíveis com CatalystUI podem ser construídas.

Uma linguagem não precisa satisfazer esses requisitos da mesma maneira que outra. Linguagens diferentes usam sintaxes, sistemas de tipos, bibliotecas padrão, compiladores, runtimes e padrões de projeto diferentes. A Verificação da CatalystUI permite essas diferenças, desde que os conceitos exigidos possam ser expressos de forma clara, confiável e consistente.

## O que significa “dentro da especificação”

Quando uma linguagem de programação é considerada **dentro da especificação**, isso significa que a Equipe CatalystUI revisou manualmente a linguagem e considerou razoável concluir que o comportamento exigido descrito pelas especificações aplicáveis pode ser expresso nessa linguagem.

Isso não exige um único padrão rígido de implementação. Uma linguagem pode satisfazer um requisito por meio de primitivas integradas, recursos da biblioteca padrão, comportamento do compilador, comportamento do runtime, garantias documentadas ou outro mecanismo estável apropriado para essa linguagem.

A verificação se preocupa com a capacidade prática de representar e preservar o significado da especificação, não com o fato de a linguagem usar exatamente os mesmos nomes, estruturas, sintaxe ou desenho interno do texto da especificação.

## Por que esta verificação existe

A CatalystUI foi projetada em torno de clareza, consistência e da representação fiel de como humanos e computadores interagem. As linguagens de programação importam porque determinam o que os desenvolvedores conseguem expressar de forma realista, com que segurança esses sistemas podem ser modelados e com que clareza implementações de nível superior podem ser construídas.

Se uma linguagem não consegue fornecer os conceitos fundamentais exigidos de forma estável, então implementações CatalystUI de nível superior se tornam mais difíceis de confiar. Desenvolvedores podem ser empurrados para abstrações pouco claras, comportamento imprevisível, dependências frágeis ou reescritas desnecessárias simplesmente para expressar ideias que deveriam ser confiáveis desde o início.

A Verificação de Linguagens de Programação existe para identificar quais linguagens fornecem uma base forte o suficiente para o trabalho com CatalystUI. Ela oferece a desenvolvedores, projetistas de linguagens e organizações uma compreensão mais clara sobre se uma linguagem é adequada para construir sistemas compatíveis com CatalystUI.

## Como uma linguagem se torna verificada

Para se tornar **CatalystUI Verified para linguagens de programação**, uma linguagem deve ser revisada em relação às especificações listadas nesta seção.

O processo geral é:

1. As especificações aplicáveis da CatalystUI são identificadas.
2. A linguagem é revisada em relação a cada especificação exigida.
3. A Equipe CatalystUI determina se a linguagem satisfaz a intenção e os requisitos das especificações.
4. Se a linguagem for considerada dentro da especificação, ela poderá receber a Verificação da CatalystUI.
5. Depois de verificada, a linguagem poderá ser listada na página de [Linguagens verificadas](/verified/).

A revisão pode considerar documentação oficial da linguagem, comportamento da biblioteca padrão, comportamento do compilador, comportamento do runtime, exemplos de implementação, casos de teste e outras evidências necessárias para determinar se a linguagem atende aos requisitos.

O comportamento do compilador e do runtime pode ser considerado durante a revisão quando esse comportamento faz parte da forma como a linguagem é comum e oficialmente usada. No entanto, verificar uma linguagem de programação não verifica automaticamente todos os compiladores, runtimes, pacotes, frameworks, bibliotecas, aplicações ou ferramentas no ecossistema dessa linguagem.

## Especificações aplicáveis

As especificações listadas nesta seção definem os requisitos usados para a Verificação de Linguagens de Programação.

Para linguagens de programação, a base ativa atualmente se concentra nas seguintes categorias de especificação:

* **FDEFSPEC**, que define representações de dados fundamentais.
* **FRELSPEC**, que define relações fundamentais entre representações de dados.

Juntas, essas especificações estabelecem a base mínima necessária para que uma linguagem de programação represente sistemas compatíveis com CatalystUI.

Especificações adicionais podem ser introduzidas posteriormente para categorias de verificação mais especializadas. Essas especificações podem definir requisitos de implementação de nível superior, plataforma, acessibilidade, internacionalização, framework, serviço ou runtime. No entanto, essas especificações posteriores se apoiam na base em vez de substituí-la.

Uma linguagem de programação se torna verificada ao satisfazer as especificações exigidas para esta categoria. Não se espera que ela satisfaça requisitos específicos de implementação não relacionados, a menos que esses requisitos sejam adicionados à Verificação de Linguagens de Programação.

## Escopo da verificação

A Verificação da CatalystUI para Linguagens de Programação se aplica à linguagem de programação conforme revisada.

Uma linguagem verificada fornece uma base adequada para o desenvolvimento compatível com CatalystUI. Ela não garante que todo projeto escrito nessa linguagem siga a CatalystUI corretamente, nem verifica automaticamente o ecossistema ao redor.

Ferramentas, bibliotecas, frameworks, runtimes, aplicações, serviços ou implementações separados podem exigir sua própria revisão, dependendo da categoria de verificação solicitada.

A Verificação de Linguagens de Programação deve, portanto, ser entendida como uma checagem de base. Ela confirma que a linguagem pode representar os conceitos exigidos. Ela não confirma que todo uso da linguagem aplica esses conceitos corretamente.

## Validade da verificação

A Verificação da CatalystUI se aplica apenas ao estado revisado de uma linguagem de programação no momento em que a verificação é emitida.

Linguagens de programação são tratadas como um caso especial porque muitas linguagens preservam compatibilidade entre várias versões. Uma linguagem pode manter sua verificação em versões posteriores desde que preserve compatibilidade retroativa com os recursos, primitivas, representações e comportamentos dos quais a revisão original dependia.

Novos recursos da linguagem, por si só, não invalidam a verificação. Uma versão futura pode exigir uma nova revisão somente se remover, quebrar ou alterar substancialmente a base verificada.

Em outras palavras, estender uma linguagem geralmente é aceitável. Quebrar a base verificada pode exigir revisão.

## Linguagens verificadas

As linguagens de programação verificadas conhecidas são listadas separadamente na página de [Linguagens verificadas](/verified/).
