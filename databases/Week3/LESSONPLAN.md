# Bancos de dados do plano de aula Semana 3

O plano de aula é escrito principalmente para os professores, para que eles possam
use exemplos e anedotas deste documento em conjunto com o README
e explicar melhor os conceitos na aula.

## Tópicos (essencialmente iguais ao arquivo README)

0. Super Chave vs Chave Candidata vs Chave Primária
1. Normalização
2. Transações
3. Injeção de SQL
4. NoSQL (com MongoDB)

## 0. Super Chave vs Chave Candidata vs Chave Primária

#### Explicação

1. A superchave é um conjunto de colunas que identifica exclusivamente uma linha.
2. A chave candidata é uma superchave mínima que pode identificar exclusivamente uma linha.
3. A chave primária é uma escolha de chave candidata escolhida pelo designer do banco de dados.

#### Exemplo

Para a seguinte tabela
`Funcionário (employee_id, employee_name, gênero, salário, departamento, idade, cidade)`

- Duas super chaves desta tabela são

1. SK1 = `{nome_funcionário, departamento, idade, cidade}`
2. SK2 = `{employee_id, Employee_name, salário}`

- As chaves candidatas derivadas dessas superchaves podem ser

1. CK1 de SK1 = `{employee_name, cidade}`
   se dois funcionários com o mesmo nome sempre vêm de cidade diferente.
   Então, não precisamos das colunas `age` e `department` nesta chave candidata.
2. CK2 de SK2 = `{employee_id}` se um identificador diferente for gerado para cada
   empregado. Então não precisamos das colunas `employee_name` e `salary` nesta chave candidata.

- A chave primária escolhida dessas chaves candidatas pode ser `employee_id`.

#### Exercício

Considere a seguinte tabela:
`Livro (ISBN int, nome_do_livro, nome_do_autor, ano_de publicação, editora, idioma_do livro)`.
Descubra 2 conjuntos de superchaves, chaves candidatas e escolha uma chave primária apropriada.

#### Essência

A chave primária identifica exclusivamente as linhas.
As superchaves e as chaves candidatas são usadas no design do banco de dados.

## 1. Normalização e formas normais

### Explicação

O objetivo da normalização é reduzir a duplicação de dados.
Diferentes níveis de normalização são chamados de _formas normais_.
Diz-se que uma tabela está na 'forma normal X' se satisfizer todas as regras
definido por essa forma normal e todas as formas normais antes de X.

#### 1NF (5 regras)

1. Colunas de valor único (cada coluna deve ter valor atômico, sem valores múltiplos)
2. O domínio da coluna (para qualquer coluna) não deve ser alterado.
3. Nomes exclusivos para colunas.
4. A ordem (das linhas/colunas) não importa.
5. Nenhum registro duplicado (todo registro possui uma chave primária).

#### 2NF (1NF + regra)

- nenhuma coluna não principal que não faça parte da chave primária
  deve ser funcionalmente dependente de qualquer subconjunto adequado de uma chave candidata.
  Em outras palavras, deve haver
  Nenhuma dependência parcial (nenhuma coluna deve depender da parte da chave primária).

```
Dependência funcional: denotada com A => B.
A e B são colunas de uma tabela. Uma explicação simplificada da dependência de função é
do seguinte modo.
Se eu conheço um valor na coluna A, com certeza conheço o valor na coluna B
mas o inverso não é verdade.
Por exemplo. A é o número do aluno e B é o nome do aluno.
Eu posso dizer o nome do aluno pelo número do aluno, mas
Não consigo distinguir o número do aluno do nome porque pode haver vários alunos com o mesmo nome.
```

Se você se sente aventureiro, leia esta [Functional Dependency Wikipage](https://en.wikipedia.org/wiki/Functional_dependency)

#### 3NF (2NF + regra)

- Nenhuma dependência transitiva (ou seja, nenhuma coluna deve depender de uma coluna não chave).

#### 3.5NF AKA BCNF (3NF + regra)

- Para qualquer dependência A => B, A deve ser uma superchave.
  Em outras palavras, para uma dependência A => B, A não pode ser uma coluna não principal, se B for uma coluna principal.

#### 4NF (3NF + regra)

- Nenhuma dependência de vários valores.

### Exemplo

#### 1NF

Considere a seguinte tabela

```
+-------------+------------+---------------------- -+
| ID do funcionário | Nome | Contato |
+-------------+------------+---------------------- -+
| 101 | Amit | 0684927317 |
| 102 | Ben | 0634899234, ben@bu.nl |
| 103 | Cathy | 0647882102, cat@dog.us|
| 104 | Dua | 0622467559 |
+-------------+------------+---------------------- -+
```

Esta tabela não está na 1NF porque a regra (1) da 1NF é violada porque
a linha 2 e a linha 3 contêm vários valores para a coluna `Contato`.
Também a regra (2) de 1NF é violada porque a coluna `Contato` contém
valores numéricos (para números de telefone) e valor de string (para e-mails).

Esta tabela pode ser convertida para 1NF da seguinte forma:

```
+-------------+------------+---------------------- --+
| ID do funcionário | Nome | Telefone | E-mail |
+-------------+------------+---------------------- --+
| 101 | Amit | 0684927317 | NULO |
| 102 | Ben | 0634899234 | ben@bu.nl |
| 103 | Cathy | 0647882102 | cat@dog.us|
| 104 | Dua | 0622467559 | NULO |
+-------------+------------+---------------------- - +
```

Na vida real, você realmente precisa

- Contato da coluna DROP.
- ADD coluna Telefone com o tipo int.
- ADD coluna Email com o tipo varchar(50).

#### 2NF

Considere a tabela a seguir (tabela de relacionamento M-M empregado-projeto).

```
+-------------+------------+---------------------- -+
| ID do funcionário | ID do projeto | Orçamento do Projeto |
+-------------+------------+---------------------- -+
| 101 | 1001 | 317 |
| 102 | 1001 | 234 |
| 103 | 2001 | 102 |
| 104 | 2001 | 559 |
+-------------+------------+---------------------- -+
```

2NF é violado aqui porque

```
porj_budget (coluna não principal)
proj_no => proj_budget (funcionalmente dependente de proj_no)
proj_no (Faz parte da chave candidata)
emp_no + proj_no (é uma chave candidata)
```

Esta tabela pode ser convertida para 2NF removendo a coluna 'Orçamento do Projeto' e
adicionando-o à tabela do projeto.

#### 3NF

Considere a tabela a seguir (funcionários)

```
+-------------+------------+---------------------- -+
| ID do funcionário | ID de departamento | Localização do Departamento |
+-------------+------------+---------------------- -+
| 101 | 2221 | Amsterdã |
| 102 | 2221 | Amsterdã |
| 103 | 3335 | Roma |
| 104 | 3335 | Roma |
+-------------+------------+---------------------- -+
```

Esta tabela viola a 3NF porque há uma dependência transitiva.
`Employee Id => Dept Id` e `Dept Id => Dept Location.`
A coluna "Dept Location" depende do "Dept Id" que não é uma coluna de chave primária.

#### 3.5 NF (AKA BCNF)

Considere a tabela a seguir (alunos optando por disciplinas)

```
+-------------+------------+---------------------- -+
| ID do aluno | Assunto | Professor |
+-------------+------------+---------------------- -+
| 101 | Java | X |
| 102 | Java | X |
| 101 | C++ | S |
| 103 | C++ | S |
| 103 | Java | X |
| 104 | C++ | S |
+-------------+------------+---------------------- -+
```

Esta tabela viola a 3.5NF porque existe uma dependência funcional
`Professor => Assunto` e `Professor` não é uma super chave.
`ID do Aluno + Assunto` é a chave primária. Portanto, `Assunto` é uma coluna principal.

Esta tabela pode ser convertida para 3.5NF da seguinte forma:

```
+-------------+------------+
| ID do aluno | ID do Prof |
+-------------+------------+
| 101 | P0001 |
| 102 | P0001 |
| 101 | P0002 |
| 103 | P0002 |
| 103 | P0001 |
| 104 | P0002 |
+-------------+------------+
```

e

```
+-------------+------------+----------+
| ID do Prof | Professor | Assunto |
+-------------+------------+----------+
| P0001 | X | C++ |
| P0002 | S | Java |
+-------------+------------+----------+
```

#### 4NF

Considere a tabela a seguir (alunos optando por disciplinas)

```
+-------------+------------+-----------+
| Aluno | Assunto | Passatempo |
+-------------+------------+-----------+
| Beno | Excel | Violino |
| Beno | Python | Marcenaria |
| Beno | Holandês | Pintar |
| Lucas | Java | Correndo |
| Lucas | C++ | Leitura |
+-------------+------------+-----------+
```

Esta tabela viola a 4NF porque `Subject` e `Hobby` são independentes um do outro.
Daí o hobby do aluno deve ser repetido na tabela com cada assunto
o aluno escolhe.

```
+-------------+------------+---------------------- -+
| Aluno | Assunto | Passatempo |
+-------------+------------+---------------------- -+
| Beno | Excel | Violino |
| Beno | Excel | Marcenaria |
| Beno | Excel | Pintar |
| Beno | Python | Violino |
| Beno | Python | Marcenaria |
| Beno | Python | Pintar |
| Beno | Holandês | Violino |
| Beno | Holandês | Marcenaria |
| Beno | Holandês | Pintar |
+-------------+------------+---------------------- -+
```

Isso leva a muita repetição.
Esta tabela pode ser convertida para 4NF dividindo-a em duas.

```
+-------------+------------+
| Aluno | Assunto |
+-------------+------------+
| Beno | Excel |
| Beno | Python |
| Beno | Holandês |
| Lucas | Java |
| Lucas | C++ |
+-------------+------------+
```

e

```
+-------------+-----------+
| Aluno | Passatempo |
+-------------+-----------+
| Beno | Violino |
| Beno | Marcenaria |
| Beno | Pintar |
| Lucas | Correndo |
| Lucas | Leitura |
+-------------+-----------+
```

### Exercício

Normalize a tabela a seguir.

```
+-------------+------------+---------------------- -------------------------+------------+
| Nome completo | Endereço | Filmes alugados | Saudação |
+-------------+------------+---------------------- -------------------------+------------+
| Janet Jones | 5 João St | Pirata do Caribe, Fúria de Titãs | Sra. |
| Rob Smith | 12 Ann St | Redenção Shawshank, mente bonita | Sr. |
| Rob Smith | 9 Joy St | Confronto de Titãs | Sr. |
+-------------+------------+---------------------- -------------------------+------------+
```

### Essência

Os formulários normais ajudam em um melhor design de banco de dados principalmente reduzindo a redundância.

## 2. Transações

### Explicação

Explicamos a necessidade da transação com a seguinte ilustração anedótica:

Suponha que o saldo no banco de Ali seja de 500€ e
o saldo na conta bancária da Birgul é de 700€.
Imagine que Ali está transferindo 50€ para Birgul. Então, no final
desta transação em dinheiro, Ali deveria ter 450€ e Birgul deveria ter 750€.
Observe que isso envolveu duas consultas de banco de dados.

1. Atualize a linha da conta de Ali e _subtraia_ o saldo em 50.
2. Atualize a linha da conta de Birgul e _adicione_ o saldo em 50.

Essas duas consultas de banco de dados juntas formam uma transação. Se executarmos apenas
um deles, então há inconsistência.

As transações têm a seguinte sintaxe:

```
iniciar transação;
Comando SQL 1
Comando SQL 2...
Comando SQL N

reversão OU confirmação;

# "rollback" aborta a transação (também encerra a transação)
# "commit" confirma a transação (também encerra a transação)
```

> Observe que não há comando "finalizar transação". Para encerrar a transação,
> temos que confirmar a transação ou reverter a transação.

#### Propriedades do ácido

As transações em bancos de dados relacionais (como MySQL) seguem o
seguintes propriedades.

1. Atomicity : Execute todos os comandos na transação ou execute zero comandos na transação (todos ou nenhum).
2. Consistência: Uma transação traz o banco de dados de um estado válido para o próximo estado válido.
3. Isolamento: A execução simultânea de transações (possivelmente por usuários diferentes) deve deixar o banco de dados em um estado consistente.
4. Durabilidade: Quando uma transação é confirmada, ela permanecerá confirmada mesmo em caso de falha do sistema. Em outras palavras,
   as transações confirmadas são gravadas no disco.

### Exemplo

A atomicidade pode ser demonstrada com os seguintes exemplos de `rollback` e `commit`:

#### Exemplo de reversão

```
definir autocommit = 0; # padrão é 1 que automaticamente confirma cada comando como transação.

iniciar transação;

selecione * de funcionários; # Mostra todas as linhas da tabela

atualize os funcionários defina o salário = 10000 em que funcionário_id = 101; # Atualizar o salário de um funcionário

selecione * de funcionários; # Mostra o novo salário

reversão; # Não mostra nenhuma saída, mas na verdade reverte a transação

selecione * de funcionários; # Mostra o salário antigo
```

> Pode haver centenas de comandos após `start transaction`. comando rollback irá desfazer todos eles.

#### Exemplo de commit

```
definir autocommit = 0; # padrão é 1 que automaticamente confirma cada comando como transação.

iniciar transação;

selecione * de funcionários; # Mostra todas as linhas da tabela

atualize os funcionários defina o salário = 10000 em que funcionário_id = 101; # Atualizar o salário de um funcionário

selecione * de funcionários; # Mostra o novo salário

comprometer-se; # Não mostra nenhuma saída, mas realmente confirma a transação

selecione * de funcionários; # Mostra o novo salário
```

> Após o commit, as alterações são gravadas permanentemente no disco.

#### Exemplos de isolamento e consistência

Inicie dois clientes de linha de comando `mysql`.

```
# Primeiro cliente

atualizar funcionários definir cidade = 'Mumbai' onde funcionário_id = 101;

comprometer-se;
```

No segundo cliente, mostre que o valor está atualizado.

```
# Segundo cliente
selecione * de funcionários;

```

> A alteração feita por um cliente de banco de dados no servidor de banco de dados será vista pelo(s) outro(s) cliente(s). Por isso,
> ambos os clientes têm a visão consistente no banco de dados.

```
# Primeiro cliente

definir autocommit = 1;

BLOQUEAR TABELAS funcionários ESCREVER;

atualize os funcionários defina o salário = 7000 em que funcionário_id = 101;

```

```
# Segundo cliente

selecione * de funcionários; # Vai travar porque o primeiro cliente tem o bloqueio WRITE nessa tabela
```

Assim que o primeiro cliente executa o comando `UNLOCK TABLES;`,
o segundo cliente obterá a saída do comando `select`.

> As transações também podem ser criadas a partir do cliente JavaScript. O programa de demonstração é [async-transaction](async-transaction.js).

### Exercício

Discuta a transação no contexto de uma corrida Uber. Quantas operações/ações estão envolvidas na transação bem-sucedida?
Quando a transação pode ser abortada? Quais seriam as tabelas do banco de dados?

### Essência

Uma transação é um conjunto de comandos SQL que é tratado como UM comando.

## 3. Injeção de SQL

### Explicação

A injeção de SQL é um tipo de ataque de hacker em que o invasor tenta fazer com que o programa execute uma consulta para leitura/gravação
os dados aos quais não devem ter acesso.

### Exemplo

Use o pacote `prompt` em `input-demo.js` para simular a entrada de formulários HTML.

`sql-injection.js` contém três maneiras de passar a entrada para a consulta de seleção

```
// 1. Maneira ingênua de passar o parâmetro para a consulta
const select_query = `select * from employees WHERE employee_id = ${input_number};`
```

Desta forma fica vulnerável aos seguintes ataques.

```
$ node sql-injection.js # Executa o programa Javascript a partir do terminal (código VS).

prompt: número_funcionário: 1234 OU 1=1
# selecione * de funcionários onde employee_id = 1234 OR 1=1;


prompt: número_funcionário: 1234 OU 1=1; mostrar tabelas;
# selecione * de funcionários onde employee_id = 1234 OR 1=1; mostrar tabelas;


prompt: número_funcionário: 1234 OU 1=1; demonstração de mesa suspensa;
# selecione * de funcionários onde employee_id = 1234 OR 1=1; demonstração de mesa suspensa;
```

Para resolver esse problema, existem duas maneiras de sanitizar a entrada:

```
// 1. Escapando o parâmetro (substituindo os caracteres indesejados)
const select_query = `select * from employees WHERE employee_id =` + connection.escape(input_number);

// 2. Usando uma sintaxe de ponto de interrogação para fazer o escape
const select_query = `select * from employees WHERE employee_id = ?`
```

### Exercício

https://www.hacksplaining.com/exercises/sql-injection#/start

### Essência

As injeções de SQL são perigosas. Sempre limpe a entrada de seus formulários HTML.

## 4. Sem SQL

### Explicação

### Exemplo

> use as mesmas tabelas aqui (como plano de aula da Semana 1) para ser consistente e mostrar aos alunos como fazer bancos de dados semelhantes usando MySQL e MongoDB

### Exercício

### Essência
