# Operadores

## Operadores de comparação

>Observe os dois usos diferentes do sinal de igual:
>Um único sinal de igual (=) é usado para atribuir um valor a uma variável.
Um sinal de igual triplo (===) é usado para comparar dois valores (consulte Operadores de igualdade).

### Operadores de igualdade

* Igualdade `==`
* Desigualdade `!=`
* Identidade / igualdade estrita `===` (preferencial)
* Não identidade / desigualdade estrita `!==` (preferencial)

Como isso funciona na prática?

``` js
1 == 1 // -> verdadeiro
7 == '7' // -> verdadeiro
1 != 2 // -> verdadeiro
5 === 5 // -> verdadeiro
9 === '9' // -> falso
3 !== 3 // -> falso
3 !== '3' // -> verdadeiro
```

> por que `7 == '7'` retorna verdadeiro e `9 === '9'` retorna falso?

É altamente recomendável que você sempre use a forma estrita ao comparar para igualdade (`===`) ou desigualdade (`!==`). Use os formulários não estritos apenas quando houver uma razão convincente para fazê-lo (você terá dificuldade em encontrar tal razão).

### Operadores relacionais

* Maior que o operador `>`
* Operador maior ou igual `>=`
* Operador menor que `<`
* Operador menor ou igual `<=`

``` js
4 > 3 // -> verdadeiro
3 >= 3 // -> verdadeiro
13 < 12 // -> falso
3 <= 4 // -> verdadeiro
```

Mais sobre [operadores de comparação](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

## Operadores aritméticos

* Adição `+`
* Subtração `-`
* Multiplicação `*`
* Divisão `/`
* Restante (às vezes chamado de módulo) `%`
<br>Retorna o restante que sobrou depois que você compartilhou o número da esquerda em um número de partes inteiras iguais ao número da direita.

``` js
8 + 9 // -> 17, soma dois números.
20 - 12 // -> 8, subtrai o número direito do esquerdo.
3 * 4 // -> 12, multiplica dois números juntos.
10 / 5 // -> 2, divide o número esquerdo pelo direito.
8 % 3 /// -> 2, pois três entra em 8 duas vezes, deixando 2 sobrando.
```

Mais sobre [operadores aritméticos](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#.25_.28Modulus.29)

## Operadores lógicos

* E `&&`
* OU `||`

``` js
verdadeiro && falso //-> falso
false && true //-> false
falso || verdadeiro //-> verdadeiro
verdadeiro || falso //-> verdadeiro
```

Dado que x = 6 e y = 3
``` js
x < 10 && y > 1 // -> verdadeiro
x === 5 || y === 5 // -> falso
x !== y // -> verdadeiro
```

NÃO Lógico

* NÃO `!`

``` js
verdadeiro === !falso
falso === !verdadeiro
```

Mais sobre [operadores lógicos](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)

### tipo de operador

Para obter o tipo de um valor atribuído a uma variável, use o seguinte código:

``` js
deixe barra = 42;
typeof bar //-> 'number'
tipo de barra; //-> 'cadeia'
```

Portanto, o tipo de dados que `typeof` retorna é sempre uma string, bar, por outro lado, ainda é um número.

## Operadores de atribuição

Além do operador de atribuição simples `=`, existem também operadores de atribuição compostos, como `+=`. As duas atribuições a seguir são equivalentes:

``` js
x += 1;
x = x + 1;
```

|Operador| Exemplo| Igual a|
|:------:|:--------:|:-------:|
|`=` | `x = y` | `x = y`|
|`+=`| `x += y` | `x = x + y`|
|`-=`| `x -= y` | `x = x - y`|
|`*=`| `x *= y` | `x = x * y`|
|`/=`| `x /= y` | `x = x / y`|
|`%=`| `x %= y` | `x = x %y`|

Confira também [caracteres especiais e seus nomes](names_of_special_characters.md)
