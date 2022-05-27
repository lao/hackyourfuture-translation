# Manipulações de matriz

[MDN em matrizes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
Como já sabemos, arrays são coleções de valores.

Como veremos, muitas vezes há muitas maneiras de conseguir a mesma coisa ao trabalhar com arrays. Com o tempo, você adicionará diferentes técnicas à sua caixa de ferramentas mental para alcançar o resultado desejado rapidamente.

O básico.

- Como criamos um array?
- Como adicionamos itens a um array?
- Como alteramos os itens de um array?
- Como removemos itens de um array?
- Como sabemos o comprimento de uma matriz?
- Como iteramos sobre uma matriz?

## Como criamos um array?

Um array pode ser criado de várias maneiras

Do princípio:

``` js
const a = []; // resultado: []
const b = ['item1', 'item2']; // resultado: ['item1', 'item2']

// Os exemplos com new Array() NÃO são recomendados e mostrados aqui apenas para fins de demonstração.
const c = new Array(); // resultado: []
const d = new Array('item 1', 'item2'); // resultado: ['item1', 'item2']
const e = new Array(20); // resultado: [ <20 itens vazios> ]
const f = new Array(20, 21); // resultado: [20, 21]
// Note que `e` e `f` são um belo exemplo de como o JavaScript pode ser estranho e inesperado.
// Você deve usar `a` ou `b` por padrão.
```

From value (como exemplo, muitas maneiras de criar uma matriz a partir de outro valor):

``` js
const a = 'olá mundo'; // resultado: 'olá mundo'
const b = a.split(' '); // resultado: ['hello', 'world']
```

## Comprimento da matriz

Cada array tem como propriedade 'estática' `length'. O que significa que podemos obter facilmente a quantidade de itens em uma matriz.

``` js
const f = ['oi', 'lá'];
console.log(f.comprimento); // 2
```

## Índice de matriz

Podemos acessar os elementos do array através da posição do elemento no array. Isso é chamado de índice. Índices (plural de índice) são baseados em 0, o que significa que o índice do primeiro item é 0, o segundo elemento é 1.

``` js
const x = ['primeiro', 'segundo', 'terceiro'];
console.log(x[0]); // 'primeiro'

x[3] = 'quarto';
```

Observe que os arrays podem ter valores vazios. Isso deve ser evitado geralmente para evitar comportamentos inesperados.

``` js
x[10] = 'décimo primeiro';
console.log(x); // [ 'primeiro', 'segundo', 'terceiro', 'quarto', <6 itens vazios>, 'décimo primeiro' ]
```

Ao lado do índice, temos uma ampla gama de ferramentas para manipular arrays.

## Métodos de matriz

Esses métodos são essenciais.

**Extremamente importante é lembrar de sempre fazer essas duas perguntas**:

- Qual é o valor de retorno deste método?
- O que esse método faz com o array original em que é usado?

**Adicionando itens**

- [`.push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) Adicionar item ao final do array.
  Exemplo:

``` js
const animais = ['porcos', 'cabras', 'ovelhas'];

// 1.Qual é o valor de retorno deste método?
// retorna o comprimento do novo array
console.log(animais.push('vacas'));
// saída esperada: 4

// 2. O que esse método faz com o array original em que é usado?
// modifica o array original - adiciona no final do array o(s) elemento(s) dado(s)
console.log(animais);
// saída esperada: Array ["porcos", "cabras", "ovelha", "vacas"]

// pode adicionar vários elementos em uma chamada
animais.push('galinhas', 'papagaio');

console.log(animais);
// saída esperada: Array ["porcos", "cabras", "ovelha", "vacas", "galinha", "papagaio"]
```

> _Veja isso em ação neste [JSBin](https://jsbin.com/lawovip/edit?js,console)._

- [`.unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) Adicionar item ao início do array.
  Exemplo:

``` js
const array1 = [1, 2, 3];

// 1.Qual é o valor de retorno deste método?
// retorna o comprimento do novo array
console.log(array1.unshift(4, 5));
// saída esperada: 5

// 2. O que esse método faz com o array original que é usado
// modifica o array original - adiciona no início do array o(s) elemento(s) dado(s)
console.log(array1);
// saída esperada: Array [4, 5, 1, 2, 3]
```

> _Veja isso em ação neste [JSBin](https://jsbin.com/pikupol/edit?js,console)._

**Removendo itens**

- [`.shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) Remova o primeiro elemento do array.
  Exemplo:

``` js
const array1 = [1, 2, 3];

const primeiroElemento = array1.shift();

// 1.Qual é o valor de retorno deste método?
// retorna o primeiro elemento do array
console.log(firstElement);
// saída esperada: 1

// 2. O que esse método faz com o array original que é usado
// modifica o array inicial - remove o primeiro elemento
console.log(array1);
// saída esperada: Array [2, 3]
```

> _Veja isso em ação neste [JSBin](https://jsbin.com/madaxuq/edit?js,console)._

- [`.pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) Remova o último elemento do array. Exemplo:

``` js
const plantas = ['brócolis', 'couve-flor', 'repolho', 'couve', 'tomate'];

// 1.Qual é o valor de retorno deste método?
// retorna o último elemento
console.log(plantas.pop());
// saída esperada: "tomate"

// 2. O que esse método faz com o array original que é usado
// modifica o array original - remove o último elemento do final do array
console.log(plantas);
// saída esperada: Array ["brócolis", "couve-flor", "repolho", "kale"]

plantas.pop();

console.log(plantas);
// saída esperada: Array ["brócolis", "couve-flor", "repolho"]
```

> _Veja isso em ação neste [JSBin](https://jsbin.com/nicazaf/edit?js,console)._

- [`.splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) Remova um elemento específico do array usando index.
  Exemplo:

``` js
const meses = ['Jan', 'Março', 'Abril', 'Junho'];

// 1.Qual é o valor de retorno deste método?
// retorna um array contendo os elementos removidos
console.log(meses.splice(1, 0, 'fev'));

// 2. O que esse método faz com o array original que é usado
// modifica o array original:

// insere na 1ª posição do índice
console.log(meses);
// saída esperada: Array ['Jan', 'Fev', 'Março', 'Abril', 'Junho']

console.log(meses.splice(4, 1, 'maio'));
// substitui 1 elemento no 4º índice
console.log(meses);
// saída esperada: Array ['Jan', 'Feb', 'March', 'April', 'May']
```

> _Veja isso em ação neste [JSBin](https://jsbin.com/yuriyer/edit?js,console)._

**Iteradores úteis sobre arrays**

- [`.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) cria um novo array com os resultados da chamada de uma função fornecida em cada elemento na matriz de chamada.
- [`.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) cria um novo array com todos os elementos que passam no teste implementado pela função fornecida.
- [`.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) classifica os elementos de um array no lugar e retorna o array

Exemplos detalhados: [`aqui`](https://github.com/HackYourFuture/fundamentals/blob/master/fundamentals/map_filter.md)
