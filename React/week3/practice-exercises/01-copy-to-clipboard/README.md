# Copiar para área de transferência

Você pode fazer um gancho que pegue uma entrada do usuário e a copie para a área de transferência do computador?

1. Crie um novo aplicativo via `create-react-app`
2. Adicione um novo componente, com um campo de texto simples que o usuário pode digitar.
3. Adicione outro componente que consiste em um botão.
4. Armazene a entrada do usuário. (Pergunta bônus: como você deve armazenar esse valor? No componente? API de contexto? App.js?)
5. É hora de fazer nosso anzol!

- Crie uma pasta `hooks` em seu projeto, e dentro crie um arquivo chamado `useCopy.js`.
- Crie (e exporte!) uma função chamada `useCopy` e dentro dela crie outra função `handleCopy`.
- Handle copy deve ter uma string como parâmetro, copie esse parâmetro para a área de transferência.
- Para isso, vamos precisar do [objeto navigator](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/clipboard). Procure o método que adiciona texto à área de transferência do usuário.
- Retorna a função `handleCopy`. (Para uma sintaxe familiar, você pode querer exportá-la assim: `return [handleCopy]`.)

6. Importe `handleCopy` da função `useCopy`. Com base em como você armazenou a entrada do usuário, você precisará chamá-la em lugares diferentes, mas certifique-se de que ela seja acionada por um clique de botão.
7. Vamos ver se funciona!

Extra:

- Podemos fazer e devolver algo mais deste gancho? Talvez algo para indicar que o usuário copiou para a área de transferência?
- Podemos fazer alguma coisa para garantir que o tipo de dados seja válido? E se os usuários estiverem inserindo letras em um campo de número de telefone?
