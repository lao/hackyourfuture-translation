# Objetos

Variáveis que são objetos também contêm uma lista de coisas, mas ao invés de estarem em alguma ordem específica, elas podem ser atribuídas a palavras, chamadas "chaves". Em vez de "elementos", as coisas que estão dentro dos objetos são chamadas de "propriedades".


``` js
let obj = {nome: 'João', idade: 24};
```

Este objeto tem duas propriedades: `name` e `age`. O "valor" da propriedade `name` é a string `'John'`. O "valor" da propriedade `age` é o número `24`.

Ao acessar as propriedades do objeto, você pode usar a notação de ponto: `obj.name` ou a notação de colchetes: `obj["name"]`. Observe que o último se parece muito com a maneira de acessar os elementos do array. No entanto, aqui o que está dentro do colchete (chamado "chave" para objetos, em vez de "índice") deve ser uma string.

``` js
console.log(obj.name); // -> 'João'
console.log(obj['nome']); // -> 'João'
```

Assim como com os arrays, você também pode usar uma variável para acessar as propriedades, desde que essas variáveis sejam strings. Neste caso, você não pode usar a notação de ponto!

``` js
const idadeKey = 'idade';
console.log(obj[ageKey]); // -> 24
```

Lembre-se que há uma grande diferença entre `obj[name]` e `obj["name"]`.

> Nota:
>
> Pensando em arrays, o comprimento de um array pode ser recuperado por `arr.length`. Então, como mencionado anteriormente, os arrays são como outros objetos JavaScript. Você pode até escrever `arr['length']` para acessar a propriedade `length` do array. JavaScript vai olhar: o que colocamos entre colchetes é um número? Então é um índice e procuraremos o elemento correto do array. Se for uma string, é uma chave e procuraremos a propriedade correspondente.
