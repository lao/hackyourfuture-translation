# Como configurar seu primeiro banco de dados

Neste documento você aprenderá como configurar seu primeiro banco de dados. A maioria dos comandos é feita na linha de comando, portanto, certifique-se de ter o seu aberto antes de começar.

**Etapa 1: Fazendo login com o usuário `root`**

Para começar com seu novo cliente MySQL, primeiro temos que fazer login com o usuário `root`.

> Um usuário root, também conhecido como `superusuário` é uma conta de usuário especial que tem acesso a todos os comandos e arquivos de qualquer software em particular.

No sistema operacional Windows, se você clicar no menu Iniciar e digitar `MySQL Command line Client`, então
o MySQL Command Line Client fornece um prompt `msql>` após digitar sua senha de root.
Note que esta senha é aquela que você usou para o `usuário root` do mysql durante a instalação.
Usuários de Linux e MAC podem executar `mysql -uroot -p` e então digitar sua senha de root.

**Etapa 2: criando uma conta `hyfuser`**

Após o login com o usuário root, é hora de criar a conta que usaremos para este módulo. Execute os seguintes comandos, um após o outro:

```bash
# Passo 1: Este comando cria um usuário 'hyfuser' com senha 'hyfpassword' para o servidor de banco de dados em 'localhost'

mysql> cria usuário 'hyfuser'@'localhost' identificado com mysql_native_password por 'hyfpassword';

# Se isso não funcionar, tente o comando alternativo:

mysql> cria usuário 'hyfuser'@'localhost' identificado por 'hyfpassword';

# Passo 2: Este comando dá todas as permissões ao usuário 'hyfuser'. O (*.*) significa cada tabela de cada banco de dados.

mysql> concede todos os privilégios em *.* para 'hyfuser'@'localhost';

# Etapa 3: Este comando libera todos os privilégios

msyql> privilégios de descarga;

# Passo 4: Este comando cria um banco de dados chamado 'userdb'

mysql> criar banco de dados userdb;
```

**Etapa 3: Instalando o driver MySQL para usar com Node.js**

Queremos usar MySQL com JavaScript e para isso, usamos o seguinte [pacote](https://github.com/mysqljs/mysql).

- Use o comando `npm install -g mysql` para instalá-lo.
- Navegue até a pasta `Week1` do terminal VScode e execute o comando `node connection-test.js`

A saída deve ser 'A solução é: 2'.
