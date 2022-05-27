# Escopo, encerramentos e 'isto'

Escopo, encerramento e 'isto' são sobre *contexto*.

Este post explica muito bem: [Leitura recomendada por Todd Motto on Scope](https://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/)

Nesta revisão, não abordaremos como o JavaScript implementa o escopo. Estaríamos apenas reescrevendo o post acima de Todd Motto.

Em vez disso, vamos nos concentrar em algumas **palavras** importantes que são usadas para explicar o escopo. Entender o lado JavaScript das coisas pode ser difícil se não entendermos completamente essas palavras.

## Como pensar em contexto?
Considere as seguintes frases:
> Eyad é um ótimo cozinheiro. *Ele* adora fazer ravióli.

> Gijs é um ótimo cozinheiro. *Ele* adora fazer ravióli.

Em ambos os casos, a segunda frase é exatamente a mesma. No entanto, a palavra *ele* refere-se a uma pessoa completamente diferente. Ele é definido pelo contexto.

Um segundo exemplo:
> *Ele* adora fazer ravióli.

Agora, quando esta frase é escrita sem *ele* ser definido no contexto, a frase não faz sentido.

## Contexto na programação:
Um exemplo de JavaScript:
``` js
função minhaFunção() {
  const a = 'ravioli';
  console.log(a);
}
```

``` js
função minhaFunção() {
  console.log(a);
}
```

Em ambos os casos, `console.log(a)` é exatamente o mesmo. No entanto, o contexto define o valor de a e se ele é definido.

## O Escopo do Contexto
Vamos primeiro olhar para uma definição de `escopo`
> (1) a extensão da área ou assunto que algo trata ou para o qual é relevante.
> (2) a oportunidade ou possibilidade de fazer ou lidar com algo.

Então, em palavras mais aplicáveis ao nosso escopo de situação, significa:
> código que está ao alcance do nosso código.

Considere dois arquivos JavaScript completamente diferentes
``` js
// aFile.js
const a = 10;
```

``` js
// outroArquivo.js
console.log(a);
```

Quando executamos esses arquivos separadamente, a instrução `console.log(a)` em outroFile.js obviamente não pode alcançar `const a = 10`. Por quê? Está além do escopo do nosso contexto. Quando executamos um arquivo em JavaScript, o programa cria um novo contexto de nível superior que chamamos de escopo global.

De agora em diante, chamaremos 'contexto com escopo' simplesmente 'escopo'.

## Criando escopo dentro de um programa
Assim como dois programas têm escopos completamente diferentes, também podemos criar escopos diferentes dentro de um programa. Fazemos o mesmo em nossa linguagem:
> Eyad é um ótimo cozinheiro. *Ele* adora fazer ravióli. Gijs é ótimo em encontrar os melhores ingredientes. *Ele* tem um faro de verdade para isso.

Na escola se aprende que *ele* vai se referir ao último sujeito masculino introduzido no texto. Existem regras que restringem isso. Na programação, dependemos muito do contexto, e as regras são mais rígidas do que na linguagem natural.

Existem *cinco maneiras diferentes* de criar um novo contexto em JavaScript:
- O contexto global (como já vimos)
- O contexto de função simples
- O contexto de construção do objeto
- O contexto do método do objeto
- O contexto do ouvinte de eventos

Mais informações sobre isso [neste ótimo post](https://zellwk.com/blog/this/)

Outro ótimo artigo sobre `this`: [Entendendo a invocação de funções JavaScript e "this"](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).

