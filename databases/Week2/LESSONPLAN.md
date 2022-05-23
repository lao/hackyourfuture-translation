# Bancos de dados do plano de aula Semana 2

O plano de aula é escrito principalmente para os professores, para que eles possam
use exemplos e anedotas deste documento em conjunto com o README
e explicar melhor os conceitos na aula.

## Tópicos

0. Natureza assíncrona da interação MySQL-Nodejs
1. Identificadores (chave primária, chave estrangeira, chave composta)
2. Relacionamentos (um para um, um para muitos, muitos para muitos)
3. Junções (interna, esquerda e direita) e aliases
4. Mais cláusulas SQL (agrupar por, ter, funções distintas e agregadas)
5. Índices
6. Modelagem de domínio (ERD)

### 0. Natureza assíncrona da interação MySQL-Nodejs

#### Explicação

A natureza das consultas de banco de dados é assíncrona.
Algumas consultas podem levar muito tempo para serem executadas.
Quando nosso cliente MySQL JavaScript está enviando as consultas para o servidor MySQL,
ele pode não querer bloquear até que a resposta seja retornada.
No entanto, se o cliente MySQL MySQL estiver enviando várias consultas, como
a segunda consulta (por exemplo, inserir) depende da primeira consulta (por exemplo, criar),
então deve esperar até que a execução da primeira consulta seja bem sucedida.
Para garantir uma interação suave com o servidor MySQL, promessas podem ser usadas em conjunto
com o método await().

#### Exemplos)

Demonstre com quatro programas em [este repositório](https://github.com/unmeshvrije/database_examples)
Como as

1. O programa `1-db-naive.js` falha porque a conexão foi encerrada prematuramente.
2. O programa `2-db-callback.js` resolve o problema, mas parece feio por causa do callback-hell.
3. O programa `3-db-promise.js` usa o encadeamento de promessas para torná-lo melhor.
   sobre construir essas promessas
4. O programa `4-db-await.js` usa promisify() e await() para torná-lo o melhor.

#### Exercício

O programa chamado `async-create-insert.js` pode ser encontrado na pasta `Week2`.
Adicione uma consulta de seleção a esse programa usando await e promisify.

#### Essência

> palavra-chave async : para criar uma função assíncrona e garantir que eles retornem a promessa sem ter que se preocupar

> await : para chamar uma função retornando promessa sem ter que chamar .then() sobre essa promessa

> promisify() : para converter uma função baseada em callback em uma função baseada em promessa.

### 1. Identificadores (chave primária, chave estrangeira, chave composta)

#### Explicação

1. Uma coluna pode ser declarada como a coluna UNIQUE. Essa coluna tem valores ÚNICOS.
   Também pode ter valores NULL. Assim, duas linhas podem ter o mesmo valor NULL na coluna que
   é declarado como UNIQUE (em outras palavras, esta é uma UNIQUE CONSTRAINT naquela coluna).
2. Uma coluna pode ser declarada como a coluna PRIMARY KEY. Essa coluna também tem valores UNIQUE.
   Eles não podem ser valores NULL. Assim, duas linhas NUNCA podem ter os mesmos valores na coluna
   que é declarado como PRIMARY KEY (em outras palavras, esta é uma PRIMARY KEY CONSTRAINT nessa coluna).

> Existem mais restrições no MySQL. Leia mais sobre eles [aqui](https://www.w3resource.com//creating-table-advance/constraint.php).

#### Exemplo

Considere os seguintes comandos (# representa comentários).

```sql
# cria tabela com duas colunas. um com chave primária e outro com restrição de chave exclusiva
CREATE TABLE pri_uniq_demo(id_pr int PRIMARY KEY, id_un int UNIQUE);

# Observe o erro que diz que a coluna de chave primária não pode ser NULL
INSERT INTO pri_uniq_demo VALUES (NULL, NULL);
#ERROR 1048 (23000): a coluna 'id_pr' não pode ser nula

# Observe que a coluna de chave UNIQUE pode ser NULL
INSERT INTO pri_uniq_demo VALUES (1, NULL);
#Query OK, 1 linha afetada (0,00 s)

# Inserção normal
INSERT INTO pri_uniq_demo VALUES (2, 2);
#Query OK, 1 linha afetada (0,05 seg)

# Observe que você não pode inserir 2 na coluna id_un porque deve ser ÚNICO
INSERT INTO pri_uniq_demo VALUES (3, 2);
#ERROR 1062 (23000): Entrada duplicada '2' para a chave 'id_un'

# Observe que você não pode inserir 2 na coluna id_pr porque é PRIMARY KEY
INSERT INTO pri_uniq_demo VALUES (2, 3);
#ERROR 1062 (23000): Entrada duplicada '2' para chave 'PRIMARY'

```

#### Exercício

```
# Descubra o tipo T e a restrição C para cada coluna.
CREATE TABLE Airline_passengers(ticket_numer T C, passage_name T C, date_of_birth T C, passaporte_number T C);

Dica: Um bebê muito pequeno pode não precisar de um ingresso!
```

#### Essência

Chave primária é um caso especial de chave UNIQUE. A chave UNIQUE pode ser NULL e
chave primária não pode ser NULL. Uma tabela pode ter várias chaves ÚNICAS, mas APENAS UMA chave primária.

### 2.1 Relacionamentos (um para um, um para muitos, muitos para muitos)

#### Explicação

Quando uma entidade está relacionada a outra, tal relacionamento tem a chamada **cardinalidade**.
A cardinalidade determina quantas instâncias de uma entidade podem participar do relacionamento
com quantas outras instâncias da outra entidade.

Por exemplo, um funcionário pode ter apenas uma conta na empresa.
Além disso, uma conta está vinculada a exatamente um funcionário.
Esse relacionamento funcionário e conta tem cardinalidade "1-1" (leia como um para um).
Isso significa que uma instância de Employees (digamos John Smith) tem exatamente uma conta
(instância com ID de conta 3409011) em alguma empresa X.

Um funcionário pertence a exatamente um departamento, no entanto, um departamento pode ter muitos funcionários.
Essa relação entre funcionário e departamento tem cardinalidade `M-1` (leia muitos-para-um).
Inversamente, o relacionamento entre departamento e funcionário tem cardinalidade `1-M` (leia-se um para muitos).
Observe que as cardinalidades `1-M` e `M-1` são apenas inversas uma da outra.
As duas frases a seguir transmitem a mesma informação em palavras diferentes.

1. O departamento de vendas (uma instância da entidade Departamento) da empresa X tem três funcionários.
2. John Smith, Raj Joshi e Su Li são funcionários da empresa X que pertencem ao Departamento de Vendas.

Para representar o relacionamento `1-1` ou `1-M` em tabelas MySQL, precisamos de uma coluna em uma tabela
que `refere` uma coluna em outra tabela. Essa coluna deve ser uma coluna de chave primária de outra tabela
e é chamado de `chave estrangeira`.
Na tabela Account, `employee_id` é a coluna que atua como a chave estrangeira que **refere-se ao
Coluna employee_id da tabela de funcionários na qual funciona como chave primária.**
Na tabela Employees, `dept_id` é a coluna que atua como a chave estrangeira que **refere-se ao
coluna dept_id da tabela de departamentos na qual funciona como chave primária.**

#### Exemplo

```sql
# Adicione a coluna dept_id à tabela de funcionários
 ALTER TABLE funcionários ADD COLUMN dept_id int;

# Adiciona a chave estrangeira de restrição
 ALTER TABLE funcionários ADD CONSTRAINT fk_dept FOREIGN KEY(dept_id) REFERENCES departamentos(dept_id);

# Adicione algumas linhas de amostra na tabela de departamentos
 INSERIR VALORES NOS departamentos (5001, "Vendas");
 INSERIR VALORES NOS departamentos (5002, "Desenvolvimento");
 INSERIR VALORES NOS departamentos (5003, "Marketing");

# Tente atualizar o dept_id de um funcionário com um departamento existente
 UPDATE funcionários SET dept_id = 5001 onde funcionário_id = 101;

# Tente atualizar o dept_id de um funcionário com um departamento que não existe
 UPDATE funcionários SET dept_id = 9999 onde funcionário_id = 101;

# Exemplo de relacionamento 1-1
# Criando a tabela Account com a mesma chave primária da tabela Employees
CRIAR CONTA DE TABELA(
funcionário_id int,
e-mail varchar(50),
chave primária (employee_id),
CONSTRAINT fk_emp FOREIGN KEY(employee_id) REFERENCES funcionários(employee_id)
);

```

#### Exercício

1. Escreva uma consulta INSERT para a tabela Account que retorne um erro.
2. Escreva uma consulta INSERT para a tabela Account que seja válida (não retorna nenhum erro).

#### Essência

Para um relacionamento com cardinalidade `1-M`. A chave primária do lado '1' do relacionamento
torna-se a chave estrangeira do lado 'M' do relacionamento.
Por exemplo. `Departamentos-Funcionários`. A chave primária da tabela Departamentos (dept_id)
torna-se a chave estrangeira na tabela Funcionários.

### 2.2 Relacionamentos (M-M e chaves compostas)

#### Explicação

A cardinalidade de um relacionamento também pode ser `M-M` (leia-se muitos-para-muitos) onde
uma instância de uma entidade participa de muitas outras instâncias da outra entidade
e vice-versa.
Por exemplo, um funcionário pode trabalhar em muitos projetos ao mesmo tempo.
Um projeto pode ter muitos funcionários trabalhando nele.

Para representar um relacionamento `M-M` no MySQL, precisamos de uma **nova tabela de relacionamentos**
que usa duas chaves estrangeiras (chaves primárias de ambas as tabelas). Para tal relacionamento
tabela, a chave primária é composta por duas chaves estrangeiras.
Por exemplo, uma entrada na tabela de relacionamento funcionário-projeto representa
**X** está trabalhando no projeto **Y**.
Pode haver outras linhas com o funcionário **X**,
Pode haver outras linhas com o projeto **Y**
Portanto, nenhuma dessas colunas pode atuar como chave primária sozinha.
A chave primária deve ser a combinação de duas colunas. Um tal primário
key é chamada de **Chave composta**

#### Exemplo

```sql
#cria tabela de projetos
CREATE TABLE projetos (proj_id int, proj_name varchar(50), start_date datetime);

# Inserir valores de amostra
INSERT INTO projetos VALUES(9001, "Jazz", "2018-01-01");
INSERT INTO projetos VALUES(9002, "Mellow", "2019-03-01");
INSERT INTO projetos VALUES(9003, "Clássico", "2020-01-01");

# cria tabela de relacionamento emp_proj com chave primária composta
CRIAR TABELA emp_proj (
emp_id int,
proj_id int,
CHAVE PRIMÁRIA(emp_id, proj_id),
CONSTRAINT fk_emp FOREIGN KEY(emp_id) REFERENCES funcionários(employee_id),
CONSTRAINT fk_pro FOREIGN KEY(proj_id) REFERENCES projetos(proj_id)
);
```

#### Exercício

1. Escreva uma consulta INSERT para a tabela emp_proj que retorne um erro.
2. Escreva uma consulta INSERT para a tabela emp_proj que seja válida (não retorna nenhum erro).

#### Essência

Para um relacionamento 'M-M' entre duas tabelas, uma nova tabela deve ser criada que usa um primário composto
key que consiste em chaves estrangeiras que fazem referência às chaves primárias de ambas as tabelas.

### 3.1 Junções (vírgula, interna)

#### Explicação

Quando a resposta da consulta não puder ser encontrada em apenas uma tabela, devemos unir as duas tabelas.
Se não unirmos a tabela, essa consulta deve ser escrita usando subconsulta aninhada.
Por exemplo, considere a seguinte consulta: **Descubra todos os funcionários que trabalham no departamento de vendas.**
Suponha também que o nome do departamento seja obtido do formulário HTML como entrada.
assim, você deve obter o `dept_id` da tabela de departamentos onde o nome é **Vendas**.
A pergunta a seguir deve dar a resposta.
`SELECT dept_id FROM departamentos onde dept_name = Sales;`
Agora, podemos usar a consulta acima como a (sub)consulta aninhada da seguinte maneira:
`SELECT employee_name FROM employees WHERE dept_id in (SELECT dept_id FROM departamentos onde dept_name = Sales);`

Outra maneira de resolver essa consulta é usar **junções**.
A maneira preferida de unir duas tabelas é usar a cláusula **INNER JOIN** seguida de **ON** seguida de
a condição que geralmente corresponde às colunas compartilhadas pelas duas tabelas que estamos unindo.
Outra maneira é usar uma **vírgula (,) entre os nomes das tabelas** depois de FROM e as colunas correspondentes no **WHERE**
cláusula.

#### Exemplo

```sql
#Devemos juntar as tabelas `employees` e `departments` e depois escolher as linhas relevantes.

# JUNÇÃO INTERNA
SELECIONAR nome_do_funcionário
DE funcionários como E
JUNÇÃO INTERNA
departamentos como D
ON E.dept_id = D.dept_id
WHERE D.dept_name = "Vendas";

# Vírgula (,) ou junção CROSS
SELECIONAR nome_do_funcionário
DE funcionários como E, departamentos como D
onde E.dept_id = D.dept_id
e D.dept_name = "Vendas";
```

#### Exercício

1. Adivinhe a saída da consulta a seguir.
   `SELECT count(*) FROM funcionários, departamentos, projetos;`

2. Imprima a soma salarial de todos os funcionários que trabalham no departamento de "Vendas" e
   trabalhar no projeto "Jazz".

#### Essência

> Quando usamos uma vírgula (,) após a cláusula FROM do MySQL, ela fornece o produto vetorial de duas tabelas.

> No MySQL, não há diferença entre
> (1) Um INNER JOIN com condição de correspondência de colunas após ON e
> (2) A junção usando uma vírgula (,) entre tabelas e cláusula where com condição para correspondência de colunas.

### 3.2 Junções (auto)

#### Explicação

Quando a resposta da consulta não pode ser facilmente encontrada com uma cláusula where, mas a(s) resposta(s) pode(m) ser encontrada(s)
na mesma tabela, considere o seguinte caso:

1. Uma coluna da tabela contém valores da outra coluna da mesma tabela (mas linhas diferentes)
   Por exemplo. A coluna `reports_to` da tabela Employees contém valores do `employee_id`.
2. Queremos imprimir linhas que compartilham valores de coluna de outras linhas
   Por exemplo. Digamos que adicionamos uma coluna `city` à tabela Employees, então
   queremos imprimir todos os funcionários que vêm da mesma cidade que `John Smith`

Para ambos os casos, uma tabela deve ser unida a si mesma (auto-junção).
para autojunção, devemos usar **aliases** para que a desambiguação dos nomes das colunas possa ser alcançada.

#### Exemplo

```sql
Quando queremos imprimir funcionários e seus gerentes de relatórios.
SELECIONE E1.employee_name como Funcionário, E2. nome_funcionário como gerente
DE funcionários como E1
JUNÇÃO INTERNA
funcionários como E2
ON E1.reports_to = E2.employee_id
```

#### Exercício

```sql
# Adicione a coluna da cidade, atualize os registros na tabela de funcionários
Funcionários ALTER TABLE adicionam a coluna cidade varchar(50);
UPDATE funcionários SET cidade = 'Berlim' onde funcionário_nome = 'João';
UPDATE funcionários SET cidade = 'Berlim' onde funcionário_name = 'Amigo de John';
UPDATE funcionários SET cidade = 'Berlim' onde funcionário_name = 'Outro amigo de John';

SELECT nome_do_funcionário, cidade
DE funcionários
WHERE cidade = (SELECT cidade FROM funcionários WHERE funcionário_nome = 'João');
```

Reescreva a consulta acima para imprimir os nomes dos funcionários que vêm da mesma cidade que João usando **autoassociação**.

<details><summary>Revelar consulta</summary>
<p>

```sql
SELECIONE E1.nome_funcionário, E2.cidade
DE funcionários como E1
Funcionários da INNER JOIN como E2
ON E1.cidade = E2.cidade
WHERE E2.employee_name = 'João';
```

</p>
</detalhes>

#### Essência

Para autojunções, devem ser usados aliases para tabelas. Caso contrário, os nomes das colunas são ambíguos.

### 3.3 Junções (LEFT OUTER e RIGHT OUTER)

#### Explicação

Quando juntamos duas tabelas com base em uma coluna comum, algumas linhas não têm correspondência na outra tabela.
Na seguinte instrução `FROM A LEFT JOIN B ON A.col = B.col`,
a tabela A é a tabela LEFT e a tabela B é a tabela RIGHT.
Em um LEFT JOIN, imprimimos **todas as linhas** da tabela LEFT mesmo que elas não tenham uma correspondência na tabela RIGHT.

Na seguinte instrução `FROM A RIGHT JOIN B ON A.col = B.col`,
a tabela A é a tabela LEFT e a tabela B é a tabela RIGHT.
Em um RIGHT JOIN, imprimimos **todas as linhas** da tabela RIGHT mesmo que elas não tenham uma correspondência na tabela LEFT.

#### Exemplo

Alguns funcionários podem não ter um departamento associado a eles, mas
ainda são empregados da empresa.
Assim, se quisermos imprimir todos os funcionários e seus nomes de departamentos,
então um LEFT JOIN (de funcionários para departamentos) nos permite imprimir **tudo** da tabela LEFT
e as linhas correspondentes da outra tabela.

#### Exercício

Use a junção à esquerda para imprimir todos os funcionários e seus gerentes.
Observe que também deve incluir os funcionários que não possuem manjedouras.

<details><summary>Revelar consulta</summary>
<p>

```sql
SELECIONE E.employee_name como Funcionário, E2. nome_funcionário como gerente
DE funcionários como E1
ASSOCIAÇÃO À ESQUERDA
funcionários como E2
ON E1.reports_to = E2.employee_id
```

</p>
</detalhes>

#### Essência

- LEFT JOIN : Todas as linhas da tabela LEFT
- RIGHT JOIN: Todas as linhas da tabela RIGHT

### 4.1. Funções agregadas

#### Explicação

No gerenciamento de banco de dados, uma função agregada é uma função em que os valores de várias linhas são agrupados
juntos como entrada em determinados critérios.
Algumas funções agregadas importantes são

1. SOMA
2. CONTAGEM
3. MÁX.
4. MIN
5. Média

#### Exemplo

Queremos devolver a soma dos salários de todas as funcionárias:

```sql
SELECT SUM(E.salário) AS Despesas de funcionários como E WHERE gênero = 'f';
```

Ou obtenha o número de funcionários:

```sql
SELECT COUNT(*) FROM empregados;
```

#### Exercício

Escreva consultas SQL para obter o máximo e a média dos salários de todos os funcionários.

#### Essência

Usando essas funções, você pode fazer algum processamento de dados no nível do banco de dados. Por exemplo, você pode obter o máximo ou o mínimo dos dados que existem no banco de dados sem a necessidade de processá-los.

### 4.2. DISTINTO

#### Explicação

Distinto: esta instrução é usada para retornar apenas valores distintos (diferentes). Esta palavra-chave evita os valores duplicados.

#### Exemplo

Queremos obter o número de departamentos que possuem pelo menos um funcionário:

```sql
SELECT COUNT(DISTINCT E.dept_id) AS Working_Departments
DE funcionários como E
```

#### Exercício

N / D

#### Essência

Distinto dá valores únicos.

#### 4.3 Agrupar por

#### Explicação

Agrupar por: esta instrução agrupa linhas que têm o mesmo valor em uma determinada coluna e geralmente
aplica uma função agregada em outra coluna

#### Exemplo

Queremos obter a soma do salário e número de funcionários agrupados por gênero:

```sql
SELECT sexo, contagem(employee_id), soma(salário)
DE funcionários
Agrupar por gênero;
```

#### Exercício

Escreva uma consulta que recupere todos os gerentes com o número de funcionários subordinados a eles.

<details><summary>Revelar consulta</summary>
<p>

```sql
SELECT E2.employee_name , count(E1.employee_name) como Employee_cnt
FROM empregado como E1 LEFT JOIN empregado como E2
ON E1.reports_to = E2.employee_id
agrupar por E2.employee_name;
```

</p>
</detalhes>

#### Essência

A cláusula Group by só pode imprimir colunas agrupadas por ou aplicar funções de agregação nas outras colunas.

### 4.4 Tendo

#### Explicação

A cláusula Tendo foi adicionada ao SQL porque a palavra-chave WHERE não pôde ser usada com funções agregadas.
Usando a cláusula havendo você pode ter cláusulas condicionais em funções agregadas.

#### Exemplo

Imprima todos os departamentos que estão gastando mais de 5.000 em salários
(Em outras palavras, todos os departamentos onde a soma dos salários dos funcionários que trabalham neles é superior a 5000)

```sql

SELECT nome_dept, soma(salário)
DE funcionários como E
JUNÇÃO INTERNA
departamentos como D
ON E.dept_no = D.dept_no
GROUP BY dept_name
TENDO soma(salário) > 5000;
```

#### Exercício

Escreva uma consulta que recupere todos os gerentes com mais de 3 funcionários subordinados a eles.
Dica: Nesta consulta, use as palavras-chave DISTINCT e GROUP BY com a cláusula HAVING.

#### Essência

A cláusula Tendo só pode filtrar as linhas com colunas selecionadas pela cláusula GROUP BY.

### 5. Índices

#### Explicação

Índices são um tipo de tabela de consulta em que o servidor de banco de dados pode pesquisar rapidamente linhas nas tabelas de banco de dados.
Os índices são criados quando as linhas são inseridas ou são atualizados quando as colunas indexadas são atualizadas no banco de dados.
Criar ou atualizar índices leva tempo de computação e armazenar índices ocupa espaço de armazenamento de dados.
No entanto, ao recuperar uma linha específica do banco de dados, o banco de dados pode usar esses índices armazenados para localizar a(s) linha(s) solicitada(s) muito mais rapidamente.
Portanto, os índices tornam as operações de atualização ou inserção mais caras/lentas, porém aceleram as operações de recuperação de dados (SELECT/JOIN/WHERE/...).
Além disso, eles aumentam o tamanho total do banco de dados, pois são armazenados junto com suas tabelas correspondentes.

##### Analogia

Imagine um livro (técnico) que tenha o índice no final. Este índice contém palavras-chave nesse livro e informa em quais páginas essas palavras-chave aparecem.
Ajuda a encontrar páginas que contenham a palavra "promessa" em vez de procurar cada página uma por uma. Observe que uma palavra-chave pode aparecer em mais de uma página.
Nesse caso, você verá todas as páginas nas quais essa palavra-chave aparece. Em um livro JavaScript, a palavra `função` pode aparecer em muitas páginas enquanto a palavra
`prototype chaining` pode aparecer apenas uma vez. No índice, você pode encontrar rapidamente em qual página essas palavras aparecem.

Aqui está um [link para um artigo do Medium](https://medium.com/javarevisited/indexes-when-to-use-and-when-to-avoid-them-39c56e5a7329) que descreve os índices de forma concisa.

#### Exemplo

Primeiro vamos criar uma tabela com um grande número de registros.
O programa completo pode ser encontrado em `Week2/generate_big_table.js`, mas aqui está o trecho

```
função assíncrona seedDatabase() {

    const CREATE_TABLE = `
        CRIE TABELA SE NÃO EXISTE grande
        (
            id_pk INT PRIMARY KEY AUTO_INCREMENT,
            número INT
        );`;

    execQuery(CREATE_TABLE);
    deixe linhas = []
    for (i = 1; i <= 1.000.000; i++) {
        linhas.push([i]);
        if(i%10000 === 0){
            console.log("i="+i);
            await execQuery('INSERT INTO big(number) VALUES ?',[rows]);
            linhas = [];
        }
    }
}
```

As duas consultas a seguir mostrarão a diferença (em tempo de execução) entre usar o índice e não usar o índice quando recuperamos os dados.

```
mysql> SELECT * FROM big WHERE id_pk = 1000;
+-------+--------+
| id_pk | número |
+-------+--------+
| 1000 | 1000 |
+-------+--------+
1 linha em conjunto (0,00 seg)

mysql> SELECT * FROM grande WHERE número = 1000;
+-------+--------+
| id_pk | número |
+-------+--------+
| 1000 | 1000 |
+-------+--------+
1 linha em conjunto (0,19 seg)
```

O resultado da primeira consulta é instantâneo porque a cláusula `WHERE` usa a coluna `id_pk` que é uma chave primária.
Observe que para uma coluna de chave primária, o MySQL cria automaticamente um índice. Isso pode ser confirmado com a seguinte consulta

```
mysql> MOSTRA índices de big;
+-------+------------+----------+--------------+-- -------+-----------+-------------+----------+- -------+------+------------+
| Tabela | Não_único | Nome_chave | Seq_in_index | Column_name | Agrupamento | Cardinalidade | Sub_parte | Embalado | Nulo | Tipo_índice |
+-------+------------+----------+--------------+-- -------+-----------+-------------+----------+- -------+------+------------+
| grande | 0 | PRINCIPAL | 1 | id_pk | A | 12769223 | NULO | NULO | | BTREE |
+-------+------------+----------+--------------+-- -------+-----------+-------------+----------+- -------+------+------------+
1 linha em conjunto (0,01 seg)
```

A consulta `SELECT * FROM big WHERE number = 1000` demora mais para ser executada porque a coluna `number` não está indexada. MySQL tem que
vá na tabela `big` e pesquise linha por linha para verificar qual linha contém o valor 1000 na coluna `number`.

O comando `describe` mostra quantas linhas são acessadas para buscar o resultado da consulta.
Verifique a coluna `rows` na saída das seguintes consultas.

```
mysql> DESCRIBE SELECT * FROM big WHERE número = 1000;
+----+-------------+-------+------------+------+-- -------------+------+---------+------+----------+- ---------+-------------+
| identificação | select_type | mesa | divisórias | tipo | chaves_possíveis | chave | key_len | ref | linhas | filtrado | Extra |
+----+-------------+-------+------------+------+-- -------------+------+---------+------+----------+- ---------+-------------+
| 1 | SIMPLES | grande | NULO | TODOS | NULO | NULO | NULO | NULO | 998568 | 10h00 | Usando onde |
+----+-------------+-------+------------+------+-- -------------+------+---------+------+----------+- ---------+-------------+
1 linha em conjunto, 1 aviso (0,00 seg)

mysql> DESCRIBE SELECT * FROM big WHERE id_pk = 1000;
+----+-------------+-------+------------+-------+- --------------+---------+---------+-------+------+ ----------+-------+
| identificação | select_type | mesa | divisórias | tipo | chaves_possíveis | chave | key_len | ref | linhas | filtrado | Extra |
+----+-------------+-------+------------+-------+- --------------+---------+---------+-------+------+ ----------+-------+
| 1 | SIMPLES | grande | NULO | const | PRINCIPAL | PRINCIPAL | 4 | const | 1 | 100,00 | NULO |
+----+-------------+-------+------------+-------+- --------------+---------+---------+-------+------+ ----------+-------+
```

Agora podemos criar um índice na coluna `number` da seguinte forma:

```
CREATE INDEX idx_number ON big(number);
```

Agora podemos executar novamente a consulta de seleção que será mais rápida:

```
mysql> SELECT * FROM grande WHERE número = 1000;
+-------+--------+
| id_pk | número |
+-------+--------+
| 1000 | 1000 |
+-------+--------+
1 linha em conjunto (0,00 seg)
```

Vimos que ter um índice ajuda a buscar os dados mais rapidamente. No entanto, para atualizações/inserções, ter um índice
É mais caro. Depois de fazer uma atualização na coluna indexada, o MySQL também precisa atualizar internamente os índices dessa coluna.

Observe a consulta abaixo:

```
mysql> UPDATE grande SET numero = numero + 100000;
Consulta OK, 1.000.000 linhas afetadas (14,01 s)
Linhas correspondidas: 1.000.000 Alteradas: 1.000.000 Avisos: 0
```

Agora, vamos remover o índice

```
mysql> DROP INDEX número_idx ON grande;
Consulta OK, 0 linha afetada (1,59 s)
Registros: 0 Duplicatas: 0 Avisos: 0
```

e execute novamente a consulta de atualização.

```
mysql> UPDATE grande SET numero = numero + 100000;
Consulta OK, 1.000.000 linhas afetadas (6,14 segundos)
Linhas correspondidas: 1.000.000 Alteradas: 1.000.000 Avisos: 0
```

Podemos ver que sem o índice, a atualização da coluna de número é muito mais rápida (6 segundos em comparação com 14).

#### Exercício

Crie um índice composto usando colunas (`nome_employee e salário`) na tabela `employees` e verifique o desempenho das consultas a seguir

```
DESCRIBE SELECT * FROM employees WHERE employee_name = 'John' e salário = 50000
DESCRIBE SELECT * FROM employees WHERE employee_name = 'John'
DESCRIBE SELECT * FROM empregados ONDE salário = 50.000
```

Certifique-se de ter pelo menos 100 registros na tabela `employees`, incluindo alguém chamado `John` com salário 50.000.

#### Essência

Índices em bancos de dados podem ser usados para aumentar o desempenho para localizar e recuperar linhas específicas.
No entanto, eles também adicionam sobrecarga ao banco de dados (especialmente para atualizações/inserções), portanto, devem ser usados com cuidado.

### 6. Modelagem de Domínio

#### Explicação

- Modelagem de domínio é fazer os modelos para o domínio do problema ou do sistema.
- Faz uso dos conceitos como entidades e relações.
- Diagramas de Entidade-Relacionamento (ERD) são amplamente utilizados na modelagem de domínio.
- No ERD, **entidades** são mostradas por caixas e são coisas abstratas. Por exemplo. John Smith é um exemplo. O aluno é a entidade. Uma entidade no ERD é convertida em uma tabela no MySQL.
- As entidades são conectadas entre si por uma linha (**relacionamentos**) com **cardinalidades** (1-1, 1-M etc.).
- Entidades têm **atributos** mostrados na forma de uma elipse. Um atributo da entidade é traduzido para
  a coluna da tabela correspondente.

#### Exemplo

Desenhe o **ERD** para os funcionários, departamentos e projetos.

#### Exercício

Desenhe o **ERD** para o banco de dados da escola. Identificar tabelas, atributos e relacionamentos.

#### Essência

A modelagem de domínio usando diagramas ERD ajuda os analistas de sistema e designers de banco de dados a ter uma visão concreta do sistema e como aplicá-lo em bancos de dados.
