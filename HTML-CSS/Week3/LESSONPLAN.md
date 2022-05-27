# Plano de aula Semana 3

## Agenda

O objetivo desta aula é apresentar ao aluno:

- O que é ramificação GIT?
- Filiais remotas vs. locais
- O que é um pull request?

- O que é um quadro?
- Estruturas CSS populares
- Framework vs CSS personalizado

## Conceitos Fundamentais

PRIMEIRA METADE (12h00 - 13h30)

## 1. Ramificação GIT

### Explicação

- Um branch é um experimento, uma possível forma de seu projeto evoluir.
- O branch local pode ser criado com o comando `git branch <name>`. A ramificação remota deve ser definida usando a opção `--set-upstream` ao empurrar
- Pull request é um `diff` entre dois pontos de commit. Ele pode ser mesclado quando queremos sugerir alterações em um repositório do Github ao qual não temos acesso de gravação.

### Exemplo

Crie um repositório e inicialize o GIT. Mostrar o uso de `git branch`, `git checkout -b`

### Exercício

Um exercício divertido do [Arco](https://github.com/ArcoMul) para praticar a criação de pull requests: [Cat pull request exercise](https://github.com/ArcoMul/netlify-cats)

Instruções sobre como configurar as coisas no Netlify: https://github.com/ArcoMul/netlify-cats/blob/main/SETUP.md

### Essência


SEGUNDA METADE (14.00 - 16.00)

## 2. Estrutura CSS

### Explicação

- Uma estrutura de software é um código pré-escrito que fornece funcionalidade genérica e uma estrutura para construir aplicativos com
- Analogia do pote de ingredientes (veja [exemplo](./README.md) na seção 2)
- Estruturas CSS permitem um desenvolvimento mais rápido

- Prós e contras da estrutura

    - PRO: Acelera seu desenvolvimento
    - PRO: Ativa a funcionalidade entre navegadores
    - PRO: Geralmente são mantidos por uma comunidade de desenvolvedores
    - CONTRA: Leva tempo para aprender uma estrutura
    - CONTRA: Falta de compreensão do CSS subjacente

- Prós e contras do CSS personalizado
    - PRO: Satisfaz suas necessidades específicas
    - PRO: Controle total sobre a direção do CSS
    - PRO: Cria um visual único
    - CONTRA: Tem que manter código próprio
    - CONTRA: Você precisa ter certeza de que funciona em vários navegadores

### Exemplo

Mostrar vários frameworks CSS: [MaterializeCSS](https://materializecss.com/), [Bootstrap](https://getbootstrap.com/), [Foundation](https://foundation.zurb.com/)

### Exercício

Dê aos alunos um exercício para reconstruir um botão e uma barra de navegação com CSS personalizado. Então deixe-os fazer o mesmo com qualquer um dos frameworks CSS com os quais você se sinta mais confortável!

### Essência

Um framework CSS é usado para acelerar o desenvolvimento: é um código pré-escrito que fornece ao desenvolvedor estrutura e estilo básicos para criar uma interface de usuário apresentável.
