# O que é isto'?

Em qualquer ponto durante a execução de um programa JavaScript existe um valor dependente do contexto que você pode acessar através da palavra-chave `this`. Muitas vezes, o valor de `this` é simplesmente `undefined` e, portanto, não tem muita importância para uso em seu próprio código.

> Nota: O valor de `this` só é útil se usado dentro de uma função. Quando acessado fora de qualquer função, o valor de `this` é diferente dependendo se você executa seu programa no navegador ou no Node. No caso do navegador, o valor de `this` refere-se ao objeto global `window`. No caso do Node, o valor de `this` fora de qualquer função é um objeto vazio (`{}`).

## Funções regulares e `this`

Vejamos o valor de `this` quando usado em uma função regular:

``` js
'usar estrito';

function whatIsThis(arg) {
  console.log(arg, this);
}

whatIsThis('Olá'); // --> Olá indefinido
```

Como mencionado, o valor de `this` neste caso é `undefined`. Note, entretanto, que este é apenas o caso se iniciarmos nosso arquivo com a string literal `'use strict'`. (Nas versões de JavaScript anteriores ao ES5 a opção `'use strict'` não existia.) Se você deixar de fora `'use strict'` então `this` se refere ao 'contexto global' (no navegador este é o ` window`, no Node é o objeto `global`).

No exemplo abaixo você pode ver o efeito (a saída mostrada é para o navegador).

``` js
// deixado de fora: 'use strict';

function whatIsThis(arg) {
  console.log(arg, this);
}

whatIsThis('Olá'); // --> Olá
                     // ▶︎ Janela {postMessage: f, ...}
```

Acessar o contexto global através do `this` (acidentalmente ou de propósito) nunca é uma boa ideia, principalmente quando se trata de esquecer de declarar uma variável. Os designers de JavaScript reconheceram isso como um problema e forneceram a opção `'use strict'` no ES5 como um remédio.

Mais informações sobre o MDN: [modo estrito](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)

## Invocação de função através do método `call`

Quando você chama uma função regular especificando seu nome seguido por zero ou mais argumentos entre parênteses, o mecanismo JavaScript de fato invoca o método `call` que existe em cada função (sim, uma função é na verdade um tipo especial de objeto JavaScript) . O trecho de código abaixo mostra como uma função regular é invocada nos bastidores pelo mecanismo JavaScript, definindo o valor `this` (o primeiro argumento do método `call`) para `undefined`.

``` js
'usar estrito';

function whatIsThis(arg) {
  console.log(arg, this);
}

whatIsThis.call(undefined, 'Olá'); // --> Olá indefinido
```

Podemos usar o método `call` e passar outra coisa no lugar de `undefined`, conforme mostrado no próximo trecho:

``` js
whatIsThis.call('mundo!', 'Olá'); // --> Olá mundo!
```

No entanto, na prática, não há muitas ocasiões em que precisaríamos usar o método `call` para definir o valor de `this`.

A seguir, veremos como `this` se torna relevante quando usado em combinação com objetos JavaScript.

Mais informações sobre propriedades e métodos da função `this` e JavaScript:

- [Compreendendo a invocação de função JavaScript e "isto"](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/), por Yehuda Katz.
- MDN: [objeto de protótipo de função](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function#Function_prototype_object)

## Objetos JavaScript e 'this'

Quando usado em conjunto com métodos JavaScript (incluindo aqueles de classes ES6), a palavra-chave `this` ganha importância primordial.

> **O que é um método?** Um método é uma função JavaScript normal que é 'chamada' em um objeto, usando a notação de ponto. Em quase todos os casos esta função será definida como uma propriedade do objeto (ou seu protótipo) que é chamado. Nas classes ES6, os métodos são definidos diretamente como funções-membro na classe.

O exemplo abaixo mostra um objeto simples com uma propriedade de dados `myData` e uma propriedade de método `myMethod`. Quando `myMethod` é chamado usando a notação de ponto, como mostrado no exemplo abaixo, o valor `this` dentro do método é definido para o próprio objeto. Portanto, `myMethod` tem acesso à propriedade `myData` através da palavra-chave `this`.

``` js
const meuObj = {
  myData: 'Olá mundo!',
  meuMétodo: function() {
    console.log(this.myData);
  }
};

meuObj.meuMétodo(); // --> Olá mundo!
```

## Função.prototype.bind

Existe ainda outra maneira de definir o valor `this`. Isso pode ser feito através do método `bind` que está disponível em todas as funções (embora não tenha efeito nas funções fat arrow).

Para definir o valor de `this` você chama o método `bind` com um único parâmetro, passando o valor a ser atribuído a `this`. (O método `bind` aceita parâmetros adicionais, mas seu uso está além do escopo deste artigo. Consulte a referência abaixo para obter mais informações).

O método `bind` retorna uma nova função para a qual o valor `this` é fixado no valor especificado no parâmetro `bind`, conforme mostrado abaixo.

``` js
const meuObj = {
  myData: 'Olá mundo!'
};

função imprimirMeuDados() {
  console.log(this.myData);
}

const novaFunção = printMyData.bind(myObj);
novaFunção(); // --> Olá mundo!
```

Usando a função `printMyData` como base, o método `bind` fixa o valor `this` para `myObj` e retorna uma nova função atribuída aqui à variável `newFunction`. Quando chamamos `newFunction` o valor `this` será `myObj`, e portanto podemos console.log `myData` através da palavra-chave `this`.

Você encontrará o método `bind` extensivamente no módulo HYF React.

MDN: [Function.prototype.bind()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

## Funções de seta gorda e 'this'

Em funções de setas gordas, o valor de `this` é inalterado em relação ao seu escopo. Isso torna as funções fat arrow especificamente úteis como manipuladores de eventos e callbacks quando usadas em objetos e classes ES onde `this` é usado.

No exemplo abaixo nós definimos uma classe ES6 simples que usa um `setTimeout` para console.log o valor `myData` após um segundo. O retorno de chamada passado como o primeiro parâmetro de `setTimeout` é escrito como uma função de seta gorda. Portanto, o valor `this` dentro da função de seta gorda se refere ao valor `this` do método `sayDelayed`. Como `sayDelayed` é chamado usando a notação de objeto, o valor `this` é definido para o próprio objeto. Assim, o resultado esperado é impresso.

Se tivéssemos escrito o retorno de chamada como uma função regular (anônima), usando a palavra-chave `function`, isso teria falhado, pois seu valor `this` teria sido definido como `undefined`. Tente!

``` js
class MinhaClasse {

  construtor(){
    this.myData = 'Olá mundo'
  }

  digaAtrasado() {
    setTimeout(() => {
      console.log(this.myData);
    }, 1000);
  }
}

const minhaClasse = new MinhaClasse();
minhaClasse.sayDelayed();
```

No entanto, existem maneiras de usar funções regulares neste cenário, como era o caso comum antes das funções de setas gordas serem introduzidas no ES6. Uma maneira é usar `bind` como neste exemplo:

``` js
class MinhaClasse {

  construtor(){
    this.myData = 'Olá mundo'
  }

  digaAtrasado() {
    setTimeout(função() {
      console.log(this.myData);
    }.bind(este), 1000);
  }
}

const minhaClasse = new MinhaClasse();
minhaClasse.sayDelayed();
```

Outra maneira é introduzir uma variável intermediária, geralmente chamada de `self` ou `that`, em um encerramento:

``` js
class MinhaClasse {

  construtor(){
    this.myData = 'Olá mundo'
  }

  digaAtrasado() {
    const self = this;
    setTimeout(função() {
      console.log(self.myData);
    }, 1000);
  }
}

const minhaClasse = new MinhaClasse();
minhaClasse.sayDelayed();
```