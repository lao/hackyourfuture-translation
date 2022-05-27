# Lendo Material Usando API's Semana 2

## Agenda

Estes são os tópicos da semana 2:

1. [Application Programming Interface (API)](https://study.hackyourfuture.net/#/the-internet/api)
   - APIs públicas/privadas
   - Conexão com APIs
2. [Buscar API](https://study.hackyourfuture.net/#/the-internet/fetch)
3. [Async/Await](https://study.hackyourfuture.net/#/javascript/modern-js)
   - Capturando erros com try/catch
4. [Preparação da entrevista](https://github.com/HackYourFuture/interviewpreparation)

## Metas da semana

Todas as informações detalhadas sobre cada conceito estão em seu livro de estudo. A explicação do objetivo a seguir irá ligá-lo ao local correto para começar a estudar. Leia a descrição do objetivo uma vez para ter uma ideia do que você aprenderá e, em seguida, acesse os diferentes links (da agenda ou desta lista de objetivos).

Esta semana, finalmente aprendemos o que é uma API, embora você provavelmente já tenha uma ideia. Leia a explicação completa [aqui](https://study.hackyourfuture.net/#/the-internet/api). Agora que sabemos o que estamos fazendo, vamos aprender a fazer!

Existem muitas maneiras de solicitar dados de uma API, inicialmente tudo era feito usando [XMLHttpRequest](https://developer.mozilla.org/nl/docs/Web/API/XMLHttpRequest), mas agora quase não é mais usado. É bom saber que existe e você verá em alguns vídeos, mas não é algo para se focar. Em seguida, bibliotecas como [Axios](https://github.com/axios/axios) foram criadas para facilitar o uso. Atualmente, todos os navegadores modernos, no entanto, têm uma [Fetch API](https://study.hackyourfuture.net/#/the-internet/fetch) integrada que facilita ainda mais a conexão com APIs de seu aplicativo front-end. Portanto, para nosso currículo, vamos nos concentrar apenas na API Fetch e apenas mencionar as outras maneiras para que você saiba do que as pessoas estão falando quando ouvir esse termo.

Na semana passada, aprendemos sobre Promises e com o aumento do uso de promessas, o JavaScript moderno introduziu algumas novas sintaxes que podem ser usadas com essas promessas. Dê uma olhada na seção sobre Async/await na página JavaScript moderna do seu livro de estudos [aqui]((https://study.hackyourfuture.net/#/javascript/modern-js)) agora que você sabe quais são as promessas para que você saiba o que ele faz.

Você provavelmente se perguntará agora qual é a melhor maneira de lidar com código assíncrono e a resposta é que não há melhor maneira. Geralmente, os retornos de chamada são ótimos para aplicativos simples, mas entre no inferno do retorno de chamada se as coisas ficarem muito complicadas. Promessas com cadeias `.then` são ótimas para situações mais complexas onde o encadeamento pode ser muito poderoso, mas pode ser um pouco difícil de seguir para pessoas que não têm muita experiência com elas. Usar async/await faz com que o código pareça um pouco mais síncrono novamente e isso pode facilitar o acompanhamento. No entanto, torna um pouco mais complexo lidar com erros ou situações em que algo absolutamente precisa ser feito (um 'finalmente' é inestimável nessas situações). Então, cabe a você decidir com base na situação o que usar.

## Formação profissional II (preparação para entrevista)
Se você ainda não terminou todo o material, continue com ele esta semana.

## Finalizado?

Você terminou de passar pelos materiais? Toca aqui! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
