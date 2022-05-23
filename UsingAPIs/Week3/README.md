# Semana 3

Na última semana do módulo Using API's, você colocará em prática tudo o que aprendeu e construirá seu próprio aplicativo de página única conectado a uma API! O que você constrói depende totalmente de você. Talvez você já tenha uma ideia na cabeça há algum tempo, ou talvez se inspire em todas as API's abertas que estão disponíveis.

Este é um empreendimento bastante grande, portanto, durante o projeto, um dos mentores deste módulo será designado a você. Sinta-se à vontade para pedir ajuda se estiver travado ou inseguro, mas eles foram instruídos a não escrever nenhum código para você :).

## Requisitos do projeto
Queremos que você fique animado e seja livre para construir algo pelo qual você é apaixonado, mas há algumas coisas que precisamos ver que você dominou. Isso significa que existem alguns requisitos:

- O aplicativo precisa ser um aplicativo de página única. Isso significa que apenas um arquivo `index.html` e JavaScript precisa atualizar o html usando a manipulação do DOM.
- O aplicativo precisa interagir com uma API para coletar dados.
- O aplicativo precisa ter carregamento/tratamento de erros para a interação com a API.
- O aplicativo precisa de alguma interação do usuário, de modo que você precise obter dados diferentes da API. Portanto, você não pode simplesmente pegar tudo da API e armazená-lo localmente com uma busca.
- Siga as [diretrizes para atribuições técnicas](https://github.com/HackYourFuture/ta_guidelines). Isso ajudará você a não ficar preso ou acabar com apenas metade de um aplicativo e garantir que o que você tenha no final seja algo apresentável.

## Ideias
Existem muitas APIs abertas para obter dados, dê uma olhada nas listas a seguir para ver se há um tópico que lhe interessa:

- [publicapi.dev](https://publicapi.dev)
- [repositório de API público](https://github.com/public-apis/public-apis)
- [lista de APIs](https://apilist.fun/)
- [APIs públicas](https://public-apis.io/)

Ao verificar se uma API é adequada para você, há algumas perguntas a serem verificadas:
1. A API é classificada e, em caso afirmativo, como?

`Rated` em um contexto de API significa quantas solicitações você pode fazer. Pode ser avaliado em tempo (quantas solicitações você pode fazer por segundo) ou em solicitações totais. Evite aqueles que têm uma taxa total de solicitações. Geralmente, esses aplicativos não fazem muitas solicitações por segundo, então isso não é um problema. Se você não precisa de uma chave de API, geralmente está seguro.
Se você não tiver certeza, entre em contato com o mentor do seu projeto.

2. Estão disponíveis os dados que desejo?

Dê uma olhada nos endpoints (há documentação para cada API) e verifique como os endpoints estão estruturados. Quais dados estão disponíveis e você será capaz de obter o que precisa? Você pode até mesmo consultá-lo um pouco com o `Postman` para experimentar algumas coisas.

3. A API suporta CORS?

CORS significa Cross-Origin Resource Sharing e pode ser um problema ao interagir com uma API. Em algumas das listas acima, você pode ver ou filtrar se é compatível e deve ficar bem. A melhor maneira de verificar isso é tentar fazer uma solicitação da API por meio de um comando de busca no navegador, como você aprendeu na semana passada. Então você sabe com certeza que funciona como esperado!
Para obter mais informações sobre o CORS, consulte o [artigo do MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

Se você realmente está preso e não tem inspiração, converse com o mentor do seu projeto e conversem juntos para chegar a algo.

## Produto final
O produto final (o repositório é o produto, não apenas o aplicativo) deve ser algo que você possa exibir em seu currículo. Portanto, dê uma olhada em nossas diretrizes de atribuição técnica [aqui](https://github.com/HackYourFuture/ta_guidelines) e nossas diretrizes de design [aqui](https://github.com/HackYourFuture/design_guidelines) para ver o que isso implica . Seguindo essas diretrizes, seu aplicativo E seu código ficarão ótimos, tornando-se uma ótima coisa para mostrar aos empregadores. Você também adquirirá o hábito de fazer isso com todas as atribuições técnicas que receber durante sua busca de emprego.

## Planejamento e prazos
Existem apenas 2 prazos no projeto, como você divide seu tempo para o resto é com você.

### Prazo 1: Definição do projeto
Até *Quinta-feira 18:00PM CET* (mas quanto mais cedo melhor) você deve enviar uma breve descrição do que seu aplicativo será, bem como o nome da empresa cuja marca/paleta de cores você irá imitar ao seu mentor de projeto.

A descrição deve deixar claro que seu aplicativo cumprirá os requisitos. É melhor dividi-lo em partes 'obrigatórias' (que atendem aos requisitos e serão construídas primeiro) e partes 'bom ter' (recursos que você pode adicionar mais tarde para tornar seu aplicativo mais legal). O motivo para fazer essa divisão é ter certeza de que você também priorizará seu trabalho corretamente. Você provavelmente terá problemas de tempo no final, e é possível cortar recursos extras, mas não os "obrigatórios". Uma semana não é muito para construir um aplicativo e no final só poderemos avaliar com base no que está funcionando.

A paleta de cores/marca da empresa ajudará você a criar algo que pareça bom, conforme explicado em nossas [diretrizes de design](https://github.com/HackYourFuture/design_guidelines).

### Prazo 2: Candidatura
Até *terça-feira 23:59 PM CET* você deve enviar um link para o seu projeto github para o Diretor de Educação. Certifique-se de que tudo funciona para eles! A melhor maneira de testar isso é clonar seu repositório para um novo diretório em seu computador e tentar executá-lo lá.

## Classificação
Depois de terminar o projeto, você receberá outra entrevista técnica sobre seu próprio projeto para determinar se pode passar para o próximo módulo. Esta entrevista técnica é semelhante ao que você teve no [módulo de navegadores](https://github.com/HackYourFuture/Browsers/blob/main/PROJECT.md#the-interview), exceto que em vez de explicar como implementar um recurso, você receberá algum código JavaScript e algumas perguntas sobre ele. Fique de olho no canal da sua turma para saber quando serão.

_Nota: A dificuldade do aplicativo afeta a classificação de duas maneiras:_
- Você ganha pontos extras por criar um aplicativo difícil (coisas como várias páginas, usar várias fontes de dados, ter muitos recursos etc.)
- Esperamos que aplicativos mais simples tenham código melhor estruturado e sejam mais tolerantes em aplicativos mais complexos

_Observação: seguir as diretrizes de atribuição técnica também fará parte da classificação_
- Certifique-se de ler as [diretrizes de design](https://github.com/HackYourFuture/design_guidelines) e de que o design do seu aplicativo segue essas diretrizes
- Certifique-se de ter lido as [diretrizes de atribuição técnica](https://github.com/HackYourFuture/ta_guidelines) e que seu código e README seguem estas diretrizes

## Considerações finais
Como todos vocês estão trabalhando nos projetos esta semana, não haverá uma sessão de perguntas e respostas no domingo desta semana.

Aproveite para ser prático!


