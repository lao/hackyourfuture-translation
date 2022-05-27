# Exercício de preparação - Tratamento de erros

Até esta semana, o código em que você está trabalhando é principalmente seu e geralmente é muito estático, o que significa que, se funcionar uma vez, provavelmente continuará funcionando da mesma maneira. Ao interagir com APIs externas pela internet, isso sai pela janela. Você não tem controle sobre os dados que a API fornece e, embora geralmente tudo bem, a Internet sempre não será confiável. Isso significa que seu código precisa ser capaz de lidar com isso quando algo der errado e informar o usuário.

Neste exercício, vamos nos concentrar na parte de busca e tratamento de erros ao trabalhar com uma API, que você pode usar para trabalhar com qualquer outro código onde um possível problema possa ocorrer. O `index.js` fornece instruções sobre o que fazer, já existe algum código lá, mas sinta-se à vontade para alterá-lo se necessário.

O comportamento esperado é o seguinte:

- Quando você pressiona o botão **Obter dados** com a caixa de seleção **Usar URL inválido** **desmarcada**, os dados da API Pokemon serão buscados e renderizados como JSON na página.
- Ao pressionar o botão com a caixa de seleção **marcada**, uma mensagem de erro HTTP será renderizada na página.
## Coisas para pensar

- Se você olhar para o `index.html` você pode ver que nosso erro de renderização é colocado em um elemento `div` normal, mas nosso pokemon json é colocado em um elemento `pre`. Por que é que?
- Os comentários dizem para tratar o erro na função principal. Quais você acha que são as vantagens de fazê-lo desta forma? E se você fizesse o tratamento de erros na função `fetchJSON`?
- Alguns alunos nos perguntam por que não apenas colocar blocos `try/catch` ao redor da função principal e tê-la como o local para capturar todos os erros. Por que você acha que não sugerimos fazer isso?