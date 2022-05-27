# Fundamentos de JavaScript - exercícios

### Dado o seguinte código:

``` js
let s = "Olá";
deixe x = s.toLowerCase();
deixe l = s.comprimento;
```

**1. Quais são os tipos de:**

1. `s`
2. `x`
3. `s.toLowerCase()`
4. `s.toLowerCase`
5. `s.comprimento`
6. `l`

----

### 2. Em `let x = 5 + 6;`, o que é `+`?

1. Função
2. Operador
3. Número
4. Agregador

----

### 3. Em `let x = 5 + 6;`, o que é `let`?

1. Variável
2. Palavra-chave
3. Operador
4. Constante

----

### Dado o seguinte código:

``` js
seja x = z[y];
```

**4. O que é "s"?**

1. Índice
2. Chave
3. Índice ou chave
4. Matriz

----

### Dado o seguinte código:

``` js
seja y = 1;
seja x = [1, 2, 3];
seja z = x[y];
```

**5. O que é "s"?**

1. Índice
2. Chave
3. Índice ou chave
4. Matriz

----

### Dado o seguinte código:

``` js
deixe joe = {
  nome: 'João',
  idade: 24
};
deixe joesName = joe.name;
let joesIdade = joe['idade'];
```

**6. O que é "idade" na última linha?**

1. Índice
2. Chave
3. Matriz
4. Objeto

**7. O que são `name` e `age` do objeto `joe`?**

1. Índice
2. Chave
3. Objeto
4. Propriedade

----

### Dado o seguinte código:

``` js
deixe y = 'comprimento';
seja x = [1, 2, 3];
seja z = x[y];
```

**7. O que é `s`**

1. Índice
2. Chave
3. Índice ou chave
4. Matriz

**8. Qual é o elemento para o índice `1` no array `x`?**

**9. Preencha: "O valor do (...) `comprimento` de `x` é (...)"**

----

### 10. Qual é o nome dessas funções?

1. `função a() { return true; }`
2. `deixe a = function b() { return true; }`
3. `let c = function () { return true; }`

----

### 11. Escreva uma função que tenha dois parâmetros chamados `first` e `second`

----

### 12. Escreva uma chamada de função que passe três argumentos.

----

### 13. Escreva o código para o seguinte

1. Declare uma variável chamada `x` e inicialize-a com a string "Hello".
2. Declare uma variável chamada `y` e inicialize-a com a propriedade `length` de `x`.
3. Declare uma variável chamada `z` e inicialize-a com o resultado da chamada do método `toUpperCase` em `x`
4. Declare uma função chamada `myFunction`. Essa função deve receber dois argumentos e deve chamar o segundo argumento com o primeiro argumento como seu argumento. Então, declare uma variável chamada `f` e inicialize-a com uma função anônima vazia, e chame `myFunction` com os argumentos `10` e `f`.

----

### 14. Explique o mais precisamente possível (em inglês) o que o código a seguir faz, linha por linha

(Dica: deve se parecer com os itens da pergunta anterior!)

``` js
let s = "HackYourFuture";
let i = s.indexOf("Seu");
função soma(a, b) { return a + b; }
deixe s = soma(4, 5);
deixe r = Math.sqrt(s);
```

----

### 15. Indique para cada uma delas se é uma expressão ou uma declaração:

1. `l`
2. `l = 4;`
3. `l == 4`
4. `if (l == 4) { console.log("sim"); }`
E. `console.log("sim");`
F. `"sim"`
G. `console.log(l == 4 ? "sim" : "não")`
H. `função a() { return 4; }`
I. `deixe a = function () { return 4; }`

----

### 16. Como você pode dizer se algo é uma afirmação?

----

### 17. Como você pode dizer se algo é uma expressão

----

### Dado o seguinte código:

``` js
let s = "Olá".toLowerCase();
deixe l = s.comprimento;

função soma(a, b) {
  retornar a + b;
}
deixe max = função (a, b) {
  retorna a > b ? a: b;
}

deixe s1 = soma(4, 5);
seja s2 = 4 + 5;

if (s2 == s1) {
  console.log("mesmo");
} senão {
  console.log("não é o mesmo");
}
```

**18. Liste todas as 11 *instruções* no código acima**

**19. Liste todas as 28 *expressões* no código acima (BÔNUS!)**
