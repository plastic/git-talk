![git](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png "git")

# git
============================
Guia de referência sobre GIT

## git init
- Cria um repositório, também podemos criar um repositório sem o working directory utilizando ```--bare```

## git add
- Adiciona arquivos (untracked, modified e etc) na staging area
- Normalmente usamos ```git add .```, ```git add -A``` ou ```git add <file>```

## git status
- Retorna o status dos arquivos no diretório de trabalho com ```git status```

## git commit 
- Adiciona os arquivos rastreados no repositório
- Normalmente utilizamos ```git commit -m 'commit message'```

## git log
- Usamos para visualizar a árvore de commits com o comando ```git log --oneline --decorate --all --graph```
- Também podemos usar para visualizar as alterações de um determinado arquivo com ```git log -p <file>```

## git show
- Mostra as alterações realizadas no último commit com ```git show```

## git tag
- Adiciona uma etiqueta para marcarmos um commit e poder filtrar depois de uma forma simples.
- Podemos criar uma tag com ```git tag -a v1.0 -m 'message'``` ou ```git tag -a v1.0 -m 'message' m1e2```
- Podemos listar as tags disponíveis com ```git tag```
- Podemos visualizar com ```git show v1.0```
- Podemos fazer checkout para uma determinada tag com ```git checkout v1.0```

## git rm
- Remove um arquivo da staging area com ```git rm --cached <file>```

## git reset
- Comando responsável por alterar a referência do HEAD e também remover um determinado commit.
- ```git reset --soft``` Apenas altera a referência mas mantém os arquivos na staging area
- ```git reset --mixed``` Faz soft mas remove os arquivos da staging area
- ```git reset --hard``` Faz soft e apaga os arquivos
- ```--keep``` Mantém os arquivos alterados do diretório de trabalho (working directory)

## git revert
- Reverte um commit criando um novo com o código revertido.
- ```git revert <commit>```

## git reflog
- Lista o histórico de commits de um reposótio
- Muito utilizado para voltar um commit apagado

## git branch
- Cria uma nova linha de desenvolvimento isolada. (faz um apontamento utilizando o hash de um commit)
- Path para visualizar os branches criados (.get/refs/heads/<branch>)
- Podemos criar um branch com ```git branch <name>```
- Podemos apagar com ```git branch -d <name>```
- Listar apenas com ```git branch```

## git checkout
- Faz o chaveamento entre os branches.
- Podemos visualizar onde estamos olhando o path (.get/HEAD)
- Podemos criar um branch e á mudar a referência para o mesmo com ```git checkout -b <name>``` 
- Utilizamos também para desfazer alterações nos arquivos modificados e rastreados com ```git checkout HEAD/commit <file>```

## git merge
- ```fast-forward``` é apenas uma atualização da referência e só é possível quando não existe divergência entre as branchs
- ```recursive strategy``` é utilizada quando temos divergências
- ```--no-ff``` Usamos para criar um novo commit com o merge

## git stash
- Área onde podemos armazenar código sem a necessidade de um commit
- ```git stash save "identificador"```
- ```git stash list```
- ```git stash apply stash@{0}``` ou ```drop```
- ```git stash pop``` faz o apply e drop do topo da pilha
- ```git stash branch <name>``` cria um novo branch a partir do stash

## git blame
 - Mostra quem alterou e quando com ```git blame <file>```

## git remote
- Adiciona uma referência remota para o repositório atual
- ```git remote add <name> <url>```
- ```git remote -v``` lista os remotes existentes

## git config
- Podemos configurar por repositório ou de forma global, algumas variáveis como autor e etc...
- ```git config user.name <name>```

## git push
- Atualiza uma referência remota a partir da local
- ```git push <name> <branch>```
- ```git push --all```

## git pull
- Posto do push mas faz merge automaticamente.
- ```git pull <name> <branch>```

## git fetch
- Traz as atualizações sem fazer merge.

## git diff
- Usado para listar a diferença entre commits/file
- ```git diff master origin/master``` podemos fazer um diff antes de subir

# GitFlow
=========
- É uma forma de estruturar o versionamento dos projetos com convenções

## Regras
- Não commitamos na master
- Master apenas recebe commit/referências
- Devemos sempre apagar as branches de suportes após o merge

## Branches
- Devemos seguir da seguinte forma.

### Branches obrigatórios
- ```master``` - código em produção
- ```develop``` - código para a próxima versão do projeto/desenvolvimento

### Branches de suporte
- ```feature``` - a partir da branch develop, criaremos as features necessárias
- ```hotfix``` - a partir da master, bug crítico em produção que devemos resolver com prioridade
- ```release``` - branch para lançamento de uma feature/versão

![git-flow](https://leanpub.com/site_images/git-flow/git-workflow-release-cycle-3release.png "git flow")

### Fluxo padrão do desenvolvimento
```
git init
git checkout -b develop
git add -A && git commit -m 'commit message'
git pull origin develop
git push origin develop
```

### Fluxo de uma feature
```
git checkout -b feature/task develop
git add -A && git commit -m 'commit new feature'
git checkout develop
git merge --no-ff feature/task
git branch -d feature/task
git pull origin develop
git push origin develop
```

### Fluxo do hotfix
```
git checkout -b hotfix/1.1.1 master
git add -A && git commit -m 'commit new hotfix and new version 1.1.1'
git checkout master
git merge --no-ff hotfix/1.1.1
git tag -a v1.1.1
git checkout develop
git merge --no-ff hotfix/1.1.1
git branch -d hotfix/1.1.1
```

### Fluxo de lançamento
```
git checkout -b release/1.2.0 develop
git add -A && git commit -m 'commit new version 1.2.0'
git checkout master
git merge --no-ff release/1.2.0
git tag -a v1.2.0
git checkout develop
git merge --no-ff release/1.2.0
git branch -d release/1.2.0
```
