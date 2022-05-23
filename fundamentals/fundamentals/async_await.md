# assíncrono e aguardando

## Revisitando promessas

O exemplo mostrado na Listagem 1 abaixo foi usado no fundamental sobre [promises](./promises.md) para ilustrar o encadeamento de promessas com um `.catch()` final no final da cadeia para lidar com erros.

``` js
function fetchAndRender(url, otherUrl) {
  buscarJSON(url)
    .then(dados => {
      renderData(dados);
      return fetchJSON(otherUrl);
    })
    .then(otherData => {
      renderOutroDados(outrosDados);
    })
    .catch(erro => {
      renderError(erro);
    });
}
```

Listagem 1. Promessas encadeadas.

Neste exemplo, a função `fetchJSON()` busca dados de uma API remota e retorna uma promessa. Quando a promessa retornada pela primeira chamada para `fetchJSON()` é resolvida, os dados retornados são renderizados para o DOM por meio da função `renderData()`. Subsequentemente, uma segunda chamada é feita para `fetchJSON` para buscar outros dados. Quando a promessa dessa segunda chamada é cumprida, os dados suplementares são renderizados ao DOM.

Como há um atraso de tempo entre a chegada do primeiro conjunto de dados e a chegada do segundo conjunto de dados, um usuário olhando para a página da Web verá a página sendo preenchida em duas atualizações separadas. Pode ser uma experiência melhor para o usuário se as atualizações da página forem feitas de uma só vez. Poderíamos modificar o código da Listagem 1 para adiar a renderização do primeiro conjunto de dados até que o segundo conjunto de dados (`otherData`) seja recebido. Isso é ilustrado na Figura 2.

``` js
function fetchAndRender(url, otherUrl) {
  buscarJSON(url)
    .then(dados => {
      return fetchJSON(otherUrl)
        .then(otherData => {
          renderData(dados);
          renderOutroDados(outrosDados);
        });
    })
    .catch(erro => {
      renderError(erro);
    });
}
```

Listagem 2. Promessas aninhadas.

Agora, quando a promessa retornada pela segunda chamada para `fetchJSON()` é cumprida, o método `.then()` chamado diretamente nessa segunda promessa é usado para renderizar ambos os dados da primeira chamada `fetchJSON()` ( ainda acessível através de um _closure_) e o `otherData` da segunda promessa.

Ainda devemos retornar o resultado da cadeia de promessa interna para garantir que qualquer rejeição de promessa nessa cadeia interna seja capturada pelo `.catch()` final da cadeia externa. Esse resultado será neste exemplo uma promessa que é cumprida com o valor `undefined` ou uma promessa rejeitada em caso de erro.

Para atingir o objetivo deste exemplo de renderização de uma só vez, há ainda outra opção disponível para nós usando promessas, desde que a segunda chamada para `fetchJSON()` não dependa dos dados da primeira chamada. Neste exemplo, este é realmente o caso. Isso torna possível usar o método `Promise.all()`, conforme mostrado na Listagem 3.

``` js
function fetchAndRender(url, otherUrl) {
  Promise.all([fetchJSON(url), fetchJSON(otherUrl)])
    .then(([dados, outrosDados]) => {
      renderData(dados);
      renderOutroDados(outrosDados);
    })
    .catch(erro => {
      renderError(erro);
    });
}
```

Listagem 3. Executando promessas em paralelo usando Promise.all().

As promessas das duas chamadas para `fetchJSON()` agora são executadas em paralelo. `Promise.all()` retorna uma nova promessa que é resolvida se todas as promessas passadas no argumento array forem resolvidas ou rejeitadas assim que qualquer uma das promessas for rejeitada. Seu valor cumprido é uma matriz dos valores cumpridos das promessas individuais, na mesma ordem. Como as promessas são executadas em paralelo, o navegador pode enviar dois XMLHttpRequests simultâneos, melhorando assim o desempenho geral.


### A alternativa assíncrona/aguardar

As palavras-chave `async` e `await` foram introduzidas no ECMAScript 2017 como uma nova maneira de 'consumir' promessas. Ele evita a necessidade de usar `.then()` e `.catch()` e torna possível escrever código que usa promessas de forma "síncrona".

Voltando ao snippet de código da Listagem 1, agora podemos reescrever esse código conforme mostrado na Listagem 4 abaixo:

``` js
função assíncrona fetchAndRender(url, otherUrl) {
  experimentar {
    const data = await fetchJSON(url);
    renderData(dados);
    const otherData = await fetchJSON(otherUrl);
    renderOutroDados(outrosDados);
  }
  pegar (errar) {
    renderError(erro);
  }
}
```

Listagem 4. Reimplementação da Listagem 1 usando async/await

A palavra-chave `await` faz com que a execução do código seja suspensa de maneira não bloqueante até que a promessa retornada por `fetchJSON()` seja resolvida. Depois que a promessa é resolvida, a expressão esperada retorna o valor cumprido da promessa e a execução é retomada no ponto em que foi interrompida.

> Se você esquecer de usar a palavra-chave `await` você receberá a promessa em si ao invés de seu valor cumprido. E, claro, não haverá 'espera'.

Você só pode usar a palavra-chave `await` em funções marcadas com a palavra-chave `async`. O valor de retorno (se houver) dessa função também é uma promessa.

Note que você deve usar um bloco `try`-`catch` para lidar com erros. Consulte o fundamento [try...catch](./try_catch.md) para obter mais informações.

Voltando às promessas aninhadas da Listagem 2, agora podemos com `async`/`await` atingir nosso objetivo de renderização de uma só vez simplesmente movendo a chamada para `renderData()` após a segunda chamada `fetchJSON()`, conforme mostrado na Listagem 5. O que pode ser mais fácil do que isso?

``` js
função assíncrona fetchAndRender(url, otherUrl) {
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
```

Listagem 5. Reimplementação da Listagem 2 usando async/await

Com `async`/`await` também podemos aproveitar a execução de promessas em paralelo. Neste caso devemos usar o mesmo método `Promise.all()` mostrado na Listagem 3. A versão com `async`/`await` é mostrada na Listagem 6 abaixo.

``` js
função assíncrona fetchAndRender(url, otherUrl) {
  experimentar {
    const [data, otherData] = await Promise.all([fetchJSON(url), fetchJSON(otherUrl)]);
    renderData(dados);
    renderOutroDados(outrosDados);
  }
  pegar (errar) {
    renderError(erro);
  }
}
```

Listagem 6. Reimplementação da Listagem 3 usando async/await

Mais informações sobre o MDN:

- [função assíncrona](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [aguarda](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)

Vídeo de Wes Bos em `async`/`await`: https://youtu.be/9YkUCxvaLEk

