# Funções

Considere esta **função** de [matemática do ensino médio](https://www.mathplanet.com/education/algebra-2/how-to-graph-functions-and-linear-equations/functions-and-linear -equações):

> 𝑓(x) = x + 7
>
> _se x = 2 então_
>
> 𝑓(2) = 2 + 7 = 9

O valor da função 𝑓(x) depende do valor que você fornece para seu argumento x. (Em vez do termo 'argumento', às vezes a palavra 'parâmetro' é usada).

Aqui está a função JavaScript equivalente:

``` js
//definição da função
função f(x) {
    retorna x + 7;
}

// chama a função e registra seu valor para x = 2
console.log(f(2)); // -> 9
```

Esta função adiciona 7 ao valor de seu argumento. Sempre que precisarmos adicionar 7 a algum número, podemos reutilizar essa mesma função várias vezes.

Durante a execução, o valor de x no corpo da função (a parte entre as chaves) é substituído pelo valor 'passado' durante a chamada da função.

Uma função, portanto, é um pedaço de código reutilizável (veja _Por que usar funções_ abaixo). As funções são *muito* importantes em JavaScript, na medida em que algumas pessoas chamam JavaScript de uma linguagem "orientada a funções". Como mencionado acima, as variáveis podem ser do tipo função. Na verdade, *toda função é uma variável*.

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

## Parâmetros e argumentos

Ao escrever `função sum(a, b)`, `a` e `b` são os "parâmetros" da função. Dizemos que esta função tem dois parâmetros. (Às vezes, você verá a palavra "arity": esta função tem "arity" 2, mas isso é algo que você não precisa usar por enquanto.)

Agora, ao *chamar* a função soma, por exemplo `let s = sum(4, 5);`, dizemos que os números `4` e `5` são os "argumentos" da função. Os argumentos são "passados" para a função: "passamos `4` e `5` para a função `sum`".

Portanto, lembre-se da diferença entre a palavra "parâmetro" e "argumento". Muitas pessoas confundem, e isso não é um grande problema, mas entender a diferença é sempre bom:

* Um parâmetro é o nome que você deseja dar à variável que está disponível dentro da função.
* Um argumento é o valor real que você deseja atribuir aos parâmetros ao chamar a função.

Uma função que "tem dois parâmetros" também é chamada de "aceitar/aceitar dois argumentos". Mas, às vezes você vai ouvir as pessoas dizerem: "a função tem dois argumentos" ou "a função recebe dois parâmetros". Embora formalmente incorreto, você saberá o que eles significam.

## Chamando uma função em algo

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

## Por que usar funções?

> O seguinte foi adaptado de https://www.cs.utah.edu/~zachary/computing/lessons/uces-10/uces-10/node11.html

A primeira razão é a **reutilização**. Uma vez que uma função é definida, ela pode ser usada repetidamente. Você pode invocar a mesma função muitas vezes em seu programa, o que economiza seu trabalho.

Outro aspecto da reutilização é que uma única função pode ser usada em vários programas diferentes (e separados). Quando você precisa escrever um novo programa, você pode voltar aos seus programas antigos, encontrar as funções que você precisa e reutilizá-las em seu novo programa. Você também pode reutilizar funções que outra pessoa escreveu para você.

A segunda razão é a **abstração**. Para usar uma função específica, você precisa saber o seguinte:

1. O nome da função;
2. O que a função faz;
3. Quais argumentos você deve dar à função; e
4. Que tipo de resultado a função retorna.

Mas observe: se você quer apenas usar a função em seu programa, não precisa saber como ela funciona por dentro! Você não precisa entender nada sobre o que acontece dentro da função.

É como dirigir um carro ou usar um telefone. Com um automóvel, você não precisa entender todos os detalhes sobre o motor, trem de força e rodas, se tudo o que você quer fazer é dirigir o carro. Da mesma forma, com um telefone, você não precisa entender tudo sobre o sistema telefônico para fazer uma chamada.

A única vez que você precisa saber como uma função funciona internamente é quando você precisa escrever a função ou alterar como ela funciona. (É como um carro novamente; você precisa saber como um carro funciona para construir um ou consertar um.) Mas uma vez que uma função está escrita e funcionando, você nunca mais precisa olhar para dentro dela.

Juntas, essas duas razões tornam as funções extremamente úteis - praticamente essenciais! - para programadores que escrevem programas grandes. A capacidade de dividir um programa em partes abstratas e reutilizáveis é o que torna possível escrever grandes programas que realmente funcionam corretamente.