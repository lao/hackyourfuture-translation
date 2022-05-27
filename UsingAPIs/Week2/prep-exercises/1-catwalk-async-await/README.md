# Exercício de preparação - Cat walk com async/await

Na semana anterior nós mudamos o cat walk para uma implementação usando `Promise`s. Vamos agora usar a nova sintaxe `async/await` para simplificar um pouco mais. Dê uma olhada no `index.js` para ver o que fazer.

As funções `dance` e `walk` são idênticas às da semana passada, mas nossa função `catWalk` agora pode ser implementada usando um loop padrão `while`. Tente implementar isso e observe as seguintes perguntas.

## Coisas para pensar

- Você acha que esta versão é mais fácil de ler do que a versão que você fez na semana anterior?
- Esta versão é mais eficiente ou não ou não há diferença?
- Async/await faz o código esperar até que a Promise seja resolvida. Isso também bloqueia a execução de outras funções? Por que ou por que não?