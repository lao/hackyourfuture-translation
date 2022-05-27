# Hora da festa

Você está animado para a maior festa do planeta? Estamos e gostaríamos de convidar a todos, mas o número de vagas é limitado.

Comece dando uma olhada na documentação da API: https://reservation100-sandbox.mxapps.io/rest-doc/api.
Ao ler a documentação, certifique-se de observar o seguinte:

- Quais métodos estão disponíveis (GET ou POST)?
- Qual é a rota?
- Que cabeçalhos são esperados?
- O que deve conter o corpo da solicitação e como deve ser formatado?

Depois de entender a API, escreva uma função que faça uma reserva e registre a resposta no console. Siga os passos:

1. Use `node-fetch` para fazer uma solicitação com os cabeçalhos e o formato do corpo corretos
2. Use `async/await` e `try/catch`
3. Imprima a resposta no console

Dicas:

- Para definir os cabeçalhos use `fetch(<URL>, { headers: { 'XXXX': 'YYYY' } }`
- A documentação em https://www.npmjs.com/package/node-fetch pode ser de grande ajuda
