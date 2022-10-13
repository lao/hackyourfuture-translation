# Material de leitura HTML/CSS/GIT Semana 3

## Agenda

Estes são os tópicos da semana 3:

1. Ramificação GIT
   - Filiais locais
   - Trabalhando com branches no GitHub
   - Fazer pull request
2. Estruturas CSS
   - Por que usar um framework?
   - Estruturas mais populares
   - CSS Framework vs. CSS personalizado

## 0. Vídeo-aulas

Seu professor Arco fez videoaulas para o material desta semana. Você pode encontrá-los aqui: [Vídeos 12 - 15](https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYXbAL_Hps1Y--THRmaTFipj" target="_blank"><img src="../assets/week1-arco.png" width="600 " height="400" alt="HYF Video" /></a>

## 1. Ramificação GIT

### Filiais locais

`Ramos` são um recurso central do GIT. Uma ramificação permite que você trabalhe em uma "versão" diferente do seu projeto. Dê uma olhada na imagem a seguir:

![filiais](ativos/filiais.png)

Sempre que você cria uma ramificação, está criando uma cópia exata da sua área de trabalho com a qual pode trabalhar. Experimente:

``` md
Entre em uma pasta e inicialize o GIT para criar um repositório local. Em seguida, crie uma ramificação. Neste novo branch, crie alguns arquivos básicos. **faça o estágio** e **comprometa** as alterações que você fez. Agora, volte para o branch original (**main**). O que você vê? Nada! Isso porque nesse branch você não fez essas alterações. Se você voltar para a outra ramificação, verá os arquivos que criou novamente. Magia!
```

Você pode ver um branch como um experimento, uma possível forma de seu projeto evoluir. Normalmente, cada branch (exceto o branch `main`) contém código para o que é chamado de novo `feature`: uma funcionalidade que você deseja adicionar ao seu software. Vamos pegar o Facebook como um exemplo simples: depois de criar uma conta (que é um recurso em si) você pode fazer várias coisas. Cada "coisa" é uma característica: ter um feed de notícias, poder enviar solicitações de amizade ou curtir postagens.

Trabalhar com branches é especialmente importante ao trabalhar com outros desenvolvedores. Isso só se aplica ao trabalhar com um repositório **remoto**, sobre o qual falaremos na próxima seção.

Ao trabalhar com diferentes ramificações, é útil ter uma única ramificação que contenha todo o código de trabalho e finalizado: a ramificação `main` (nós a chamamos de main por convenção, mas na verdade você pode nomeá-la como quiser). Sempre que você está trabalhando em um projeto que já foi colocado na internet, é o código do branch principal que está online.

No entanto, geralmente há uma ramificação separada que contém todo o código de desenvolvimento. Claro, isso é chamado de ramo `desenvolvimento`. Este branch é uma cópia quase exata do main, mas contém recursos que ainda não foram testados.

Depois de terminar um recurso, é hora de mesclar a ramificação na ramificação principal. Geralmente é a ramificação `main` ou `development`.

Uma vez testada e aprovada a nova versão do software, o ciclo se repete!

Acesse os seguintes recursos para saber mais:

- [Tutorial do Git: Ramos](https://www.youtube.com/watch?v=sgzkY5vFKQQ)
- [Introdução ao GIT - Branching and Merging](https://www.youtube.com/watch?v=FyAAIHHClqI)

### Trabalhando com branches no GitHub

Enquanto trabalhar com branches funciona um pouco diferente no GitHub (por causa de sua interface de usuário), o conceito permanece o mesmo: você sempre quer ter um branch principal que mantenha todo o seu código estável e funcional. Quaisquer outras ramificações conterão recursos de software que eventualmente serão mesclados no main.

Veja o projeto a seguir para aprender a trabalhar com branches no GitHub:

- [Projeto 'Hello World' do GitHub](https://guides.github.com/activities/hello-world/)

### Fazendo pull requests

Uma **solicitação pull** é um termo que o GitHub usa para se referir a uma solicitação para incorporar alterações de código de uma ramificação feita por um desenvolvedor (seja você ou outro desenvolvedor) no código armazenado em uma ramificação diferente de um repositório.

> Às vezes você ouvirá desenvolvedores falarem de "solicitações de mesclagem". Este é apenas outro nome para a mesma coisa: puxar alterações de outra ramificação ou bifurcação para sua ramificação e mesclar as alterações com seu código existente. Plataformas de desenvolvimento de software como o GitLab (uma alternativa ao GitHub) usam o termo "solicitação de mesclagem" em vez de "solicitação pull".

Essas mudanças são feitas em um branch, e o pull request geralmente é feito para mesclar no branch `main`. No entanto, isso não acontece diretamente: em circunstâncias normais, deve haver pelo menos uma outra pessoa analisando a proposta antes que ela seja aprovada para ser mesclada. A razão é simples: é muito fácil mesclar código que pode estar com bugs ou em conflito com o que já existe.

- [Solicitação de pull do GitHub em 100 segundos](https://www.youtube.com/watch?v=8lGpZkjnkt4)

As solicitações de pull só acontecem em repositórios remotos. Isso pode acontecer de 2 formas:
(1) De um branch para outro **dentro do mesmo repositório**. Para mais informações sobre isso, leia:

- [Criando uma solicitação pull](https://help.github.com/en/articles/creating-a-pull-request)

(2) De uma ramificação para outra ramificação **de um repositório bifurcado para o repositório original**. Um `fork` é uma cópia de um repositório, que é armazenado em sua conta pessoal do GitHub. As bifurcações permitem que você faça alterações em um projeto sem afetar o repositório original. Você pode buscar atualizações ou enviar alterações para o repositório original com pull requests.

Embora ambos sejam importantes para conhecer, é útil estudar a segunda maneira um pouco mais a fundo, porque é assim que você enviará sua lição de casa:

- [Sobre garfos](https://help.github.com/en/articles/about-forks)
- [Fluxo de lição de casa do GitHub](https://www.youtube.com/watch?v=CpYARPYGQU8)

## 2. Estruturas CSS

Para explicar os frameworks CSS, primeiro devemos entender o que é um framework. Vamos ilustrar isso usando uma analogia.

Vamos supor que você queira fazer um chá de gengibre diariamente. Você faz isso com vários ingredientes: água, pedaços de gengibre e açúcar. Ao fazer isso, você descobrirá que é realmente difícil colocar todos os ingredientes nas proporções certas, para obter o sabor certo, o tempo todo.

Uma manhã você tem a ideia de misturar todos os ingredientes em um frasco na proporção correta, de modo que cada colher sirva a quantidade certa para fazer o chá.

Este jar é o seu framework. Ao usá-lo você não precisa pensar nos ingredientes, nem nas proporções. Apenas sobre o quanto você deseja usar para atender às suas necessidades.

Ou aqui está outra analogia:

Imagine que você quer fazer panquecas em forma de estrela. Isso é muito difícil de fazer por si só, então você escolhe usar um molde. O molde ajuda a "estruturar" a panqueca. Tudo o que você precisa adicionar é o conteúdo certo, que é a massa de panqueca.

Este molde é a sua estrutura. Ao usá-lo, você só precisa pensar no conteúdo real que deseja usar. O resto será cuidado para você.

> Dica: O conceito de framework voltará muitas vezes, pois não queremos reinventar a roda toda vez que criamos uma nova aplicação. O objetivo de qualquer software é escrevê-lo da forma mais simples possível, e um framework realmente ajuda nisso. Então mantenha isso em mente!

### Por que usar um framework CSS?

Um framework CSS permite que você estilize seu HTML de forma confiável, fazendo uso de regras CSS pré-definidas. Dessa forma, você não precisa pensar em qual CSS personalizado precisa escrever para fazer algo do jeito que deseja. Isso é útil principalmente para **acelerar o desenvolvimento**.

Há outras razões também que você pode aprender no seguinte artigo:

- [Quais são os benefícios de usar uma estrutura CSS](https://css-tricks.com/what-are-the-benefits-of-using-a-css-framework/)

Ele vem com uma desvantagem, no entanto, e é que o força a um design específico e ajustar as coisas às suas necessidades será mais difícil.

### Estruturas mais populares

Existem muitos frameworks CSS diferentes, cada um com seus prós e contras. No vídeo a seguir, você aprenderá sobre vários dos principais usados e quais problemas exatamente eles estão tentando resolver:

- [estruturas CSS](https://www.youtube.com/watch?v=AMDx0IIgiK4)

### CSS Framework vs. CSS personalizado

Como regra geral, você sempre deseja escrever CSS personalizado quando necessário. E se você estiver usando um framework, você precisa pelo menos saber por que ele funciona da maneira que funciona. Isso significa que você deve examinar primeiro a **documentação** desse framework CSS específico. Alternativamente, você também pode examinar a definição de classe dentro da folha de estilo (você pode usar o inspetor do navegador para isso, mais sobre isso depois).

No entanto, escrever CSS personalizado na prática nem sempre é possível. Isso pode ser devido aos prazos do projeto, falta de habilidade ou querer fazer prototipagem rápida (uma técnica para construir rapidamente uma versão funcional para testar se funciona). É quando usamos frameworks para nos ajudar.

Tenha em mente que uma estrutura deve estar lá apenas para auxiliar, não compensar ou definir sua aplicação. Pesquise os seguintes recursos para aprender sobre os prós e contras dos frameworks CSS:

- [Os frameworks CSS são ruins?](https://www.youtube.com/watch?v=VlY5CfkL760)
- [Discutindo os prós e contras de usar uma estrutura CSS](https://speckyboy.com/discussing-the-pros-and-cons-of-using-a-css-framework/)

## Finalizado?

Você terminou de passar pelos materiais? Bom trabalho!!! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
