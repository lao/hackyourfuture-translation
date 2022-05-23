Esta pasta contém uma pequena base de código para configurar um banco de dados com algum conteúdo.
O banco de dados conterá informações sobre os usuários, seus projetos e tarefas.
As tarefas podem ser atribuídas aos usuários opcionalmente, o que resulta em algumas consultas de exemplo interessantes.

Crie um banco de dados chamado `db_qa_session` ou faça alterações no `knexfile.js`

```
npm instalar
npm install -g knex
knex migrar:latest
semente knex: correr
```

Seu banco de dados deve ser preenchido com algum conteúdo de demonstração :)

Essas sementes e migrações em si não estão no escopo deste curso.
É apenas uma maneira conveniente de criar o banco de dados de demonstração que terá algum conteúdo significativo para demonstrar consultas.

Alguns exercícios que cobrem os tópicos desta semana:

1. Liste todas as tarefas
    1. mostre apenas os que ainda não estão prontos.
       `NOW()` pode ser usado para o dateTime atual.
    2. adicione o nome e sobrenome do usuário atribuído
    3. adicione o projeto para a tarefa

2. Liste todos os projetos
    1. reduza a lista aos projetos que não terminaram
    2. adicione uma coluna com a quantidade de tarefas no projeto

3. Em seu frontend você pode ter uma url como `/projects/3` ou ainda mais bonita `/projects/{CODE}`.
   Escolha um código de um projeto.
    1. Busque todas as tarefas desse projeto (não retorne as colunas da tabela do projeto)

4. Para uma página de administração, você deseja listar os usuários com seus projetos e seus aliases de projetos

5. Para análise, queremos ter a quantidade de tarefas feitas por usuário por mês.
   1. Crie uma consulta separada com a quantidade média de tarefas realizadas por mês por usuário.
      Por exemplo retornando: Tomas termina 4 tarefas por mês em média.
   
   
     
    

