# Entendendo os fundamentos do JavaScript

Ao falar sobre JavaScript, é importante que você use a terminologia correta. Dessa forma, se você falar sobre código com outras pessoas, elas entenderão o que você quer dizer sem qualquer ambiguidade.

## Variáveis

Uma "variável" é um local onde você pode armazenar informações, como uma string ou um número.

### Declaração de variável

As variáveis são "declaradas" usando as palavras-chave `let` e `const` (ou a antiga palavra-chave `var`):

``` js
seja x = 5;
```

Aqui, dizemos: "declare a variável x e inicialize-a com o número 5".

### Tipos de variáveis

Todas as variáveis têm um tipo. Em nosso exemplo acima, a variável `x` é um `number`. JavaScript suporta os seguintes tipos:

* `string`, por exemplo "HackYourFuture"
* `número`, por exemplo 5 ou 10,6
* `booleano`, por exemplo `verdadeiro` ou `falso`
* `matriz`\*, por exemplo `[1, 2, 3]` ou `['o que', 'é', 'seu', 'nome']`
* `objeto`, por exemplo `{name: 'John', age: 24}`, ou o objeto especial `null`
* `função`, por exemplo `função() { return 4; }`
* `símbolo`

Além disso, uma variável pode ser `indefinida`. Este também é um tipo especial.

Para obter o tipo de uma variável, use o seguinte código:

``` js
seja x = 5;
deixe typeOfX = typeof x; // -> "número"
```

Observe que coloquei um asterisco atrás de 'array'. Isso porque em JavaScript, array é um tipo especial de objeto:

``` js
deixe arr = [1, 2, 3];
deixe typeOfArr = typeof arr; // -> "objeto"
```

No entanto, em nossa comunicação, chamaremos essas variáveis de arrays.

### Nulo e indefinido

Os valores `null` e `undefined` são muito semelhantes em JavaScript, mas se comportam de forma um pouco diferente. A diferença é que `null` sempre tem o tipo "object", e `undefined` sempre tem o tipo "undefined".

Sempre que você declarar uma variável, mas não definir um valor, a variável se tornará `undefined`. JavaScript nunca tornará uma variável `null` a menos que você a programe explicitamente.

``` js
deixe x;
console.log(tipo de x); // -> "indefinido"
```


## Matrizes

Variáveis que são arrays contêm uma lista de coisas, em vez de apenas uma coisa. O que está dentro da matriz, normalmente chamamos de "elementos". Assim, o array `[1, 2, 3]` tem três elementos. A matriz `[]` não possui elementos e, portanto, está vazia. O número de elementos em uma matriz é chamado de "comprimento".

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



## Objetos

Variáveis que são objetos também contêm uma lista de coisas, mas ao invés de estarem em alguma ordem específica, elas podem ser atribuídas a palavras, chamadas "chaves". Em vez de "elementos", as coisas que estão dentro dos objetos são chamadas de "propriedades".


``` js
let obj = {nome: 'João', idade: 24};
```

Este objeto tem duas propriedades: `name` e `age`. O "valor" da propriedade `name` é a string `'John'`. O "valor" da propriedade `idade` é o número `24`.

Ao acessar as propriedades do objeto, você pode usar a notação de ponto: `obj.name` ou a notação de colchetes: `obj["name"]`. Observe que o último se parece muito com a maneira de acessar os elementos do array. No entanto, aqui o que está dentro do colchete (chamado "chave" para objetos, em vez de "índice") deve ser uma string.

``` js
console.log(obj.name); // -> 'João'
console.log(obj['nome']); // -> 'João'
```

Assim como com os arrays, você também pode usar uma variável para acessar as propriedades, desde que essas variáveis sejam strings. Neste caso, você não pode usar a notação de ponto!

``` js
deixe idadeKey = 'idade';
console.log(obj[ageKey]); // -> 24
```

Lembre-se que há uma grande diferença entre `obj[name]` e `obj["name"]`.

> Nota:
>
> Pensando em arrays, o comprimento de um array pode ser recuperado por `arr.length`. Então, como mencionado anteriormente, os arrays são como outros objetos JavaScript. Você pode até escrever `arr['length']` para acessar a propriedade `length` do array. JavaScript vai olhar: o que colocamos entre colchetes é um número? Então é um índice e procuraremos o elemento correto do array. Se for uma string, é uma chave e procuraremos a propriedade correspondente.


## Funções

Uma função é um pedaço de código reutilizável. As funções são *muito* importantes em JavaScript, na medida em que algumas pessoas chamam JavaScript de uma linguagem "orientada a funções". Como mencionado acima, as variáveis podem ser do tipo função. Na verdade, *toda função é uma variável*.

Os dois trechos de código a seguir têm exatamente o mesmo resultado:

``` js
função soma(a, b) {
  retornar a + b;
}
```

e

``` js
deixe soma = função (a, b) {
  retornar a + b;
}
```

> Nota
>
> Isso não é totalmente verdade, pois no segundo código, a função é "anônima", ou seja, não tem nome. Mas em ambos os casos, você pode chamar a função assim: `sum(4, 5)`.

### Parâmetros e argumentos

Ao escrever `função sum(a, b)`, `a` e `b` são os "parâmetros" da função. Dizemos que esta função tem dois parâmetros. (Às vezes, você verá a palavra "arity": esta função tem "arity" 2, mas isso é algo que você não precisa usar por enquanto.)

Agora, ao *chamar* a função soma, por exemplo `let s = sum(4, 5);`, dizemos que os números `4` e `5` são os "argumentos" da função. Os argumentos são "passados" para a função: "passamos `4` e `5` para a função `sum`".

Portanto, lembre-se da diferença entre a palavra "parâmetro" e "argumento". Muitas pessoas confundem, e isso não é um grande problema, mas entender a diferença é sempre bom:

* Um parâmetro é o nome que você deseja dar à variável que está disponível dentro da função.
* Um argumento é o valor real que você deseja atribuir aos parâmetros ao chamar a função.

Uma função que "tem dois parâmetros" também é chamada de "aceitar/aceitar dois argumentos". Mas, às vezes você vai ouvir as pessoas dizerem: "a função tem dois argumentos" ou "a função recebe dois parâmetros". Embora formalmente incorreto, você saberá o que eles significam.

### Chamando uma função em algo

Em JavaScript, você pode chamar funções *em* algo. Com isso, queremos dizer que você usa o ponto para chamar a função. Por exemplo, quando dizemos "chamar o método `trim` na string `s`", queremos dizer:

``` js
let s = "isso é uma string";
s.trim(); // -> "isto é uma string"
```

> Nota
>
> Tecnicamente, isso significa que a string `s` se tornará a variável especial `this` dentro da função.

No entanto, existem funções que você não chama em nada:

``` js
função soma(a, b) { return a + b; }
soma(4, 5); // -> 9
```

Aqui, você chama a função `sum` em nada.

A maioria das funções integradas em JavaScript, como funções matemáticas ou funções de registro, também usam o ponto:

``` js
Math.round(4.5);
console.log("Olá");
Array.from([1, 2, 3]);
```

Na verdade, essas funções também são chamadas de "on" `Math`, `console`, `Array` e assim por diante. No entanto, neste caso, seu objetivo é mais agrupá-los logicamente, então aqui não é muito importante usar essa terminologia. Preferimos dizer: "chamar a função `Math.round` com `4.5` como argumento", ou seja, incluímos no nome completo dos métodos.

É mais quando você pensa em quais funções você pode chamar "em" suas próprias variáveis (strings, arrays, números, etc):

``` js
minhaString.trim();
meuArray.fatia();
meuNúmero.toString();
...
```


## Declarações e expressões

A maioria das linguagens de programação que você encontrará na vida real são chamadas de linguagens de programação "imperativas". JavaScript é uma linguagem de programação tão imperativa. Imperativo é outra palavra para tipo de comando. Ou seja, você dá ao computador um monte de comandos um após o outro. Primeiro faça isso, depois faça aquilo, etc.

Esses comandos individuais são chamados de "instruções" em linguagens de programação imperativas. Você pode compará-los com frases no idioma inglês. Eles têm um uso por si mesmos e não precisam de outra coisa. "O homem come pão." é uma frase completa, ela transmite um significado por si só. Uma frase em inglês é sempre terminada por um ponto.

Da mesma forma, uma instrução em JavaScript deve fornecer um comando por si só. As instruções JavaScript são (quase sempre) terminadas por um ponto e vírgula.

Esta é uma declaração completa:

``` js
let s = "HackYourFuture";
```

É um comando completo: declare uma variável `s` e inicialize-a com `"HackYourFuture"`. JavaScript não precisa de nenhuma outra informação para saber o que queremos. A instrução é terminada com um ponto e vírgula.

No entanto, esta não é uma afirmação completa:

``` js
4 + 5
```

Isso é igual a `9`, mas o que o JavaScript tem a ver com isso? Não fornece um comando. Você precisaria fazer algo com ele, por exemplo. `let x = 4 + 5;` ou `callFunction(4 + 5)`. Chamamos essas partes de declarações de "expressões". As expressões não são terminadas por ponto e vírgula. As expressões sempre "avaliam em um valor". Em nosso exemplo, a expressão `4 + 5` "avalia em `9`". Se as expressões não puderem ser avaliadas em um valor, elas serão inválidas. Por exemplo, `4 +` não é uma expressão válida, está incompleta, porque precisamos de outra coisa depois do sinal de mais.

Assim, as declarações podem *conter* expressões. As expressões podem conter declarações? Não, eles não podem. No entanto, eles podem conter expressões. Pense em `4 + 5`: contém as expressões `4` e `5`, pois ambas são avaliadas em um valor: a expressão `4` é avaliada no número `4`, é uma expressão muito simples. Da mesma forma, `true`, `null`, `undefined` são todas expressões.

### Exemplos de expressões

Aqui estão alguns exemplos de expressões. Lembre-se: as expressões são avaliadas em um valor, mas não fornecem um comando:

* `soma (a, b)`
* `a`
* `a > 4 ? "sim": "não"`
* `a + b`
* `a && b || c`
* `arr.length`
* `obj["nome"]`
* `[1, 2, 3]`
* `arr[1]`
* `[1]` (este é um array com um elemento!)
* `função a() { return 4; }`

O último requer um pouco de explicação. Se você escrever:

``` js
função a() { return 4; }
```

por si só, esta é uma *instrução* (uma declaração de função). No entanto, se você escrevê-lo como parte de uma declaração, como:

``` js
deixe b = função a() { return 4; }
```

agora é uma expressão. Esta é uma situação excepcional onde algo pode ser uma afirmação ou uma expressão.

### Exemplos de não-expressões

Não são expressões:

* `let` -> esta é uma palavra-chave, veja abaixo
* `let x;` -> esta é uma declaração
* `+` -> este é apenas um operador
* `if (a > 4) { return "sim"; } else { return "não"; }`

`if` também é uma declaração. No entanto, é uma afirmação bastante complexa. Também é chamado de "construção", assim como `for`, `while`, `try`, etc.

### Palavras-chave

Algumas palavras em JavaScript são especiais, por exemplo. `var`, `if`, `while`, `return`. Estes são chamados de "palavras-chave". Você normalmente não pode usar essas palavras como nomes para suas variáveis, funções.