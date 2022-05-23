# Exercício de preparação - Servidor Web

Neste exercício, você construirá um servidor web simples. Ele servirá apenas um arquivo HTML e um arquivo JavaScript. Isso é suficiente para um site mínimo.

Para ajudá-lo a começar, algum código já foi fornecido para você. Verifique o arquivo `server.js` e tente entender o que o código faz.

Verifique se o código está funcionando bem executando-o e abrindo o site em seu navegador em `http://localhost:3000`. Você deverá ver o texto `Hello World!`. Ao trabalhar neste exercício e no projeto, certifique-se de verificar constantemente se suas alterações funcionam conforme o esperado executando seu código e verificando o navegador.

Seu trabalho é alterar o código para que ele sirva HTML em vez de apenas `Hello World!`.

Usando node, leia o conteúdo do arquivo `index.html` e envie-o como resposta. Certifique-se de definir o cabeçalho `Content-Type` correto.

Execute o código e verifique se ele funciona abrindo um navegador em `http://localhost:3000`.

Se você abrir a aba Rede (nas ferramentas do desenvolvedor do seu navegador) você notará que o navegador tenta carregar o JavaScript `index.js`, mas falha. Isso ocorre porque nosso servidor ainda não **veicula** esse arquivo.

Até agora o servidor serve apenas uma coisa, o arquivo HTML. Para servir coisas diferentes, de alguma forma temos que determinar o que está sendo solicitado. É aqui que entra o `request.url`.

Se você abrir a aba Rede você pode ver que quando o navegador está solicitando o código HTML ele está usando a url `http://localhost:3000/`. Por outro lado, quando o navegador está solicitando o javascript está usando a url `http://localhost:3000/index.js`.

Vamos alterar nosso código para enviar uma resposta diferente, dependendo da URL da solicitação.

Para fazer isso, você precisa escrever 2 instruções if condicionais.

1. Se o URL for `/`, envie o arquivo HTML, como antes
2. Se a URL for `/index.js`, envie o arquivo JavaScript correspondente após lê-lo do sistema de arquivos. Não se esqueça de definir o cabeçalho `Content-Type` correto.

Execute o código e verifique se ele funciona abrindo um navegador em `http://localhost:3000`. Você deverá ver a mensagem _Welcome to Server-land!_.

Parabéns, você criou seu próprio servidor web funcional!

> Em poucas palavras, é assim que a maioria dos sites funciona. O cliente solicita recursos, o servidor os envia e, em seguida, o cliente processa a resposta com base no tipo de conteúdo. Esse processamento geralmente leva a novas solicitações e o ciclo continua até que tudo esteja carregado e pronto para o usuário interagir.

Pontas:

- Para definir um cabeçalho de resposta [response.setHeader(name, value)](https://nodejs.org/api/http.html#http_response_setheader_name_value)
- Para ler um arquivo do sistema de arquivos [fsPromises.readFile(path[, options])](https://nodejs.org/docs/latest-v14.x/api/fs.html#fs_fspromises_readfile_path_options)
- Cansado de reiniciar seu servidor!? [nodemon](https://www.npmjs.com/package/nodemon) está aqui para ajudar.

_BÔNUS_
 Nosso site está funcionando, mas parece obsoleto. Tente adicionar algum estilo a ele. O estilo deve ser de uma fonte externa. Adicione isso ao seu arquivo HTML.

```html
<link rel="stylesheet" type="text/css" href="style.css" />
```

Quando o servidor recebe uma solicitação em `http://localhost:3000/style.css`, responda com um arquivo CSS que contém algumas regras básicas de CSS, por exemplo, `#conteúdo { cor: azul }`. Não se esqueça de especificar o `Content-Type` no cabeçalho da solicitação!

## Coisas para pensar

- Por que temos que construir um servidor inteiro apenas para servir uma página da web?
- É assim que todas as páginas da web são enviadas aos usuários?
- Todas as páginas da Web são atendidas enviando um arquivo de volta em uma solicitação? E isso também funcionaria para enviar arquivos (pense em compartilhar uma imagem ou um vídeo)?
- No mundo da computação em nuvem, isso muda alguma coisa na hospedagem dessas páginas?
