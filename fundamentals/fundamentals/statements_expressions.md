# Declarações e expressões

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

## Exemplos de expressões

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

## Exemplos de não-expressões

Não são expressões:

* `let` -> esta é uma palavra-chave, veja abaixo
* `let x;` -> esta é uma declaração
* `+` -> este é apenas um operador
* `if (a > 4) { return "sim"; } else { return "não"; }`

`if` também é uma declaração. No entanto, é uma afirmação bastante complexa. Também é chamado de "construção", assim como `for`, `while`, `try`, etc.

