# Material de leitura JavaScript2 Semana 3

## Agenda

Estes são os tópicos da semana 3:

1. Escopo
   - Global vs. local (função e bloco)
   - Const e deixe
2. Içamento
   - Quando acontece o içamento?
3. Fechamentos
   - Contexto de execução
   - Por que precisamos de fechamentos?
4. Pensando como um programador II

## 0. Vídeo-aulas

Seu professor Wilgert fez palestras em vídeo para o material desta semana. Você pode encontrá-los aqui: [Vídeos 22 - 30](https://www.youtube.com/playlist?list=PLVYDhqbgYpYU-7_oyPBkUuuis5bL1Dk8n)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYU-7_oyPBkUuuis5bL1Dk8n" target="_blank"><img src="../assets/wilgert.png" width="600" height= "350" alt="HYF Video" /></a>

## 1. Escopo

Um dos conceitos centrais na programação é a ideia de `contexto`: o significado de qualquer coisa em particular só é determinado em relação ao seu entorno direto. Tomemos a linguagem, por exemplo. Se eu disser a seguinte frase:

> Eu nunca disse que ela roubou meu dinheiro.

Lendo isso, não é óbvio como interpretar do que se trata a situação. Dependendo da ênfase das palavras, pode significar qualquer um dos seguintes:

- _Eu_ nunca disse que ela roubou meu dinheiro.
- Eu _nunca_ disse que ela roubou meu dinheiro.
- Eu nunca _disse_ que ela roubou meu dinheiro.
- Eu nunca disse que _ela_ roubou meu dinheiro.
- Eu nunca disse que ela _roubou_ meu dinheiro.
- Eu nunca disse que ela roubou _meu_ dinheiro.
- Eu nunca disse que ela roubou meu _dinheiro_.

Depende do `contexto` para eu saber o que realmente aconteceu.

Vamos traçar a linha para a programação. Simplificando, assim como o contexto dá significado a uma palavra, `scope` dá significado a uma variável/objeto.

Esse significado é definido se a variável é acessível ou não. Se a variável não estiver dentro do "escopo" de um determinado bloco de código, ela não poderá acessá-lo. O que significa que não existe da perspectiva desse bloco de código.

Isso é realmente uma coisa boa: queremos garantir que partes de nossos dados tenham acessibilidade limitada. Imagine que a senha da sua conta de e-mail estaria disponível em todos os lugares, e você poderia facilmente acessá-la escrevendo algum código no console do seu navegador. Você sabe como seria fácil invadir sua conta?

Para mais pesquisas, confira o seguinte:

- [Escopo e contexto da variável](https://www.youtube.com/watch?v=WPcW83BMT3Y)

### Global vs. local (função e bloco)

O escopo pode ser dividido em dois tipos básicos: escopo global e local. Em qualquer aplicativo, há um escopo global. Mas pode haver muitos escopos locais. Qualquer variável declarada fora de uma função pertence ao escopo global e, portanto, é acessível de qualquer lugar no código. Variáveis declaradas dentro de um escopo local são acessíveis somente dentro desse escopo.

O escopo local pode ser dividido em duas categorias: função e bloco. Vejamos primeiro o **escopo da função**.

Um escopo local exclusivo é criado sempre que uma função é declarada. As variáveis declaradas dentro só serão acessíveis dentro desse escopo, em nenhum outro lugar. Isso torna possível declarar variáveis dentro do mesmo nome em cada escopo local diferente. Isso também significa que não é possível fazer referência a uma variável declarada em um escopo local, dentro de outro escopo local.

``` js
função criarLocalScope() {
  const localVariable = 'esta variável só pode ser acessada dentro desta função';
  console.log(localVariable);

  const localOnlyHere = 'Esta variável só pode ser acessada aqui, em nenhum outro lugar';
}

function createAnotherLocalScope() {
  const localVariável =
    "Mesmo que esta variável tenha o mesmo nome, ela não tem nada a ver com a outra localVariable, pois não existe fora dessa função";
  console.log(localVariable);
  console.log(localOnlyHere);
}

criarLocalScope();
createAnotherLocalScope();
```

No entanto, variáveis declaradas dentro do escopo global podem ser acessadas em qualquer lugar! Na verdade, esse é o propósito do escopo global. No contexto de funções, isso significa que você não precisa passá-lo como um argumento, mas pode se referir diretamente a ele dentro da função.

``` js
const globalVariable = 'Esta variável pode ser acessada em qualquer lugar do código';

function accessGlobalVariable() {
  console.log(globalVariable);
}
console.log(globalVariable);
accessGlobalVariable();
```

O segundo tipo de escopo local é chamado de **escopo de bloco**. Um bloco, geralmente falando, é qualquer código dentro de `{ }`. Isso inclui instruções condicionais (`if` e `switch`) e loops (`for`, `while` e `do/while`).

Consulte os seguintes recursos para saber mais sobre `scope`:

- [JavaScript: introdução ao escopo (escopo da função, escopo do bloco)](https://dev.to/sandy8111112004/javascript-introduction-to-scope-function-scope-block-scope-d11)
- [Entendendo o escopo em JavaScript](https://www.youtube.com/watch?v=SBjf9-WpLac)
- [Tudo o que você queria saber sobre o escopo do JavaScript](https://ultimatecourses.com/blog/everything-you-wanted-to-know-about-javascript-scope)

### Const e deixe

Como mencionado no módulo anterior, preferimos declarar variáveis usando `const` e `let`. Isso ocorre porque as palavras-chave são mais descritivas e restritivas. Isso os torna mais fáceis de trabalhar.

Em relação ao escopo, ambos também se comportam de forma diferente: eles têm escopo de bloco. Isso significa que eles podem ser acessados de fora de um `{ }`.

Acesse os seguintes recursos para saber mais sobre isso:

- [Como let e const são definidos em JavaScript](https://wesbos.com/javascript-scoping/)
- [Você realmente nunca deve usar var?](https://dev.to/johnwolfe820/should-you-never-truly-use-var-bdi)

## 2. Içamento

Se você procurar o termo "içamento" em qualquer dicionário, encontrará algo assim:

> "Levantar [algo] por meio de cordas e polias"

Um exemplo simples de hasteamento é o hasteamento de uma bandeira em um mastro. Você puxa a corda e lenta mas seguramente a bandeira é levantada.

Em JavaScript, a elevação refere-se ao mecanismo do compilador JavaScript do navegador para trazer cada função e declaração de variável para o topo de seu `escopo`, antes de começar a executar qualquer coisa. Isso pode ser de escopo global ou local, dependendo de onde está definido.

No entanto, isso NÃO significa que o valor real dado à variável ou função também será elevado. É apenas a declaração: que existem variáveis/funções que existem com esse nome.

### Quando acontece o içamento?

O içamento acontece durante o `tempo de compilação`.

Quando você executa seu código JavaScript, o interpretador passa pelo código duas vezes. A primeira vez é chamada de `compile-time`, que é quando seu código está pronto para ser executado: haverá verificações de segurança, pequenas otimizações e certificando-se de que a sintaxe está escrita corretamente.

A segunda vez é chamada de `run-time`, que é onde ele realmente executa seu código passando por ele linha por linha, fazendo as atribuições, chamando as funções, etc.

Para mais pesquisas, confira o seguinte:

- [O que é içamento em JavaScript?](https://medium.com/javascript-in-plain-english/https-medium-com-javascript-in-plain-english-what-is-hoisting-in-javascript- a63c1b2267a1)

## 3. Fechamentos

Simplificando, um encerramento é uma função que é definida dentro de outra função. Essa função especial tem acesso ao escopo externo (e, portanto, suas variáveis), o escopo criado pela função que contém a função de fechamento.

Isso é legal e tudo, mas para realmente entender o que é e por que precisamos dele, precisamos dar uma olhada em outro conceito.

### Contexto de execução

O contexto de execução equivale aproximadamente ao 'ambiente' em que uma função é executada. Isso consiste no seguinte:

- Os escopos das variáveis
- Argumentos da função
- O valor do objeto `this` (mais sobre isso em JavaScript3)

Confira o seguinte para saber mais sobre por que isso é importante:

- [O que é o Contexto de Execução e Pilha em JavaScript?](https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0)

### Por que precisamos de fechamentos?

Os fechamentos são comumente usados para dar privacidade aos dados dos objetos. Não queremos que determinados dados estejam disponíveis globalmente. Pense nisso como "manter algo em segredo. Veja, por exemplo, a seguinte situação:

> Você deseja fazer login em sua conta de e-mail, então você precisa de uma senha. Normalmente você tem essa senha na cabeça, ou em algum lugar anotado em um lugar que só pode ser acessado de uma certa maneira. Não está disponível em público, podendo ser acessado por qualquer pessoa.

Neste exemplo, sua senha são os dados que você deseja manter no escopo local. Seu ato de fazer login é a função interna. A função externa pode ser seu ato de estar no computador, onde sua senha está armazenada em um arquivo em algum lugar.

Para um estudo mais aprofundado, verifique os seguintes recursos:

- [O guia definitivo para contextos de execução, elevação, escopo e fechamentos em JavaScript](https://www.youtube.com/watch?v=Nt-qa_LlUH0)
- [Entendendo encerramentos](https://www.youtube.com/watch?v=rBBwrBRoOOY)
- [Domine a entrevista JavaScript: o que é um encerramento](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)
- [Eu nunca entendi os fechamentos de JavaScript](https://medium.com/dailyjs/i-never-understood-javascript-closures-9663703368e8)

## 4. Pensando como um programador II

Tornar-se um bom desenvolvedor não significa ser bom em nenhuma linguagem de programação específica: na verdade, a linguagem não importa muito.

Este é o segredo por trás de ser um bom desenvolvedor: se você entende o conceito, a estrutura e os princípios do que faz um programa de software funcionar, não importa de que maneira (a sintaxe) ele está escrito.

Essa também é a razão pela qual a maioria dos desenvolvedores, uma vez que dominam os fundamentos, são capazes de aprender outra linguagem com bastante facilidade. Não é porque eles têm boa memória; é porque eles podem reconhecer os padrões dentro da linguagem.

- [Como pensar como um programador](https://www.youtube.com/watch?v=azcrPFhaY9k)
- [Fundamentos da linguagem de computador: cinco conceitos principais](https://blog.upperlinecode.com/computer-language-fundamentals-five-core-concepts-1aa43e929f40)

## Finalizado?

Você terminou de passar pelos materiais? Toca aqui! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
