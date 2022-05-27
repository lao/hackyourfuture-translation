# Entrega de trabalhos de casa
Se o repositório do módulo não especificar um processo diferente, a maneira padrão de entregar o dever de casa é a seguinte.

## Configuração inicial (apenas uma vez)
Existe um único repositório com todos os trabalhos de casa que você fará para o HackYourFuture que pode ser encontrado [aqui](https://www.github.com/HackYourFuture/homework). Siga estas etapas para configurar:

- Fork o repositório. No canto superior direito da página do repositório de trabalhos de casa, clique no botão de bifurcação para bifurcá-lo no seu github.
- Configure um upstream remoto emitindo o seguinte comando: `git remote add upstream https://www.github.com/HackYourFuture/homework`

Uma vez feito, seu próprio repositório bifurcado é o que você estará trabalhando, certifique-se de nunca enviar nada para o branch `main` para que você possa continuar atualizando seu fork para as alterações mais recentes.

(OPCIONAL): Para se lembrar de que existe uma função no github para proteger certos branches, muitas vezes o branch `main` será protegido de pushs diretos, pois o branch `main` é o que o usuário está trabalhando. Erros empurrados para tal ramo podem ser desastrosos. Para proteger seu branch principal, siga os seguintes passos:
- Vá para o seu repositório bifurcado. Algo como https://www.github.com/GITHUBNAME/Homework
- Clique em `Configurações`
- No menu lateral clique em `Ramos`
- Ao lado do título "Regras de proteção de ramificação", clique no botão "Adicionar regra"
- Preencha `main` como o `Padrão de nome da ramificação`
- Marque a caixa `Exigir revisões de pull request antes de mesclar`. Isso significa que a única maneira de obter algo nessa ramificação é por meio de uma solicitação pull.
- Marque a caixa `Incluir administradores`. Isso significa que você também será bloqueado por ser o administrador.
- Clique em 'Salvar' e está configurado!

## Semana de lição de casa (todas as semanas)
Se sua semana no currículo exigir a entrega de lição de casa, as etapas a seguir devem ser seguidas. Esse processo tornará mais fácil para nossos mentores fornecer feedback sobre seu código e nos permitirá acompanhar como todos estão se saindo.

1. Verifique se você está atualizado com a versão mais recente do dever de casa emitindo os seguintes comandos:
  - `git fetch upstream` para verificar a versão mais recente
  - `git checkout main` para ter certeza de que você está no seu branch principal
  - `git rebase -Xtheirs upstream/main` para pegar a versão mais recente do repositório HYF Homework
  - `git push` para atualizar o branch principal do seu repositório bifurcado no GitHUb (Lembre-se de remover sua proteção de branch e reativar isso se você fez isso na configuração)
  - `npm install` para garantir que todos os pacotes necessários sejam instalados
2. Crie uma nova ramificação `MODULENAME-WEEKNAME`. Por exemplo, a primeira semana de JavaScript deve ser chamada de `JavaScript-Week1`
3. Faça sua lição de casa! Lembre-se que existe um executor de testes que faz alguns testes automatizados de sua lição de casa, você pode descobrir sobre isso no `README`.
4. Depois de concluído, adicione e confirme tudo no branch
5. Envie a ramificação para seu repositório
6. Crie um pull request clicando no botão `create pull request` na sua página de repositório do github (`https://github.com/GITHUBNAME/Homework/pulls`). O pull request deve ser do seu branch para o branch principal. *Não* crie um pull request para o repositório HYF Homework.
7. Adicione um problema ao seu repositório de classe com o nome `YOURNAME - MODULENAME (WEEKNAME)`. Nele, compartilhe um link para a solicitação de RP que você acabou de criar. Atribua também o marco correto (o nome do módulo), o rótulo de semana correto e certifique-se de atribuir a si mesmo ao problema.
8. Por último, adicione o rótulo 'Precisa de revisão' para que nossos mentores saibam que podem começar a revisá-lo.

## Processo de revisão
Todos os seus trabalhos de casa serão revisados por um de nossos mentores de uma maneira muito semelhante que as revisões de código acontecem em qualquer empresa em que você vai trabalhar. As questões de lição de casa que você cria toda semana passarão pelo seguinte processo:

1. Inicialmente, o rótulo "Precisa de revisão" é definido.
2. Quando o mentor começa a revisar, o rótulo 'Revisão em andamento' é adicionado.
3. Uma vez concluídos, o mentor decide se o dever de casa é bom o suficiente ou se ainda é necessário algum trabalho. Se a lição de casa for boa o suficiente, a edição receberá o rótulo "Aprovado". Caso contrário, o rótulo "Revisado com feedback" será definido.
4. O aluno observa o feedback e corrige o dever de casa. Depois de concluído, o rótulo "Precisa de revisão" é definido novamente. Voltamos então ao passo 2.

Portanto, se um problema for atribuído a um aluno com o rótulo "Revisado com feedback", isso significa que o aluno precisa trabalhar nele. Se um problema tiver o rótulo "Precisa de revisão", significa que é para o mentor analisar. No final, todos os problemas devem receber o rótulo "Aprovado"! O mentor da turma ficará de olho nas questões e fechará as questões assim que tudo for verificado.
