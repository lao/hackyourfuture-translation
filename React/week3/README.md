# Material de Leitura Reagir Semana 3

## Agenda

Estes são os tópicos da semana 3:

1. [API de contexto](https://study.hackyourfuture.net/#/react/context-api.md)
   - Gerenciamento de estado global
   - Estado de conexão ao componente
2. [Ganchos personalizados](https://study.hackyourfuture.net/#/react/custom-hooks.md)
   - Construindo ganchos personalizados
   - Usando ganchos personalizados de outras pessoas
3. Teste
   - [teste e2e](https://study.hackyourfuture.net/#/testing/e2e-testing.md)
   - [react-testing-library](https://study.hackyourfuture.net/#/react/testing.md)

## Nota importante sobre React

> No mundo React, há uma grande mudança acontecendo desde a introdução dos 'hooks' em 2018. Antes dos hooks, o React foi construído usando componentes de classe e função. Atualmente, é recomendado usar apenas componentes de função em combinação com ganchos para todo o código que você construir a partir de agora. No entanto, quando você vai fazer pesquisa por conta própria ou quando você entra em seu estágio, você vai se deparar com componentes de classe. Isso será cada vez menos com o passar do tempo e esperamos que possamos remover isso em algum momento no futuro.

> Nós do HackYourFuture ensinaremos apenas a maneira recomendada de criar aplicativos e fornecemos uma seção no livro de estudo para compartilhar os detalhes mais básicos sobre como ler os componentes da classe [aqui](https://study.hackyourfuture.net/ #/react/class-vs-function-components.md). Se você encontrar componentes de classe em sua pesquisa, tente procurar um tutorial, pergunta ou vídeo mais atualizado. Se você encontrar componentes de classe durante seu estágio, converta-o em um componente de função. Os desenvolvedores vão te amar :).

## Metas da semana

Esta semana vamos olhar para alguns tópicos mais avançados.

Primeiramente, vamos dar uma olhada na API de contexto, que soa como algo externo, mas na verdade é algo que o React nos fornece. Dê uma olhada [aqui](https://study.hackyourfuture.net/#/react/context-api.md). Um erro comum que os alunos cometem é pensar que você cria apenas um contexto para cada aplicativo, mas deve pensar na API de contexto como uma forma de consolidar o estado e as funções que o cercam em um só lugar para todos os subcomponentes usarem. Então, ao pensar em usar a API de contexto, pense nisso como uma maneira de manter o código que pertence em um só lugar!

Como você provavelmente notou na biblioteca de roteadores na semana passada, eles construíram seus próprios ganchos para fornecer alguns dos arquivos . Podemos fazer isso também e é extremamente poderoso. Dê uma olhada na seção de gancho personalizado [aqui](https://study.hackyourfuture.net/#/react/custom-hooks.md) para ver como fazer isso.

Finalmente, é hora de revisitar o tópico de testes novamente. Queremos apresentar a você duas maneiras de testar: [teste de ponta a ponta (e2e)](https://study.hackyourfuture.net/#/testing/e2e-testing.md) e o [react-testing- biblioteca](https://study.hackyourfuture.net/#/react/testing.md). Esta semana, vamos nos concentrar mais em testes de ponta a ponta, pois os testes estão se afastando da cobertura pesada de testes de unidade e avançando para testes mais centrados no usuário, dos quais o teste e2e é o mais centrado no usuário que você pode obter. Teremos alguns exercícios de teste com a react-testing-library que você pode fazer, mas eles são opcionais para quando você tiver tempo extra.

Agora, a primeira pergunta que sempre recebemos é 'Qual é a melhor maneira de testar?' e para evitar essa pergunta na sessão de perguntas e respostas: não há melhor maneira de testar. O teste é sempre um equilíbrio entre a quantidade de cobertura necessária com a quantidade de tempo a ser gasta nele. Certos aplicativos críticos precisarão de mais testes e outros aplicativos menos críticos muito pouco. Certas empresas terão testes automatizados classificados como extremamente importantes, outras terão seu foco em testes manuais. Como tal, não há resposta para a pergunta, você desejará ter um entendimento básico de ambos para estar preparado, mas será uma decisão da empresa/equipe sobre como abordar o tópico de teste para sua aplicação específica. Observe que dizemos `compreensão básica`, pois tentar aprender esse tipo de teste em 1 semana é impossível.

Esses são tópicos complexos, então brinque com esse novo conhecimento em seus próprios aplicativos!

## Finalizado?

Você terminou de passar pelos materiais? Toca aqui! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
