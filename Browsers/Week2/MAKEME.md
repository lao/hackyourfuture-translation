# Trabalho de casa Navegadores Semana 2

## **Lista de afazeres**

1. Trabalho de apresentação 1
2. Refatorações JavaScript 30 (opcional)
3. Projeto!
4. Opcional: ideias de projetos paralelos pós-projeto

## **1. Apresentação**

Dê uma olhada na atribuição [aqui](https://github.com/HackYourFuture/presentation-module/blob/main/assignment1.md).

## **2. Refatorações JavaScript 30 (opcional)**

Se você tiver tempo antes do início do projeto, continue com a refatoração do JavaScript 30 que você iniciou na semana passada. Isso ajudará você a navegar em bases de código maiores.

## **3. Projeto**

Dê uma olhada na [descrição do projeto](../PROJECT.md) para ver o que fazer aqui.

## **4. Opcional: ideias de projetos paralelos pós-projeto**

> Uma parte do currículo do HackYourFuture é trabalhar em tantos projetos paralelos quanto possível ao longo do tempo que você tem. Esta é uma boa maneira de adicionar conhecimento extra ao seu arsenal e mostrar em seu currículo que você está motivado para aprender novas tecnologias. Este também é um ótimo momento para aprender coisas novas, pois há muitos mentores disponíveis para ajudá-lo no canal `#projects`! Você não terá essa quantidade de tempo e suporte assim que começar a trabalhar. Dê uma olhada no [repositório hyf_projects](https://github.com/HackYourFuture/hyf_projects/blob/main/README.md#project-2-a-try-out-application) para mais detalhes.

### 4.1 Reescrita do projeto

Durante o projeto você usou uma estrutura específica que preparamos para você ou que seu mentor decidiu, mas nesse tipo de projeto existem muitas maneiras de abordá-lo. Uma maneira de ter uma ideia melhor de como as estruturas de pastas funcionam é refatorando o mesmo projeto, mas usando uma diretriz diferente de dividir os componentes.

Em nosso projeto estamos separando os componentes `view` da `logic` e `data` da nossa aplicação. Esta é uma maneira muito comum de dividir através do que é chamado de método Model View Controller (onde controller é sinônimo de `logic` e model é sinônimo de `data`). No restante do currículo, você verá esse padrão muito usado com nomes variados, mas com uma ideia semelhante.

#### 4.1.1 Divisão baseada em recursos
Outra maneira de separar seu código que alguns de nossos mentores fazem em seu trabalho é separá-lo por recurso. Então, em vez de uma pasta `view`, você teria uma pasta `question` que contém toda a lógica/html/dados que esse recurso específico precisa. Quaisquer dados globais e a inicialização do seu aplicativo estariam na pasta principal. Por exemplo:


```
├── público
└── src
    └── características
    | └── pergunta
    | | └── questionHandlers.js
    | | └── questionViews.js
    | | └── questionData.js
    | └── temporizador
    | | └── timerHandlers.js
    | | └── timerViews.js
    | | └── timerData.js
    | └──...
    └── útil
    app.js
    constantes.js
    data.js
```

Você ainda pode ver a mesma divisão em arquivos dentro de cada pasta `feature` (manipuladores como lógica, visualizações como visualizações e dados como modelo), mas cada recurso é dividido em uma pasta separada. Em projetos maiores, isso será obrigatório, pois sua pasta `views` será preenchida com centenas de arquivos.

Para tentar, crie uma nova pasta em sua pasta do quiz chamada `component-structure` e copie todos os arquivos atuais no diretório `src`. Então comece a criar alguns arquivos em `src` para criar essa estrutura. Você pode copiar e colar o código da estrutura 'antiga' procurando na pasta 'component-structure'.

Queremos que você perceba como é fácil fazer esse tipo de alteração porque usamos a separação de código e as importações. Imagine ter que mudar o `index.html` para importar todos os novos arquivos ao invés de apenas `app.js` em sua pasta `src`!

#### 4.1.2 Alterar a estrutura de dados para uma metodologia de programação orientada a objetos (OOP)
Seu arquivo `data.js` no repositório inicial contém um objeto simples com algumas propriedades. A manipulação desses dados é então tratada em todos os outros arquivos, o que pode se tornar um problema se você gastar um pouco mais neste projeto. A razão é que esses dados agora são 'globais' e, como tal, podem ser alterados de qualquer lugar para o que você quiser. Para nos salvar de alguns bugs estranhos no futuro, poderíamos reescrever isso usando a maneira de pensar OOP usando classes. As aulas estão fora do escopo do currículo, pois a comunidade JavaScript está se afastando delas, mas se você conseguir um emprego em uma linguagem de programação diferente, poderá estar trabalhando de maneira diferente.

Para tentar, estude a ideia por trás da OOP e então altere seu arquivo `data.js` para exportar uma classe chamada `QuizManager`. Então pense sobre qual funcionalidade em outros arquivos deve ser um `método` na classe ao invés de uma função nos diferentes arquivos.