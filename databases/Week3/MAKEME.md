# Bases de dados de trabalhos de casa Semana 3

## **Lista de afazeres**

1. Pratique os conceitos
2. Exercícios de preparação
3. Exercícios de banco de dados
4. Codifique junto

## 1. **Pratique os conceitos**

Vamos fazer um aquecimento com alguns exercícios interativos! Vamos começar fazendo a lição 13-18 do seguinte:

- [SQLBolt](https://sqlbolt.com/lesson/select_queries_introduction)

Então vamos praticar algumas consultas do MongoDB! Comece criando uma conta Atlas [aqui](https://www.mongodb.com/cloud/atlas/lp/try2). Atlas é o próprio serviço de nuvem do MongoDB que hospeda bancos de dados mongodb e, felizmente, eles oferecem uma camada gratuita muito graciosa para brincar. Depois de criar uma conta, certifique-se de criar um cluster de banco de dados que pode ser seu playground para o seguinte:

- [Exercícios práticos do MongoDB](https://gist.githubusercontent.com/theRemix/7305403e1ab6fc8674f0/raw/c068ab51e930eb133a9443caa314205a89ef4d61/exercise.md) Observe que este é um arquivo raw markdown, então você pode copiá-lo em seu editor e salvá-lo como `.md` para obter realce de sintaxe. A versão ao vivo tem comentários com respostas que você pode conferir depois [aqui](https://gist.github.com/theRemix/7305403e1ab6fc8674f0#file-exercise-md).

## 2. **Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `databases`, vá para a pasta `Week3`. Dentro dessa pasta, navegue até o arquivo `QA_PREP_EXERCISE.md` que explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## 3. **Exercícios de banco de dados**

> Você precisará fazer alguma pesquisa para resolver esses exercícios. Todos os conceitos necessários para resolver esses exercícios NÃO são abordados no material de leitura. Isso é de propósito.

> Salve todos os seus arquivos na pasta `homework` dentro de `Week3`!

### 3.1. **Exercício 1: Normalização**

O gerente do clube de jantar gostaria de gerenciar o sistema de informação que o ajuda a acompanhar os jantares dos membros.
Como o gestor não é especialista em Sistemas de Informação, ele utiliza a tabela a seguir para armazenar as informações.
Ajude o gerente usando o conhecimento das formas normais do banco de dados.
Salve todas as respostas em um arquivo de texto/arquivo MD.

1. Quais colunas violam a 1NF?
2. Quais entidades você reconhece que podem ser extraídas?
3. Nomeie todas as tabelas e colunas que fariam uma solução compatível com 3NF.

```
+-----------+---------------+----------------+---- -------+-------------+------------+--------------- ----+-----------+------------------+
| id_membro | nome_membro | endereço_membro | jantar_id | jantar_data | local_code | local_descrição | food_code | comida_descrição |
+-----------+---------------+----------------+---- -------+-------------+------------+--------------- ----+-----------+------------------+
| 1 | Amit | 325 Parque máximo | D00001001 | 2020-03-15 | B01 | Grande Salão de Baile | C1, C2 | caril, bolo |
| 2 | Ben | 24 pista Hudson | D00001002 | 15/03/2020 | B02 | Topo de telhado Zoku | S1, C2 | sopa, bolo |
| 3 | Cristina | 516 6th Ave | D00001002 | 15/03/2020 | B02 | Topo de telhado Zoku | S1, C2 | sopa, bolo |
| 4 | Dan | 89 Rua João | D00001003 | 20-03-2020 | B03 | Fazenda de cabras | P1, T1, M1| torta, chá, mousse |
| 1 | Amit | 325 Parque máximo | D00001003 | 20-03-2020 | B03 | Fazenda de cabras | P1, T1, M1| torta, chá, mousse |
| 3 | Cristina | 516 6th Ave | D00001004 | 25 de março '20 | B04 | Cozinha da mamãe | F1, M1 | Falafal, Mousse |
| 5 | Gabor | 54 Rua Vivaldi | D00001005 | 26 de março '20 | B05 | Hungria com fome | G1, P2 | Goulash, Pasca |
| 6 | Hema | 9 Pedro St | D00001003 | 01-04-2020 | B03 | Fazenda de cabras | P1, T1, M1| torta, chá, mousse |
+-----------+---------------+----------------+---- -------+-------------+------------+--------------- ----+-----------+------------------+
```

### 3.2. **Exercício 2: Transações**

1. Crie duas tabelas `account` e `account_changes` (grave o arquivo transaction-create-tables.js)
2. A tabela `account` deve ter os seguintes campos: `account_number, balance`.
3. A tabela `account_changes` deve ter os seguintes campos: `change_number, account_number, valor, change_date, remark`.
4. Escolha os tipos de dados e chaves apropriados para essas tabelas.
5. Insira alguns dados de amostra nessas tabelas. (gravar o arquivo transaction-insert-values.js)
6. Transfira o valor de 1000 da conta número 101 para a conta número 102 e registre as alterações na tabela `account_changes`.
   Faça isso em uma _transação única_ (grave o arquivo transaction.js)

Envie todos os três arquivos (`transactions-create-tables.js`, `transactions-insert-values.js` e `transaction.js`).

### 3.3. **Exercício 3: injeção de SQL**

Você recebe a função abaixo que retorna a população de um país específico do banco de dados [world](../Week2/world.sql).

``` js
function getPopulation(País, nome, código, cb) {
  // supondo que a conexão com o banco de dados seja estabelecida e armazenada como conn
  consulta.con.(
    `SELECT Population FROM ${Country} WHERE Nome = '${name}' e código = '${code}'`,
    função (erro, resultado) {
      if (err) cb(err);
      if (result.length == 0) cb(new Error("Não encontrado"));
      cb(null, resultado[0].nome);
    }
  );
}
```

1. Dê um exemplo de um valor que pode ser passado como `nome` e `código` que aproveitaria a injeção de SQL e (busca todos os registros no banco de dados)
2. Reescreva a função para que ela não seja mais vulnerável à injeção de SQL

### 3.4. **Exercício 4: MongoDB CRUD**

Você já deve ter uma conta atlas que usaremos novamente para este exercício. Vamos primeiro criar um novo banco de dados que este exercício pode usar: `databaseWeek3` e a coleção `bob_ross_episodes`. Você pode fazer isso manualmente no Atlas, veja como fazer isso sozinho.

Depois de criar o banco de dados, é hora de configurar nosso ambiente para que nosso código possa se conectar a esse banco de dados. No passado, você pode ter colocado essas informações de conexão (pense em chaves de API) em seus PRs, mas a partir de agora isso não deve acontecer mais. A maneira como geralmente fazemos isso é criando um arquivo `.env` e adicionando-o ao arquivo `.gitignore` para que ele não seja enviado para o git. Nós configuramos o arquivo `.gitignore` e fornecemos um arquivo `.env.example` que dá um exemplo de como o arquivo `.env` deve se parecer. Dê uma olhada nele para ver como você deve criar o arquivo `.env`.

> Você precisará descobrir uma maneira de colocar essas variáveis `.env` no ambiente do processo. Isso quase sempre é feito usando uma biblioteca, mas cabe a você descobrir qual é e configurá-la corretamente.

Agora que tudo está configurado, dê uma olhada em `index.js` para ver o que gostaríamos que você fizesse. Fornecemos um arquivo `seedDatabase` que limpa o banco de dados e a coleção para garantir que você esteja sempre trabalhando com os mesmos dados.

> O arquivo `index.js` também assume que algumas coisas estão configuradas, ao executá-lo você encontrará um erro que você precisará resolver.

Neste exercício, vamos trabalhar com os dados do episódio de Bob Ross, se você não ouviu falar de Bob Ross, ele era um pintor que fez um programa de TV lendário chamado [The Joy of Painting](https://en.wikipedia. org/wiki/The_Joy_of_Painting). Em cada episódio ele criou uma pintura de paisagem que foi fácil de acompanhar, dê uma olhada no [canal oficial do youtube](https://www.youtube.com/c/BobRossIncVideos) para assistir! Os dados no arquivo `data.json` são uma lista de todos os episódios, com seu título e os elementos que ele pintou naquele episódio. Note que nós massageamos esses dados um pouco no arquivo `seedDatabase` então dê uma olhada lá e no seu banco de dados sobre qual é a estrutura no final.

## **4. Código junto**

No código desta semana, você construirá um aplicativo CRUD completo. No entanto, em vez de usar o MySQL, será o MongoDB que você usará como banco de dados!

- [Aplicativo CRUD do zero usando Node.js](https://www.youtube.com/watch?v=CyTWPr_WwdI)

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! A lição de casa que precisa ser enviada é a seguinte:

1. Exercícios de banco de dados

Carregue seu código para o repositório de bancos de dados bifurcados no GitHub. Faça um pull request para o repositório bifurcado do HackYourHomework.

> Esqueceu como fazer o upload de sua lição de casa? Vá até o [guia](../hand-in-homework-guide.md) para aprender como fazer isso novamente.

_Prazo terça-feira 23.59 CET_
