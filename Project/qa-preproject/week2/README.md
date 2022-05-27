# Material de leitura QA Pré-Projeto Semana 2

## Agenda

Estes são os tópicos da semana 2:

- Planos/cenários/casos de teste
- Pepino
- Criando problemas
- Testes Ágeis
- (Opcional) ISTBQ

### Planos/cenários/casos de teste

Precisamos consolidar nossas ideias de teste para recursos específicos e poder comunicá-los por meio de um plano de teste para que todos saibam o que o recurso deve fazer.

Saiba como fazer isso lendo os seguintes recursos:

- [O que é Cenário de Teste? Modelo com exemplos](https://www.guru99.com/test-scenario.html)
- [Como escrever casos de teste: modelo de amostra com exemplos](https://www.guru99.com/test-case.html)
- [Plano de teste de uma página](https://www.ministryoftesting.com/dojo/series/the-testing-planet-2016/lessons/the-one-page-test-plan)

Exemplos :

- [Lista de verificação de teste de aplicativos da Web](https://www.guru99.com/complete-web-application-testing-checklist.html)
- [Lista de verificação de planejamento de teste de software](https://www.ministryoftesting.com/dojo/series/the-testing-planet-2019/lessons/the-software-testing-planning-checklist)

### pepino

Nem todos podem falar JavaScript, mas quase todos podem falar [Gherkin](https://cucumber.io/docs/gherkin/reference/)!

Gherkin é uma linguagem específica de domínio criada especialmente para descrições de comportamento de negócios sem a necessidade de entrar em detalhes de implementação. Uma vez que está ligado ao comportamento, está fortemente ligado ao Behavior-Driven Development (BDD).

Exemplo:

```
Dado que eu visito "/login"
  Quando insiro "Bob" no campo "nome de usuário"
    E eu insiro "testador" no campo "senha"
    E eu pressiono o botão "login"
  Então eu deveria ver a página "bem-vindo"
```

Você entendeu o comportamento desejado? Aí você fala Gherkin também ;)

Domine a linguagem Gherkin conhecendo a sintaxe aqui:

- [O que é Gherkin?](https://www.guru99.com/gherkin-test-cucumber.html)

Recurso extra: [Referência Gherkin](https://cucumber.io/docs/gherkin/reference/)

### Criando problemas (Bug)

Imagine que você tem seus cenários de teste (traduzidos para Gherkin ou não), e ao executá-los algo deu errado... você não está vendo o que deveria ver, o comportamento real não é o esperado!

Então você pode ter pego um bug 🐞! Para saber o que é um bug e quais são os tipos de bugs.. veja isso:

- [Testes essenciais - O que é um bug?](https://www.youtube.com/watch?v=jvBoKXDCvLE)

Para comunicar um bug aos desenvolvedores, queremos discutir a arte de 🐞contar histórias.

> Os testadores são contadores de histórias. Vindo de uma formação em comunicação, um dos paralelos marcantes que fiz desde que trabalhei em garantia de qualidade e teste de software é que uma parte importante de seu papel é contar histórias curtas por meio de feedback imediato do produto. Um poderoso dispositivo de contar histórias que eles usam para conseguir isso é: o relatório de bug. (Por Anneliese Herbosa)

- [The Art Of The Bug Report](https://www.ministryoftesting.com/dojo/series/the-testing-planet-2019/lessons/the-art-of-the-bug-report)

### Testes Ágeis

Como parte da equipe, os engenheiros de controle de qualidade têm um papel importante em todo o processo de desenvolvimento. O Agile Testing não é sequencial (no sentido em que é executado somente após a fase de codificação), mas sim contínuo.

Saiba mais através do seguinte curso:

- [Teste ágil](https://www.linkedin.com/learning/agile-testing-2/uplevel-with-agile-testing)

### (Opcional) ISTQB

Da _Wikipédia_

> O International Software Testing Qualifications Board (ISTQB) é um conselho de certificação de teste de software que opera internacionalmente. O ISTQB Certified Tester é uma qualificação padronizada para testadores de software e a certificação é oferecida pelo ISTQB.

> Os fluxos ISTQB se concentram em:
>
> - Core – estes módulos correspondem às certificações “históricas” do ISTQB
> - Agile – esses módulos abordam práticas de teste especificamente para o Agile SDLC
> - Especialista – esses módulos são novos no portfólio de produtos do ISTQB e atendem

O syllabus do ISTQB Foundation Level declarou os princípios de teste de software, leia sobre eles aqui:

- [7 Princípios de teste de software](https://www.toolsqa.com/software-testing/principles-of-software-testing/)

Este site também oferece muitas outras informações sobre testes do padrão! Portanto, nas próximas semanas/meses, continue voltando para ver o que mais está fora do escopo do nosso currículo.
