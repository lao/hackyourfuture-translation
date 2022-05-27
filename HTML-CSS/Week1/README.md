# Material de leitura HTML/CSS/GIT Semana 1

## Agenda

Estes são os tópicos da semana 1:

1. O que é a interface de linha de comando (CLI)?
2. Introdução ao HTML:
   - Rota de colisão
   - As tags mais usadas
   - HTML semântico
3. Introdução ao CSS:
   - Rota de colisão
   - Onde escrevê-lo?
   - O modelo da caixa
   - O efeito cascata
   - Especificidade
4. Trabalhando com os navegadores
   - O que é um navegador da web?
   - Escolhendo o navegador certo
   - Como usar o inspetor
   - Extensões de navegador úteis

## 0. Vídeo-aulas

Seu professor Arco fez videoaulas para o material desta semana. Você pode encontrá-los aqui: [Vídeos 1 - 6](https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj" target="_blank"><img src="../assets/week1-arco.png" width="600 " height="400" alt="HYF Video" /></a>

## 1. O que é a interface de linha de comando (CLI)?

A `interface de linha de comando` (também conhecida como CLI ou shell) é uma maneira de navegar pelo conteúdo do seu computador (mídia, pastas, aplicativos, etc.) sem uma interface de usuário visual. Ele permite que você digite comandos de texto para executar tarefas específicas. Como você pode controlar diretamente o computador digitando, muitas tarefas podem ser executadas mais rapidamente e algumas tarefas podem ser automatizadas com comandos especiais que percorrem e executam a mesma ação em muitos arquivos.

Como um desenvolvedor iniciante, é importante se familiarizar com ele, pois ele ensinará como os computadores funcionam: como ferramentas às quais você dá instruções. Isso não é diferente de programar para desenvolvimento web; mas em vez de escrever instruções diretamente para o computador, você escreve instruções para os navegadores executarem!

A primeira coisa que você notará é que, uma vez que você digita um comando, o computador nem sempre dá feedback. Isso é completamente normal. A maior parte do desenvolvimento de aplicativos é assim, e é bom se acostumar com isso.

**Observação para usuários do Windows**: instale o [Git for Windows](https://gitforwindows.org). Ele vem com um aplicativo chamado _Git BASH_ que simula comandos CLI frequentemente usados no estilo Unix. Isso alinha nosso trabalho aqui neste curso, pois todos podemos usar os mesmos comandos. Mas há uma razão ainda maior: estar confortável no shell Unix Bash é muito importante para um desenvolvedor web, já que os servidores web geralmente rodam Linux.

Para obter mais informações, verifique os seguintes recursos e codifique:

- [Compreendendo a linha de comando para iniciantes](https://learntocodewith.me/getting-started/topics/command-line/)
- [Uma cartilha de linha de comando para iniciantes](https://lifehacker.com/a-command-line-primer-for-beginners-5633909)
- [Curso rápido de linha de comando](https://www.youtube.com/watch?v=yz7nYlnXLfE)

## 2. Introdução ao HTML

### Rota de colisão

HTML é a base do desenvolvimento web. É um acrônimo para **HyperText Markup Language**. Ele é usado para estruturar o conteúdo em uma página da web. O que entendemos por conteúdo? Texto simples, imagens, vídeos, links para outros sites, etc. A estrutura dá significado ao conteúdo definindo-o como, por exemplo, títulos, parágrafos ou imagens.

Para aprender HTML corretamente é importante saber o que é. Acesse os seguintes recursos para saber mais sobre isso:

- [Noções básicas de HTML5 - História do HTML](https://www.youtube.com/watch?v=NzzGt7EmXVw)
- [Curso intensivo de HTML](https://www.youtube.com/watch?v=UB1O30fR-EE)

### As tags mais usadas

Se em algum momento você passou a acreditar que teria que aprender uma lista inteira de tags de cor para escrever um ótimo HTML, você está com sorte: isso não é necessário.

O mais importante a saber é que as tags são usadas para **estruturar o conteúdo**, ou seja: para decidir como cada parte está organizada para entender mais facilmente o que a página está tentando comunicar.

É útil memorizar esta lista, mas não sinta que precisa aprender e memorizar _toda_ tag HTML. Depois de entender o básico, você pode procurar facilmente qual tag precisa.

Confira o artigo a seguir para encontrar uma lista das tags mais usadas: [As tags mais usadas](https://www.geeksforgeeks.org/most-commonly-used-tags-in-html/)

## HTML semântico

HTML semântico são tags HTML que introduzem significado à página da Web em vez de apenas apresentação. Por exemplo, uma tag `<p>` indica que o texto incluído é um parágrafo. Uma tag `<nav>` indica algum tipo de menu de navegação. Ambos os exemplos mostram significado e estrutura, desta forma fica mais fácil de entender tanto para o navegador quanto para o desenvolvedor.

Isso leva ao seguinte insight sobre como escrever código: embora o código seja escrito para produzir um software funcional, ele também deve ser escrito para que **outros desenvolvedores possam lê-lo e entendê-lo com facilidade**. É por isso que é tão importante escrever um código significativo: se outra pessoa puder lê-lo e entender o que você quis dizer, você fez um ótimo trabalho!

Dê uma olhada nos seguintes recursos para saber mais sobre HTML semântico:

- [HTML semântico](https://www.internetingishard.com/html-and-css/semantic-html/)
- [HTML5 o mais rápido possível](https://www.youtube.com/watch?v=IsXEVQRaTX8)

## 3. Introdução ao CSS

### Rota de colisão

CSS é tão importante quanto HTML. É um acrônimo para **Cascading Style Sheets**. É uma linguagem criada para alterar a aparência do conteúdo. Ao consultar as tags HTML, você pode 'estilizar' de várias maneiras: alterar o 'tamanho da fonte', aumentar a 'altura' ou anexar uma 'imagem de fundo' a ela.

Assista ao vídeo a seguir para entender melhor os fundamentos do CSS:

- [Curso intensivo de CSS](https://www.youtube.com/watch?v=yfoY53QXEnI)

### Onde escrever?

Existem 3 maneiras básicas de escrever CSS:

- Em uma folha de estilo externa: um arquivo `.css`, que está vinculado a um arquivo `.html` usando a seguinte tag:

```html
<link href="/path/to/style.css" rel="stylesheet" />
```

- No `<head>` de um arquivo `.html`. Isso é feito usando a tag `<style>`. Isso é chamado de `folha de estilo interna`:

```html
<cabeça>
  <estilo>
    corpo {
      cor de fundo: azul;
    }
  </style>
</head>
```

- Como parte do atributo `style` dentro de qualquer tag HTML. Isso é chamado de `estilo embutido`:

```html
<div style="background-color: blue;">HackYourFuture é legal!</div>
```

Na prática, você sempre escreverá seu CSS em arquivos `.css` separados. Isso ocorre porque você deseja garantir que **todo arquivo tenha um único propósito**: um arquivo HTML deve conter apenas o conteúdo e a estrutura de uma página, enquanto uma folha de estilo deve conter apenas regras de estilo que se aplicam a uma página.

Este é um princípio de design de software chamado [`separação de interesses`](https://softwareengineering.stackexchange.com/questions/32581/how-do-you-explain-separation-of-concerns-to-others).

### O modelo da caixa

"Em CSS, tudo é uma caixa". Esta frase resume um conceito central em HTML/CSS: o modelo de caixa. Ao construir uma página web cada elemento pode ser considerado uma caixa que possui as seguintes propriedades: `margin`, `border`, `padding` e `content`. A partir do primeiro elemento dentro do `<body>`, tudo o que vem depois será empurrado para baixo (graças a essas 4 propriedades).

Para saber mais sobre o modelo de caixa, acesse o seguinte:

- [Aprenda o modelo de caixa CSS em 8 minutos](https://www.youtube.com/watch?v=rIO5326FgPE)
- [Abrindo o modelo da caixa](https://learn.shayhowe.com/html-css/opening-the-box-model/)

### O efeito cascata

O primeiro C em CSS significa Cascading e é crucial para aprender a usar CSS corretamente. Essencialmente, significa que importa
(1) **em que ordem** e
(2) **quão específico** você escreve regras CSS.

Leia os seguintes artigos para aprender sobre isso:

- [O "C" em CSS](https://css-tricks.com/the-c-in-css-the-cascade/).
- [Como o CSS funciona: entendendo a cascata](https://blog.logrocket.com/how-css-works-understanding-the-cascade-d181cd89a4d8)

### Especificidade

Como existem várias maneiras de escrever seu código CSS, o que leva a várias regras aplicadas ao mesmo elemento html, o CSS precisa decidir qual regra seguir. Na forma mais simples, se tivermos, por exemplo, o seguinte HTML:

```html
<p>Este parágrafo deve ser estilizado normalmente</p>
<p class="explicação">
  Este parágrafo deve ter um estilo diferente à medida que adicionamos uma classe ao elemento
</p>
```

e o seguinte CSS:

``` css
p.explicação {
  peso da fonte: 600;
}

p{
  peso da fonte: 400;
}
```

Então porque a regra `p .explanation` é mais específica que a regra `p`, o `peso da fonte` do nosso segundo parágrafo será `600` mesmo que a outra regra tenha sido aplicada por último. Leia os seguintes artigos para saber mais sobre como funciona:

- [Aprenda seletores CSS básicos em 15 minutos](https://www.youtube.com/watch?v=7kxhOI1Y38Y)
- [Especificações sobre especificidade CSS](https://css-tricks.com/specifics-on-css-specificity/)
- Opcional, pois entra em todos os detalhes: [guia do MDN sobre Especificidade](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)

## 4. Trabalhando com o navegador

### O que é um navegador da web?

Você provavelmente usa diariamente. Vamos dar uma olhada no que realmente é.

Um `navegador da web` é um software que permite visualizar páginas da web, recuperadas da Internet ou carregadas do seu computador. A principal função de um navegador web é renderizar arquivos HTML: transformando todo o código (HTML, CSS e JavaScript) bem como as referências (imagens, vídeos, etc.) para exibir uma página corretamente.

Para um estudo mais aprofundado, aprofunde-se no seguinte:

- [O que é um navegador?](https://www.youtube.com/watch?v=TcbhVv9ty44)
- [Como funcionam os navegadores da web](https://www.youtube.com/watch?v=WjDrMKZWCt0)
- [Sobre seu navegador da web](http://www.allaboutcookies.org/browsers/)

### Escolhendo o navegador certo

Como desenvolvedor web, você escreverá código que será exibido em diferentes navegadores. Como tal, é importante que você se familiarize com a maioria dos principais navegadores em uso hoje. Esses são:

- [Internet Explorer](https://support.microsoft.com/en-us/help/17621/internet-explorer-downloads)
- [Google Chrome](https://www.google.com/chrome/)
- [Safari](https://support.apple.com/downloads/safari)
- [Mozilla Firefox](https://www.mozilla.org/en-GB/firefox/new/)
- [Microsoft Edge](https://www.microsoft.com/en-us/windows/microsoft-edge) (ainda não disponível para Mac/Linux)
- [Opera](https://www.opera.com/download)

Em sua jornada HackYourFuture, você usará principalmente o **Google Chrome** ao desenvolver, pois possui ótimas ferramentas de desenvolvedor que nos permitem desenvolver aplicativos da Web de maneira mais fácil e clara.

### Como usar o inspetor do navegador

O inspetor é uma parte dos navegadores que os desenvolvedores podem usar para examinar mais de perto a composição dos elementos HTML. Isso torna mais fácil escrever código HTML e CSS que funcione.

Assista os vídeos a seguir e acompanhe:

- [Usando as ferramentas do inspetor do navegador](https://www.youtube.com/watch?v=WJIqIDm7CoA)
- [Curso rápido de ferramentas para desenvolvedores do Google Chrome](https://www.youtube.com/watch?v=x4q86IjJFag)

### Extensões úteis do navegador

Como desenvolvedores da web, estaremos lidando com o navegador o tempo todo. Por que não atualizar nosso navegador para facilitar nossa vida de programação?

Uma `extensão do navegador` é um software que alguém escreveu para aumentar a capacidade do navegador da web. Por exemplo, se você odeia receber anúncios, provavelmente usa algo como [Adblock](https://chrome.google.com/webstore/detail/adblock/gighmmpiobklfepjocnamgkkbiglidom) para bloquear todos os anúncios indesejados que você pode encontrar em suas páginas da web (se não , faça o download o mais rápido possível!).

A seguir está uma lista de extensões que provaram ser úteis durante o desenvolvimento web. Esta lista se aplica apenas ao Google Chrome, portanto, se você não a tiver, [instale-a](https://www.google.com/chrome/).

Extensões:

- Modificar as tecnologias subjacentes a cada site, em tempo real, usando [Desenvolvedor da Web](https://chrome.google.com/webstore/detail/web-developer/bfbameneiokkgbdmiekhjnmfkcnldhhm/related?hl=en-US)
- Expor quais tecnologias um site está usando com o [WhatRuns](https://chrome.google.com/webstore/detail/whatruns/cmkdbmfndkfgebldhnkbfhlneefdaaip?hl=en-US)
- Se você sempre quis saber a cor exata de qualquer elemento em uma página, agora pode fazê-lo com [ColorZilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp?hl=en-US )
- Ao desenvolver, você usará texto fictício para preencher seus elementos. Digite [Loren Ipsum Generator](https://chrome.google.com/webstore/detail/lorem-ipsum-generator-def/mcdcbjjoakogbcopinefncmkcamnfkdb?hl=en%20)

Há muito mais dessas extensões e recomendamos que você explore. Veja o que se adapta às suas necessidades!

## Finalizado?

Você terminou de passar pelos materiais? Bom trabalho!!! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
