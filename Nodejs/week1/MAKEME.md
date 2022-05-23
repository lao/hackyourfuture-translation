# Homework Node.js Semana 1

## Lista de afazeres

1. Curso intensivo
2. Pratique os conceitos
3. Exercícios de preparação
4. Exercícios Node.js
5. PROJETO: HackYourTemperature I

> Antes de prosseguirmos, vamos verificar se temos as versões mais recentes do Node.js e do Node Package Manager (NPM) instalados. Você pode fazer isso indo para a linha de comando (CLI) e executando `node -v` e `npm -v`. O Node.js deve ser pelo menos **v12** e o NPM deve ser pelo menos **v6**.

## **1. Rota de colisão**

Há um ótimo curso intensivo disponível aqui: https://www.youtube.com/watch?v=2LUdnb-mls0. Ele apresenta muitos dos conceitos que você praticará esta semana.

## **2. Pratique os conceitos**

> Os problemas na seção _praticar os conceitos_ são projetados para aquecê-lo para os exercícios reais abaixo. Você não precisa enviar seu código, mas precisa concluir todos os exercícios.

Nos exercícios interativos desta semana, voltaremos à linha de comando. Usaremos o software da [Nodeschool](https://nodeschool.io/) para fazer alguns exercícios.

Vá para sua interface de linha de comando favorita e execute o seguinte comando

``` md
npm install -g learnyounode
```

Quando estiver tudo instalado, execute o comando:

``` md
aprenderyounode
```

E o menu será aberto. **Faça o exercício 1 (HELLO WORLD) até 8 (HTTP COLLECT)**!

## **3. Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `Node.js`, vá para a pasta `week1`. Dentro dessa pasta, navegue até `/prep-exercises`. Para cada exercício, você encontrará uma pasta separada. O `README` explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## **4. Pratica exercícios**

Dentro do seu fork `Node.js`, vá para a pasta `week1`. Dentro dessa pasta, navegue até `/practice-exercises`. Para cada exercício, você encontrará uma pasta separada. O `README` explica o que precisa ser feito. Passe por eles para praticar os conceitos que você aprendeu!

## **5. PROJETO: HackYourTemperature I**

> Nesta parte do dever de casa você estará configurando a base do seu projeto: `HackYourTemperature`. Dentro da pasta `homework`, crie uma nova pasta chamada `hackyourtemperature`. Você vai adicionar a ele toda semana.

Neste módulo você estará reconstruindo um aplicativo existente, começando do zero. O aplicativo é chamado `HackYourTemperature` e você pode encontrá-lo aqui: [HackYourTemperature](https://hackyourtemperature.herokuapp.com/).

Cada semana você estará construindo uma certa parte dele. Esta semana, começaremos a criar um servidor web, usando [Express.js](https://expressjs.com/). Dentro da pasta `hackyourtemperature`:

1. Crie um arquivo JavaScript chamado `server.js` (pode ser qualquer nome, mas é mais significativo)
2. Inicialize o Node Package Manager e crie um arquivo `package.json` executando `npm init -y`
3. Instale e carregue os módulos necessários para este projeto: eles são `express` (nosso servidor web), `express-handlebars` (nosso mecanismo de modelagem) e `node-fetch` (uma biblioteca para lidar com solicitações http no nó)
4. Como queremos usar as instruções `import` do modernJS, adicione a linha `"type": "module"` ao arquivo `package.json`
5. Configure seu servidor web usando o Express (criando uma instância do Express, ouça **porta 3000**)
6. Faça uma solicitação `GET` para `/` que envia a mensagem `hello from backend to frontend!` para o cliente

Depois de escrever todo esse código, você pode verificar se está funcionando executando `node server.js` na linha de comando e verificando seu navegador em `http://localhost:3000`. A página deve exibir a mensagem `hello from backend to frontend!`.

### 4.1 Adicionando uma solicitação POST

Nesta parte adicionaremos outro endpoint, com um método `POST`.

1. Crie uma rota `POST`, que tenha como endpoint: `/weather`
2. Para tornar o Express ciente de qual tipo de dados são os dados de entrada (que é JSON). Fazemos isso usando o método `json()` no objeto Express. Usando a função `use()` do `app`, passe o `json()` do `express`.
3. Dentro da função callback da rota `POST`, acesse o `cityName` e coloque-o dentro de uma variável. Dica: use o objeto `body` da requisição para encontrá-lo.
4. Envie a entrada do formulário de volta como resposta ao cliente

Teste seu trabalho usando o Postman e certifique-se de que sempre que você enviar algo no formulário, ele retorne como resposta do servidor as palavras exatas que você enviou.

Se você está cansado de reiniciar constantemente seu servidor, pesquise no Google o pacote `nodemon` para ver se isso será útil para você!

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! Dê uma olhada no seguinte [guia](../hand-in-homework-guide.md) para ver como isso é feito.

A lição de casa que precisa ser enviada é a seguinte:

1. Projeto: HackYourTemperature I

_Prazo terça-feira 23.59 CET_
