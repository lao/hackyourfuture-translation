# Construindo um contador

O contador é uma das melhores maneiras de aprender sobre gerenciamento de estado, pois é agradável e simples e isola o gerenciamento de estado. Vamos criar um contador de números simples, começando de 0 até infinito!

1. Execute `create-react-app` nesta pasta para criar seu ambiente
2. Crie 3 componentes funcionais chamados `<Counter>`, `<Count>` e `<Button>`
3. Dentro de `<Counter>`, defina uma variável de estado chamada `count` (inicializada com o valor `0`) e um manipulador de estado chamado `setCount`
4. Dentro de `<Button>` crie um `<button>` com o texto `Add 1!` e o atributo `onClick`
5. Passe a variável de estado `count` para `<Count>` e o `setCount` para `<Button>`
6. Dentro de `<Counter>`, declare uma variável chamada `feedback` acima da instrução return. Dê a esta variável um valor de operador ternário: se `count` for maior que 10, deve exibir a string `"É maior que 10!"`, caso contrário, exibirá `"Continue contando..."`
7. Teste se funciona importando `<Counter>` para o componente de nível superior, que é `<App>`

## Coisas para pensar

Construir este pequeno aplicativo deve ser simples, agora vamos fazer com que esses *sucos cerebrais* fluam. Antes da sessão de domingo, pense no seguinte:

- Como você implementaria um botão de diminuição que reduz a contagem em 1? Você faria 2 funções <Button> diferentes ou adicionaria props ao componente para lidar com a mudança no texto?
- Uma vez que você pode decrementar também, como você implementaria nunca abaixo de 0?
- O que você precisaria mudar para ter também um botão que soma 2 e outro que remove 2? Isso criará um problema com sua lógica para nunca ficar abaixo de 0?
