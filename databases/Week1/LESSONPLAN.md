# Bancos de dados do plano de aula Semana 1

O plano de aula é escrito principalmente para os professores, para que eles possam
use exemplos e anedotas deste documento em conjunto com o README
e explicar melhor os conceitos na aula.

## Tópicos (essencialmente iguais ao arquivo README)

1. O que é uma informação (sistema)?
2. O que são entidades?
3. O que é um banco de dados?
4. Qual é a função de um banco de dados em um aplicativo?
5. O que é a Linguagem de Consulta Estruturada (SQL)?
6. O que são tipos de dados (aplicados a bancos de dados)?
7. Como usar o SQL para criar, ler, atualizar e excluir (CRUD)?
8. O que é um dump de banco de dados?

> Antes de começar, pergunte e certifique-se de que todos tenham instalado com sucesso o [MySQL Community Edition Server](https://dev.mysql.com/downloads/mysql/)

## 1. O que é uma informação (sistema)?

### Explicação

Um sistema de informação (no contexto de computadores) consiste em três componentes.

1. Um local onde as informações são mantidas.
2. Uma ferramenta (programa) que pode interagir com este local
3. Uma interface de usuário

### Exemplo

Serviço de e-mail. Qualquer servidor de e-mail mantém a lista de usuários cadastrados, suas mensagens etc (componente 1).
Um cliente de e-mail é o programa que pode interagir com ele (componente 2).
Um navegador ou o computador fornece uma interface de usuário (componente 3).

### Exercício

_Cite três outros sistemas de informação e explique seus componentes._

### Essência

Os sistemas de informação processam e interpretam informações por meio de computadores e pessoas.

## 2. O que são entidades?

### Explicação

Entidade é um conceito abstrato em oposição a um conceito concreto. Descreve algo que não é tangível.
Possui atributos que fornecem mais informações sobre ele. Uma instância é a manifestação da entidade.

### Exemplo

1. O carro é uma Entidade. Os atributos do carro são 'Nome do fabricante', 'Nome do modelo', 'número', 'tração nas quatro rodas' etc.
   Jeep modelo Renegade com o número NL65JY é uma instância da _car entity_.
2. Se você considerar uma tabela em uma planilha do Excel, o nome da tabela é a entidade e as linhas são as instâncias.

### Exercício

_Dê mais três exemplos de entidades e suas instâncias._

### Essência

Entidades são nomes gerais dados aos tipos/classes de coisas.

## 3. O que é um banco de dados?

### Explicação

Um banco de dados é uma coleção de tabelas e usuários e permissões concedidas a esses usuários e regras para
o acesso das mesas. Sistema de gerenciamento de banco de dados (DBMS) é o termo frequentemente usado para descrever
o sistema que gerencia o acesso ao banco de dados. Esse gerenciamento envolve o armazenamento do banco de dados,
criando usuários, dando aos usuários permissões apropriadas, suportando linguagem de consulta etc.

### Exemplo

Exemplos de implementações de SGBD: MySQL, MongoDB, PostgreSQL, DynamoDB etc.
Usamos MySQL para a demonstração.

O comando a seguir mostra todo o banco de dados existente:

```
mostrar bancos de dados;
```

O comando a seguir cria um banco de dados:

```
CRIAR BANCO DE DADOS da empresa;
```

O comando a seguir seleciona (muda para) um banco de dados:

```
USE empresa;
```

O comando a seguir mostra o banco de dados atual:

```
selecione banco de dados();
```

### Exercício

_Explicar como o banco de dados é um exemplo de sistema cliente/servidor._

### Essência

Banco de dados é usado para armazenar dados de forma organizada.

## 4. Qual é a função de um banco de dados em um aplicativo?

### Explicação

Muitos aplicativos desejam armazenar os dados fora do programa e acessar
isso sempre que necessário. Este **fora** pode ser um computador realmente diferente
onde o banco de dados é armazenado. Nesse caso, precisamos da capacidade de falar com
este computador externo e acessar o banco de dados. Assim, precisamos do exterior
computador para atuar como servidor e nosso aplicativo atua como cliente.
Desta forma, o papel principal de um banco de dados é separar a manipulação de dados
da lógica do negócio.

### Exemplo

Em um sistema de reserva de passagens, o banco de dados contém as informações
sobre todos os passageiros, trens, horários, estações etc. Todas essas informações
pode ser armazenado em um banco de dados e o aplicativo externo pode consultar os dados relevantes
detalhes por solicitação.

```
Use o arquivo connection-test.js para demonstrar a conexão do banco de dados.
```

### Exercício

_Descubra 2 aplicativos em seu laptop/telefone que exigem um banco de dados e 2 aplicativos que não exigem um banco de dados._

### Essência

A função de um banco de dados é a separação dos dados da lógica de negócios do aplicativo.

## 5. O que é Structured Query Language (SQL)?

### Explicação

SQL é uma linguagem para interagir com o banco de dados. É composto por quatro categorias.

1. Linguagem de Definição de Dados (DDL)
2. Linguagem de consulta de dados (DQL)
3. Linguagem de Manipulação de Dados (DML)
4. Linguagem de Controle de Dados (DCL)

### Exemplo (no formato Idioma: Comandos)

1. DDL: `CREATE`, `ALTER`
2. DQL: `SELECT`
3. DML: 'INSERIR', 'ATUALIZAR'
4. DCL: `GRANT`, `REVOKE`

### Exercício

_Adivinhe a diferença entre os comandos ALTER e UPDATE_

### Essência

SQL suporta vários comandos para interagir com o banco de dados.

## 6. O que são tipos de dados (no contexto de bancos de dados)?

### Explicação

Quando os dados são armazenados em um banco de dados. Deve ser classificado adequadamente.
Os números devem ser armazenados de forma diferente de uma sequência de alfabetos.
Os valores booleanos precisam de muito menos espaço do que um BLOB (Binary Large OBject) de imagem.
Quando as tabelas são criadas no banco de dados, todas as suas colunas devem
têm tipo de dados fixo. Uma coluna de idade deve ter um número como tipo de dados.

### Exemplo (para MySQL 5.0.3 e superior)

| Tipo | Descrição | Valor de exemplo |
| ---------- | --------------------------------------------- | ----------------------- |
| int | Números | 42 |
| flutuar | Números decimais | 3.14 |
| varchar(N) | String com máximo variável de N caracteres | "Dragão" |
| texto | String com máximo fixo de 65535 caracteres | "Positivo" |
| datahora | Armazenar data e hora sem fuso horário | 01-01-2019 22:10:23 |
| carimbo de data/hora | Armazenar data com fuso horário (por exemplo, último login) | 01-01-2019 22:10:23 UTC |
| ENUM | Defina um conjunto de valores permitidos | (MASCULINO, MULHER) |
| BLOB | Armazenar arquivos binários | uma imagem |

### Exercício

_Quais tipos de dados devem ser usados para armazenar um valor booleano?_

### Essência

Os tipos de dados MySQL são usados para definir quais tipos de valores as colunas das tabelas no banco de dados contêm.

## 7. Como usar o SQL para criar, ler, atualizar e excluir (CRUD)

### Explicação

Usaremos o cliente de linha de comando MySQL e o cliente JavaScript para demonstrar o
interação com o servidor SQL.

`Use os arquivos create-table.js, insert-values.js` para mostrar como a criação da tabela, inserção etc.
pode ser feito via cliente JavaScript

### Exemplo

Todos os exemplos podem ser executados no `cliente de linha de comando MySQL`.
Lembre-se que todos esses comandos também podem ser enviados via clientes JavaScript.
Verifique os arquivos `.js` disponíveis na pasta `Week1`.

#### CRIO

O comando a seguir cria uma tabela chamada `employees` (no banco de dados `company`)
com cinco colunas:

1. `employee_id` que contém um número inteiro.
2. `employee_name` que contém nomes alfabéticos (de no máximo 50 caracteres).
3. `salário` que contém um número decimal.
4. `joining_date` que contém uma data e hora.
5. `gender` que pode ser `'m'` ou `'f'`.

```
CREATE TABLE funcionários (
    funcionário_id int,
    nome_funcionário varchar(50),
    flutuação salarial,
    join_date datahora,
    gênero enum('m', 'f')
);
```

#### INSERIR

O comando a seguir insere uma linha na tabela `employees`.
Observe que a sequência de colunas deve ser seguida.

```
INSERIR NOS VALORES dos funcionários (101, "Dan", 5000, "2019-06-24", 'm');
```

O comando a seguir usa a sintaxe do nome da coluna (também conhecido como nome do campo às vezes):

```
INSERT INTO funcionários (nome_do_funcionário, salário, id_do_funcionário, sexo, data_de entrada) VALUES("Dany", 5000, 102, 'f', "2019-05-20");
```

O comando a seguir usa a mesma sintaxe para adicionar várias linhas por vez

```
INSERT INTO funcionários (nome_do_funcionário, salário, id_do_funcionário, sexo, data_de entrada) VALUES("Ben", 7000, 103, 'm', "2019-07-20"), ("Benta", 3000, 104, 'f', "2019-10-12"), ("Raj", 9000, 105, 'm', "2019-01-01");
```

O comando a seguir usa a sintaxe SET para inserir valores em uma ordem aleatória de colunas:

```
INSERT INTO funcionários SET funcionário_nome = "Joe", salário = 4000, data_de ingresso = "2019-07-01", gênero = 'f', funcionário_id = 100;
```

> Se você não se lembrar dos nomes das colunas, use descrever funcionários; comando que lista os nomes das colunas e seus tipos de dados.

#### SELECIONE

O comando a seguir exibe a tabela inteira. O `*` significa todas as colunas.

```
SELECIONAR * DE funcionários;
```

O comando a seguir exibe os nomes dos funcionários cujo salário é maior que 3.000.
Ele usa a cláusula `WHERE` que filtra as linhas com base na condição.
A condição é aplicada na coluna `salário` de cada linha.
`SELECT employee_name` imprimirá apenas a coluna `employee_name` das linhas
onde a coluna `salário` tem o valor `>3000`.

```
SELECIONE o nome_do_funcionário dos funcionários
ONDE salário > 3000;
```

#### ATUALIZAR

O comando a seguir atualiza o salário do funcionário cujo `employee_id` é 102.
Observe que `=` funciona como um operador de atribuição em `SET salário = 8000`
mas funciona como um operador de comparação na cláusula WHERE `employee_id = 102`.

```
ATUALIZAR funcionários
Salário SET = 8000
ONDE funcionário_id = 102;
```

#### APAGAR

O comando a seguir exclui todos (linhas de) funcionários que ingressaram após 1º de julho de 2019.

```
EXCLUIR de funcionários
ONDE join_date > "2019-07-01";
```

### Exercício

1. Escreva uma consulta SQL para localizar todos os funcionários do sexo masculino.
2. Escreva uma consulta SQL para inserir mais 4 registros na tabela de funcionários.
3. Escreva uma consulta SQL para atualizar o salário de todas as funcionárias para 12.000.
4. Escreva uma consulta SQL para excluir todos os funcionários cujo nome comece com 'B'.
5. Escreva uma consulta SQL para criar uma tabela chamada `departments` com as seguintes colunas: `dept_id`, `dept_name`, `manager`.

### Essência

Os comandos SQL fornecem uma maneira organizada e estruturada de interagir com as tabelas do banco de dados.

## 7.5 Conceitos diversos

### Aliases em consultas SELECT

#### Explicação

Os aliases dão apelidos aos nomes das colunas ao exibi-los. Eles são especialmente úteis no caso de consultas aninhadas
quando as tabelas têm nomes longos e junções são usadas.

#### Exemplo (sem consulta aninhada)

`SELECT Employee_id como "Número do Funcionário", employee_name como "Nome do Funcionário", salário como Ganhos dos funcionários;`

### Valores NOT NULL e DEFAULT para colunas

#### Explicação

Ao criar uma tabela, algumas colunas podem ser declaradas como `NOT NULL` ou `DEFAULT` com um valor,
ou ambos. Por exemplo, `gender` do funcionário NÃO pode ser nulo. Também algumas colunas como
`Número de feriados` pode ter valores padrão. É uma boa prática marcar explicitamente
as colunas como `NOT NULL` para que o MySQL possa fazer otimizações no armazenamento/indexação.

#### Exemplo

Demonstre a diferença com a execução ao vivo da seguinte sequência de comandos:

```
CREATE TABLE default_not_null_demo(num1 int, num2 int NOT NULL, num3 int default 5555, num4 int não null default 1111);
DESCREVER default_not_null_demo;
INSERT INTO default_not_null_demo set num2 = 1, num4 = default;
SELECT * de default_not_null_demo;
INSERT INTO default_not_null_demo set num2 = 1, num3 = 233, num4 = default;
```

### O que é int(N) ?

#### Explicação

O número N representa o número de espaços decimais que podem ser preenchidos ao exibir o número.
Não indica o número mais alto que pode ser armazenado na coluna. Por exemplo. A coluna `cost int(3)`
pode conter números maiores que 999.

#### Exemplo

Ilustre a diferença com a execução ao vivo da seguinte sequência de comandos:

```
CREATE TABLE test_int(num1 int(4) ZEROFILL, num2 int(6));
INSERT INTO valores test_int (23,34);
valores INSERT INTO test_int (3.534);
valores INSERT INTO test_int (14563.534);
valores INSERT INTO test_int (12345,98534);
valores INSERT INTO test_int (12345,1234567);
SELECT * FROM test_int;
```

### Data e hora x carimbo de data/hora

#### Explicação

Tanto Datetime quanto Timestamp aceitam valores no formato `YYYY-MM-DD HH:MM:SS`.
No entanto, o MySQL armazenou o valor do carimbo de data/hora junto com as informações de fuso horário do sistema atual.
Se o fuso horário for alterado, o valor armazenado no banco de dados será alterado de acordo.
Datetime pode ser um tipo de dados adequado para a `data de entrada`, enquanto timestamp
pode ser um tipo de dados adequado para `último login` onde a hora exata e o fuso horário podem ser cruciais.

#### Exemplo

Demonstre com a execução ao vivo da seguinte sequência de comandos:

```
CREATE TABLE test_timestamp (dt datetime, ts timestamp);

INSERT INTO test_timestamp VALUES ("2020-01-01 00:00:00", "2020-01-01 00:00:00");

SELECT * FROM test_timestamp;

SET time_zone = '+05:30';

SELECT * FROM test_timestamp;

```

## 8. O que é um dump de banco de dados?

### Explicação

Um dump de banco de dados é um arquivo. Este arquivo contém comandos SQL (principalmente CREATE e INSERT)
que refletem o estado atual do banco de dados.

### Exemplo

Para criar o dump SQL, execute o seguinte comando no terminal do MAC/Linux.

```
mysqldump -uhyfuser -p empresa > /path/to/store/dump/file/company-db-snapshot.sql
```

Para criar o dump SQL no Windows, você terá que
[inclua o caminho da sua instalação do MySQL na variável de ambiente `Path`](https://www.computerhope.com/issues/ch000549.htm).
Então você pode executar o seguinte comando

```
mysqldump.exe -uhyfuser -p empresa > /path/to/store/dump/file/company-db-snapshot.sql
```

Observe que o caminho deve ser um local onde o usuário tenha permissão de 'gravação' (por exemplo, área de trabalho),
caso contrário, você receberá erros de permissão.

Para aplicar o dump do prompt de comando mysql (`mysql>`), use o seguinte comando

```
fonte /caminho/para/o/despejo/arquivo
```

Para aplicar o dump do terminal (geralmente com um prompt de dólar `$`), use o seguinte comando

```
mysql -uhyfuser -p [banco de dados] < /path/to/the/dump/file
```

Use [este](https://john-dugan.com/dump-and-restore-mysql-databases-in-windows/) link para saber mais sobre
como fazer isso no Windows (usando `cmd`).

### Exercício

Faça o dump do banco de dados `company` e use o arquivo dump para recriar o banco de dados.

### Essência

Os arquivos de despejo funcionam como um instantâneo do banco de dados que permite voltar aos estados anteriores do banco de dados.
