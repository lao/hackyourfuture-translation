# Plano de aula Semana 1

## Agenda

O objetivo desta aula é apresentar ao aluno:

1. Noções básicas de trabalho com a interface de linha de comando
2. Conceitos básicos de HTML/CSS:
   - Noções básicas de HTML
   - Diferença entre as tags `<head>` e `<body>`
   - HTML5 semântico
   - Noções básicas de CSS
   - O modelo da caixa

## Conceitos principais

**PRIMEIRA METADE (12h - 13h30)**

## 1. Noções básicas da interface de linha de comando

### Explicação

- A interface de linha de comando (CLI) é uma maneira de navegar em seu computador emitindo comandos diretos
- No passado, o computador tinha **SOMENTE** uma linha de comando
- A CLI nem sempre dá feedback, como qualquer outro programa em seu computador daria
- Ícones de aplicativos da área de trabalho são atalhos visuais (Windows: mostre `$ calc` para iniciar a calculadora)

### Exemplo

| Comando | Descrição |
| -------------------------------------------------- ------------- | -------------------------------------------------- ---------------------------------------- |
| `pwd` | diretório de trabalho atual |
| `ls` | Listar arquivos no diretório |
| `cd` | alterar o diretório |
| `toque` | Crie um arquivo vazio |
| `eco` | exibir a string |
| `eco -n` | Exibe a string sem nova linha |
| `echo “algo” > arquivo` | Redirecione a saída do eco e crie o arquivo |
| `echo “outra coisa” >> arquivo` | Anexe a string ao arquivo |
| `mkdir` | fazer um novo diretório |
| `cd ~` | casa |
| `cd -` | diretório anterior |
| `cd ..` | diretório pai |
| `ls -a` | Listar todos os arquivos, incluindo arquivos ocultos |
| `cd /` | mude para o diretório raiz |
| `gato` | Concatenar o arquivo linha por linha e exibi-lo no terminal |
| `menos` | Imprima o arquivo grande linha por linha |
| `vim <arquivo>` | abra o editor com <file> {`a:` para ir para o modo de inserção, <ESC>`:wq` para escrever e sair } |
| `para var em {START..END}; faça <COMMAND1>; <COMANDO2>;...; ; feito' | |
| `head <arquivo>` | exibir as primeiras 10 linhas do arquivo |
| `cauda <arquivo>` | exibir as últimas 10 linhas do arquivo |
| `head -n <arquivo>` | exibir as primeiras n linhas do arquivo |
| `tail -n <arquivo>` | exibir as últimas n linhas do arquivo |
| `man <COMANDO>` | Exibir manual do COMANDO |

### Exercício

- Abra uma linha de comando (Git Bash no Windows)
- Crie uma pasta de projeto para conter todo o seu trabalho HYF (mkdir)
- Crie uma pasta de módulo (cd, mkdir)
- Crie um arquivo de texto: notes.txt (cd, touch)
- Abra o Visual Studio Code e adicione algumas notas (code .)
- Renomeie o arquivo para palestra1.txt (mv)

_"Vou de férias e levo comigo"_ com comandos CLI:

- Eles têm que repetir os comandos ditos antes deles.
- Adicione um novo comando e explique o que ele faz.
- Deixe a rodada continuar duas vezes, caso contrário os alunos que foram primeiro não precisam repetir todos os comandos.

Por exemplo, o primeiro aluno diz _"ls : listas de comandos"_. O segundo aluno deve dizer _"ls and cd: change directory"_. Então o terceiro aluno deve dizer _"ls, cd and pwd : show print working directory"_ e assim por diante.
_Por [@unmeshvrije](https://github.com/unmeshvrije)_

### Essência

SEGUNDA METADE (14.00 - 16.00)

## 2. Noções básicas de HTML

### Explicação

- HTML é apenas texto simples, nada de especial
- Os navegadores lêem o HTML e CSS e renderizam uma bela página da web
- O HTML de um site vem de um servidor (que é apenas outro computador em algum lugar)
- Diferença `<head>` e `<body>`

Modelo de caixa

- Tudo é uma caixa
- A "caixa" refere-se aos atributos universais para cada elemento: `margin`, `padding`, `border`
- Cada elemento empurra um contra o outro

### Exemplo

- Mostre a estrutura HTML mais básica, também mostre como o Visual Studio Code pode autocompletar a estrutura html apenas digitando: html
- `<título>`, `<link>`, `<meta>`
- Mostrar exemplo do modelo de caixa usando o inspetor do navegador em vários elementos

### Exercício

- Usando a linha de comando, crie uma pasta de projeto, um arquivo html e um arquivo css
- Crie uma estrutura html básica e vincule a um arquivo css externo
- Crie uma página da web que use todas as tags html e propriedades css que foram discutidas

### Essência

## 3. HTML5 semântico

### Explicação

- Explique por que existem `<h1>`, `<h2>`, `<h3>`
- Em teoria, uma página pode ser construída usando apenas `<div>`s
- Tags semânticas tornam o código mais compreensível
- Ajuda a organizar a página

### Exemplo

- Mostrar exemplos de HTML semântico: `<header>`, `<footer>`, `<main>`, `<section>`, `<article>`, `<nav>`, `<aside>`

### Exercício

### Essência
