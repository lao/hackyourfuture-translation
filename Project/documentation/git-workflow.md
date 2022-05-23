# Guia de fluxo de trabalho do projeto Git

Haverá 1 repositório remoto (seu repositório de projeto de classe) com o qual todos trabalharão.

Antes de iniciar o sprint, você deve seguir estas etapas:
1. `Clone` o repositório
2. `Busca` o commit mais recente
3. `Instale` todos os módulos do nó (para backend e frontend)

### CONTROLO REMOTO

- O repositório remoto terá um branch `master` e um branch `development` (ramificado do master)
- A ramificação `development` conterá todo o código do recurso mesclado
- Cada equipe criará uma ramificação para cada recurso
- Cada membro da equipe usará essa ramificação de recursos para trabalhar a partir

### LOCAL

- O repositório local também terá um branch `master` e `development`. Você buscará e enviará código para suas respectivas ramificações remotas
- Cada membro da equipe também terá uma ramificação para cada ramificação em que estiver trabalhando (portanto, haverá _2_ ramificações de recursos para cada membro da equipe no total)
- Cada membro da equipe trabalhará em sua parte do recurso localmente e, quando tiver confirmado localmente, envie-o para o remoto (GitHub) para que os outros o retirem

## DIRETRIZES DE COMUNICAÇÃO

Comunique-se com a maior frequência possível. No início de cada dia, faça uma reunião sobre quem vai fazer o quê naquele dia. Este é o `diariamente standup/scrum`.

Depois, você pode dedicar algum tempo para discutir como abordar cada tarefa.

Dicas para comunicar:

- Anote suas tarefas usando listas de verificação. Isso cria clareza e fornece uma visão geral para você e seus membros da equipe
- Faça uso do bate-papo por vídeo quando necessário. A opção “Compartilhar tela” no Slack é útil para ajudar uns aos outros a depurar o código

## GIT FLUXO DE TRABALHO

### Fluxo de trabalho diário:

1. Escreva algum código na ramificação **local** [FEATURE_NAME], por exemplo, “social-media-login-feature”
2. Adicione e confirme este código **localmente**
3. Envie o código para a ramificação **remota** com o mesmo nome, "recurso de login de mídia social"
4. O membro da sua equipe extrai o código do branch **remoto** "social-media-login" para o branch **local** "social-media-login-feature"
5. Repita as etapas 1 a 4

### Quando o recurso estiver concluído:

1. Certifique-se de que todos os membros da equipe tenham mesclado seu código com a ramificação **remota** “social-media-login-feature”
2. Certifique-se de que todos os membros da equipe possam usar funcionalmente o recurso em 3. seu projeto **local**
3. Um membro da equipe faz uma **solicitação de pull para o desenvolvimento remoto** da ramificação, mas **não a mescla**!

## IMPORTANTE!

1. Mesclar código com `development` e `master` só será feito no **remote** (GitHub), por meio de pull requests
2. Cada membro da equipe trabalhará em um recurso enquanto estiver na ramificação desse recurso. Assim que terminar o dia, `git push origin [BRANCH_NAME]` o código para o branch remoto. No início de um novo dia, `git pull origin [BRANCH_NAME]` para obter a versão mais recente da base de código
3. Espera-se que você implemente um recurso a cada semana, que será apresentado ao restante da turma naquele domingo
4. Vamos **mesclar os recursos na ramificação de desenvolvimento** no domingo
5. Quando precisar de ajuda: entre em contato com o Product Owner
