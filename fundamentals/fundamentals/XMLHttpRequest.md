# XMLHttpRequest

**XMLHttpRequest** é um objeto para interagir com servidores. Você pode recuperar dados de uma URL sem precisar atualizar a página inteira. XMLHttpRequest é muito usado na programação Ajax - [MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest).

Então, o que é Ajax?

**Ajax** é um método de troca de dados com um servidor e atualização de partes de uma página da web sem recarregar a página inteira.

Vamos mergulhar no código:

Primeiro, precisamos fazer uma instância do objeto 'XMLHttpRequest'.

``` js
deixe http = new XMLHttpRequest();
```

Quando estamos fazendo uma requisição ela passa por 5 estados:

| Valor | Descrição |
| :---: | --------------------------- |
| 0 | pedido não é inicializado. |
| 1 | pedido foi configurado. |
| 2 | pedido foi enviado. |
| 3 | pedido está em andamento. |
| 4 | pedido está completo. |

No código abaixo, estamos verificando se a solicitação está completa ou não, e verificamos o status === 200 apenas para garantir que não recebemos um erro 404 - Leia mais sobre isso aqui: [HTTP Status Code](https ://httpstatuses.com).

``` js
http.onreadystatechange = function() {
  if (http.readyState === 4 && http.status === 200) {
    console.log('Resposta do servidor: ' + http.response);
  }
};
```

Existem métodos para lidar com um servidor como (GET, POST, UPDATE, DELETE…)

| Método | Descrição |
| -------- | ---------------------------- |
| `GET` | recuperar dados do servidor. |
| `POST` | enviar dados para o servidor. |
| `ATUALIZAÇÃO` | atualizar dados no servidor. |
| `EXCLUIR` | excluir dados do servidor. |

Para inicializar uma solicitação, usamos o método [open](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/open). A sintaxe é:

``` js
XMLHttpRequest.open(método, url, assíncrono, usuário, senha);
```

Os parâmetros _method_ e _url_ são obrigatórios, _user_ e _password_ são opcionais. True é um valor padrão para _async_.

``` js
http.open('GET', URL, true/false);
```

No final, temos que enviar nossa solicitação ao servidor através do método [send](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/send). Em nossa situação estamos recuperando um dado do servidor, então não precisamos passar um parâmetro para a requisição de envio.

``` js
http.send();
```
