![git](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png "git")

# git
Guia de referência sobre GIT

## git init
Cria um repositório, também podemos criar um repositório sem o working directory utilizando ```--bare```

## git add
Adiciona arquivos (untracked, modified e etc) na staging area
Normalmente usamos ```git add .```, ```git add -A``` ou ```git add <file>```

## git status
Retorna o status dos arquivos no diretório de trabalho com ```git status```

## git commit 
Adiciona os arquivos rastreados no repositório
Normalmente utilizamos ```git commit -m 'commit message'```

## git log
Usamos para visualizar a árvore de commits com o comando ```git log --oneline --decorate --all --graph```
Também podemos usar para visualizar as alterações de um determinado arquivo com ```git log -p <file>```

## git show
Mostra as alterações realizadas no último commit com ```git show```

## git tag
- Adiciona uma etiqueta para marcarmos um commit e poder filtrar depois de uma forma simples.
- Podemos criar uma tag com ```git tag -a v1.0 -m 'message'``` ou ```git tag -a v1.0 -m 'message' m1e2```
- Podemos listar as tags disponíveis com ```git tag```
- Podemos visualizar com ```git show v1.0```
- Podemos fazer checkout para uma determinada tag com ```git checkout v1.0```

## git rm
Remove um arquivo da staging area com ```git rm --cached <file>```

## git reset
Comando responsável por alterar a referência do HEAD e também remover um determinado commit.
soft - apenas altera a referência mas mantem os arquivos na staging area
mixed - idem soft mas remove os arquivos da staging area
hard - idem ao soft e apaga os arquivos
--keep - mantem os arquivos não commitados

## git revert <commit>
Reverte um commit criando um novo com o código revertido.

## git reflog
desfazer um reset

## git branch
Cria uma nova linha de desenvolvimento isolada. (faz um apontamento utilizando o hash de um commit)
(.get/refs/heads/...)

## git checkout
Faz o chaveamento entre os branches
(.get/HEAD)
git checkout HEAD/commit <file> = desfaz alterações do working

## git merge
fast-forward é apenas umas atualização da referencia e só é possível quando nao existe divergencia entre as branchs
estrategia recursiva é utilizada quando temos divergencias

## git stash
Área onde podemos armazenar código sem a necessidade de um commit
git stash save "identificador"
git stash list
git stash apply stash@{0} ou drop
git stash pop = faz o apply e drop do topo da pilha
git stash branch xpto = cria um novo branch a partir do stash

## git rebase

## git blame <file>
Quem alterou e quando

## git remote
add name/url
-v

## git config
user.name ou user.email

## git pull
oposto do push mas faz merge automaticamente.

## git push
Atualiza uma referencia remota a partir da local

## git fetch
Só traz as atualizacoes sem fazer merge.

## git diff
git diff master origin/master

# gitflow
É uma forma de estruturar o versionamento dos projetos com convenções

## Regras
Não commitamos na master
Master apenas recebe commit/referências

## Branches
Devemos seguir da seguinte forma.

### branches obrigatórios
master - código em produção
develop - código para a próxima versão do projeto/desenvolvimento

### branches de suporte
feature - a partir da branch develop, criaremos as features necessárias
hotfix - a partir da master, bug crítico em produção que devemos resolver com prioridade
release - branch para lançamento de uma feature/versão

![git-flow](https://leanpub.com/site_images/git-flow/git-workflow-release-cycle-3release.png "git flow")

### fluxo padrão do desenvolvimento
```
git init
git checkout -b develop
git add -A && git commit -m 'commit message'
git pull origin develop
git push origin develop
```

### fluxo de uma feature
```
git checkout -b feature/task develop
git add -A && git commit -m 'commit new feature'
git checkout develop
git merge --no-ff feature/task
git branch -d feature/task
git pull origin develop
git push origin develop
```

### fluxo de um hotfix
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

### fluxo de um lançamento
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
