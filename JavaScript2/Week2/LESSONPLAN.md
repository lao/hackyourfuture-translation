# Plano de aula JavaScript2 Semana 2

## Agenda

O objetivo desta aula é apresentar ao aluno:

- O que são processos síncronos vs. assíncronos
- O que são callbacks e como escrever o seu próprio
- Como funciona o loop de eventos
- Mostrar 3 funções de matriz comumente usadas (filtro, redução, mapa)

## Conceitos principais

PRIMEIRA METADE (12h00 - 13h30)

## 1. Perguntas e respostas sobre os conceitos e trabalhos de casa da semana passada

- DOM
- Manipulação DOM
- funções definidas pelo navegador

Nota: Você pode pedir aos alunos que expliquem um conceito ou resumir a última aula por conta própria

## 2. Quais são os processos síncronos vs. assíncronos

### Explicação

### Exemplo

### Exercício

### Essência

Notas:

- Síncrono refere-se a um processo de execução linear: um passo de cada vez
- Assíncrono nos ajuda a fazer várias coisas em paralelo

## 3. Retornos de chamada

### Explicação

Um retorno de chamada em JavaScript é basicamente uma função (retorno de chamada) sendo passado como um parâmetro para outra função que, após algum ponto do tempo, executaria a função passada ou invocaria o retorno de chamada.

Os retornos de chamada foram introduzidos principalmente em JavaScript para obter um comportamento assíncrono
(https://codeburst.io/javascript-what-the-heck-is-a-callback-aba4da2deced)

### Exemplo

Considere uma situação em que a pessoa A deseja ir ao cinema com uma pessoa amiga B uma noite. A pessoa A descobre a hora e o local e agora precisa compartilhar com B. A pega o telefone e tenta ligar para B. Digamos que B está ocupado com algum trabalho e não pode atender o telefone. A pessoa A agora tem duas opções. Uma opção é ficar na linha até que B atenda o telefone e depois compartilhar os detalhes do filme. Ou A pode enviar uma mensagem de voz e pedir a B que **retorne a chamada** uma vez gratuitamente.

```javascript
function doHomework(assunto, retorno de chamada) {
  alert(`Iniciando meu dever de casa ${subject}.`);
  ligar de volta();
}
function alertFinished() {
  alert('Terminei meu dever de casa');
}
doHomework('matemática', alertFinished);
```

mais exemplos (feitos por Yash): https://github.com/HackYourFuture/JavaScript2/blob/master/assets/callbacks.js

### Exercício

#### 1. O que vai acontecer?

#### 2. Como inverter a ordem de saída?

```javascript
função primeiro() {
  // Simula um atraso de código
  setTimeout(function(){
    console.log(1);
  }, 500);
}
função segundo() {
  console.log(2);
}

primeiro();
segundo();
```

### Essência

você não pode simplesmente chamar uma função após a outra e esperar que elas sejam executadas na ordem correta. Os retornos de chamada são uma maneira de garantir que determinado código não seja executado até que outro código já tenha concluído a execução.

SEGUNDA METADE (14.00 - 16.00)

## 4. Loops de eventos

### Explicação

https://github.com/HackYourFuture/fundamentals/blob/master/fundamentals/event_loop.md

### Exemplo

```Javascript
const bar = () => console.log('bar')

const baz = () => console.log('baz')

const foo = () => {
  console.log('foo')
  bar()
  baz()
}


foo()
```

Saída:

```Javascript
foo
bar
baz
```

Pilha de chamadas
![Call Stack](../assets/call_stack_example.png)

### Exercício

> [Visualisation of an eventloop](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)

### Essência

## 5. filtrar, reduzir, mapear

### Explicação

**map**, **filter** e **reduce** são três métodos de array que iteram (loop!) em todo o array e realizam um cálculo ou uma transformação.
Eles têm em comum que retornam um novo array baseado nas transformações/cálculos.

> [definição de MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map): o método **map()** cria um novo array com o resultados de chamar uma função fornecida em cada elemento na matriz de chamada.

> [definição de MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter): O método **filter()** cria um novo array com todos elementos que passam no teste implementado pela função fornecida

> [definição de MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce): O método **reduce()** executa um **reducer* * função (que você fornece) em cada membro da matriz, resultando em um único valor de saída†.

Escrevendo as funções você mesmo: https://github.com/HackYourFuture/fundamentals/blob/master/fundamentals/map_filter.md

### Exemplo

```Javascript
const números = [1, 2, 3, 4];
const quadrado = x => x * x;
const squaredNumbers = números.map(quadrado);

console.log(squaredNumbers); // -> [ 1, 4, 9, 16 ]
```

```Javascript
const números = [1, 2, 3, 2];
const éDois = x => x === 2;
const Dois = números.filtro(isDois);

console.log(Dois); // -> [ 2, 4 ]
```

```Javascript
const números = [1, 2, 3, 4];

soma const = (a, b) => a + b;
const total = números.xxx(soma, 0);

console.log(total); // -> 10
```

### Exercício

Preencha o xxx com map, filter ou reduce:

```Javascript
const números = [1, 2, 3, 4];
const dobrou = números.xxx(item => item * 2);
console.log(dobrado); // [2, 4, 6, 8]
```

```Javascript
const números = [1, 2, 3, 4];

const vezes = (a, b) => a * b;
const total = números.xxx(vezes, 0);

console.log(total); // -> 10
```

```Javascript
const números = [1, 2, 3, 4];
const pares = números.xxx(item => item % 2 === 0);
console.log(evens); // [2, 4]
```

Yash fez um exercício muito legal (com respostas):
https://github.com/yash-kapila/HYF-JS2-Week2/tree/master/src

### Essência

Métodos fáceis para transformar arrays, o que você terá que fazer com bastante frequência, mantendo o array original intacto.
Você pode vê-lo como um atalho. Claro que você pode escrever esses métodos muitas vezes, mas 'eles' já fizeram isso por você
