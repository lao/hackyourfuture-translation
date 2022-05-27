# Projeto

construa um portfólio usando a API do GitHub e hospede-o como sua página inicial com o GitHub Pages, você precisará criar um repositório chamado `your-user-name.github.io`

---

> copiado do módulo Be async, há menos detalhes no prompt do BE do que no AMS porque os alunos já aprenderam a planejar e estruturar seus projetos, então espera-se que eles criem seu próprio plano

Você chegou até aqui, hora de se exibir um pouco! Crie um portfólio doentio para mostrar todo o seu trabalho até agora. Usando a [API do GitHub](https://docs.github.com/en/free-pro-team@latest/rest) reúna estatísticas, links e colaboradores para mostrar seu melhor trabalho. Aqui está um [tutorial útil](https://www.youtube.com/watch?v=5QlE6o-iYcE) para você começar (dica: evite enviar seu token de autenticação do GitHub!).

### Lista de controle

``` md
- [ ] [repo](https://github.com/_/_.github.io) (com um README completo)
- [ ] [demonstração ao vivo](https://_.github.io)
- Planejamento de Projetos
  - [ ] [Backlog](https://github.com/_/_/tree/master/project-planning/backlog.md)
  - [ ] [Estratégia de Desenvolvimento](https://github.com/_/_/tree/master/project-planning/development-strategy.md)
  - [ ] [Quadro do projeto](https://github.com/_/_/projects/_)
- Implementação
  - [ ] Módulos ES (`import`/`export`)
  - [ ] pelo menos uma `class`
  - [ ] pelo menos uma chamada para a API do GitHub
  - [ ] Logs de cada interação do usuário
```

Procurando um desafio extra? Tente implementar estes conceitos:

- [learn-component-architecture](https://github.com/oliverjam/learn-component-architecture)
- [client-side-routing](https://github.com/oliverjam/learn-client-side-routing)

---

> do módulo AMS JS3

## **4. PROJETO: Hackear seu repositório I**

Nas três semanas seguintes, você escreverá um aplicativo que usa a [API do GitHub](https://developer.github.com/v3/guides/getting-started/). Cada semana é construída em cima da outra, assim como um aplicativo do mundo real!

[![Exemplo de IU](./assets/hyf-github.png)](https://js3-spa.herokuapp.com/)
Clique na imagem para abrir a demonstração do aplicativo!

Este aplicativo, HackYourRepo, faz 2 coisas:

1. Ele faz conexão com a API do GitHub e recupera todos os repositórios encontrados na [conta HackYourFuture](https://www.github.com/hackyourfuture).
2. Ele exibe esses repositórios em uma lista ordenada alfabeticamente. Quando um usuário clica em qualquer um dos nomes de repositório, ele mostrará mais detalhes sobre ele.

Nas próximas 3 semanas você estará escrevendo o código necessário para fazer tudo isso funcionar!

### 4.1 Requisitos

Para começar, verifique se você está na ramificação GIT correta: `week1-[YOURNAME]`. Em seguida, navegue até a pasta `hackyourrepo-app` e familiarize-se com os arquivos de lá.

Esta semana você deve (1) configurar a estrutura HTML do aplicativo. Além disso, espera-se que você (2) estilize o aplicativo para torná-lo fácil de usar.

Aqui estão os requisitos para o HTML:

- Incluir 3 tags `<seção>`
- Incluir uma tag `<select>`
- Use os seguintes dados de espaço reservado:

``` js
const placeholderRepos = [
  {
    nome: 'SampleRepo1',
    descrição: 'Este repositório é para ser uma amostra',
    garfos: 5,
    atualizado: '2020-05-27 12:00:00',
  },
  {
    nome: 'AndAnotherOne',
    descrição: 'Outro repositório de amostra! Você acredita nisso?',
    garfos: 9,
    atualizado: '2020-05-27 12:00:00',
  },
  {
    nome: 'HYF-É-O-Melhor',
    Descrição:
      "Este repositório contém todas as coisas do HackYourFuture. Isso porque HYF é incrível!!!!",
    garfos: 130,
    atualizado: '2020-05-27 12:00:00',
  },
];
```

Aqui estão os requisitos para o CSS:

- Faça uso de `flexbox`
- Faça uso de `media-queries` e `calc()` para tornar a página responsiva ([mobile, tablet, desktop](https://tinyurl.com/yc5zmste))

Fora isso você pode criar sua própria versão da página!

## **4. PROJETO: Hackeie seu Repo II**

> Esta semana continuaremos a desenvolver o nosso trabalho da semana passada. Certifique-se de navegar até a pasta `hackyourrepo-app` e comece com base no código que você escreveu!

Esta semana vamos fazer algumas coisas:

1. Vamos remover nossos elementos HTML e refazê-los usando apenas JavaScript!
2. Substituiremos nossos dados de espaço reservado por dados reais da API do GitHub
3. Exibiremos esses dados em uma coluna separada da interface do usuário

Na superfície, parecerá exatamente o mesmo. Mas funcionalmente, ele será baseado apenas em JavaScript!

Aqui estão os requisitos:

- Remova os elementos HTML que você criou na semana passada e mantenha apenas a tag `<script>` (você pode manter o estilo)
- Recrie todos os elementos HTML usando JavaScript
- Preencha o `<select>` com opções. Use os dados buscados na API do GitHub, usando este URL:

``` js
const url = 'https://api.github.com/orgs/HackYourFuture/repos?per_page=100';
```

- Quando um usuário altera a opção na tag `<select>`, ouça esse evento "change" e faça uma solicitação HTTP para a API do GitHub para obter dados específicos do repositório. Leia a documentação para descobrir qual URL você precisa usar: [Documentação da API do GitHub](https://developer.github.com/v3/)
- Quando o repositório específico tiver sido buscado, preencha as colunas corretas: contribuidores e detalhes do repositório.
- Se houver um erro na solicitação HTTP, exiba o seguinte:

![Erro HTTP](./assets/hyf-github-error.png)

- Crie uma função `main` que executará todas as suas funções somente quando a janela estiver totalmente carregada

O resultado final deve ser semelhante a este no estilo, mas exatamente na funcionalidade:

[![Exemplo de IU](./assets/hyf-github.png)](https://js3-spa.herokuapp.com/)
Clique na imagem para abrir a demonstração do aplicativo!

Boa sorte!

## **4. PROJETO: Hackear seu repositório III**

> Esta semana continuaremos a desenvolver o nosso trabalho da semana passada. Certifique-se de navegar até a pasta `hackyourrepo-app` e comece com base no código que você escreveu!

Nosso aplicativo está parecendo muito bom até agora! Esta semana vamos fazer 2 coisas:

1. Vamos refatorar e modularizar nosso aplicativo
2. Adicionaremos um recurso: paginação!

Vamos separar cada um deles.

### 4.1 Refatorar e modularizar o aplicativo

Vamos começar com a refatoração, para que tenhamos uma base de código limpa para construir.

Como você aprendeu esta semana, refatorar é escrever "código limpo": código que seja legível e fácil de adicionar.

Ao escrever o código JavaScript na semana passada, provavelmente você escreveu tudo em um único arquivo JavaScript (o `script.js`). Esta semana vamos criar muitos outros arquivos, que então todos reuniremos nesse arquivo `script.js` para executar. Esse ato é chamado de 'modularização', e você praticará cada vez mais com o passar do tempo.

Além disso, você refatorará seu código usando os princípios de design de software que aprendeu nesta semana: DRY, KISS e outros que você pode ter aprendido. Como ficaria exatamente em sua base de código é deixado para você.

Aqui estão os requisitos:

- Crie um `.js` separado para cada função que você criar
- Importe todas as funções de nível superior para o arquivo `script.js` para executar quando a janela for carregada
- Reescreva sua lógica para ser o mais simples possível. Use loops e operadores lógicos quando necessário
- Renomeie suas funções e variáveis para serem o mais semânticas possível
- Armazene todos os seus arquivos JavaScript, além de `script.js` em uma pasta chamada `util` (abreviação de funções utilitárias)

> Funções utilitárias são funções reutilizáveis feitas para resolver problemas comuns. São funções regulares que realizam tarefas como: realizar um cálculo, transformar um tipo de dado em outro ou realizar uma operação DOM.

### 4.2 Adicionar um recurso: paginação

Você deve ter notado que quando um usuário seleciona um repositório que tem muitos contribuidores, a altura da página se torna cada vez maior (forçando assim o usuário a rolar para baixo). Vamos mudar isso adicionando paginação!

O que é paginação? Dê uma olhada neste:

![Exemplo de paginação](https://lorisleiva.com/content/images/2020/10/laravel-pagination-with-tailwindcss.png)

Na ilustração, cada número representa uma página. Você pode ter visto isso antes em sites como a Amazon, quando você está navegando em diferentes produtos.

Replicaremos essa funcionalidade para permitir que um usuário navegue por diferentes contribuidores sem precisar rolar incessantemente.

Aqui estão os requisitos:

- Cada "página" deve conter no máximo 5 colaboradores. Se o repositório selecionado contiver mais de 5 contribuidores, ele será dividido em uma página diferente (e, assim, criará outra adição)
- Divida a matriz em partes menores e crie uma nova página toda vez que o máximo for atingido
- Permitir que um usuário clique de página em página clicando no número ou em uma seta para avançar ou retroceder uma página

Boa sorte!
