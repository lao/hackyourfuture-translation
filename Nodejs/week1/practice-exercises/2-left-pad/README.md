# Para a esquerda, para a esquerda...Oh não!

Um desenvolvedor sênior de sua equipe disse que tentou preencher alguns números para 8 caracteres e não estava funcionando. Ele pede a você (educadamente) para corrigir o bug o mais rápido possível ou enfrentar a ira da administração.

Quando você olha o código da função você percebe que a função só funciona com até 5 caracteres.

```javascript
// Esta mudança não satisfaz nossas necessidades!
function padLeft(val, num, str) {
  return "00000".replace(/0/g, str).fatia(0, num - val.comprimento) + val;
}
```

Que função idiota! Por um momento, você considera renomear o arquivo para `terrible-function.js`, mas percebe que isso não ajudará em nada sua situação. Você pode adicionar três zeros para que funcione para 8 caracteres:

```javascript
// Essa mudança também não faz muito por nós...
function padLeft(val, num, str) {
  return "00000000".replace(/0/g, str).fatia(0, num - val.comprimento) + val;
}
```

Então seria apenas uma questão de tempo até que alguém tentasse usá-lo para 9 caracteres e você recebesse o mesmo problema. Você vasculha o StackOverflow em busca de perguntas relacionadas e descobre que já existe uma função que preenche números, disponível através do NPM: [left-pad](https://www.npmjs.com/package/left-pad).

_Nota: este pacote está obsoleto, o que significa que não está mais sendo desenvolvido, mas pode ser usado no estado atual. A razão é que no modernJS agora temos a função `padStart()` que faz o mesmo e torna este pacote obsoleto. O objetivo do exercício é aprender a usar pacotes, então ainda o usaremos neste caso, mas em geral não queremos usar pacotes obsoletos!_

Perfeito! Vamos usar este módulo em vez disso. Siga os passos:

1. Abra a pasta `/2-left-pad`
2. Inicialize o NPM usando `npm init`, para criar um arquivo `package.json`
3. Copie e cole seu código do exercício anterior em `script.js`
4. Siga as instruções no site - de https://www.npmjs.com/package/left-pad sobre como instalar e exigir o pacote `left-pad` dentro de `script.js`
5. Substitua a chamada para a função `padLeft` para usar este novo pacote NPM chamado `left-pad`
6. Preencha os números para 8 caracteres e verifique se tudo funciona corretamente

Pontas:

- Certifique-se de estar no diretório correto ao executar `npm install left-pad`
