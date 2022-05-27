# Convenções de nomenclatura

## Fundo

Na programação, você precisará criar nomes apropriados para suas variáveis, funções e parâmetros de função.

> _A consideração mais importante ao nomear uma variável é que o nome descreva completa e precisamente a entidade que a variável representa. Uma técnica eficaz para criar um bom nome é declarar em palavras o que a variável representa. Muitas vezes, essa declaração em si é o melhor nome de variável. É fácil de ler porque não contém abreviações enigmáticas e é inequívoco. Porque é uma descrição completa do
entidade, não será confundido com outra coisa. E é fácil de lembrar porque o nome é semelhante ao conceito._

> Fonte: [Code Complete 2, Steve McConnell](https://www.amazon.de/Code-Complete-Practical-Construction-Costruction/dp/0735619670)

Os nomes que você escolhe são para o benefício do consumidor humano do seu código. Acima de tudo, esse consumidor humano será você mesmo: ao escrever o código, nomes cuidadosamente escolhidos o ajudam a manter o foco no problema de negócios que você está tentando resolver. Quando surgir a necessidade de revisitar seu código no futuro, nomes cuidadosamente escolhidos o ajudarão a reconstruir seu estado de espírito no momento em que você escreveu o código originalmente.

Na prática, seu código pode precisar ser mantido por outras pessoas, à medida que você avança para outros projetos ou trabalhos. Para os desenvolvedores que fazem manutenção, é ainda mais importante usar nomes cuidadosamente escolhidos, pois eles não têm o benefício de ter passado por seus processos de pensamento.

O consumidor menos interessado nos nomes que você escolhe é o ambiente de tempo de execução (ou seja, o mecanismo JavaScript em seu navegador ou Node). O ambiente de tempo de execução não se importa com nomes de variáveis de uma letra sem sentido. Na verdade, um processo chamado 'minificação' às vezes é usado para criar uma versão minificada de seu código JavaScript para execução no navegador, cujo objetivo é acelerar a busca de seu código pela Internet.

## camelCase vs PascalCase vs snake_case vs kebab-case

Esses termos são usados para descrever as convenções para a ortografia de nomes de variáveis (e funções) com várias palavras.

### camelCase

Em JavaScript, a convenção é soletrar os nomes das variáveis que contêm dados usando _camelCase_, ou seja, a primeira palavra no nome da variável deve começar com uma letra minúscula e cada palavra subsequente com uma letra maiúscula. Chama-se _camelCase_ porque a corcova no meio da palavra tem alguma semelhança com a corcova de um camelo.

Exemplo:

``` js
deixe meusFilmes Favoritos;
```

### PascalCase

Essa caixa é restrita em JavaScript a nomes de classes e funções construtoras. Esse estilo de caixa era habitual na linguagem de programação Pascal.

Exemplo:

``` js
classe Filme {
  ...
}
```

### snake_case

Essa caixa geralmente não é usada em JavaScript, exceto para nomear constantes globais. Neste caso, o nome da variável deve estar completamente em maiúsculas.

``` js
const MAX_IDADE = 60;
```

### caixa de kebab

Essa caixa é usada para nomes de classes em CSS e às vezes para nomes de arquivos em JavaScript.



``` css
.título da página {
  cor: #ff23be.
}
```

```html
<h1 class="page-title">Lindo título</h1>
```

``` js
const fileName = 'movie-collection.js';
```


## Nomes de variáveis para dados

As variáveis que contêm dados devem ser nomeadas usando frases nominais, ou seja, ter um substantivo como palavra principal. O nome deve estar em camelCase. Exemplo:

``` js
deixe meuFilme Favorito;
```

Se os dados consistem em um único item, o substantivo deve estar na forma singular, como no exemplo acima. Se os dados consistirem em uma coleção, como uma matriz JavaScript ou um objeto JavaScript que é usado como uma coleção com chave, uma forma plural deve ser usada:

``` js
deixe meusFilmes Favoritos;
```

Às vezes, um substantivo de massa é usado como palavra principal em vez de uma forma plural explícita para nomear uma coleção. Exemplos de substantivos de massa são `data`, `input`, `money`.

## Nomes de funções

Nomes de funções (exceção: funções construtoras, veja abaixo) geralmente devem começar com um verbo para indicar a _ação_ executada pela função. O nome deve estar em camelCase. Exemplo:

``` js
function buscarFilme() {
  ...
}
```

## Funções construtoras e nomes de classes

A convenção de nomenclatura para funções construtoras, ou seja, funções que são usadas em conjunto com a palavra-chave `new` e nomes de classe ES6 é usar uma frase nominal em PascalCase. Exemplo:

``` js
classe Filme {
  ...
}
```

## Palavras-chave reservadas

Certos nomes são reservados pelo JavaScript para seu próprio uso. Você não pode usar os nomes para sua variável. Por exemplo, você não pode nomear uma variável como `if`.

Para obter uma lista completa de nomes reservados, consulte a página MDN para [Palavras-chave](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).




