# Entrega de trabalhos de casa

Começando com o módulo JavaScript2, esperamos que você entregue o dever de casa usando o GitHub [Forking Workflow](https://github.com/HackYourFuture/Git/blob/master/Lecture-3.md). Isso envolve as seguintes etapas:

## Bifurcação

1. Vá para a [página do GitHub do HackYourFuture](https://github.com/HackYourFuture) e clique no repositório do módulo HYF atual, por exemplo, `JavaScript2`.

2. No canto superior direito, pressione o botão [**Fork**].

3. Na caixa de diálogo subsequente, selecione sua própria conta do GitHub como o local para fazer o fork deste repositório.

4. Após alguns segundos, você será levado para sua própria conta do GitHub, no repositório que acabou de bifurcar.

5. Agora, clone este repositório bifurcado (_não o HYF original!_) para o seu laptop.

## Confirmar e enviar

Para o dever de casa de cada semana, repita os seguintes passos.

1. Se houver alterações pendentes da semana anterior, confirme ou descarte-as.

2. Comece de novo redefinindo seu repositório local de volta para o branch `master`. Isso garante que o novo dever de casa não seja misturado com o dever de casa das semanas anteriores. (Essa lição de casa anterior ainda estará disponível em suas respectivas ramificações.) Use este comando:

    ```
    mestre de checkout git
    ```

3. Crie um novo branch para o dever de casa desta semana (substitua `new-branch-name` pelo nome do seu novo branch, por exemplo, 'homework-week1'):

    ```
    git checkout -b nome-novo-ramo
    ```

4. Faça alterações em seu diretório de trabalho local conforme exigido pela(s) tarefa(s) de casa.

5. Confirme suas alterações conforme e quando necessário. A maneira recomendada de adicionar e enviar arquivos é manter um arquivo `.gitignore` na pasta raiz do seu diretório de trabalho que lista todos os arquivos e diretórios que você deseja deixar sem rastreamento pelo Git. Agora, quando você usa um comando `git add .`, todos os arquivos novos, alterados e/ou excluídos, exceto aqueles de `.gitignore`, são adicionados à área de teste.

    ```
    gi adicionar.
    git commit -m "sua mensagem de commit"
    ```

    Certifique-se de que suas mensagens de commit sejam significativas e descrevam com precisão sobre o que é o commit. Mensagens como `minhas alterações` não estão corretas. Se você precisar voltar no tempo para revisar uma alteração específica do passado, as mensagens de confirmação são as únicas pistas para encontrar a confirmação relevante. Para uma discussão aprofundada sobre como escrever boas mensagens de commit, veja [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/).

6. Envie seus commits para o GitHub. Você não precisa fazer isso após cada commit individual, mas é aconselhável enviar frequentemente para o seu próprio repositório como uma proteção contra falhas de disco em seu laptop. A primeira vez que você enviar seu novo branch, você deve usar o seguinte comando (substitua `new-branch-name` pelo nome do seu novo branch, por exemplo, 'homework-week1'):

    ```
    git push -u origin new-branch-name
    ```

    Empurrões subsequentes podem ser feitos simplesmente com:

    ```
    git push
    ```

## Criar solicitação pull

Quando você terminar sua lição de casa e desejar entregá-la, faça-o por meio de um **pull request** (PR).

1. Certifique-se de ter confirmado e enviado por push suas alterações finais no diretório de trabalho.

2. Acesse sua conta do GitHub e selecione o repositório que contém sua lição de casa.

3. Clique no botão [**New pull request**].

4. Selecione a ramificação mestre do repositório HackYourFuture à esquerda e a ramificação do repositório e da lição de casa à direita.

5. Pressione o botão verde [**Create pull request**] para continuar.

6. Adicione um título para sua solicitação pull, por exemplo, 'Semana de lição de casa 1'. Opcionalmente, você pode adicionar comentários para o revisor de pull request, por exemplo, problemas conhecidos com sua lição de casa atual.

7. Por fim, pressione o botão verde [**Create pull request**] para finalizar o envio da pull request.

## Recursos

Dê uma olhada em [este vídeo](https://www.youtube.com/watch?v=-o0yomUVVpU)
feito por Daan, onde ele explica esse processo em detalhes.

Revise também o [material de fluxo de trabalho do Git](https://github.com/HackYourFuture/Git/blob/master/Lecture-3.md)
e use-o como referência.
