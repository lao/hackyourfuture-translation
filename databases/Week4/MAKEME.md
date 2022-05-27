# Bases de dados de trabalhos de casa Semana 4

## **Lista de afazeres**

1. Pratique os conceitos
2. Exercícios de preparação
3. Exercícios do MongoDB
4. Codifique junto

## 1. **Pratique os conceitos**

Vamos praticar algumas consultas avançadas do MongoDB. Dê uma olhada nos exercícios a seguir. Se você não tiver certeza sobre os comandos que usou na semana passada, sinta-se à vontade para também fazer 01 e 02 desta série. Você precisará voltar para 00 para importar os dados para seu banco de dados:

- [Exercícios avançados do MongoDB](https://github.com/mattdavis0351/mongodb-labs/blob/master/exercises/03_advanced-mongo-queries.md)

## 2. **Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `databases`, vá para a pasta `Week4`. Dentro dessa pasta, navegue até o arquivo `QA_PREP_EXERCISE.md` que explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## 3. **Exercícios do MongoDB**

Vamos criar um novo banco de dados para a lição de casa desta semana. Você pode criar um banco de dados chamado `databaseWeek4` que pode ser usado para os exercícios a seguir.

### 3.1 **Exercício 1: Agregação**

Vamos praticar algumas consultas de agregação, para isso teremos que usar alguns dados e felizmente [kaggle](https://www.kaggle.com/) é um ótimo site que fornece conjuntos de dados para usar. Na pasta `ex1-aggregation` você encontrará um arquivo csv com dados para você.

1. Encontre uma maneira de obter os dados do arquivo csv em seu banco de dados MongoDB. Os documentos devem se parecer com:

``` js
{
  _id: ObjectId(625ff77ada84ee8b5dd06e82),
  País:"Afeganistão",
  Ano: 1950,
  Idade: "20-24",
  M:374109,
  F:318392
}
```

2. Escreva uma função que retornará a matriz da população total (M + F em todas as faixas etárias) para um determinado "País" por ano. O resultado deve ser algo assim, estes são os valores para `Holanda`:

``` js
[
  { _id: 1950, countPopulation: 10042051 },
  { _id: 1960, countPopulation: 11448815 },
  { _id: 1970, countPopulation: 13001941 },
  { _id: 1980, countPopulation: 14148410 },
  { _id: 1990, countPopulation: 14965442 },
  { _id: 2000, countPopulation: 15926188 },
  { _id: 2010, contagemPopulação: 16682925},
  { _id: 2020, countPopulation: 17134872 },
  { _id: 2022, contagemPopulação: 17211448},
];
```

3. Escreva uma função que retornará todas as informações de cada continente para um determinado campo `Year` e `Age`, mas adicione um novo campo `TotalPopulation` que será a adição de `M` e `F`. Por exemplo, se eu der `2020` para o `Year` e `100+` para a `Age`, ele deve retornar algo assim:

``` js
[
  {
    _id: new ObjectId("62600561b0a05834e3382cf8"),
    País: "ÁFRICA",
    Ano: 2020,
    Idade: "100+",
    M: 1327,
    F: 2723,
    População Total: 4050,
  },
  {
    _id: new ObjectId("62600561b0a05834e3382da0"),
    País: "ÁSIA",
    Ano: 2020,
    Idade: "100+",
    M: 57019,
    F: 207883,
    População Total: 264902,
  },
  {
    _id: new ObjectId("62600561b0a05834e33832a1"),
    País: "EUROPA",
    Ano: 2020,
    Idade: "100+",
    M: 22579,
    F: 102056,
    População Total: 124635,
  },
  {
    _id: new ObjectId("62600561b0a05834e33835d4"),
    País: "AMÉRICA LATINA E CARIBE",
    Ano: 2020,
    Idade: "100+",
    M: 19858,
    F: 49218,
    População Total: 69076,
  },
  {
    _id: new ObjectId("62600561b0a05834e3383946"),
    País: "AMÉRICA DO NORTE",
    Ano: 2020,
    Idade: "100+",
    M: 22267,
    F: 83419,
    População Total: 105686,
  },
  {
    _id: new ObjectId("62600561b0a05834e3383985"),
    País: "OCEANIA",
    Ano: 2020,
    Idade: "100+",
    M: 1094,
    F: 3980,
    População Total: 5074,
  },
];
```

### 3.2 **Exercício 2: Transações**

Assim como na semana passada, vamos resolver o mesmo problema de transação, mas no MongoDB. Observe que você precisará incluir algumas bibliotecas, o que significa que você precisará configurá-las também (use a pasta `ex2-transactions` para isso). Você provavelmente também desejará adicionar um `index.js` que chame as funções que criaremos para testá-lo, deixamos a implementação disso para você. Agora vamos começar, vamos dividir nosso código em vários arquivos novamente, primeiro sendo o arquivo de configuração:

1. Crie um arquivo `setup.js`.
2. Ele deve limpar o array `accounts` e então preenchê-lo com alguns dados de exemplo. Assim como na semana passada, queremos que um documento de conta tenha um campo `account_number` e `balance`. Então ele deve ter outro campo chamado `account_changes` que é um array que contém os campos: `change_number, amount, changes_date, remark`.
3. Provavelmente é melhor fazer disso uma função que você possa exportar e chamar

Então é hora de escrever nossa função de transação:

1. Crie um arquivo `transfer.js` que conterá nossa função `transfer`.
2. Deve transferir dinheiro de uma conta para outra, pelo que terá de saber o seguinte: de qual conta, para qual conta, o valor e a observação desta transação.
3. Isso deve atualizar os saldos de ambas as contas e, para cada conta, adicionar uma alteração à lista. O número da alteração deve ser incrementado, portanto, se o último `change_number` for 30, o `change_number` para a nova alteração deverá ser 31.
4. Teste se funciona chamando a função para transferir 1000 da conta número 101 para a conta número 102.

Envie os arquivos `setup.js` e `transfer.js`.

## 4. **Código junto**

Esta semana temos um pequeno código junto para mostrar como implementar a paginação e torná-la reutilizável para todas as suas rotas!

- [API paginada com Node e Mongoose](https://www.youtube.com/watch?v=ZX3qt0UWifc). Estaremos trabalhando no Mongoose no projeto final, mas isso dá um pequeno teaser sobre o que é o mangusto!

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! A lição de casa que precisa ser enviada é a seguinte:

1. Exercícios do MongoDB

Carregue seu código para o repositório de bancos de dados bifurcados no GitHub. Faça um pull request para o repositório bifurcado do HackYourHomework.

> Esqueceu como fazer o upload de sua lição de casa? Vá até o [guia](../hand-in-homework-guide.md) para aprender como fazer isso novamente.

_Prazo terça-feira 23.59 CET_
