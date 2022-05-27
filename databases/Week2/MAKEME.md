> Este dever de casa pressupõe que você instalou o software [MySQL](https://dev.mysql.com/downloads/installer/) em seu computador. Se não, por favor, faça isso primeiro!

# Bases de dados de trabalhos de casa Semana 2

## **Lista de afazeres**

1. Pratique os conceitos
2. Exercícios de preparação
3. Exercícios MySQL

## 1. **Pratique os conceitos**

Vamos fazer alguns exercícios interativos primeiro. No curso online a seguir, **faça as seções 3 (Funções Agregadas) e as seções 4 (Múltiplas Tabelas)**.

- [Codecademy: Aprenda SQL](https://www.codecademy.com/learn/learn-sql)

Também reserve um tempo para fazer a lição 6-12 do seguinte:

- [SQLBolt](https://sqlbolt.com/lesson/select_queries_with_joins)

## 2. **Exercícios de preparação**

> Exercícios de preparação são exercícios que você deve trabalhar _antes_ da sessão de domingo. Estes são um pouco mais difíceis ou mostram um conceito importante e, como tal, são um ótimo exercício para conversar com seu mentor. Tenha uma solução pronta até domingo, pois pode ser solicitado que você mostre o que fez.

Dentro do seu fork `databases`, vá para a pasta `Week2`. Dentro dessa pasta, navegue até o arquivo `QA_PREP_EXERCISE.md` que explica o que precisa ser feito. Haverá também algumas perguntas na parte inferior para pensar. Passe por eles _antes_ da sessão no domingo, pois será coberto então.

## 3. **Exercícios de MySQL**

> Você precisará fazer alguma pesquisa para resolver esses exercícios. Todos os conceitos necessários para resolver
> estes exercícios NÃO são abordados no material de leitura. Isso é de propósito.

Esta semana vamos praticar um pouco mais com a escrita de consultas SQL usando JavaScript. Para cada exercício crie um arquivo `.js` separado; certifique-se de dar-lhe um nome apropriado!

**Exercício 1: Chaves**

1. Crie uma tabela, chamada `autores`. Forneça os seguintes campos: `(author_no(Primary Key), author_name, university, date_of_birth, h_index, gender)`
2. Escreva uma consulta que adiciona uma coluna chamada `mentor` à tabela `authors` que faz referência à coluna `author_no`.
   Para integridade, adicione uma `chave estrangeira` nesta coluna.

**Exercício 2: Relacionamentos**

1. Crie outra tabela, chamada `research_Papers` com os seguintes campos: `(paper_id, paper_title, conference, publish_date, ...)`
2. Qual é a relação entre autores e artigos de pesquisa? Faça as alterações necessárias em `autores` e
   tabelas `research_Papers` e adicione mais tabelas se necessário.
3. Leia os exercícios 3 e 4 e, em seguida, adicione informações (inserir linhas) de 15 autores e 30 trabalhos de pesquisa, de modo que
   todas as consultas nos exercícios 3 e 4 retornarão algumas respostas

**Exercício 3: Juntas**

1. Escreva uma consulta que imprima os nomes de todos os `autores` e seus respectivos `mentores`.
2. Escreva uma consulta que imprima todas as colunas de `authors` e seus `paper_title` publicados.
   Se houver um autor sem nenhum `research_Papers`, imprima as informações desse `autor` também.

**Exercício 4: Funções agregadas**

Escreva algumas consultas para recuperar as seguintes linhas:

1. Todos os artigos de pesquisa e o número de autores que escreveram esse artigo.
2. Soma dos trabalhos de pesquisa publicados por todas as autoras.
3. Média do índice h de todos os autores por universidade.
4. Soma dos trabalhos de pesquisa dos autores por universidade.
5. Mínimo e máximo do índice h de todos os autores por universidade.

## ** ENVIE SUA LIÇÃO DE CASA!**

Depois de terminar sua lista de tarefas, é hora de nos mostrar o que você tem! A lição de casa que precisa ser enviada é a seguinte:

1. Exercícios MySQL

Faça upload de ambos para o repositório de bancos de dados bifurcados no GitHub. Faça um pull request para o repositório bifurcado do HackYourFuture.

> Esqueceu como fazer o upload de sua lição de casa? Vá até o [guia](../hand-in-homework-guide.md) para aprender como fazer isso novamente.

_Prazo terça-feira 23.59 CET_
