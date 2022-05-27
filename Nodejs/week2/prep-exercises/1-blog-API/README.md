## Faça uma API de blog

Alguém aqui ainda se lembra dos blogs!? Eles estavam na moda há cerca de 10 anos. Estamos um pouco atrasados para a festa, mas acho que ainda podemos ganhar algum dinheiro com um aplicativo de blog.

Como você acabou de aprender sobre REST e APIs, vamos usá-los ao escrever este aplicativo. O recurso na aplicação são `blogs`. Cada blog terá um `título` e um `conteúdo`. O `title` também servirá como um `id` identificando exclusivamente uma postagem do blog.

Também queremos que nossos blogs sejam armazenados `persistentemente`. Persistência de dados significa manter os dados com os quais você está trabalhando independentemente de o serviço Node.js ser reiniciado ou não. Para conseguir isso, cada postagem do blog será armazenada como um arquivo separado no disco rígido, onde o título da postagem do blog corresponderá ao nome do arquivo.

Antes de começarmos a codificar, precisamos definir quais operações serão suportadas por meio de nossa API. Aqui está o que vamos fazer...

| Operação | Descrição | Método | Rota |
| --------- | -------------------------------------------------- ----- | ------ | ----- |
| Criar | Dado um título e conteúdo crie um novo post | | |
| Leia um | Dado um título, retorne o conteúdo de uma única postagem do blog | | |
| Atualizar | Dado um título e atualização de conteúdo de uma postagem de blog existente | | |
| Excluir | Dado um título, exclua uma postagem de blog existente | | |

O que você acha que deve ser preenchido nas colunas `Method` e `Route`? Pense nisso e veja se você consegue adivinhar o que deveria ser...

Quando estiver pronto, vamos começar configurando nosso ambiente. Siga os passos:

**Configuração:**

1. Navegue até a pasta de exercícios `1-blog-api`
2. Na pasta já existe um arquivo `server.js` e `package.json` preparado para você com algum código inicial e a dependência expressa.
3. Instale as dependências localmente executando `npm install`. Este comando irá ler as dependências do `package.json` e baixá-las em seu computador.

Isso não foi muito difícil, foi? Agora você está pronto para a codificação real. Começaremos por...

**1.1 Criando novas postagens**

Para criar uma nova postagem no blog, precisamos de 2 coisas:

1. Um usuário que envia dados de um cliente (por exemplo, uma página da Web que contém um `<form>`)
2. Um servidor web que escuta uma requisição que chega em um certo `endpoint`.

Não trabalharemos no primeiro ponto, mas assumiremos que os dados recebidos do cliente estarão no formato JSON. Por exemplo: `{ "title": "Meu primeiro blog", "content": "Lorem ipsum" }`.

Você precisa criar outro endpoint em nosso servidor web que receberá os dados e os armazenará em um arquivo separado. O armazenamento de arquivos acontecerá com o uso do [fs](https://nodejs.org/api/fs.html#fs_file_system), um módulo nativo do Node.js que nos permite interagir com o sistema de arquivos do nosso computador para que possamos criar novos arquivos.

Siga os passos:

1. Dentro de `server.js`, adicione o seguinte código inicial no local correto:

```javascript
const fs = require("fs");

app.<MÉTODO>('/blogs', (req, res) => {
    // Como obter o título e o conteúdo da requisição??
    fs.writeFileSync(título, conteúdo);
    res.end('ok')
})
```

2. Substitua `<MÉTODO>` pelo verbo HTTP correto.
3. Descubra como acessar as propriedades `title` e `content` fora da solicitação.

Dica: Lembre-se de `express.json()`. Por que o usamos durante nossas palestras?

Depois de terminar de escrever seu código, use o Postman para testar se seu código funciona. Envie uma solicitação usando o URL e o verbo HTTP corretos. Como os dados que você enviará no corpo da solicitação, você pode usar o exemplo: `{ "title": "Meu primeiro blog", "content": "Lorem ipsum" }`. Certifique-se de especificar o `Content-Type` como JSON!

Saída esperada:
Você deve obter uma resposta `ok` e ver um novo arquivo `My first blog` na sua pasta `1-blog-api`.

![Obama nada mal](https://nwlc.org/wp-content/uploads/2016/09/notbad.jpg)

A seguir:

**1.2 Atualizando postagens existentes**

Atualizar postagens é muito semelhante a criá-las. Você só precisa usar um MÉTODO diferente e adicionar uma instrução condicional que verifica se a postagem do blog que o usuário está tentando atualizar já existe com `fs.existsSync()`.

Desta vez vamos usar um _parâmetro de url_ no Express para enviar o `título` enquanto o `conteúdo` fará parte do `corpo`.

Siga os passos:

1. Dentro de `server.js`, adicione o seguinte código inicial no local correto:

```javascript
app.<METHOD>('/posts/:title', (req, res) => {
    // Como obter o título e o conteúdo da solicitação?
    // E se a solicitação não tiver título e/ou conteúdo?
    E se () {
      fs.writeFileSync(título, conteúdo);
      res.end('ok')
    }
    senão {
      //Envia resposta com mensagem de erro
    }
})
```

2. Substitua `<MÉTODO>` pelo verbo HTTP correto.
3. Adicione uma condição: se o arquivo com o título fornecido existir, reescreva-o com o conteúdo fornecido. Caso contrário, responda com uma mensagem dizendo 'Esta postagem não existe!'. Use o `fs.existsSync(title)` para verificar se existe um arquivo.

Depois de terminar de escrever seu código, use o Postman para testar se seu código funciona. Envie uma solicitação usando o URL e o verbo HTTP corretos. Como os dados que você enviará no corpo da solicitação, você pode usar o exemplo: `{ "title": "Meu primeiro blog", "content": "Este conteúdo já está atualizado!" }`.

Ele envia a resposta correta caso o post exista ou não?

Saída esperada:
Se a solicitação puder ser tratada, responda com 'ok', senão responda com 'Esta postagem não existe!'.

Próximo:

**1.3 Excluindo postagens**

Para deletar postagens, usaremos novamente os `parâmetros de URL`, desta vez para especificar qual postagem queremos deletar.

Como estamos excluindo uma postagem, não há necessidade de enviar nenhum conteúdo na solicitação. Para excluir o correspondente, você pode usar `fs.unlinkSync(<filename>)`.

Siga os passos:

1. Dentro de `server.js`, adicione o seguinte código inicial no local correto:

```javascript
app.<METHOD>('/blogs/:title', (req, res) => {
    // Como obter o título dos parâmetros de url?
    if () { // Adiciona condição aqui
      fs.unlinkSync(título);
      res.end('ok');
    } senão {
      // Responda com mensagem aqui
    }
})
```

2. Substitua `<MÉTODO>` pelo verbo HTTP correto.
3. Descubra como obter o `título` da solicitação.
4. Adicione uma condição, exclua o arquivo somente se ele existir. Faça uso do método `fs.existsSync(title)`.
5. Exclua o arquivo passando o título para o método `fs.unlinkSync()`.

Depois de terminar de escrever seu código, use o Postman para testar se seu código funciona. Envie uma solicitação usando o URL e o verbo HTTP corretos. Nenhum conteúdo corporal necessário!

**1.4 Lendo postagens**

Querer ler um arquivo é a forma mais comum de solicitação que um cliente pode enviar. Digite `https://www.google.com/` no seu navegador e você está enviando uma solicitação, querendo ler um arquivo!

Quando um servidor web recebe uma solicitação para ler um arquivo, ele envia de volta uma resposta incluindo o arquivo que precisa ser lido.

Em nosso aplicativo de blog, enviaremos o arquivo correto dependendo do título da postagem do blog. Especificamos isso em nossa solicitação colocando o título desse blog nos parâmetros de URL, como `http://localhost:3000/blogs/blogtitle`.

No momento em que o servidor da web receber uma solicitação em nosso novo endpoint, examinaremos os parâmetros de URL e responderemos com o arquivo correto.

Siga os passos:

1. Dentro de `server.js`, adicione o seguinte código inicial no local correto:

```javascript
app.<METHOD>('/blogs/:title', (req, res) => {

    // Como obter o título dos parâmetros de url?
    //verifica se o post existe
    post const = fs.readFileSync(título);
    //envia resposta
})
```

2. Substitua `<MÉTODO>` pelo verbo HTTP correto.
3. Descubra como obter o `título` da solicitação.
4. Adicione uma condição, só envie a postagem se ela existir. Faça uso do método `fs.existsSync(title)`.

Depois de terminar de escrever seu código, **use o Postman para testar se seu código funciona**. Envie uma solicitação usando o URL e o verbo HTTP corretos.

Saída esperada:
Se a postagem solicitada existir, a resposta deve ser o conteúdo da postagem como texto simples. Caso contrário, a resposta deve ser 'Esta postagem não existe!'. Ambas as respostas devem ter o status apropriado.

Tudo feito? Parabéns!

![Parabéns](https://media.giphy.com/media/l1AsI389lnxkvQHAc/giphy.gif)

**Bônus: Lendo todas as postagens**
Além de ler o conteúdo de uma única postagem, crie uma operação que leia todas as postagens existentes. Para limitar o tamanho da resposta, envie apenas o título das postagens do blog, por exemplo. `[{"title":"Meu Primeiro Blog"}, {"title":"Segundo Blog"}]`

```javascript
app.<MÉTODO>('/blogs', (req, res) => {
    // como obter os nomes dos arquivos de todos os arquivos em uma pasta??
})
```

## Coisas para pensar

- Por que você precisa colocar o `:` em certas URLs?
- O que você deve fazer se o sistema de arquivos apresentar um erro (a linha `fs.readFileSync` por exemplo)? Qual é a melhor maneira de lidar com isso?
- Por que usamos a função síncrona para leitura de arquivos do sistema?
- Devemos sempre enviar de volta apenas um objeto JSON?
