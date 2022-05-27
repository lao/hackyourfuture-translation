# Promessas


## O que é uma promessa?

Por que uma 'promessa' JavaScript ES6 é chamada de 'promessa'? Aqui está um trecho da definição de 'promessa' do *Oxford Dictionary of English*:

> **promessa** |ˈprɒmɪs|<br>
substantivo<br>
1 declaração ou garantia de que alguém fará algo ou que algo em particular acontecerá

Isso resume muito bem o que uma promessa significa em JavaScript: algo que será entregue no futuro (se e quando a promessa for *cumprida*).

Tradicionalmente, *callbacks* são usados como uma forma de receber os dados que são entregues de forma assíncrona (o que significa que os dados provavelmente não estarão disponíveis no momento em que são solicitados, mas podem ser esperados algum tempo depois). O uso de retornos de chamada pode se tornar rapidamente complicado ao lidar com muitos eventos assíncronos (por exemplo, chamadas ajax), especialmente quando eles dependem um do outro (google para *callback hell*).

JavaScript ES6 apresenta promessas como uma alternativa melhor para retornos de chamada ao lidar com eventos assíncronos.

Podemos declarar vários fatos simples sobre as promessas do ES6:

- Uma promessa é um objeto JavaScript (`typeof somePromise === 'object'`) que serve como um espaço reservado para um valor (futuro).
- Como uma promessa é um objeto JavaScript comum, você pode passá-la como um argumento para uma função, retorná-la de uma função, atribuí-la a uma variável, enviá-la para um array, etc.
- Você pode receber o valor 'promised' chamando o método `.then()` da promessa, passando a ele uma função que receberá esse valor como seu argumento assim que estiver disponível.
- Você pode criar uma promessa chamando a função construtora `Promise` do ES6 com `new` (veja a Listagem 1 abaixo), então chame `resolve()` quando os resultados estiverem prontos ou `reject()` ao detectar um erro.
- Às vezes, você pode obter uma promessa pronta chamando uma API ou função de biblioteca apropriada, como a função `fetch()` Web API na Listagem 1.
- Internamente, uma promessa pode estar em um dos três estados:
   - **pendente**: o resultado assíncrono ainda está aguardando entrega
   - **cumprido**: o resultado assíncrono foi entregue e está disponível (`resolve()` foi chamado)
   - **rejected**: foi encontrado um erro: a promessa não pôde ser cumprida (`reject()` foi chamado)
- Uma promessa que não está mais pendente porque foi cumprida ou rejeitada é considerada _settled_.
- Uma promessa _settled_ atingiu seu estado final. Seu estado e valor não podem mais ser alterados. Tornou-se _imutável_. Chamar subsequentemente `resolve()` ou `reject()` não afeta mais o resultado da promessa.

## Código de exemplo

A Listagem 1 mostra um exemplo baseado em um XMLHttpRequest assíncrono que usaremos no restante desta discussão.

``` js
'usar estrito';

função buscarJSON(url) {
  return new Promise((resolver, rejeitar) => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.responseType = 'json';
    xhr.onreadystatechange = () => {
      if (xhr.readyState === 4) {
        if (xhr.status < 400) {
          resolve(xhr.resposta);
        } senão {
          rejeitar(novo Erro(xhr.statusText));
        }
      }
    };
    xhr.send();
  });
}

// alternativo:
// const fetchJSON = url => fetch(url).then(res => res.json());

const url = 'http://api.nobelprize.org/v1/laureate.json?gender=female';

buscarJSON(url)
  .then(data => renderData(data))
  .catch(err => renderError(err));

função renderDados(dados) {
  console.log(dados);
}

função renderError(err) {
  console.error(err.message);
}
```

Listagem 1. `XMLHttpRequest` assíncrono (e alternativa `fetch`) usando uma promessa.

A função `fetchJSON()` na Listagem 1 retorna uma `promise` que resolve para um valor convertido de dados JSON recebidos de um ponto de extremidade de API remoto. A versão alternativa de `fetchJSON()` (comentado aqui) usa uma função de navegador mais moderna que retorna uma promessa nativamente.


## O método .then()

Uma promessa expõe um método `.then()` através do qual você pode obter seu valor cumprido ou um valor de erro caso a promessa tenha sido rejeitada:

``` js
somePromise.then(onFulfilled, onRejected);
```

O método `.then()` tem como parâmetros duas funções **opcionais**, a primeira lidando com o cenário 'feliz' (a promessa é cumprida) e a segunda lidando com o caso de erro (a promessa é rejeitada ). Se você estiver interessado apenas no caso de sucesso, pode deixar de fora o segundo parâmetro:

``` js
somePromise.then(data => {
  // ...
});
```

Se você está interessado apenas no caso de erro, você pode passar `null` para o primeiro argumento:

``` js
somePromise.then(null, err => {
  //...
});
```

ou você pode usar outro método disponível em uma promessa, `.catch()`, que é apenas um atalho para chamar `then()` com `null` como seu primeiro argumento:

``` js
alguma promessa
  .then(dados => {
    // ...
  })
  .catch(erro => {
    // ...
  });
```

Observe que as funções de manipulador `onFulfilled` e `onRejected` sempre são executadas de forma assíncrona. Quando a promessa é resolvida, o manipulador `onFulFilled` ou `onRejected` é colocado na fila de evento/retorno de chamada. Eles são executados quando o código JavaScript atualmente em execução é concluído, fazendo com que a [pilha de chamadas](./event_loop.md#call-stack) fique vazia e permitindo que o loop de eventos processe o próximo evento da fila. Isso vale mesmo que a promessa seja imediatamente cumprida ou rejeitada, como neste exemplo:

``` js
Promessa.resolver(42)
  .then(dados => console.log(dados));

console.log('depois da promessa');

// saída do console:
// depois da promessa
// 42
```

Este exemplo também mostra como você pode criar uma promessa que é resolvida imediatamente. Não há necessidade de usar `new` ou passar uma função `(resolve, rejeitar) => {}` para o construtor `Promise`. Da mesma forma, você pode criar uma promessa que é imediatamente rejeitada:

``` js
Promise.reject(new Error('oops'))
  .catch(err => console.log(err.message));

console.log('depois da promessa');

// saída do console:
// depois da promessa
// opa
```

## Encadeamento de promessas

É importante entender que o método `.then()` retorna uma nova promessa que resolve o valor de retorno de `onFulfilled` (se especificado) no caso do cenário 'happy' ou o valor de retorno de `onRejected()` (se especificado) em caso de erro. Se o valor de retorno dessas funções for um valor JavaScript simples, a nova promessa será imediatamente cumprida com esse valor. Se o valor de retorno for mais uma promessa, o resultado será determinado pela promessa interna, uma vez liquidada. Se a função não retornar um valor, a nova promessa é imediatamente cumprida com o valor `undefined`.

Como `.then()` (e `.catch`) retornam novas promessas, você pode encadeá-las de modo que seu código possa ser lido como: do *this*, then do *that* e então *that*, etc. :

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

fetchAndRender();
```

Listagem 2. Encadeamento de `then` e `catch`

Vamos examinar a Listagem 2 com um pouco mais de detalhes. Existem duas chamadas para `fetchJSON()`. Os erros são tratados em um só lugar, por meio do método `.catch()` que encerra a promessa "chain".

Se você incorporar outra promessa dentro da função que você passa para o método `.then()` (na Listagem 2 isso é feito no primeiro `.then()`), você deve retornar essa promessa como o valor de retorno da função. Se você não retornar a promessa, não há como o `.catch()` no final da cadeia "ver" um `reject()` da promessa interna, deixando a rejeição sem tratamento.

Caso uma promessa na cadeia seja rejeitada devido a algum erro, a cadeia de promessas será percorrida até que um manipulador `onRejected` (por exemplo, em um método final `.catch()`) seja encontrado. Todos os manipuladores `onFulfilled` intermediários (por exemplo, `.then()`) serão ignorados.

O tratamento de erros no final de uma cadeia de promessas é uma grande vantagem sobre a repetição do código de tratamento de erros no caso de retornos de chamada.

Note, entretanto, que um método `.catch()` não precisa necessariamente ser o último método na cadeia. Ele pode ser usado para lidar com erros no meio do caminho. Como mencionado anteriormente, o método `.catch()` retorna uma nova promessa que pode ser usada para fornecer algum valor de "retorno" em caso de erros.

No exemplo abaixo é criada uma promessa que é imediatamente rejeitada. A promessa é subsequentemente "consumida" duas vezes.

1. No primeiro caso ('consumer 1'), a rejeição é capturada por um método `.catch()` e o valor de rejeição `'bad'` é impresso no console.

2. No segundo caso ('consumer 2'), a rejeição também é capturada por um método `.catch()`, mas agora o manipulador catch ignora completamente o valor de rejeição e apenas retorna o valor de fallback `'good.`. Isso se torna o valor cumprido da promessa retornada por `.catch()`. O próximo `.then()` na cadeia, completamente inconsciente de que um erro ocorreu, agora imprime o valor preenchido `'good'` no console.

``` js
const promessa = Promise.reject('bad');

// consumidor 1
promessa
  .catch(console.log); // -> "ruim"

// consumidor 2
promessa
  .catch(() => 'bom')
  .then(console.log); // -> "bom"
```

## Promessa.todos()

Pode haver situações em que você deseja executar várias promessas em paralelo e esperar até que todas as promessas sejam resolvidas. Obviamente, essas promessas não devem ser interdependentes (ou seja, uma promessa não deve depender do resultado de outra promessa sendo executada em paralelo). O método `Promise.all()` aceita um array (ou mais precisamente, um _iterable_) de promessas. Ele retorna uma nova promessa que é resolvida quando todas as promessas da matriz são resolvidas ou rejeitadas assim que uma das promessas da matriz é rejeitada.

O valor cumprido da nova promessa é uma matriz de valores cumpridos das promessas individuais passadas para `Promise.all()`, na mesma ordem.

Mais detalhes sobre o MDN: [Promise.all()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

## Recursos adicionais

Nossos alunos anteriores também gostaram de aprender sobre promessas em:

Em texto:

- http://javascript.info/promise-basics
- https://blog.cloudboost.io/explaining-basic-javascript-promises-in-jip-en-janneketaal-c98763c0abd6
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

Vídeo: A rede Ninja: https://www.youtube.com/watch?v=yswb4SkDoj0

MDN:

- [MDN - Definição de promessa](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN - Usando promessas](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [Promises/especificação A+](https://promisesaplus.com/)
