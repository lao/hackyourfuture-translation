# tentar... pegar

Do MDN:

> A instrução `try...catch` marca um bloco de instruções para tentar e especifica uma resposta, caso uma exceção seja lançada.

Vamos primeiro falar sobre exceções. As exceções são usadas na programação para sinalizar que uma situação inesperada surgiu ou um resultado inesperado foi recebido, geralmente devido a algum erro. Nessa situação, um programa pode lançar uma exceção. Em JavaScript isso pode ser feito da seguinte forma:

> `lançar` _expressão_;

Por convenção, espera-se que a _expression_ seja um objeto JavaScript [Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) padrão. Você pode declarar o motivo da exceção passando uma string de mensagem como argumento para o construtor do objeto `Error`, como neste exemplo.

``` js
throw new Error('Nenhuma resposta da rede.');
```

Quando você lança um erro, a execução adicional do código atual é interrompida imediatamente. O mecanismo JavaScript começará a procurar o código escrito especificamente para lidar com o erro (consulte `try..catch` abaixo). Se não houver esse código, o mecanismo JavaScript o reportará como uma exceção não tratada. Ao encontrar uma exceção não tratada no navegador, o JavaScript limpará a pilha de chamadas e aguardará a ocorrência de um próximo evento. No Node, o programa JavaScript será encerrado de forma anormal.

## Tratamento de exceção com try...catch

Se você antecipar que seu código pode estar sujeito a exceções (seja porque você mesmo lança exceções ou exceções lançadas pela API da Web ou funções de biblioteca*), você pode lidar com exceções envolvendo seu código em um bloco `try...catch`.

Exemplo: O método `JSON.parse()` pode lançar uma exceção se a string passada para `.parse()` não for um JSON válido.

``` js
experimentar {
  const obj = JSON.parse('este é um JSON inválido');
  console.log(obj);
}
pegar (errar) {
  console.error('Ocorreu um erro: ' + err.message);
}

// saída do console:
// Ocorreu um erro: token inesperado h em JSON na posição 1
```

Observe que o bloco `catch` recebe o objeto `Error` que foi lançado.

\* Nota: Você deve ser capaz de descobrir se as exceções são lançadas em uma API da Web (por exemplo, `JSON.parse()`) ou funções de biblioteca inspecionando a documentação correspondente.

## tente... capture com assíncrono e aguarde

O bloco `try...catch` também é importante ao trabalhar com `async` e `await`. Onde o método padrão de trabalhar com promessas envolve um método `.catch()` para lidar com erros, não existe tal método ao usar `async` e `await`. Promessas rejeitadas ao usar `async` e `await` são lançadas como exceções.

Este é um exemplo retirado do [fundamental on promise](./promises.md):

``` js
função assíncrona fetchAndRender() {
  experimentar {
    const data = await fetchJSON(url);
    const otherData = await fetchJSON(otherUrl);
    renderData(dados);
    renderOutroDados(outrosDados);
  }
  pegar (errar) {
    renderError(erro);
  }
}

fetchAndRender();
```

A função `fetchJSON()` retorna uma promessa. Caso essa promessa seja rejeitada, uma exceção é lançada e capturada pelo bloco `catch`.

## Quando lançar exceções

Como regra geral, você só deve lançar exceções se a situação ou resultado for realmente inesperado. Por exemplo, se você pedir a um usuário para inserir um número e o usuário digitar algo que não seja um número, você **não** deve lançar uma exceção. Isso ocorre porque é no curso normal dos eventos que você pode esperar que um usuário digite algo diferente de um número. Nesse caso, você deve lidar com isso da maneira usual, sem lançar uma exceção.

Exemplos de situações em que uma exceção é apropriada são:

- A rede caiu inesperadamente.
- Uma conexão de banco de dados foi descartada.

E assim por diante.

## Leitura adicional no MDN

[try...catch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)