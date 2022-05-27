# Material de leitura JavaScript2 Semana 1

## Agenda

Estes são os tópicos da semana 1:

1. O que é um navegador da web?
   - Como funciona um navegador
   - Diferentes navegadores funcionam de forma diferente
2. O que é o Document-Object Model (DOM)?
   - JavaScript e o navegador
   - O DOM
   - O Caminho Crítico de Renderização
   - Percorrendo o DOM
3. O que é Manipulação DOM?

   - Manipulação de elementos
   - Eventos do navegador
   - Ouvintes e manipuladores de eventos

## 0. Vídeo-aulas

Seu professor Wilgert fez palestras em vídeo para o material desta semana. Você pode encontrá-los aqui: [Vídeos 1 - 10](https://www.youtube.com/playlist?list=PLVYDhqbgYpYU-7_oyPBkUuuis5bL1Dk8n)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYU-7_oyPBkUuuis5bL1Dk8n" target="_blank"><img src="../assets/wilgert.png" width="600" height= "350" alt="HYF Video" /></a>

## 1. O que é um navegador da web?

Um navegador da web é um software que permite acessar sites.

### Como funciona um navegador

Em sua jornada para se tornar um desenvolvedor web, é importante conhecer intimamente as ferramentas que você usará. Um deles é o navegador, que será usado para exibir seus sites. Nos recursos a seguir, você aprenderá sobre as muitas partes em que consiste qualquer navegador da Web e qual é o seu uso:

- [Como funciona um navegador da web](https://www.youtube.com/watch?v=z0HN-fG6oT4)
- [Como funcionam os navegadores da Web?](https://medium.com/@monica1109/how-does-web-browsers-work-c95ad628a509)

### Diferentes navegadores funcionam de forma diferente

Um site, em última análise, é um conjunto de instruções que descrevem a aparência de uma série de páginas da web. Cabe ao navegador renderizá-lo lendo o código de seus arquivos HTML/CSS e JavaScript. Existem, no entanto, diferenças na interpretação do código dos diferentes navegadores, fazendo com que a saída pareça diferente.

É por isso que você deve verificar a aparência do seu site em diferentes navegadores durante o desenvolvimento do seu site. Isso se chama torná-lo **compatível com vários navegadores**>

Você pode usar a seguinte ferramenta online para ver a aparência de suas páginas em vários navegadores:

- [Browsershots](http://browsershots.org)

Um bom site deve ter a mesma aparência e funcionar em qualquer navegador.

Infelizmente, não existe uma solução fácil para isso. Você deve verificar as especificidades de cada navegador que não exibe seu site corretamente e fazer os ajustes necessários em seu código. Esses problemas de compatibilidade podem ocorrer não apenas em navegadores diferentes, mas também devido a uma versão antiga do navegador que não suporta completamente os padrões mais recentes.

Isso ocorre porque o desenvolvimento do navegador não ocorre na mesma velocidade que o desenvolvimento da linguagem de programação. Na maioria das vezes, as tecnologias da Web que você está usando terão mais recursos que você, como desenvolvedor, pode usar do que o navegador pode lidar atualmente. Isso é importante ter em mente.

Quando você faz seu estilo, especialmente, é importante saber se um determinado navegador (e versão do navegador) é capaz de entendê-lo. Uma ferramenta útil para identificar isso é um site chamado **caniuse.com**:

- [caniuse](https://caniuse.com/)
- [Verifique o suporte HTML5/CSS3 com CANIUSE.COM](https://www.youtube.com/watch?v=el7McMP8CB8)

De um modo geral, você deseja oferecer suporte ao maior número possível de navegadores (e versões de navegadores) com seu código.

Para mais pesquisas, confira os seguintes recursos:

- [Como lidar com a compatibilidade entre navegadores](https://www.youtube.com/watch?v=9tEixRJ3GeI)
- [Compreendendo o contexto de empilhamento para compatibilidade entre navegadores](https://medium.com/@mattcroak718/understanding-the-stacking-context-for-cross-browser-compatibility-2b21db1cf621)

## 2. O que é o Document-Object Model (DOM)?

### JavaScript e o navegador

Como aprendemos no módulo anterior, JavaScript é uma linguagem de programação. Ele permite que você escreva regras lógicas que o computador pode executar para resolver um problema. No entanto, dizer que o 'computador' o executa é realmente impreciso. Existem dois softwares específicos que executam JavaScript: **o navegador** e **Node.js**. Falaremos sobre este último em um módulo diferente.

O navegador é um software que foi construído para entender JavaScript ((e HTML/CSS)). Cada navegador diferente (Chrome, Firefox, Safari, etc.) tem, nos bastidores, um **mecanismo JavaScript** que funciona para transformar o código JavaScript que você escreve em um código que o computador entende.

- [Como funciona o mecanismo JavaScript](https://www.youtube.com/watch?v=KM9coMpy5sQ)

Toda linguagem de programação está em um certo nível de abstração, em relação à única linguagem real que um computador entende: código de máquina (que é apenas 0's e 1's). Para obter mais informações sobre isso, confira o seguinte [vídeo](https://www.youtube.com/watch?v=bUWCD45qniA)

Para nossos propósitos, é importante apenas entender que o navegador analisa o JavaScript e, em seguida, faz o que é instruído a fazer: adicionar elementos, modificar arquivos de texto ou mídia etc. Esse é o objetivo do JavaScript no navegador: adicionar interatividade com base em o comportamento do usuário.

- [JavaScript, o navegador e o DOM](https://www.youtube.com/watch?v=31ViueuIXGE)

### O DOM

O Document-Object Model (DOM) é uma representação em forma de árvore da estrutura de uma página da web. O seguinte é um exemplo simples:

![Simple DOM](./../assets/simple-dom.png)

O JavaScript torna-se acessível ao DOM incorporando-o em um arquivo HTML. Você pode ter visto o `<script></script>` antes; bem, é assim que o navegador toma conhecimento do JavaScript.

- [O que exatamente é o DOM](https://bitsofco.de/what-exactly-is-the-dom/)
- [JavaScript e o navegador](https://eloquentjavascript.net/13_browser.html)
- [Curso básico de JavaScript DOM - Parte 1](https://www.youtube.com/watch?v=0ik6X4DJKCc)

### O caminho crítico de renderização

O processo real de transformar HTML, CSS e JavaScript em uma versão visualizável pelo usuário de uma página da Web é chamado de **Caminho de renderização crítica**.

- [Entendendo o caminho crítico de renderização](https://bitsofco.de/understanding-the-critical-rendering-path/)

## 3. O que é Manipulação DOM?

**Manipulação DOM** refere-se à atividade de selecionar e modificar elementos DOM. A principal razão pela qual isso é feito é que **você deseja mostrar ao usuário coisas diferentes dependendo de sua atividade**, por exemplo, se você clicar em um [ícone de menu de hambúrguer](https://bit.ly/2Yr4O7Z) e um menu de navegação desliza.

Encontrar os elementos certos é chamado de **percorrer o DOM**. Atravessar o DOM essencial significa: usar JavaScript para selecionar certos elementos dentro do DOM para modificá-los (mudar de cor, tamanho ou fazê-los desaparecer, por exemplo).

### Manipulando elementos

Veja o exemplo de código a seguir:

``` js
const corpo = document.querySelector('corpo'); // você também pode usar 'document.body'
const newParagraph = document.createElement('p');
newParagraph.innerText = 'Este parágrafo será adicionado ao corpo!';
newParagraph.style.background = 'vermelho';
body.appendChild(newParagraph);
```

Neste exemplo, estamos executando as seguintes etapas:

1. Selecionando o corpo: isso é sempre necessário, pois só podemos adicionar ou remover elementos do corpo do documento
2. Criando um novo elemento DOM: um parágrafo, ou seja, um elemento `<p>`
3. Injetando conteúdo no elemento de parágrafo recém-criado
4. Definir a cor de fundo para o elemento de parágrafo recém-criado
5. Adicionando o elemento de elemento de parágrafo recém-criado ao corpo

Teste este código copiando e colando-o no Developer Console do seu navegador. Depois de pressionar a tecla Enter/Return, você encontrará seu novo `<p>` no final da página!

Aprender a escrever JavaScript direcionado ao DOM é uma parte essencial de ser um desenvolvedor web. Nos recursos a seguir, você saberá mais sobre como fazer isso:

- [Percorrendo o DOM com JavaScript](https://zellwk.com/blog/dom-traversals/)
- [Curso básico de JavaScript DOM - Parte 2](https://www.youtube.com/watch?v=mPd2aJXCZ2g)

### Eventos do navegador

Os eventos do navegador (também conhecidos como eventos DOM) são muito parecidos com os eventos da vida real: são coisas importantes que acontecem. Na vida real, isso pode ser conseguir um emprego, se formar na escola ou receber um presente de aniversário. Em termos de navegador, isso é muito mais pequeno: ações do usuário como `clicar`, `rolar` ou `digitar` são todos considerados eventos.

Esses eventos são importantes de se conhecer, pois com base neles manipulamos o DOM. Por exemplo, o usuário clica em uma imagem e, como resultado, ela aumenta de tamanho.

Efetivamente é causa e efeito.

Confira os recursos a seguir para saber mais sobre quais eventos existem e o que você pode fazer para manipular elementos após a ocorrência de um evento:

- [O que são eventos do navegador?](https://www.youtube.com/watch?v=LeKKU3a4AQo)
- [Introdução aos eventos do navegador](https://javascript.info/introduction-browser-events)
- [Curso básico de JavaScript DOM - Parte 3](https://www.youtube.com/watch?v=wK2cBMcDTss)

### Ouvintes e manipuladores de eventos

Dê uma olhada neste código:

``` js
const corpo = document.querySelector('corpo');
body.addEventListener('click', function() {
  body.style.background = 'preto';
});
```

Teste este código copiando e colando-o no Developer Console do seu navegador. Depois de pressionar Enter/Return, clique no site. Você deve ver todo o `<body>` ficando preto!

Esta é a manipulação do DOM em sua forma mais simples. Ele segue em três etapas essenciais:

(1) Ocorre um evento ("O usuário clica na página")
(2) JavaScript está ciente e procura por esta ação específica do usuário (O navegador está escutando o evento, neste caso um evento `click`)
(3) JavaScript modifica o DOM como resultado (uma função que torna a cor de fundo do corpo preta é executada)

A segunda etapa é chamada de **escutando o evento**. Fazemos isso usando uma função predefinida pelo navegador chamada `addEventListener()`, que obtemos do objeto `document` no navegador. O navegador precisa ouvir o evento para saber o que ele deve fazer ("tornar a cor de fundo do corpo preta") caso um determinado evento (`click`) aconteça com um determinado elemento (`body`).

A terceira e última etapa é chamada de **tratamento do evento**. O termo "manipulador" significa efetivamente "cuidar" do evento; a resposta ao evento. O manipulador em si nada mais é do que uma função que executa mais código JavaScript para manipular uma parte específica da página (seja o elemento que experimentou o evento ou uma parte totalmente diferente da página).

- [Eventos em JavaScript](https://www.youtube.com/watch?v=7UstS0hsHgI)
- [Tutorial de eventos JavaScript](https://www.youtube.com/watch?v=e57ReoUn6kM)

## Finalizado?

Você terminou de passar pelos materiais? Toca aqui! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
