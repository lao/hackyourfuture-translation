# Plano de aula Semana 2

## Agenda

O objetivo desta aula é apresentar ao aluno (1) os fundamentos do uso do GIT e (2) os fundamentos do pensamento baseado em grade e do uso do flexbox:

- Comandos básicos do GIT
- Apresentando o GitHub
- Configurando um par de chaves SSH

- Introdução ao pensamento baseado em grade
- O problema que o Flexbox resolve
- Comandos básicos do flexbox

## Conceitos Fundamentais

PRIMEIRA METADE (12h00 - 13h30)

## GIT

### Explicação
- GIT é um software que nos permite acompanhar as mudanças em nossos arquivos
- Imagine ter escrito um código complexo que estragou tudo, o GIT nos permite retornar a um estado anterior onde tudo ainda estava funcionando
- Pode ser usado através da interface de linha de comando (CLI) ou usando uma interface gráfica de usuário (também conhecida como GUI): SourceTree, SmartGit, etc.

### Exemplo
### Exercício

_Crie um novo repositório local e diga aos alunos para fazerem o mesmo_

_Mostrar o arquivo oculto `.git` na pasta_

- Quando você quiser salvar seu trabalho, você pode fazer um instantâneo do seu espaço de trabalho: isso é chamado de 'committing your work', que é outra maneira de dizer 'saving your work'

_Crie um arquivo .txt por meio da CLI e confirme-o no repositório local_

_Delete o arquivo e confirme essa alteração_

- GIT nos permite reverter nosso espaço de trabalho para um commit anterior. Podemos procurar o commit certo usando `git log`, `git checkout` e `git revert`

_Mostre ao aluno o processo de reversão para o primeiro commit_

- GitHub é uma plataforma de desenvolvimento que nos permite armazenar uma cópia do nosso código online (em termos de desenvolvedor: remoto)
- Os principais benefícios são (1) armazenar nosso código online, (2) nos permite trabalhar facilmente em conjunto com outras pessoas no mesmo repositório

_Peça aos alunos que criem uma conta se não tiverem_

- Para usar o GitHub com segurança, precisamos criar uma chave SSH
- As chaves SSH permitem que o GitHub nos identifique como uma conexão segura

_Crie uma chave SSH através da CLI_

_Vincule a chave SSH à sua conta do GitHub_

_Mostrar como clonar o repositório HTML-CSS-GIT usando SSH_

_Peça aos alunos para criarem uma chave SSH, vinculá-la à sua conta e clonar o repositório_

### Essência




SEGUNDA METADE (14.00 - 16.00)

## 2. Pensamento baseado em grade e Flexbox

### Explicação
- Flexbox nos permite alinhar facilmente elementos na página
- Substitui o web design baseado em float
- É ativado com a propriedade CSS `display: flex`, depois que você pode fazer uso de propriedades específicas do flex
### Exemplo
Dê uma olhada no seguinte [CodePen](https://codepen.io/enxaneta/pen/adLPwv) com alunos

Veja o seguinte [website](https://htmlstream.com/preview/unify-v2.6.2/unify-main/home/home-default.html) e disseque-o pensando em grades
### Exercício
Reconstrua a barra de navegação, a imagem central e o layout do site responsivo a partir deste [exemplo](https://github.com/ratracegrad/made-with-flexbox)

Jogue o jogo! : https://flexboxfroggy.com/
### Essência


