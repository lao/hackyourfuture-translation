# Material de leitura HTML/CSS/GIT Semana 2

## Agenda

Estes são os tópicos da semana 2:

1. Introdução ao GIT
   - O que é GIT?
   - Instalando o GIT
   - Comandos básicos do GIT
   - O que é o GitHub?
   - Trabalhando com SSH
2. CSS mais avançado
   - Organização flexível com flexbox
   - Usando o layout da grade
   - Seletores de pseudo classe
   - Design responsivo com media queries
3. Remarcação

## 0. Vídeo-aulas

Seu professor Arco fez videoaulas para o material desta semana. Você pode encontrá-los aqui: [Vídeos 7 - 11](https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj" target="_blank"><img src="../assets/week1-arco.png" width="600 " height="400" alt="HYF Video" /></a>

## 1. Introdução ao GIT

### O que é GIT?

GIT é um software que permite que você salve seu trabalho a qualquer momento. É normalmente chamado de `sistema de controle de versão`, o que essencialmente significa que ele permite que você crie `versões` do seu espaço de trabalho e torna possível alternar entre os estados mais antigos e mais recentes.

Você pode pensar nisso como um videogame. Você chega a um certo ponto no jogo, depois de horas de luta. Você está realmente orgulhoso de quão longe você chegou, e não quer fazer tudo de novo caso morra. Então você decide _salvar seu jogo_. Se algo ruim acontecer depois desse ponto, você sempre poderá recarregar seu jogo e começar a partir desse ponto.

Isso é exatamente o que acontece com o GIT: no entanto, em vez de chamá-lo de _salvar seu jogo_, chamamos de **confirmar suas alterações**. Uma "alteração" é uma modificação de código que você fez em um ou mais arquivos. É recomendável fazer commit várias vezes ao dia, toda vez que você fizer algo que valha a pena salvar. Fazer commits com frequência também torna mais fácil redefinir seu trabalho para o último estado de trabalho. Descartar alterações com GIT é melhor do que confiar em CTRL-Z para desfazer tentativas com falha.

Se você quiser voltar para um _game save_ anterior, você pode fazer com que o GIT o ajude a fazê-lo **conferindo esse commit**. Você aprenderá mais sobre isso nas próximas seções.

Confira o clipe curto a seguir para aprender sobre os fundamentos do GIT:

- [GIT explicado em 100 segundos](https://www.youtube.com/watch?v=hwP7WQkmECE)

### Instalando o GIT

Para usar o GIT, primeiro você precisa instalá-lo. O software é diferente dependendo do seu sistema operacional:

- Para Windows, instale o [Git Bash](https://git-scm.com/download/win)
- Para MacOS, instale [GIT](https://git-scm.com/download/mac)
- Para Linux, instale o [GIT](https://git-scm.com/download/linux)

Depois de instalá-lo, você pode usá-lo através da CLI. Para verificar se funcionou, digite o comando:

```bash
git --versão
```

Deve dizer que a versão é **2.21** (ou superior se você instalou uma nova versão).

Você pode trabalhar com GIT usando apenas a CLI, mas também pode usar uma GUI (interface gráfica do usuário).
Dois exemplos gratuitos de plataforma cruzada são [SourceTree](https://www.sourcetreeapp.com/) e [Gitkraken](https://www.gitkraken.com/).
Depende da preferência pessoal o que funciona melhor, tanto a CLI quanto a GUI usarão o mesmo sistema subjacente.
Você pode até usar ambos no mesmo projeto, por exemplo. comandos na CLI refletirão instantaneamente na GUI.
A principal vantagem de uma GUI é que ela tem uma visão geral de todos os commits e branches, locais e remotos.

Agora que você tem o GIT instalado, é importante fazer uma configuração básica. Dentro de sua CLI, digite o seguinte (Substitua "Seu nome" e "seu.email@seuservidor.com" por seu próprio nome e endereço de e-mail, respectivamente).
Caso você esteja usando uma GUI, ela provavelmente solicitará os mesmos dados na primeira vez que você abrir o aplicativo e fará esses comandos para você.

```bash
git config --global user.name "Seu nome"
git config --global user.email "seu.email@seuservidor.com"
```

Isso garante que o GIT possa identificá-lo como a pessoa que o usa para salvar seus arquivos e pastas.

### Comandos básicos do GIT

Você usará o GIT como qualquer software executado por meio da CLI.

Existem diferentes maneiras de usar o GIT. Por enquanto, aprenderemos um procedimento: **confirmando seu espaço de trabalho em um repositório local**. Vamos separar essa frase primeiro:

- **Committing** é outra palavra para salvar ou armazenar as alterações feitas nos arquivos em seu workspace. Por exemplo, alterar o conteúdo de um arquivo é uma "mudança".
- **Workspace** é outra palavra para a pasta do projeto (e seu conteúdo). Ao fazer um repositório, ele estará na raiz (em outras palavras, no nível superior) da pasta.
- **Local** refere-se ao seu computador, sem envolvimento da internet. Quando você cria um arquivo ou pasta em seu computador, você o está criando "localmente".
- **Repositório** é um local de armazenamento que contém os dados referentes à pasta do seu projeto. O GIT cria uma pasta oculta `.git` que funciona como repositório local.

Antes de começarmos, devemos conhecer o comando mais básico de todos:

```bash
git init
```

O que ele faz é criar um novo repositório **local** na pasta do seu projeto. Somente depois de fazer isso você poderá acompanhar o próximo procedimento.

Agora podemos continuar com o procedimento propriamente dito. Isso acontece em 3 etapas:

1. **Não rastreado**. Neste estágio, o GIT não está ciente das alterações em seu espaço de trabalho.
2. **Encenação**. Neste estágio as mudanças são selecionadas para o próximo commit.
3. **Commitida** Nesta etapa, suas alterações foram salvas no repositório local. Se você precisar consultar uma versão anterior do seu espaço de trabalho, poderá fazer isso com segurança agora.

Isso pode soar muito abstrato, e é. Então, para torná-lo mais compreensível, você pode assistir aos seguintes vídeos e/ou experimentar coisas no playground do Git:

- [Noções básicas de linha de comando GIT](https://www.youtube.com/watch?v=HVsySz-h9r4)
- [Aprenda Git - usando CLI e GitKraken](https://www.youtube.com/playlist?list=PLe6EXFvnTV7-_41SpakZoTIYCgX4aMTdU)
- [Introdução ao GIT - Conceitos principais](https://www.youtube.com/watch?v=uR6G2v_WsRA)
- [GIT & GitHub Crash Course](https://www.youtube.com/watch?v=SWYqp7iY_Tc)
- [Git Playground](https://git-school.github.io/visualizing-git/)

## O que é o GitHub?

O GitHub **NÃO é o mesmo** que o GIT. Enquanto o GIT é um software que permite que você acompanhe seus arquivos, o GitHub é uma plataforma de desenvolvimento de software online que permite armazenar uma cópia do seu código online. Confira o vídeo a seguir para saber mais:

- [O que é o GitHub?](https://www.youtube.com/watch?v=w3jLJU7DT5E)

Usamos o GitHub devido ao seu principal benefício: ele nos permite armazenar livremente nosso código online (ou `remoto`, como nós desenvolvedores também o chamamos). Isso é útil, por exemplo, no caso de nosso computador travar e nossos projetos forem perdidos.

O segundo benefício de usar um armazenamento de código online é que ele nos permite trabalhar em conjunto com outros desenvolvedores, usando um repositório central (e remoto). Isso é feito usando branches, sobre os quais você aprenderá [na próxima semana](../Week3/README.me).

- [GIT Good: A Practical Introduction to GIT and GitHub I](https://codeburst.io/git-good-part-a-e0d826286a2a)
- [GIT Good: A Practical Introduction to GIT and GitHub II](https://codeburst.io/git-good-a-practical-introduction-to-git-and-github-in-git-we-trust-f18fa263ec48 )

### Trabalhando com SSH

SSH significa Secure Shell e é uma maneira de fornecer aos usuários uma maneira segura de acessar (o conteúdo de) um computador em uma rede não segura. Simplificando, torna a conexão muito mais difícil de hackear ou interceptar.

Ao trabalhar com repositórios de código online (ou o que você ouvirá com mais frequência: `remoto`), você pode estar lidando com conexões não seguras. Para tornar a conexão mais segura, você deve usar uma **chave SSH**. Semelhante a uma chave real, esta chave digital permite que seu computador seja identificado pela rede que você está tentando acessar. Se a conexão foi feita, você pode acessar e modificar o conteúdo da rede.

> O conceito de rede segura através do uso de identificadores (como uma chave SSH) também é conhecido como "autenticação": você é quem diz ser? A autenticação é uma ideia central dentro da programação e você deve ter isso em mente. Você também verá mais disso em módulos posteriores!

Verifique os seguintes recursos para obter mais informações:

- [Guia para iniciantes em SSH](https://www.youtube.com/watch?v=qWKK_PNHnnA)
- [Como funciona o SSH](https://www.youtube.com/watch?v=zlv9dI-9g1U)

Ao trabalhar com o GitHub, queremos garantir o mesmo nível de segurança. Assim, teremos que fazer uma chave SSH e vinculá-la ao GitHub!

- [Como gerar uma chave SSH](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- [Adicionando chave SSH ao GitHub](https://www.youtube.com/watch?v=H5qNpRGB7Qw)

## 2. CSS mais avançado

Até agora você já teve alguma prática com CSS. Nas seções a seguir, você aprenderá mais alguns conceitos essenciais para escrever folhas de estilo modernas para a web!

### Organização flexível com flexbox

CSS é usado para ordenar e estilizar elementos HTML. Uma grande parte disso é organizar os elementos de uma maneira visualmente atraente. Isso pode ser feito usando `flexbox`.

O que ele faz é ajudar você a pensar de acordo com o `design da web baseado em grade`: os elementos não são colocados aleatoriamente na página, mas são organizados ordenadamente ao longo de uma grade.

Leia o seguinte para saber mais sobre 'design da web baseado em grade':

- [Introdução às grades no web design](https://webdesign.tutsplus.com/articles/a-comprehensive-introduction-to-grids-in-web-design--cms-26521)
- [Introdução ao Web Design Grids](https://www.youtube.com/watch?v=gjYZoPEk0ow)

Uma vez que você entenda essa maneira de pensar, você saberá por que faz sentido usar o `flexbox`.

Para utilizá-lo devemos acessá-lo através da propriedade CSS `display`:

``` css
exibição: flexível;
```

Isso nos dará as propriedades específicas do `flexbox`, para que possamos desenvolver um CSS limpo e organizado. Confira os links a seguir para entender como isso é feito:

- [CSS Flexbox em 100 segundos](https://www.youtube.com/watch?v=K74l26pE4YA)
- [O que é Flexbox e por que aprender](https://www.youtube.com/watch?v=CXSwNIPsyTs)
- [Curso de CSS Flexbox](https://www.youtube.com/watch?v=-Wlt8NRtOpo)

### Usando o layout da grade

A adição mais recente ao kit de ferramentas css para organizar seu layout está usando `display: grid`. Onde todos os outros layouts sempre vão de cima para baixo, a grade permite que você crie um layout bidimensional.

O guia completo para grid by css-tricks é o guia, leia aqui:

- [CSS-tricks complete guide to grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

### Seletores de pseudoclasses

Cada elemento HTML pode estar em diferentes estados. O estado padrão é quando um elemento é intocado. Você já sabe como estilizar para isso.

``` css
botão {
  cor de fundo: branco;
}
```

Há momentos em que um usuário interage com um elemento. Por exemplo: clicar em um botão que abre outra página. Como desenvolvedores frontend, precisamos dar feedback ao usuário sobre essa ação específica. Quando eles colocam o mouse em cima do botão, ele acende (chamamos isso de 'estado de foco'). Precisamos escrever instruções para que isso aconteça:

``` css
botão: passar {
  cor de fundo: azul;
}
```

Assim como o estado de foco, existem outros também: `click`, `focus`, `visited` e outros. Para a maioria desses estados de elementos, temos seletores especiais. Leia o artigo a seguir para saber mais sobre eles. Depois de ter feito isso, experimente-os por si mesmo!:

- [Seletores de pseudoclasse](https://css-tricks.com/pseudo-class-selectors/)
- [Pseudo-classes vs pseudo-elementos em CSS](https://www.youtube.com/watch?v=0VDx1570X3U)

### Design responsivo com consultas de mídia

Hoje em dia as pessoas usam diferentes dispositivos para acessar sites: desktops, tablets e celulares de todos os tamanhos. O design responsivo é uma maneira de montar um site para que ele dimensione automaticamente seu conteúdo e elementos para corresponder ao tamanho da tela do visualizador. Ele evita que as imagens sejam maiores que a largura da tela, para que os visitantes em dispositivos móveis também vejam um site visualmente atraente

Para obter mais informações sobre design responsivo, consulte este artigo: [Design responsivo](https://www.internetingishard.com/html-and-css/responsive-design/).

A principal maneira de criar um site responsivo é escrever um código CSS personalizado que o torne assim. Isso pode ser feito usando `consultas de mídia`: instruções CSS que se aplicam apenas a determinados tamanhos de tela.

Saiba mais sobre consultas de mídia aqui:

- [Introdução às consultas de mídia](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Media_queries).
- [Aprenda a consulta de mídia CSS em 7 minutos](https://www.youtube.com/watch?v=yU7jJ3NbPdA)

### Esquemas

Agora que você conhece todas as ferramentas à sua disposição, é hora de olhar para a criação de layouts, que são o design mais básico do seu aplicativo/site. É importante sempre fazer esta etapa primeiro, pois qualquer alteração no layout afetará todas as outras partes do site, enquanto as partes menores não devem afetar o layout.

Aprenda mais sobre eles aqui:
- [Os fundamentos dos layouts css](https://www.youtube.com/watch?v=yMEjLBKyvEg)

## 3. Remarcação

Como você provavelmente já viu, todo projeto no GitHub vem com um arquivo chamado `README.md`
Este arquivo leia-me é usado em geral para delinear o objetivo do projeto e geralmente inclui alguns exemplos de código.

Até mesmo a página que você está lendo agora também é criada usando Markdown.

Markdown não é uma sintaxe que os navegadores entendem, mas é muito simples de escrever e ler com qualquer editor de texto.
Muitas plataformas GIT online, como o GitHub, analisam arquivos Markdown e os exibem como belas páginas HTML.
Outro bom exemplo de suporte ao Markdown é o Slack. Você pode estilizar suas mensagens do Slack usando o Markdown!

Alguns exemplos do que você pode fazer com o Markdown:

| HTML | Remarcação |
| ---------------------------- | -------------------------------------------- |
| H1 | `# título` |
| H2 | `## título` |
| _Ênfase_ | `*itálico` |
| **Negrito** | `**negrito**` |
| ~~Tachado~~ | `~~Raspe isso.~~` |
| [Link](#) | `[texto do link](https://somewhere)` |
| `<p>Única linha de código</p>` | `` use `backticks` únicos em torno de seu código`` |

Se você quiser mostrar um bloco de código maior, comece e termine com 3 acentos graves

````remarcação
```
   <html>
      <head>...</head>
      <body>...</body>
   </html>
```
````

Com o Markdown você pode fazer mais coisas como imagens, listas, checklists, tabelas e muito mais.
Se você quiser saber mais sobre o Markdown, verifique estas fontes:

- [Markdown Crash Course](https://www.youtube.com/watch?v=HUBNt18RFbo)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Finalizado?

Você terminou de passar pelos materiais? Bom trabalho!!! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
