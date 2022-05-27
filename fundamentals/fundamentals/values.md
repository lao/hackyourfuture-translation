# Valores

Os valores são as "coisas" que você atribui a uma variável. Todos os valores têm um tipo. Em nosso exemplo acima, a variável `x` recebe um valor do tipo `number`. JavaScript suporta os seguintes tipos:

* `string`, por exemplo "HackYourFuture"
* `número`, por exemplo 5 ou 10,6
* `booleano`, por exemplo `verdadeiro` ou `falso`
* `matriz`\*, por exemplo `[1, 2, 3]` ou `['o que', 'é', 'seu', 'nome']`
* `objeto`, por exemplo `{name: 'John', age: 24}`, ou o objeto especial `null`
* `função`, por exemplo `função() { return 4; }`
* `símbolo`
* `indefinido`

Se você declarar uma variável sem especificar seu valor, então, por padrão, seu valor será `undefined`.

Para obter o tipo de um valor atribuído a uma variável, use o seguinte código:

``` js
seja x = 5;
deixe typeOfX = typeof x; // -> 'número'
```

Observe que coloquei um asterisco atrás de 'array'. Isso porque em JavaScript, array é um tipo especial de objeto:

``` js
deixe arr = [1, 2, 3];
deixe typeOfArr = typeof arr; // -> 'objeto'
```

No entanto, na prática, chamaremos essas variáveis de arrays.

## Nulo e indefinido

Os valores `null` e `undefined` são muito semelhantes em JavaScript, mas se comportam de forma um pouco diferente. A diferença é que `null` sempre tem o tipo `'object'`, e `undefined` sempre tem o tipo `'undefined'`.

Sempre que você declarar uma variável, mas não definir um valor, a variável se tornará `undefined`. JavaScript nunca fará uma variável `null` a menos que você atribua explicitamente o valor `null`.

``` js
deixe x;
console.log(tipo de x); // -> 'indefinido'
```


## operador `typeof`

Você pode usar o operador `typeof` para obter o tipo de uma determinada variável como você viu na seção acima 'Tipos de valor'. Como você pode ver nos exemplos a seguir, ele retorna o tipo de valor que você atribuiu à sua variável.

## Cordas

Em JavaScript você pode atribuir uma série de caracteres a uma variável, então você chama isso de string. Você pode usar todos os tipos de caracteres (texto/números, espaços ou frases) em strings. Usando o `''` você define que algo é uma string. Você também pode usar `""` para criar uma string. Ambos estão bem, desde que você seja consistente (apenas escolha qual você prefere e mantenha-o).

``` js
deixe foo = '42';
typeof foo //-> 'string'

let bar = 'Tenho 99 anos';
typeof bar //-> 'string'
```

### Índices de string e propriedades de string

Caracteres individuais em uma string podem ser acessados por sua posição (índice) dentro da string. O índice de uma string sempre começa em 0.
Strings também possuem propriedades, por exemplo `.length` você pode usar isso para encontrar o comprimento de uma string.

Assim, por exemplo:
``` js
let baz = 'Olá Mundo';
baz[0]; //-> "H"
baz.comprimento; //-> 11
```

### Métodos de string

Os métodos de string são operações nomeadas que você pode usar em valores de string para criar novos valores. Por exemplo, o método `toUpperCase` cria uma nova string com todas as letras maiúsculas.

``` js
let baz = 'Olá Mundo!';
baz.toUpperCase(); // -> 'OLÁ MUNDO'
```

Métodos diferem de propriedades (como `.length`) em que você deve sempre usá-los com parênteses de abertura e fechamento `(` e `)`.

Alguns métodos precisam de informações adicionais e você deve fornecê-las na forma de um ou mais _parameters_. Por exemplo:

``` js
let baz = 'Olá Mundo!';
baz.slice(3, 8) // -> 'lo Wo'
baz.startsWith('He') // -> true
baz.indexOf('Mundo') // -> 6
```

## Números

Todos os números em JavaScript são considerados números, com ou sem decimal.

``` js
deixe quux = 42;
typeof quux //-> 'number'

deixe quux = 3,3333;
typeof quuux //-> 'número'

```


## Matrizes

Arrays são valores que contêm uma lista de coisas, em vez de apenas uma coisa. O que está dentro da matriz, normalmente chamamos de "elementos". Assim, o array `[1, 2, 3]` tem três elementos. A matriz `[]` não possui elementos e, portanto, está vazia. O número de elementos em uma matriz é chamado de "comprimento".

Quando você deseja acessar um elemento dentro de um array, você usa um "índice". Este é o número que você coloca entre colchetes (`[]`).

Dado o seguinte código:

``` js
let arr = ['john', 'jane', 'jack'];
console.log(arr[0]);
```

O número `0` é o "índice do primeiro elemento do array `arr`". Por outro lado, o elemento "no índice 0 no array `arr` é `'john'`".

Em vez de um número, você também pode usar uma variável para acessar elementos em um array, *desde que essa variável seja um número*:

``` js
let arr = ['john', 'jane', 'jack'];
seja a = 1;
console.log(arr[a]); // -> jane
```

Se o índice que você usa não for um inteiro (um número inteiro), ou se for menor que '0' ou se for maior ou igual ao tamanho do array, você receberá de volta 'undefined'.

Mais sobre [arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
