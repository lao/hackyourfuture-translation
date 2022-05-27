# Gerar detalhes aleatórios da pessoa

Vamos criar um aplicativo simples seguindo uma abordagem passo a passo para entender as chamadas e testes de API.

A ideia do aplicativo é fazer uma aplicação web onde podemos clicar em um botão para gerar alguns dados aleatórios e falsos de uma pessoa. Podemos usar este aplicativo para gerar dados que podemos usar se estivermos criando uma demonstração de um aplicativo. Os dados parecem muito melhores do que criar 'João 1', 'João 2', etc! Conhecemos uma API que fornece os dados: [https://www.randomuser.me/](https://www.randomuser.me/).

Um problema comum é saber por onde começar!

## 1. Configuração

1. Primeiro, vamos nos certificar de que temos algum lugar para codificar. Execute `create-react-app` nesta pasta para criar seu ambiente

## 2. Pesquisa

Sempre comece com um pouco de pesquisa:

- está claro o que precisa ser feito?
- tenho todos os dados disponíveis para poder fazer o que precisa ser feito?

1. Confira a API e o que ela retorna acessando a URL `https://www.randomuser.me/api?results=1`. Podemos ver que o JSON resultante tem uma propriedade `results` que é um array e que contém um objeto descrevendo uma pessoa. Estamos interessados nos campos `first name`, `last name` e `email`, então localize onde eles estão no objeto.

## 3. Crie a solicitação

Vamos nos concentrar em colocar os dados em nosso aplicativo primeiro, depois nos preocuparemos com a interface do usuário.

1. No componente `App`, crie uma variável de estado chamada `person` que é inicializada com null.
2. Agora crie uma função chamada `getPerson`. O objetivo desta função é fazer uma chamada de API para `https://www.randomuser.me/api?results=1` e colocar o JSON resultante no estado `person`.
3. Crie um gancho `useEffect` que chamará a função `getPerson` apenas uma vez! (lembre-se da matriz de dependência).
4. Neste ponto você pode adicionar um `console.log` do objeto `person` em seu componente `App` e ver se você fez os passos acima corretamente. Ajuste onde for necessário!
5. Finalmente, crie um elemento `<ul>` simples com `<li>` filhos que mostram os campos `first name`, `last name` e `email` na página. Lembre-se que inicialmente a variável de estado `person` é nula, então adicione uma verificação de que se a pessoa for nula você não renderiza nada.
6. Execute seu aplicativo e verifique se alguma informação é mostrada na tela!

## 4. Refatorar intermezzo

Como sempre, uma vez que você tenha feito algo novo, é hora de pensar em refatorar. Se você não limpar seu código com frequência, você começará a ficar cada vez mais lento. À medida que você continua adicionando código que é focado apenas em corrigir o problema, você está criando uma confusão emaranhada que gostamos de chamar de `código espaguete`. E no final, adicionar coisas novas se tornará cada vez mais difícil, pois você perderá a visão geral.

Portanto, nunca pule essa etapa! Vamos ver:

### 4.1 Limpando o componente App

O problema mais óbvio aqui é que escrevemos tudo em nosso componente `App`. O componente `App` é o ponto de entrada do seu aplicativo e geralmente não deve conter nenhuma lógica. Então vamos corrigir isso:

1. Crie um componente `PersonController` e mova a função `getPerson`, o `useEffect` e o estado `person` para esse componente.
2. Vamos criar um componente `Person` e mover a renderização `<ul>` para dentro desse componente. Você precisará criar um prop no componente `Person` para o objeto `person`. Também mova sua verificação `null` para esse componente.
3. Agora no componente `PersonController`, retorne o componente `Person` enviando no estado `person` como o prop que você acabou de criar.
4. No componente `App` você pode apenas renderizar um componente `PersonController`.
5. Verifique se tudo funciona novamente!

Isso é chamado de padrão `Controller` em `React` e é comumente usado para separar nossa lógica de nossa renderização. Ao fazer isso, fica mais fácil saber qual componente faz o quê e isola as responsabilidades. Ao isolar você torna mais fácil depurar, testar e ler. Um ganha/ganha/ganha!

### 4.2 Separando o estado da interface do usuário

Embora tenhamos separado bem a instrução fetch da renderização dos detalhes, ainda temos uma dependência. Se você seguiu os mesmos passos, a instrução de retorno do seu componente `Person` provavelmente será semelhante a:

``` js
if (pessoa == null) {
  retornar nulo;
}

Retorna (
  <ul>
    <li>Nome: {person.name.first}</li>
    <li>Sobrenome: {person.name.last}</li>
    <li>E-mail: {pessoa.email}</li>
  </ul>
);
```

Isso não é ótimo, nós apenas enviamos o objeto pessoa para o componente de renderização sem formatá-lo. Isso criou uma dependência entre a API e nosso componente de renderização, de modo que, se a API mudar, o bug na verdade está no componente de renderização e não no componente do controlador. Também estamos enviando _todas_ as informações para nosso componente de renderização, o que não é eficiente.

Isso não é ótimo, então vamos fazer com que nosso objeto `person` que enviamos para o componente `Person` contenha apenas as informações que o componente precisa de uma maneira fácil.

1. No componente `Person`, altere a instrução return para obter o `first_name`, `last_name` e `email` do objeto. Em seguida, ajuste seu componente `PersonController` para criar esse objeto em vez de colocar todas as informações no estado.

Agora sabemos que qualquer um pode usar este componente `Person` fornecendo os dados sem depender da estrutura da API!

## Coisas para pensar

Neste exercício de preparação, passamos por algumas das etapas de um dia na vida de um desenvolvedor de software. Coisas importantes a serem observadas:

- `Comece com a pesquisa!` Você tem todas as informações de que precisa para construir o que foi incumbido de construir? A API fornece as informações corretas? Quando você é um desenvolvedor de front-end, precisará verificar com os desenvolvedores de back-end. Isso é importante porque se você não tem tudo disponível para você e só pensa nisso depois de dias de trabalho você acabou de estragar o planejamento.
- `Quebrar o problema.` Observe como começamos com apenas obter os dados e colocá-los na tela sem pensar muito? Também ignoramos os estados de carregamento e erro no início para isolar um problema a ser resolvido. Você precisará fazer isso o tempo todo, pois não pode resolver tudo de uma vez.
- `Divida o código em pedaços menores.` Observe o padrão Controller, é uma boa maneira de dividir responsabilidades, mas é apenas uma maneira de fazer isso. Sempre pergunte a si mesmo pelo que seu componente é responsável, se for várias coisas, tente dividi-lo. Isso torna seu código mais fácil de seguir para outras pessoas!
- `Refatorar FREQUENTEMENTE.` Desenvolvedores juniores tendem a tentar primeiro consertar tudo e então ir para a refatoração, que é quando eles de repente ficam assustados com uma montanha de trabalho sem saber por onde começar. Se você continuar refatorando enquanto constrói cada pequeno recurso (`manipulação do estado de carregamento` e `manipulação da mensagem de erro` são ambos pequenos recursos aqui) você terá muito mais facilidade!

Antes da sessão de domingo, pense no seguinte:

- O que você precisaria fazer para adicionar um novo campo à lista de detalhes? Digamos que queremos adicionar o número de telefone! Como a estrutura do seu código o ajudou a tornar isso mais fácil?
- O que você precisaria fazer para adicionar um botão que buscasse uma nova pessoa falsa em vez de ter um de cada vez? Como você dividiria o código então?
- Como você faria se quiséssemos 10 pessoas aleatórias na tela? Como nossa divisão do código ajuda na implementação desse recurso?
- Optamos por armazenar as informações da pessoa em nosso estado como um objeto. Uma alternativa poderia ser cada campo ter seu próprio estado, então um `[firstName, setFirstName]`, um `[lastName, setLastName]`, etc. Quais seriam as vantagens e desvantagens de fazer dessa forma?
