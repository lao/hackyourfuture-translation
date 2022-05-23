# Homework Node.js Semana 2

## Lista de afazeres

1. Exercícios de preparação
2. Pratique exercícios
3. PROJETO: HackYourTemperature II
4. Código junto
5. Opcional: ideias de projetos paralelos

## **1. Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `Node.js`, vá para a pasta `week2`. Dentro dessa pasta, navegue até `/prep-exercises`. Para cada exercício, você encontrará uma pasta separada. O `README` explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## **2. Pratica exercícios**

Dentro do seu fork `Node.js`, vá para a pasta `week2`. Dentro dessa pasta, navegue até `/practice-exercises`. Para cada exercício, você encontrará uma pasta separada. O `README` explica o que precisa ser feito. Passe por eles para praticar os conceitos que você aprendeu!

## **3. PROJETO: HackYourTemperature II**

> Esta semana você continuará desenvolvendo o `HackYourTemperature`. Use a mesma pasta da semana anterior.

Até agora você construiu um servidor web básico. Carregamos os módulos necessários. Temos um `end point`, que é `/`. Ativamos o servidor, `escutando` um número de porta. E criamos uma solicitação `POST` para lidar com a entrada do usuário.

A lição de casa desta semana vamos expandir isso, em 2 partes:

1. Vamos conectar nossa API a uma API externa para pegar os dados que queremos.
2. Vamos adicionar testes à nossa API para garantir que ela funcione conforme o esperado.

### 3.1 Adicionar API externa

Nossa API externa com a qual vamos trabalhar é a [Open Weather Map API](https://openweathermap.org/). O objetivo desta parte é aprender como fazer uma solicitação de API do back-end e, em seguida, enviar o resultado para o front-end.

#### 3.1.1 Configurando a API

1. Primeiro temos que fazer uma conta: faça isso através do [site](https://openweathermap.org/appid)
2. Volte para a pasta do seu projeto e crie uma nova pasta chamada `sources`. Dentro crie um arquivo chamado `keys.js`. Vá para sua conta OpenWeatherMap, encontre a API Key e copie-a em um objeto `keys.js` com o nome da propriedade `API_KEY`. Não se esqueça de exportá-lo

#### 3.1.2 Busque em nossa API

1. Remova a resposta da rota "POST" da semana passada, vamos reescrevê-la mais tarde
2. Dentro da rota `POST`, insira `node-fetch` e passe o valor do endpoint da API: `https://api.openweathermap.org/data/2.5/weather`. Para que funcione, primeiro temos que importar as chaves, assim:

``` js
importar chaves de "./sources/keys.js";
```

Então podemos usar esse objeto para buscar as informações, assim:

``` js
fetch(`https://api.openweathermap.org/data/2.5/weather?APPID=${keys.API_KEY}`);
```

Agora temos que enviar o nome da cidade fornecido pelo usuário, dê uma olhada na documentação de como fazer isso. Existem 2 situações que podem acontecer: se o nome da cidade não for encontrado, queremos enviar ao cliente uma resposta com uma mensagem de que a cidade não foi encontrada. No entanto, se a cidade for encontrada e queremos retornar uma mensagem que contenha o nome da cidade e a temperatura atual.

3. Se o resultado não for encontrado, enviamos de volta um objeto: `{ weatherText: "City is not found!" }`
4. Se o resultado for encontrado, também devolvemos o objeto. Apenas, em vez de apenas uma string `City is not found!`, adicione dinamicamente o `cityName` e a temperatura (obtida do resultado da chamada da API). Dica: use strings de modelo para adicionar variáveis em suas strings!

Verifique se isso funciona como esperado!

### 3.2 Adicionando casos de teste

Agora que temos o básico de nossa API funcionando, é hora de escrever os casos de teste que garantirão que quaisquer alterações que fizermos não quebrem o aplicativo. Para fazer isso, adicionaremos uma biblioteca chamada `supertest` para testar solicitações http, bem como o framework de teste escolhido para este currículo `jest`.

1. Instale ambas as bibliotecas como uma dependência do desenvolvedor. Nós não precisamos de nossos testes em produção, então nos certificamos de tê-los apenas como dependências de desenvolvimento!
2. Crie uma nova pasta chamada `__tests__`, esta é a pasta padrão onde o `jest` procura por nossos arquivos de teste. Em seguida, adicione um arquivo `app.test.js` para escrever nossos testes.
3. Dê uma olhada no seu código JavaScript para se lembrar do que `describe`, `it` e `expect` fizeram novamente e configure um teste simples:

``` js
describe("POST /", () => {
  it("Teste rápido", () => {
    expect(1).toBe(1);
  });
});
```

Configure um script de teste em seu `package.json` para verificar se funciona! Você não deve obter erros e 1 teste de aprovação.

#### 3.2.1. Configurando jest com supertest

Jest é um framework de teste JavaScript, mas `express`, `node-fetch` e `supertest` são um pouco mais do que apenas JavaScript. Então, precisamos fazer alguma configuração extra.

O primeiro problema é que usamos `modules` e `modernJS`. O Jest por si só não entende isso e precisamos configurar o `babel` para converter nosso código em JavaScript simples. `Babel` é algo que você provavelmente terá configurado em todos os seus aplicativos, mas é feito sob o capô muitas vezes. Desta vez vamos sujar as mãos!

1. Instale `babel-jest` e `@babel/preset-env` como dependências do desenvolvedor. Estes são pacotes babel que são feitos para ajudar o `jest` a compilar
2. Copie os arquivos `babel.config.cjs` e `jest.config.js` na pasta `config-files` para a pasta `hackyourtemperature`. Há alguns comentários explicando o que estamos configurando, mas será difícil saber como tudo se encaixa. Isso está fora do escopo por enquanto, mas se você estiver interessado, pode fazer uma pesquisa!
3. Reinicie o `jest` para que ele possa pegar os novos arquivos `config`

O segundo problema é que os testes no jest são executados de forma assíncrona e sempre que executarmos vários testes ao mesmo tempo, o código do nosso servidor iniciará nossa aplicação usando a mesma porta.

1. Então descubra uma maneira de dividir seu código `server.js` em um arquivo `app.js` e `server.js` para que nossos testes possam pegar o aplicativo Express sem que ele inicie o servidor. Seu `server.js` deve ser o menor possível, basta pegar o aplicativo e iniciá-lo em uma porta
2. Verifique se tudo isso funciona adicionando as seguintes importações ao seu arquivo `app.test.js`:

``` js
importar aplicativo de "../app.js";
importar superteste de "supertest";

const request = supertest(app);
```

Execute seus testes novamente e você deverá obter um teste de aprovação verde novamente sem erros.

Se você receber um erro `não pode usar a importação fora de um módulo`, isso significa que a configuração do `babel` deu errado. Verifique se você tem a versão mais recente do Node e se os arquivos de configuração estão sendo usados. Você pode verificar se os arquivos estão sendo usados adicionando um erro de sintaxe ao arquivo. Se você receber o mesmo erro, os arquivos de configuração não estão sendo compilados.

#### 3.2.2 Escrevendo os testes

Agora vem a parte divertida, é hora de escrever seus testes. Pense no que precisa ser testado! Lembre-se de que o caminho feliz é apenas uma pequena parte da sua API. E se o usuário não fornecer um cityName? E se o nome da cidade for sem sentido?

Por teste, crie um novo `it` com um bom título descritivo. Esse é o título que você verá no console, portanto, deve ficar claro o que está acontecendo de errado a partir daí.

Algumas dicas:

- A variável `request` que criamos chamando `supertest(app)` tem funções nela chamadas `get`, `post`, etc. Então para enviar um pedido `POST` você escreveria `request.post('/your -endpoint')`.
- Para enviar um corpo com sua requisição, você pode encadear um `.send({ your: 'object' })` para a promessa dada pela função `post`
- Um de seus testes não dará um resultado fixo, mas dinâmico (ou seja, a temperatura que mudará). Normalmente, você desejará zombar do código da API, mas isso está fora do escopo deste exercício. Por enquanto, pense em verificar se a string 'contém' as partes que você precisa. (Se você encontrar algum tempo e quiser ver como fazer isso, dê uma olhada na documentação do jest sobre módulos de simulação)
- Não se esqueça de verificar o código de status!

Quando todos os seus testes estiverem verdes, você pode ter certeza de que tudo funciona conforme o esperado! Dê uma olhada no seu código e limpe-o, se você escreveu bem seus testes, tudo o que você precisa fazer no final é executar seu script de teste para ver se você não quebrou nada.

## **4. Código junto**

> Lembre-se de enviar o código final de todos os códigos para o seu perfil do Github para que você possa consultá-lo a qualquer momento!

### 4.1 API de biblioteca

Nosso mentor Andrej criou seu próprio código para construir uma API de biblioteca. Caminho para ir além! Dê uma olhada e codifique para passar por todas as etapas de uma API em sua forma mais simples.

- [API da biblioteca](https://www.youtube.com/watch?v=PVb_vIyw4HI)

### 4.2 Aplicativo de vendas de e-books

Neste aplicativo você estará construindo um Aplicativo de Vendas de Ebooks. Você tornará possível adicionar novos livros a uma lista de livros. Você aprenderá até mesmo como colocá-lo online, para que possa obter um URL que pode ser usado para acessar seu aplicativo em qualquer lugar.

Aproveitar!

- [Aplicativo de vendas de e-books](https://www.youtube.com/watch?v=QT3_zT97_1g)

## **5. Opcional: ideias de projetos paralelos**

> Uma parte do currículo do HackYourFuture é trabalhar em tantos projetos paralelos quanto possível ao longo do tempo que você tem. Esta é uma boa maneira de adicionar conhecimento extra ao seu arsenal e mostrar em seu currículo que você está motivado para aprender novas tecnologias. Este também é um ótimo momento para aprender coisas novas, pois há muitos mentores disponíveis para ajudá-lo no canal `#projetos` no Slack! Você não terá essa quantidade de tempo e suporte assim que começar a trabalhar. Dê uma olhada no [hyf_projects repo](https://github.com/HackYourFuture/hyf_projects/blob/main/README.md#project-2-a-try-out-application) para mais detalhes.

### 5.1 Documente sua API!

Ao usar API's no módulo `Using API's` você terá notado que todas essas APIs possuem extensa documentação sobre como usá-las. Como os desenvolvedores gostam de construir ferramentas para tudo, existem algumas boas ferramentas para documentar semiautomaticamente sua API a partir do seu código! Economiza muito trabalho e garante que você não esqueça de atualizar a documentação caso o código mude!

Adicione documentação automática à sua API usando uma dessas ferramentas (Swagger, apiDoc ou docbox)!

### 5.2 Soquetes da Web

Está se tornando normal que todas as páginas da Web sejam atualizadas automaticamente sempre que houver novos dados disponíveis. Pense nos feeds de notícias ao vivo que informam quando há um novo item ou que há uma nova mensagem no twitter. Tudo isso é implementado usando Web Sockets, onde você como programador pode configurar um link entre sua página e o servidor.

Experimente criar um aplicativo de bate-papo simples de pilha completa com um servidor websocket expresso!

### 5.3 GraphQL

Nós nos concentramos apenas na maneira REST de construir uma API, mas existe uma maneira diferente chamada `GraphQL`. Isso permite que o frontend defina em sua consulta os dados que deseja obter de volta. Muito legal, mas também bastante complexo. Se você está pronto para um desafio, tente recriar seu projeto usando GraphQL (o pacote `express-graphql` é provavelmente a maneira mais fácil)!

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! Faça upload de todos os seus arquivos para o seu repositório bifurcado (o mesmo da semana 1). Em seguida, faça um pull request para ele.

Se você precisar de uma atualização, dê uma olhada no seguinte [guia](../hand-in-homework-guide.md) para ver como isso é feito.

A lição de casa que precisa ser enviada é a seguinte:

1. Projeto: HackYourTemperature II

_Prazo terça-feira 23.59 CET_
