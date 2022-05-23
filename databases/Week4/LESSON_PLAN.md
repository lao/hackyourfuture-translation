# Bancos de dados do plano de aula Semana 4

O plano de aula é escrito principalmente para os professores, para que eles possam
use exemplos e anedotas deste documento em conjunto com o README
e explicar melhor os conceitos na aula.

## Tópicos

1. Modelagem de dados incorporados vs normalizados
2. Operações avançadas do MongoDB
3. Paginação
4. Índices no MongoDB
5. Transações no MongoDB
6. Bancos de dados SQL vs NoSQL

## 1. Modelagem de dados incorporada x normalizada

### Explicação

1. Embutido significa que as informações são armazenadas em um subobjeto em uma coleção
2. Normalizado significa que as informações são armazenadas em coleções diferentes, mas fazem referência umas às outras

### Exemplo

Vamos dar uma olhada em um banco de dados de log de bugs.

#### A maneira incorporada

``` js
const erros = [
  {
    timestamp: new Date(),
    página: "sobre",
    stacktrace: "", // removido para maior clareza
    repórter: {
      e-mail: "rob@thebugcreator.com",
      nome: "Rob",
    },
  },
];
```

#### A maneira normalizada

``` js
contas const = [
  {
    id: ObjectId("507f191e810c19729de86032"),
    e-mail: "rob@thebugcreator.com",
    nome: "Rob",
  },
];

const erros = [
  {
    timestamp: new Date(),
    página: "sobre",
    stacktrace: "", // removido para maior clareza
    reporterId: ObjectId("507f191e810c19729de86032"),
  },
];
```

### Exercício

Discuta as diferenças e quais são as vantagens/desvantagens de cada abordagem. Por exemplo:

Incorporado permite consultas mais rápidas.
Normalizado permite menos duplicação de dados.

### Essência

Existem vantagens em ambas as abordagens e, na natureza, você terá que decidir qual usar sempre.

## 2. Operações avançadas do MongoDB

### Explicação

1. O comando `sort` permite classificar os dados que você recebe de sua consulta.
2. O comando `limit` permite limitar quantos itens você recebe de volta da sua consulta.
3. O comando `aggregate` permite a combinação e cálculo de dados em uma ou mais coleções.

### Exemplo

Vamos supor um banco de dados de log com as seguintes informações:

``` js
const erros = [
  {
    timestamp: new Date('2000-06-07T11:24:00'),
    página: "sobre",
    stacktrace: "", // removido para maior clareza
    reporterId: ObjectId("507f191e810c19729de86032"),
  }, {
    timestamp: new Date('2000-06-06T12:23:00'),
    página: "sobre",
    stacktrace: "", // removido para maior clareza
    reporterId: ObjectId("507f191e810c19729de86032"),
  }. {
    timestamp: new Date('2000-06-08T12:33:00'),
    página: "contato",
    stacktrace: "", // removido para maior clareza
    reporterId: ObjectId("e810507f191de86032c19729"),
  }, {
    timestamp: new Date('2000-06-06T12:34:00'),
    página: "casa",
    stacktrace: "", // removido para maior clareza
    reporterId: ObjectId("e810507f191de86032c19729"),
  }
];
```

#### Ordenar

Se quisermos classificar a consulta de localização no carimbo de data e hora para encontrar os bugs mais recentes, podemos executar a seguinte consulta:

``` js
client.db("log").collection("bugs").find().sort({ timestamp: -1 });
```

#### Limite

A consulta acima retornará todos os bugs, o que não é ótimo, portanto, podemos usar o comando limit da seguinte maneira:

``` js
cliente
  .db("registro")
  .collection("bugs")
  .encontrar()
  .sort({ timestamp: -1 })
  .limit(10);
```

Isso fornecerá apenas os últimos 10 bugs, o que é mais gerenciável. Note que você pode colocar os comandos `sort` e `limit` em qualquer ordem!

#### Agregado

Digamos que queremos ter uma contagem de quantos bugs aparecem por página. Para isso podemos fazer o seguinte:

``` js
cliente
  .db("registro")
  .collection("bugs")
  .agregar([
    {
      $grupo: {
        _id: "$página",
        contagem: { $contagem: {} },
      },
    },
  ]);
```

Isso devolverá um objeto com o campo page no campo `_id` e o número de bugs que foram registrados nessa página está no campo `count`!

### Exercício

Pense em algumas outras coisas para classificar ou calcular e escrever o código para fazer isso.

### Essência

O MongoDB faz muito por você, a sintaxe é um pouco diferente da conhecida, mas a documentação é bem detalhada então aproveite!

## 3. Paginação

Usando a mesma coleção de bugs, vamos examinar a paginação baseada em deslocamento e cursor usando essa coleção.

### Explicação

Vá a diferentes lojas online e veja suas páginas de resultados para mostrar a paginação em ação.

### Exemplo

Dado o banco de dados de bugs na seção anterior, vamos implementar os dois tipos de paginação:

#### Com base em deslocamento

``` js
cliente
  .db("registro")
  .collection("bugs")
  .encontrar()
  .sort({ timestamp: -1 })
  .limit(10)
  .skip(20);
```

Isso pularia 20 resultados e mostraria os próximos 10. Assim seria na página 3 se mostrarmos 10 resultados por página!

#### Baseado em cursor

``` js
const lastBugs = aguarda cliente
  .db("registro")
  .collection("bugs")
  .encontrar({
    carimbo de data/hora: { $lt: próximo || Nova data() },
  })
  .sort({ timestamp: -1 })
  .limit(10);

const cursorToGiveToUser = lastBugs[latestBugs.length - 1].timestamp;
```

Duas coisas importantes aqui:

- Você precisa sempre ter os dados classificados se fizer uma classificação baseada em cursor, pois inclui o ponto em que está na consulta.
- Você deve fornecer ao usuário do seu endpoint as informações que ele precisa enviar para a próxima consulta

No código acima fazemos isso com o timestamp, em outras implementações um ID pode ser dado.

### Exercício

Discuta as vantagens e desvantagens de ambas as abordagens.

### Essência

A paginação precisa ser feita, importante notar é que só funciona com dados ordenados!

## 4. Índices

## 5. Transações

### Explicação

A ideia por trás de um índice e uma transação já deve estar clara, pois foi tratada em SQL. Então, puramente sintaxe aqui, mas se os alunos não puderem explicar por que fazemos essas coisas, então passe por isso com eles novamente.

### Exemplo

``` js
client.db("log").collection("bugs").createIndex({ timestamp: -1 });
```

Isso cria um índice para classificação decrescente no carimbo de data/hora que temos consultado muito.

``` js
função assíncrona transferCredits(fromAccountId, toAccountId, valor) {
  const accountsCollection = client.db("cobrança").collection("contas");
  const sessão = client.startSession();

  experimentar {
    session.withTransaction(async() => {
      //Remove do usuário
      aguarde accountsCollection.updateOne(
        { _id: fromAccountId },
        { $inc: { créditos: valor * -1 } },
        { sessão }
      );

      // Adiciona a toUser
      aguarde accountsCollection.updateOne(
        { _id: toAccountId },
        { $inc: { créditos: valor } },
        { sessão }
      );
    });
  } pegar (errar) {
    aguardar sessão.abortTransaction();
  } finalmente {
    aguardar sessão.endSession();
  }
}
```

### Exercício

Discuta quando e por que fazer índices e transações. Que tipo de cenários existem.

### Essência

Tanto os índices quanto as transações têm um custo associado a eles, mas podem melhorar o desempenho e a segurança de seus bancos de dados!

## 6. SQL vs NoSQL

O exercício de preparação lida com isso, dê uma olhada [aqui](./QA_PREP_EXERCISE.md)
