# Dicas da equipe de desenvolvimento
Trabalhar em um projeto com várias pessoas traz muitos benefícios, mas também traz alguns desafios. Queremos dar algumas dicas de como fazer a transição para o projeto onde você não está mais estudando/aprendendo individualmente.

Boa sorte no projeto! Torná-lo incrível e seu currículo será muito feliz.

## Mantenha os PRs pequenos e focados!
No início da semana, certifique-se de pensar nas `etapas para concluir` o recurso. Você *não* deve fazer tudo de uma vez, mas fazer tudo em pequenos passos. Faça pequenos passos que sejam funcionalidades por si só, para que sempre que você terminar uma etapa você já possa criar um PR e ter alguém revisá-lo. A chave para manter uma base de código limpa é manter as relações públicas gerenciáveis.

Um PR enorme é muito difícil de revisar e tornará muito mais fácil para os bugs entrarem no ambiente de produção, o que é a pior coisa que pode acontecer. Portanto, mantenha os passos pequenos e facilite para todos!

Por exemplo, se você estiver criando uma lista de usuários que exija que os nomes e avatares do usuário sejam exibidos na tela, você pode dividir isso em 4 etapas diferentes:
- Criar um modelo de usuário
- Crie um endpoint para todos os usuários com roteadores e controladores
- Crie um componente visual que mostre o nome e o avatar de um único usuário
- Crie uma página que pegue a lista do endpoint e mostre nosso componente na etapa 3 para todos os usuários

Cada um desses PRs é gerenciável e revisável em um curto espaço de tempo, o que torna muito mais fácil para seus colegas revisarem. Os 3 primeiros não alteram a UI/UX de forma alguma, portanto, é seguro enviar para a base de código sem ter o restante implementado ainda.

## Não se esqueça do UX!
Não temos um designer na equipe, o que significa que você é responsável pelo design do aplicativo. Lembre-se de que o [repositório de diretrizes de design](https://github.com/HackYourFuture/design_guidelines) fornece muitas dicas sobre como fazer um aplicativo parecer bom!

## Trabalhe em equipe
Se você está lutando com um bug ou não tem certeza de como implementar algo, poste no canal da turma! Agora você tem uma equipe de desenvolvimento para apoiá-lo. Às vezes, tudo o que você precisa é de alguém para explicar seu problema para chegar a uma solução. Isso acontece o tempo todo em um ambiente de trabalho.

## O que fazer uma vez terminado?
Algumas funcionalidades serão feitas antes de outras, mas o sprint só é feito quando tudo estiver pronto! Então, quando terminar, veja qual outra equipe pode precisar de ajuda! Somente se ninguém mais precisar de ajuda é bom pegar um novo problema ou possivelmente usar o tempo para refatorar algum código! Como um de nossos mentores sempre disse: 'código nunca é feito!'.
