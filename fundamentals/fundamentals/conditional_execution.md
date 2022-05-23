# Execução condicional

A ordem normal de execução das instruções em um programa de computador é em linha reta, de cima para baixo. No entanto, às vezes é desejável executar uma ou mais instruções _condicionalmente_, ou seja, dependendo se alguma condição – determinada pelo estado do seu programa – for verdadeira.

## A instrução `if`

Em sua forma mais simples, a instrução `if` se parece com isso:

``` js
se (condição) {
    // uma ou mais instruções que serão executadas
    // se, e somente se a condição for verdadeira
}
```

Aqui, `condition` é uma expressão booleana que resolve para `true` ou `false` (ou, mais precisamente, qualquer expressão que seja 'truthy' ou 'falsy', como será explicado mais tarde).

As instruções dentro das chaves `{` e `}` serão executadas se a condição for verdadeira, caso contrário, essas instruções serão ignoradas (ou seja, ignoradas).

Um exemplo:

``` js
if (distância < 10) {
    console.log('Vou levar a bicicleta.');
}
```

Aqui, a condição é a expressão booleana `distance > 10`, que é `true` ou `false`.

Também é possível adicionar um bloco de instruções a ser executado se (e somente se) a condição **não** for verdadeira, usando uma cláusula `else`.

``` js
if (distância < 10) {
    console.log('Vou levar a bicicleta.');
} senão {
    console.log('Vou de carro.');
}
```

Uma condição pode assumir formas mais complexas, usando os operadores `&&` (AND lógico) e `||` (OR lógico):

``` js
if (distância < 10 && !chovendo) {
    console.log('Vou levar a bicicleta.');
} senão {
    console.log('Vou de carro.');
}
```

No exemplo acima `raining` é uma variável booleana (tanto `true` quanto `false`), e o ponto de exclamação é o operador lógico NOT que nega o valor booleano (se for `true` o resultado após a negação é false e vice-versa).

Para decisões mais complexas, você pode concatenar várias condições usando cláusulas `else if`.

``` js
if (distância < 1) {
    console.log('Eu vou andar.');
} else if (distância < 10) {
    console.log('Vou levar a bicicleta.');
} else if (distância < 50) {
    console.log('Vou de carro.');
} senão {
    console.log('Vou pegar o trem.');
}
```

O bloco de instrução dentro de um `if`, `else` ou `else if` pode conter instruções `if` aninhadas, como neste exemplo:

``` js
if (distância < 10) {
    se (chovendo) {
        console.log('Eu irei de transporte público.');
    } senão {
        console.log('Eu vou andar.');
    }
} senão {
    console.log('Vou de carro.');
}
```

> Como as instruções `if` (aninhadas) podem se tornar bastante complexas, é muito importante que você indente seu código-fonte para que não haja confusão sobre quais blocos de instruções são executados para cada condição, como foi feito nos exemplos.

>Mais informações sobre MDN: [if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

## O operador condicional (ternário)

Este operador pode ser usado como um atalho para uma instrução `if` ao lidar com expressões.

O formato geral é:

``` js
doença ? exp1: exp2
```

('ternário' significa: _composto de três partes_)

É frequentemente usado em combinação com uma atribuição, como neste exemplo:

``` js
const conditionOfCar = idade < 1 ? 'novo': 'usado';
```

A variável `conditionOfCar` receberá a string `'new'` se a condição `age < 1` for verdadeira, caso contrário, será atribuída a string `'used'`.

É sempre possível reescrever um operador ternário como uma instrução `if-then-else`, por exemplo:

``` js
deixe condiçãoDeCarro;
if (idade < 1) {
  condiçãoDeCarro = 'novo';
} senão {
  condiçãoDeCarro = 'usado';
}
```

Observe que você não pode usar `const` aqui para `conditionOfCar` porque não podemos combinar declaração e inicialização em uma única instrução. Portanto, agora devemos usar `let`.

**Não** é recomendado usar o operador condicional se você não pretende usar seu valor:

``` js
// Não faça isso: é um código nojento
idade < 1? console.log('novo'): console.log('usado');
```

>Mais informações sobre MDN: [Operador condicional (ternário)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

## A instrução switch

A instrução `switch` às vezes pode ser uma alternativa útil para uma concatenação de instruções `if`. Este é o caso quando a condição é uma expressão que pode ser decomposta em vários valores distintos ou _cases_, conforme mostrado no exemplo abaixo.

``` js
const hyfModule = 'JavaScript-1';

switch (hyfModule) {
  caso 'HTML/CSS':
    console.log('Neste módulo você aprenderá HTML e CSS.');
    pausa;
  case 'JavaScript-1':
    console.log('Neste módulo você aprenderá o básico sobre Git e JavaScript.');
    pausa;
  case 'JavaScript-2':
    console.log('Neste módulo você aprenderá sobre JavaScript no navegador com HTML e CSS.');
    pausa;
  case 'JavaScript-3':
    console.log('Neste módulo você aprenderá sobre chamadas Async e API.');
    pausa;
  caso 'Nó':
    console.log('Este módulo trata da construção de aplicativos de servidor e CLI usando Node.');
    pausa;
  caso 'Banco de dados':
    console.log('Neste módulo é sobre Dados Relacionais e Não Relacionais e Sistemas de Banco de Dados.');
    pausa;
  caso 'Reagir':
    console.log('Neste módulo você irá construir aplicações de página única usando React.');
    pausa;
  caso 'Projeto':
    console.log('Neste módulo final você fará seu projeto de graduação.');
    pausa;
  predefinição:
    console.log('Este módulo é desconhecido: ' + hyfModule);
}}
```

Dependendo do valor da expressão especificada na cláusula `switch`, um dos blocos de instrução `case` é executado. Cada bloco de instrução deve terminar com uma instrução `break` para garantir que um `case` não 'caia' no próximo `case`.

A instrução `default` no final é executada quando nenhum dos casos anteriores for verdadeiro. A instrução `default` não é estritamente necessária, mas é uma prática recomendada sempre especificar uma.

>Mais informações sobre MDN: [switch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch)

## verdadeiro, falso

**verdadeiro**: 'mais ou menos' 'verdadeiro'
**falso**: 'mais ou menos' 'falso'

Do MDN:

Em JavaScript, um valor **truthy** é um valor considerado verdadeiro quando avaliado em um contexto booleano. Todos os valores são verdadeiros, a menos que sejam definidos como **falsos**.

Os valores **falsos** são:

- `falso`
- `0`
- `""`
- `null`
- `indefinido`
- `NaN`

O exemplo abaixo imprimirá `x is undefined` porque `undefined` é **falsy**.

``` js
deixe x;
se (x) {
    console.log('x está definido');
} senão {
  console.log('x é indefinido');
}
```

>Mais informações sobre MDN: [Truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy), [Falsy](https://developer.mozilla.org/en-US/docs /Glossário/Falso)