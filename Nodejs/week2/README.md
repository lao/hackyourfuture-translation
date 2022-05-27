# Lendo Material Node.js Semana 2

## Agenda

1. [O que é um aplicativo CRUD?](https://study.hackyourfuture.net/#/definitions/crud)
2. [Como você projeta uma API?](https://study.hackyourfuture.net/#/the-internet/designing-apis.md)
   - O que é a Transferência Representacional do Estado (REST)?
   - O que é uma API RESTful?

3. [Fazendo uso de outras APIs](https://study.hackyourfuture.net/#/node-js/consuming-apis.md)
   - Como consumir uma API externa?
   - Exemplo de middleware
4. [Teste de API automatizado](https://study.hackyourfuture.net/#/testing/api-testing.md)
   - [Carteiro](https://www.postman.com/use-cases/api-testing-automation/)
   - [superteste](https://www.npmjs.com/package/supertest)

## 0. Vídeo-aulas

Seu professor Andrej fez videoaulas para o material desta semana que complementa o material de leitura. Você pode encontrá-los aqui: [Vídeos 7 - 11](https://www.youtube.com/playlist?list=PLVYDhqbgYpYXpc_l_Vlj8yz3LjgkkWXnn) (até e incluindo Middleware)

<a href="https://www.youtube.com/playlist?list=PLVYDhqbgYpYXpc_l_Vlj8yz3LjgkkWXnn" target="_blank"><img src="../assets/andrej.png" width="600" height="350 " alt="HYF Vídeo" /></a>

## Metas da semana

Esta semana vamos aprender mais alguns termos que surgem quando discutimos APIs. Vamos começar com o termo CRUD, leia sobre o que é [aqui](https://study.hackyourfuture.net/#/definitions/crud).

Você deve ter notado que as quatro ações CRUD se alinham bem com os métodos HTTP da semana passada:

1. Criar -> POSTAR
2. Leia -> OBTER
3. Atualizar -> COLOCAR
4. Excluir -> EXCLUIR

Tendo coberto esses termos, agora podemos examinar uma das arquiteturas de API mais comuns, a API REST. Dê uma olhada na explicação deste design [aqui](https://study.hackyourfuture.net/#/the-internet/designing-apis.md).

Também analisaremos o aprimoramento de sua API. Uma coisa a ter em mente é que sua própria API pode fazer uso de outras APIs para determinadas funcionalidades! Na verdade, isso acontece o tempo todo e é uma ótima maneira de dividir a separação de interesses. Veja como isso funciona [aqui](https://study.hackyourfuture.net/#/node-js/consuming-apis.md).

Por fim, é hora de aprender a automatizar os testes de nossas API's. Isso pode ser feito no Postman usando [testsuites automatizados](https://www.postman.com/use-cases/api-testing-automation/), mas vamos fazer isso usando código, semelhante ao teste de unidade aprendido em JavaScript . Dê uma olhada [aqui](https://study.hackyourfuture.net/#/testing/api-testing.md) sobre como fazer isso usando o [superteste](https://www.npmjs.com/package/ superteste) biblioteca.

## Finalizado?

Você terminou de passar pelos materiais? Toca aqui! Se você se sentir pronto para ser prático, clique [aqui](./MAKEME.md).
