# Variáveis

Uma "variável" é um local onde você pode armazenar informações, como uma string ou um número. Uma variável tem um _name_ (que você escolhe) e um _value_. Novas variáveis em JavaScript são declaradas usando uma das três palavras-chave: `let`, `const` ou `var`.

> Pense em nomes de variáveis como **rótulos** nas caixas, enquanto o valor da variável é o **conteúdo** da caixa - você pode alterar o conteúdo de uma caixa e deixar o rótulo intacto, o conteúdo das caixas podem ter tipos diferentes, as caixas devem ter boas etiquetas (uma caixa de livros com canetas seria muito confusa),
>
![Variáveis são como caixas](./assets/box.png)
> Foto da [Khan Academy](http://cs-blog.khanacademy.org/2013/09/teaching-variables-analogies-and.html)


## Declaração de variável

As variáveis são "declaradas" usando a palavra-chave `var`, `let` ou `const`. No exemplo a seguir, três variáveis são declaradas com os nomes `x`, `foo` e `bar`.

``` js
var x;
deixe foo;
barra const;
```

Observe que os nomes escolhidos neste exemplo não têm sentido (talvez com exceção de `x`, por exemplo, como parte de um programa matemático). Você deve fazer um esforço para sempre escolher nomes que melhor descrevam o que você pretende que essa variável mantenha.

## var

Antes do JavaScript ES6, a palavra-chave `var` era a única maneira de declarar uma variável. O ES6 introduziu duas novas palavras-chave, `let` e `const` para declarar variáveis. Eles melhoram como a antiga declaração `var` funciona (isso envolve o conceito de "escopo" que você aprenderá na terceira aula). No HackYourFuture nós encorajamos você a usar as palavras-chave mais modernas `let` e `const` em vez de `var`, mas muitas vezes você encontrará `var` em livros existentes, bibliotecas de software e exemplos na Internet, então você deve entender `var ` também.

## let e const
- leia sobre [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- leia sobre [const](https://developer.mozilla.org/nl/docs/Web/JavaScript/Reference/Statements/const)
- [let vs const] (http://wesbos.com/let-vs-const/)

Aqui, dizemos: "declare a variável x e inicialize-a com o inteiro (número) 6".

``` js
deixe foo; // declara a variável `foo`
```

``` js
deixe fo = 6; // declara e atribui uma variável ao mesmo tempo
```

Você também pode atribuir um valor a uma variável existente:
``` js
fo = 4; // muda a variável `foo`
```

