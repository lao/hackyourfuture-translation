# Formatação de código

Ao escrever seu código JavaScript, você precisa levar em consideração dois tipos de consumidor:

1. Leitores humanos (você mesmo, seus colegas de trabalho, colegas, você mesmo daqui a um ano, etc.).
2. O mecanismo JavaScript.

Começando com o último, o mecanismo JavaScript não se preocupa com a formatação do código e fica perfeitamente feliz em trabalhar com nomes de variáveis de uma letra. A 'minificação' é um processo que às vezes é usado para reduzir o tamanho dos arquivos JavaScript hospedados em um servidor da Web para que eles demorem menos tempo para serem transferidos por uma rede para um navegador da Web. O código abaixo mostra algum código 'minificado'.

``` js
const o=[6,3,10,1].reduce((o,c)=>(o.push(c*c),o),[]);console.log(o);
```

Claramente, o código acima é incompreensível para humanos. O código original é mostrado abaixo, bem formatado para benefício dos leitores humanos.

``` js
const arr = [6, 3, 10, 1];
const quadrados = arr.reduce((acc, elem) => {
  acc.push(elem * elem);
  retorno acc;
}, []);
console.log(quadrados); // -> [36, 9, 100, 1]
```

Em comparação com o código minificado, o código original faz uso de novas linhas e recuo para mostrar a estrutura e usa nomes de variáveis significativos, exclusivamente para o benefício do leitor humano.

Com o tempo, surgiu uma maneira padrão de formatar código JavaScript (na verdade, esse padrão é bastante comum em todas as linguagens derivadas da linguagem C, incluindo JavaScript, mas também C++, Java e C#).

Nas próximas seções, discutiremos as convenções de formatação de código mais importantes para JavaScript. No final deste documento você encontrará algum código que está formatado de acordo com essas regras.

## Linhas em branco

Use uma única linha em branco para separar blocos de código relacionado. Isso é semelhante a separar parágrafos com uma linha em branco em um texto escrito.

## Chaves

Chaves são usadas para iniciar e terminar blocos de código, geralmente como parte de uma instrução `if`, `switch`, `while` ou `for`. A chave de abertura deve ser colocada no final de uma linha. A chave de fechamento deve estar alinhada com o início da linha que iniciou o bloco de código.

``` js
se (condição) {
  // ...
} senão {
  // ...
}
```

## Recuo

Blocos de código dentro de chaves devem ser indentados por 2 ou 4 espaços (escolha um ou outro e, em seguida, mantenha-o). No caso de blocos de código aninhados, para cada nível de aninhamento, a quantidade de recuo deve ser incrementada pela quantidade padrão (2 ou 4):

``` js
função minhaFunção() {
  se (condição) {
    // ...
  } senão {
    // ...
  }
}
```

## Espaçamento

- Adicione um espaço após as palavras-chave, por exemplo `if (`, `for (`
- Adicione um espaço após um `,` `;` (em um loop `for`) e `:` (por exemplo, chaves de objeto)
- Adicione um espaço antes e depois dos operadores, por exemplo `a + b`

## Use VSCode para JavaScript bem formatado

Em vez de continuar e especificar cada pequeno detalhe sobre como formatar o código JavaScript em um formato padrão, podemos chamar a ajuda do VSCode.

O VSCode vem com um formatador de código integrado para JavaScript. Para formatar o documento atual de maneira padrão, pressione a seguinte combinação de teclas:

| | Janelas | Mac | Linux |
| --------- | ------- | ----- | ----- |
| **Formatar Documento** (tornar bonito) | Shift-Alt-F | ⇧⌥F| Ctrl-Shift-I |

Apenas crie o hábito de fazer esta saudação de três dedos antes de salvar seu documento ou sempre que ficar confuso e você estiver pronto para ir!

> Existem várias configurações de usuário que você pode aplicar no VSCode para habilitar a formatação automática conforme você digita (ou cola). Consulte [Dicas do VSCode](../VSCodeTips/README.md#customise-vscode-settings) para obter mais detalhes.
>

## ESLint

[ESLint](https://eslint.org/) é uma ferramenta que pode verificar seu código JavaScript em busca de erros comuns e práticas inadequadas. Veja [Dicas do VSCode](../VSCodeTips/README.md#installation-instructions) sobre como configurá-lo.

O ESLint é configurado por meio de regras definidas pelo usuário que especificam o que verificar. Essas regras devem ser definidas em um arquivo chamado `.eslintrc.json` colocado na pasta raiz do repositório do seu projeto. Para as palestras e trabalhos de casa dos três módulos HYF JavaScript, é recomendado que você crie um arquivo `.eslintrc.json` e copie e cole o conteúdo mostrado abaixo nesse arquivo.

Mais informações sobre as regras do ESLint [aqui](https://eslint.org/docs/rules/).

Certifique-se de corrigir quaisquer erros e avisos que o ESLint produz antes de considerar seu código JavaScript pronto!

``` json
{
  "env": {
    "navegador": verdadeiro,
    "commonjs": verdadeiro,
    "es6": verdadeiro,
    "nó": verdadeiro
  },
  "parserOptions": {
    "ecmaVersão": 2017,
    "ecmaFeatures": {
      "jsx": verdadeiro
    },
    "sourceType": "módulo"
  },
  "estende": [
    "eslint:recomendado"
  ],
  "as regras": {
    "no-const-assign": "avisar",
    "não-este-antes-super": "avisar",
    "no-undef": "aviso",
    "no-inalcançável": "avisar",
    "no-unused-vars": "aviso",
    "construtor-super": "avisar",
    "valid-typeof": "aviso",
    "no-var": "aviso",
    "prefer-const": "avisar",
    "no-multiple-empty-lines": "aviso",
    "eol-último": [
      "erro",
      "sempre"
    ],
    "sem console": "desligado",
    "camelcase": "aviso",
    "eqeqeq": [
      "erro",
      "sempre",
      {
        "null": "ignorar"
      }
    ],
    "semi": [
      "avisar",
      "sempre"
    ]
  }
}
```


## Exemplo de código bem formatado

(Com a ajuda do formatador VSCode e ESLint.)

``` js
'usar estrito';

placa const = [
  ['T', 'T', '.', 'F'],
  ['T', '.', '.', '.'],
  ['.', '.', '.', '.'],
  ['R', '.', '.', 'W']
];

const robô = {
  x: 0,
  y: 0,
  dir: 'para cima',
};

let flagAlcançado = false;
deixe movimentos = 0;

tabuleiro.reverso();

const trilhaIndicators = {
  esquerda: '←',
  à direita: '→',
  para cima: '↑',
  para baixo: '↓'
};

função render() {
  console.log('\n ' + movimentos + ':');
  for (let row = board.length - 1; row >= 0; row--) {
    const células = quadro[linha];
    deixe linha = '';
    for (let col = 0; col < células.comprimento; col++) {
      linha += ' ' + células[col] + ' ';
    }
    console.log(linha);
  }
  if (flagAlcançado) {
    console.log('\nHurray! Flag alcançado em ' + movimentos + ' passos!');
  }
}

função mover() {
  deixe x = robô.x;
  deixe y = robô.y;

  switch (robot.dir) {
    caso 'up':
      y = y < board.length - 1 ? y + 1 : y;
      pausa;
    caso 'para baixo':
      y = y > 0? y - 1 : y;
      pausa;
    caso 'esquerda':
      x = x > 0? x - 1 : x;
      pausa;
    caso 'certo':
      x = x < placa[y].comprimento - 1 ? x + 1 : x;
      pausa;
  }

  const cellContents = board[y][x];

  if (cellContents === '.' || cellContents === 'F') {
    board[robot.y][robot.x] = trailIndicators[robot.dir];
    robô.x = x;
    robô.y = y;
    placa[y][x] = 'R';
    if (cellContents === 'F') {
      flagAlcançado = true;
    }
  }

  movimentos += 1;
  render();
}

function turn(turnDirection) {
  if (turnDirection !== 'left' && turnDirection !== 'right') {
    console.log('ignorando curva inválida', turnDirection);
  }
  switch (robot.dir) {
    caso 'up':
      robot.dir = turnDirection === 'esquerda' ? 'esquerda direita';
      pausa;
    caso 'para baixo':
      robot.dir = turnDirection === 'esquerda' ? 'direita esquerda';
      pausa;
    caso 'esquerda':
      robot.dir = turnDirection === 'esquerda' ? 'baixo cima';
      pausa;
    caso 'certo':
      robot.dir = turnDirection === 'esquerda' ? 'cima baixo';
      pausa;
  }
}

render();

//início das instruções do jogo do robô
jogada();
Vire à direita');
jogada();
jogada();
jogada();
Vire à esquerda');
jogada();
jogada();
// fim das instruções do jogo do robô
```

