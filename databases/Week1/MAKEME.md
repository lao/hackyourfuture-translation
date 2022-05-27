> Este dever de casa pressupõe que você instalou o software [MySQL](https://dev.mysql.com/downloads/installer/) em seu computador. Se não, por favor, faça isso primeiro!

# Bases de dados de trabalhos de casa Semana 1

## **Lista de afazeres**

1. Pratique os conceitos
2. Exercícios MySQL
3. Exercícios de preparação
4. Codifique junto

## 1. **Pratique os conceitos**

Vamos começar esta semana com alguns exercícios interativos. Confira a seguir para começar a escrever suas primeiras consultas! No curso online a seguir, **faça as seções 1 (Manipulação) e as seções 2 (Consultas)**.

- [Codecademy: Aprenda SQL](https://www.codecademy.com/learn/learn-sql)

Também reserve um tempo para fazer a lição 1-5 do seguinte:

- [SQLBolt](https://sqlbolt.com/lesson/select_queries_introduction)

## 2. **Exercícios de MySQL**

> Você precisará fazer alguma pesquisa para resolver esses exercícios. Todos os conceitos necessários para resolver
> estes exercícios NÃO são abordados no material de leitura. Isso é de propósito.

**Exercício 1: criar e inserir consultas**

Escreva um arquivo JavaScript (para ser executado com Node.js) que cria e faz uma conexão com um banco de dados MySQL. Faça isso usando o pacote `mysql` (https://www.npmjs.com/package/mysql).

Lembre-se, é sempre melhor testar suas consultas assim que as tiver criado. Sinta-se à vontade para primeiro escrevê-los em qualquer ferramenta de visualização sql ou console mysql antes de escrever o programa node.

1. Crie um banco de dados chamado `meetup`
2. Faça uma conexão com seu banco de dados, usando suas credenciais de login do MySQL `hyfuser`
3. Crie uma tabela chamada `Invitee` com os seguintes campos (`invitee_no`, `invitee_name` e `invited_by`).
4. Crie uma tabela chamada `Room` com os seguintes campos (`room_no`, `room_name` e `floor_number`)
5. Crie uma tabela chamada `Meeting` com os seguintes campos (`meeting_no, meeting_title, begin_time, ending_time`,`room_no`)
6. Insira 5 linhas em cada tabela com campos relevantes. Encontre uma maneira de criar os dados para esses campos
7. Teste seu código executando `node <FILE_NAME>` no terminal. Em seguida, verifique seu banco de dados MySQL e veja se tudo foi criado conforme o esperado. Por favor, certifique-se de que seu arquivo pode ser executado mais de uma vez. Você pode descartar e criar o banco de dados toda vez que o arquivo for executado.

**Exercício 2: Selecione as consultas no banco de dados "world"**

> Para esta parte do dever de casa, use o arquivo `world.sql` na pasta `week1/databases` para criar o banco de dados e as tabelas. Antes de continuar, execute o arquivo para criar uma instância de banco de dados do banco de dados `world`, usando o console mysql ou qualquer ferramenta. Teste para ver se ele foi criado. Certifique-se de que todas as tabelas (`city`, `country` e `countrylanguage`) e os dados contidos estejam lá.

Escreva um arquivo JavaScript (para ser executado com Node.js) que consulte (usando instruções select) o banco de dados `world`. Os resultados devolvidos devem responder às seguintes perguntas:
Não deixe de testar suas consultas todas as vezes.

1. Quais são os nomes dos países com população superior a 8 milhões?
2. Quais são os nomes dos países que têm “terra” em seus nomes?
3. Quais são os nomes das cidades com população entre 500.000 e 1 milhão?
4. Qual é o nome de todos os países do continente 'Europa'?
5. Liste todos os países em ordem decrescente de suas áreas de superfície.
6. Quais são os nomes de todas as cidades da Holanda?
7. Qual é a população de Roterdã?
8. Quais são os 10 principais países por Área de Superfície?
9. Quais são as 10 cidades mais populosas?
10. Qual é o número da população do mundo?

Depois de escrever suas consultas **testadas**, teste para ver se tudo funciona executando `node <FILE_NAME>`.

## 3. **Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `databases`, vá para a pasta `Week1`. Dentro dessa pasta, navegue até o arquivo `QA_PREP_EXERCISE.md` que explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## 4. **Codifique junto**

No código desta semana, você não criará um aplicativo completo, mas se familiarizará com o uso do MySQL junto com o Node.js.

- [Usando MySQL com Node.js](https://www.youtube.com/watch?v=EN6Dx22cPRI)

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! A lição de casa que precisa ser enviada é a seguinte:

1. Exercícios MySQL

Carregue seu código para o repositório de bancos de dados bifurcados no GitHub. Faça um pull request para o repositório `HackYourHomework/databases`.

> Esqueceu como fazer o upload de sua lição de casa? Vá até o [guia](../hand-in-homework-guide.md) para aprender como fazer isso novamente.

_Prazo terça-feira 23.59 CET_
