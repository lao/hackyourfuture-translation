# Manipulação básica do DOM

O Document Object Model (DOM) é uma construção através da qual os navegadores da Web tornam a estrutura HTML de uma página da Web (= 'documento') disponível para arquivos JavaScript carregados nessa página. Podemos acessar o DOM através de um objeto global chamado `document`.

Considere este HTML:

```html
<corpo>
  <div id="root"></div>
</body>
```

Um método comum para acessar um elemento HTML através do DOM é fornecer um ID a ele e, em seguida, usar o método `document` `getElementById()`.

``` js
const rootDiv = document.getElementById('root');
```

Agora, temos uma *referência* ao elemento HTML em nosso código JavaScript. Podemos, por exemplo, definir o conteúdo do texto através da propriedade `innerText`.

``` js
rootDiv.innerText = 'Olá, mundo!';
```

Como resultado, a estrutura HTML agora se parece com isso:

```html
<corpo>
  <div id="root">Olá, mundo!</div>
</body>
```

> Veja o resultado do que este código muda neste [CodePen](https://codepen.io/remarcmij/pen/VEerRP) e brinque com ele você mesmo.

_Observe que não estamos modificando o arquivo HTML (por exemplo, `index.html`) em si. Estamos apenas modificando uma representação na memória do HTML como foi inicialmente carregado por meio do arquivo HTML._

Também podemos criar elementos:

``` js
// Cria um elemento de botão e rotula-o Click Me!
const meuBotão = document.createElement('button');
myButton.innerText = 'Clique em mim!';
```

Isso cria um elemento de botão e define seu rótulo (ou seja, `innerText`), mas isso por si só não é suficiente. Neste ponto, o botão é criado, mas ainda não adicionado ao DOM: ele ainda está em algum lugar "pendurado no ar". Precisamos anexá-lo a algum elemento pai que já faz parte do DOM. Isso é feito chamando `appendChild()` nesse elemento pai, passando uma referência para o elemento recém-criado.

``` js
rootDiv.appendChild(meuBotão);
```

Como resultado, a estrutura HTML agora se parece com isso:

```html
<corpo>
  <div id="root">
    <button>Clique em mim!</button>
  </div>
</body>
```

> Veja o resultado do que este código muda neste [CodePen](https://codepen.io/remarcmij/pen/bmEaVm) e brinque com ele você mesmo.

Podemos definir atributos em elementos:

``` js
myButton.setAttribute('class', 'meu-botão');
```

HTML resultante:

```html
<corpo>
  <div id="root">
    <button class="my-button">Clique em mim!</button>
  </div>
</body>
```

> Veja o resultado do que este código muda neste [CodePen](https://codepen.io/remarcmij/pen/wYMmpP) e brinque com ele você mesmo.

Podemos adicionar ouvintes de eventos a elementos para responder à interação do usuário. Neste exemplo estamos adicionando um ouvinte de evento ao botão que responde ao evento `click`. Este evento é acionado sempre que o usuário clica no botão.

``` js
 myButton.addEventListener('click', function() {
  const para = document.createElement('p');
  para.innerText = 'Você clicou em mim!';
  rootDiv.appendChild(para);
});
```

Adicionar um ouvinte de eventos não altera a estrutura HTML. No entanto, o ouvinte de eventos pode causar alterações no DOM (como ilustrado no exemplo acima) quando o evento é acionado.

> Veja o resultado do que este código muda neste [CodePen](https://codepen.io/remarcmij/pen/MPKVEP) e brinque com ele você mesmo.

