# Plano de aula Semana 3

## Agenda

O objetivo desta aula é ensinar ao aluno sobre:

- Roteamento do lado do cliente
- O que é a API de contexto

## Conceitos Fundamentais

1. Roteamento do lado do cliente

- O roteamento do lado do servidor é a norma, mas com o surgimento do JavaScript e dos SPAs modernos, veio o **roteamento do lado do cliente**
- Na alteração de URL **sem solicitação ao servidor** (e, portanto, sem atualização de página), **apenas alteração de estado do aplicativo e ajuste de URL**
- Para React, a biblioteca de terceiros **React-Router** é a mais popular
- Conceitos mais importantes: `<BrowserRouter />`, `<Route />`, `<Link />`, `<Switch />`, a prop `location` e o objeto `history`

_Explique o seguinte exemplo: [Exemplo básico](https://reacttraining.com/react-router/web/example/basic)_

_Exercício: ajude os alunos a recriar o Exemplo Básico (sem olhar para o código)_

## Construa com os alunos

Para ilustrar o funcionamento do React-Router, construa o seguinte pequeno aplicativo com os alunos.

- [Roteador Básico](../../examples/router-example)

Faça um menu de navegação básico que use React-Router.

- Use `react-router-dom`
- Renderize um componente diferente para cada rota

_Depois de mostrar o exemplo, esconda seu código e peça aos alunos que recriem a mesma coisa_

2. Roteamento do lado do servidor

- Refreshador de roteamento: o mecanismo pelo qual `requests` (conforme especificado por uma mudança de URL ou método HTTP) são `enviadas para um endpoint no servidor`, que então executa o código que trata a solicitação.
- O roteamento do lado do servidor acontece `quando o cliente envia uma solicitação ao servidor`, geralmente **acionado por uma alteração de URL**

## 2. Estado global com `API de contexto`

- O contexto fornece uma maneira de passar dados através da árvore de componentes sem ter que passar adereços manualmente em todos os níveis.
- O contexto é projetado para compartilhar dados que podem ser considerados “globais” para uma árvore de componentes React, como o usuário autenticado atual, tema ou idioma preferencial.

_Mostrar instância de como criar `context`, passar o `Provider` e o `Consumer` e mostrar o valor. Depois, peça aos alunos que façam o mesmo_
