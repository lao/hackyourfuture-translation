# Plano de aula Semana 2

O objetivo desta aula é ensinar ao aluno sobre:

- Como fazer `Requisições HTTP` dentro de um componente React
- Como testar no React

## Conceitos principais

## 1. Fazendo requisições HTTP dentro de um componente React

### Explicação

Fazer requisições HTTP é uma tarefa essencial do frontend. No React, fazemos essas solicitações em pontos específicos: (1) após uma ação do usuário (como um clique de botão) ou (2) em um determinado ponto do ciclo de vida do componente.

### Exemplo

``` jsx
// 1. Após uma ação do usuário
const Usuários = () => {
  const [usuários, setUsers] = useState([]);

  const fetchUsers = assíncrono () => {
    resposta const = await fetch("https://jsonplaceholder.typicode.com/users");
    const users = await response.json();

    setUsers(usuários);
  };

  Retorna (
    <div>
      {
        // Faça algo com os usuários...
      }
      <button onClick={fetchUsers}>Consiga usuários!</button>
    </div>
  );
};
```

Às vezes, também queremos fazer solicitações HTTP antes ou depois de um componente ser renderizado/atualizado:

``` jsx
// 2. Em um determinado ponto do ciclo de vida do componente
const Usuários = () => {
  const [usuários, setUsers] = useState([]);

  const fetchUsers = assíncrono () => {
    resposta const = await fetch("https://jsonplaceholder.typicode.com/users");
    const users = await response.json();

    setUsers(usuários);
  };

  useEfeito(() => {
    // Busca os usuários após o componente ser renderizado
    buscarUsuarios();
  }, []);

  Retorna (
    <div>
      {
        // Faça algo com os usuários...
      }
    </div>
  );
};
```

### Exercício

Peça aos alunos para escreverem um componente que use `useEffect` para buscar dados e preencher o estado:

- Use o gancho `useEffect` e `useState`
- Envolva a solicitação HTTP em uma função
- povoar o estado
- Exibe a propriedade `title`
- Use o seguinte endpoint de API: https://jsonplaceholder.typicode.com/todos/1

Depois, peça a 2 alunos que expliquem o que fizeram.

### Essência

Enviamos solicitações HTTP no React como consequência da interação do usuário (como um clique de botão) ou quando o componente é renderizado/atualizado. Fazemos isso em uma função separada que executamos, seja em um evento (como `onClick`) ou após um componente ser renderizado/atualizado (com `useEffect`).
