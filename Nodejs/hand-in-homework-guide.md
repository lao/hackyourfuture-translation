# Como entregar o dever de casa

Neste módulo, você enviará sua lição de casa apenas usando GIT e GitHub.

1. [GitHub](https://www.github.com/HackYourFuture/Node.js)

## 1. Guia de lição de casa do GitHub

<a href="http://www.youtube.com/watch?feature=player_embedded&v=CpYARPYGQU8" target="_blank"><img src="./assets/submit-homework.png" width="400" height ="250" alt="HYF Vídeo" /></a>

Assista ao vídeo (clicando na imagem) ou siga o passo a passo a seguir para saber como enviar sua lição de casa:

APENAS UMA VEZ (INÍCIO DE CADA MÓDULO)

1. Crie um [fork](https://help.github.com/en/articles/fork-a-repo) do repositório do módulo homework. Para Node.js, o repositório do módulo homework é `https://www.github.com/HackYourHomework/Node.js-classXX` onde XX é o número da sua turma. Você faz isso usando a opção `fork` no canto superior direito
2. Navegue até a URL do repositório clonado (deve estar na sua conta pessoal do GitHub, em "repositórios")
3. Clone o repositório, usando SSH, em sua máquina local. Você pode fazer isso digitando `git clone <git url>` na linha de comando
4. Em sua máquina local, navegue até a pasta usando a linha de comando
5. Certifique-se de ter clonado corretamente executando `git status` na linha de comando.

TODA SEMANA

1. Faça um `git pull` em seu branch principal para obter a versão mais recente.
2. Crie uma nova ramificação para cada semana que você tiver lição de casa. Por exemplo, para a lição de casa da semana 1 para o Node, crie uma ramificação chamada `YOUR_NAME-w1-Node`. Não se esqueça de fazer o checkout deste branch após criá-lo.
3. Faça sua lição de casa!
4. Quando terminar, adicione seu dever de casa a um commit. Certifique-se de *somente* enviar seus arquivos de lição de casa e nada mais. Você pode usar `git add -p` se quiser adicionar apenas alguns arquivos. Você sempre pode verificar o que está acontecendo com o comando `git status` (como um de nossos mentores sempre diz, é o console.log do git!).
5. Crie o commit (`git commit`). Torne a mensagem de confirmação significativa, por exemplo, `projeto finalizado para a semana de lição de casa1`.
6. Envie a ramificação para seu repositório bifurcado
7. Na página do GitHub do seu repositório bifurcado, clique no botão `create pull request`. Certifique-se de que o `repositório base` seja o repositório do seu professor, no branch master
8. Dê um título ao pull request no seguinte formato:

```remarcação
Lição de casa semana 1 <Seu nome>
```

9. Envie o pull request do seu branch de repositório bifurcado para o branch `main`

Se você tiver alguma dúvida ou se algo não estiver totalmente claro ¯\\\_(ツ)\_/¯, pergunte/comente no Slack!

