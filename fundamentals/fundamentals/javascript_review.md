### Revisão de JavaScript

Você precisará saber o seguinte antes de iniciar a classe Node (lembre-se que o Node é apenas JavaScript em um ambiente diferente - e você já CONHECE JS - certo?!?!)

```
De Jasão:
jason [9:11 AM]
@timirkaria os tópicos mais importantes serão sync/async e ajax. Isso e a sintaxe básica (funções nomeadas e anônimas, retornos de chamada, escopo) devem ser suficientes!
```

### AJAX
Significa *A*synchronous *J*avascript *A*nd *X*ml (pense em XML como o antigo JSON), mas agora é AJA*J*, mas isso não soa tão bem.

Então aqui está um exemplo de uma solicitação SYNCHRONOUS (ela espera a solicitação voltar antes de continuar)

Código de: `https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Synchronous_and_Asynchronous_Requests#Example_HTTP_synchronous_request`

``` js
const SECRET_MESSAGE_URL = 'https://gist.githubusercontent.com/tkaria/08325583e7411f7de6b80871780fd917/raw/61dae2869ae5013652bbeba1da2487097d8869b1/SecretMessage.txt'
solicitação const = new XMLHttpRequest(SECRET_MESSAGE_URL);
request.open('GET', SECRET_MESSAGE_URL, false); // `false` torna a solicitação síncrona
request.send(null);

if (request.status === 200) {
  console.log(request.responseText);
  console.log('Recebi a resposta');
}
console.log('Feito o pedido')

```

E aqui está um exemplo de uma versão ASYNCHRONOUS da mesma solicitação acima. Observe atentamente a saída.

``` js
const SECRET_MESSAGE_URL = 'https://gist.githubusercontent.com/tkaria/08325583e7411f7de6b80871780fd917/raw/61dae2869ae5013652bbeba1da2487097d8869b1/SecretMessage.txt'
const xhr = new XMLHttpRequest();
xhr.open("GET", SECRET_MESSAGE_URL, true);
xhr.onload = function (e) {
  if (xhr.readyState === 4) {
    if (xhr.status === 200) {
      console.log(xhr.responseText);
      console.log('Recebi a resposta');
    } senão {
      console.error(xhr.statusText);
    }
  }
};
xhr.onerror = function (e) {
  console.error(xhr.statusText);
};
xhr.send(null);
console.log('Feito o pedido');
```

### O que está acontecendo aqui?
Como sempre - leia os documentos primeiro...
`https://developer.mozilla.org/en/docs/Web/API/XMLHttpRequest`

Crie uma nova solicitação e abra-a (linhas 2 e 3)
Diga ao objeto de solicitação qual função chamar quando o conteúdo da solicitação for carregado. Dentro da função ANONYMOUS, que recebe um parâmetro `e`, verificamos o código de resposta da solicitação (isso é apenas material HTTP - nada de especial). Se o código de resposta for bom (200), imprimimos o que obtivemos.

Mais interessante é a ordem das declarações de impressão. No primeiro exemplo vimos a mensagem `Received the response` **ANTES** vimos a mensagem `Made the request` porque o programa esperou obter a resposta e imprimi-la antes de continuar a execução.

Neste caso, vemos a mensagem `Made the request` antes de vermos a resposta porque o programa continua rodando enquanto espera pela resposta. Quando a resposta é finalmente recebida, ela é impressa antes de escrever o `Received the response` no console.

Observe que usamos uma função anônima aqui - ela não tem nome. Não há nada de especial em uma função anônima. Poderíamos igualmente usar uma função nomeada no exemplo acima:

``` js
const SECRET_MESSAGE_URL = 'https://gist.githubusercontent.com/tkaria/08325583e7411f7de6b80871780fd917/raw/61dae2869ae5013652bbeba1da2487097d8869b1/SecretMessage.txt'

const xhr = new XMLHttpRequest();
function NOT_ANONYMOUS_ON_LOAD_FUNCTION(parâmetro) {
   if (xhr.readyState === 4) {
    if (xhr.status === 200) {
      console.log(xhr.responseText);
      console.log('Recebi a resposta');
    } senão {
      console.error(xhr.statusText);
    }
  }
}
xhr.open("GET", SECRET_MESSAGE_URL, true);
xhr.onload = NOT_ANONYMOUS_ON_LOAD_FUNCTION; // Nota: não estamos chamando a função - não há ()
// Vamos deixar a função de erro do jeito que está e você pode alterá-la para uma função nomeada
xhr.onerror = function (e) {
  console.error(xhr.statusText);
};
xhr.send(null);
console.log('Feito o pedido');

```

### A grande ideia:

#### Sincronização / Assíncrona
Faça solicitações sem esperar a resposta e apenas seja "notificado" quando a resposta acontecer. Essa é a parte assíncrona - não espere por isso e pare todo o resto, apenas me avise quando isso acontecer. Como o computador pode informá-lo? Você diz o que fazer quando a função assíncrona estiver pronta (tem algo a dizer - sucesso ou falha)

#### Funções nomeadas e anônimas
Algumas funções têm nomes e outras não. Às vezes, você só quer usar uma função para passá-la para outra função, para não precisar nomeá-la. Ele nunca precisa ser chamado fora da função para a qual você o está passando, portanto, não precisa de um nome.
A função assíncrona mais simples que você verá em todo lugar é chamada `setTimeout` (agora você deve estar acessando uma nova guia e digitando `MDN setTimeout` no Google). Seja paciente ao executar o abaixo - leva 3 segundos ...

Por exemplo (usando uma função nomeada):
``` js
função timeoutFunction() {
  console.log('Iniciando timeoutFunction');
  console.log('Finalizando timeoutFunction');
}
setTimeout(timeoutFunction, 3000);
console.log('Após timeoutFunction');
```

Por exemplo (usando uma função anônima):
``` js
setTimeout(function(){
    console.log('Iniciando timeoutFunction');
    console.log('Finalizando timeoutFunction');
  }, 3000);
console.log('Após timeoutFunction');
```

Por exemplo (usando uma função de seta gorda anônima):
``` js
setTimeout(() => { console.log('Iniciando timeoutFunction');
    console.log('Finalizando timeoutFunction');
  }, 3000);
console.log('Após timeoutFunction');
```

#### Chamadas de retorno
O que fazer quando o resultado de uma solicitação assíncrona é retornado. Lembre-se de que as solicitações podem ser bem-sucedidas e também falhar. Planeje (E TESTE) ambos.

#### Alcance
Acho que abordamos isso muito bem com nossa discussão sobre fechamentos na última aula, mas me avise se precisar de mais.

## Recapitulação
Leia isto - você pode não entender tudo, mas por favor leia antes de ler qualquer outra coisa sobre fechamentos. A razão é que este é o material de origem - esta é a documentação primária. Está escrito de forma muito técnica e um pouco chata, mas há uma razão (como falamos em aula). O motivo é ser claro para que a linguagem seja precisa e técnica. Tudo bem se você não entender agora, mas apenas leia e ficará na parte de trás da sua cabeça.
https://developer.mozilla.org/en/docs/Web/JavaScript/Closures

DIGITE estes exercícios - NÃO copie e cole. ANTES de executá-los, por favor, faça um palpite sobre o que vai acontecer.
``` js
função init(){
  const nome = 'Mozilla'; // nome é uma variável local criada pelo init
  function displayName() { // displayName() é a função interna, uma closure
    alerta(nome); // usa a variável declarada na função pai
  }
  Nome em Exibição();
}
iniciar();
```

``` js
função init(){
  const nome = 'Mozilla'; // nome é uma variável local criada pelo init
  function displayName() { // displayName() é a função interna, uma closure
    alerta(nome); // usa a variável declarada na função pai
  }
}
Nome em Exibição();
```

``` js
const name = 'Hackear seu futuro'
função init(){
  const nome = 'Mozilla'; // nome é uma variável local criada pelo init
  function displayName() { // displayName() é a função interna, uma closure
    alerta(nome); // usa a variável declarada na função pai
  }
  Nome em Exibição();
}
iniciar();
```

``` js
const name = 'Hackear seu futuro'
função init(nome) {
  function displayName(name) { // displayName() é a função interna, uma closure
    alerta(nome); // usa a variável declarada na função pai
  }
  displayName(nome);
}
init('Hackear seu futuro novamente')
```

Agora leia isto: http://stackoverflow.com/questions/11488014/asynchronous-process-inside-a-javascript-for-loop

E experimente os exemplos - por favor, certifique-se de entender o que está acontecendo. Faça perguntas se não.

As mesmas instruções acima, mas agora para as funções de seta (lembre-se que isso não tem a intenção de confundi-lo - é apenas código).

### Funções de seta
https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions
Então leia isso.
http://stackoverflow.com/questions/22939130/when-should-i-use-arrow-functions-in-ecmascript-6/28135120#28135120

Esta é uma função normal:
``` js
function dizerOlá(nome) {
    return 'Olá' + nome;
}
```

O mesmo que acima com notação de seta (seta gorda) - notação abreviada. Isso é fácil de estragar. Observe nenhum retorno.
``` js
const digaOlá2 = (nome) => 'Olá ' + nome;
```

O mesmo que acima com notação de seta (seta gorda) - notação abreviada. Melhor - mais fácil de ler - com retorno.
``` js
const digaOlá2 = (nome) => {return 'Olá' + nome;}
```

Pense sobre este
``` js
function Pessoa(nome) {
    this.firstName = firstName;
}
```

Parece o mesmo, mas o que acontece? Veja se você consegue descobrir por que lendo a documentação.
``` js
const Pessoa = (firstName) => {this.firstName = firstName}
```

Fechamentos e funções assíncronas
O que está acontecendo aqui - eu esperaria 3 alertas com 1,2,3 neles, mas nãooooo
``` js
for (var i = 0; i < 3; i++) {
    setTimeout(função callBackFunction() {
        alerta(i);
    }, 100);
}
```

### Faça a função acima fazer o que achamos que deveria fazer.

### Exemplos de retorno
``` js
Valores de retorno
função f1(x) {
    este.x = x + 1;
    Retorna;
}

função f2(x) {
    return this.x = x + 1;
}
```

### Membros estáticos
http://odetocode.com/blogs/scott/archive/2015/02/02/static-members-in-es6.aspx

### Exemplos de fechamentos
https://jsfiddle.net/78dg25ax/?utm_source=website&utm_medium=embed&utm_campaign=78dg25ax

### Por que os closures são úteis com código assíncrono:
http://stackoverflow.com/questions/13343340/calling-an-asynchronous-function-within-a-for-loop-in-javascript

### Promessas
http://stackoverflow.com/questions/13343340/calling-an-asynchronous-function-within-a-for-loop-in-javascript
https://www.youtube.com/watch?v=WBupia9oidU

