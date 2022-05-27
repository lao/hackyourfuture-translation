# Semana de exercícios preparatórios 1

Como etapa de preparação para as próximas perguntas e respostas, você trabalhará no exercício a seguir. O resultado esperado é uma lista de instruções SQL `CREATE TABLE` representando as tabelas que você irá projetar.

Sugerimos que você primeiro pense no design das tabelas (nomes, colunas, tipos) e, em seguida, prossiga para escrever as instruções SQL. Dessa forma, você está pensando no problema que está tentando resolver (criando um banco de dados que contém dados) em vez da implementação primeiro (criando um conjunto de instruções SQL).

## Exercício

Projete as tabelas para um banco de dados que contém receitas de alimentos.

- Cada receita deve ter um nome, uma ou mais categorias, uma lista de ingredientes e uma lista de passos a seguir para completar a receita.
- Muitas receitas podem compartilhar os mesmos ingredientes ou a mesma lista de etapas (por exemplo, "cozinhar macarrão de acordo com as instruções da embalagem" pode ser uma etapa regular vista em várias receitas).
- Você pode criar seus próprios dados, com foco em receitas japonesas, de bolo e vegetarianas. Você pode encontrar alguma inspiração online, mas mantenha-o simples!

Você não precisa escrever nenhuma consulta específica agora, mas o design deve considerar que executaremos consultas nas tabelas para extrair dados como:

- Você deve ser capaz de listar todas as receitas.
- Você deve ser capaz de listar receitas em uma única categoria (saladas, mexicana, etc).

Algumas perguntas que você pode se fazer:

- Quais entidades você consegue identificar no problema acima?
- Quais tabelas você precisa criar para armazenar os dados acima?
- Quais são as relações entre essas entidades?

Há um [vídeo curto](https://www.youtube.com/watch?v=C3icLzBtg8I) explicando como os relacionamentos funcionam, e você pode usar isso como inspiração. Vamos expandir este tópico na próxima semana.
