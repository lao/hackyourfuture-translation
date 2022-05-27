# Gerador de piadas aleatórias]

Nunca fique sem piadas com o Gerador de Piadas Aleatórias!

Neste exercício, usaremos o seguinte endpoint de API: `https://official-joke-api.appspot.com/random_joke`

1. Crie 2 componentes funcionais: `<RandomJoke>` e `<Joke>`
2. Dentro de `<RandomJoke>`, crie uma variável de estado chamada `joke` (com estado inicial `{}`) e o manipulador de estado `setJoke`
3. Use o gancho `useEffect` para fazer uma chamada de API assíncrona para o endpoint da API. Coloque o resultado final na variável de estado usando `setJoke`
4. Agora passe a variável de estado reatribuída `joke` para o componente `<Joke>`
5. Dentro do componente `<Joke>`, exiba os atributos `setup` e `punchline` em 2 tags `<p>`
6. Confira seu trabalho importando seus componentes para o componente de nível superior, que é `<App>`
