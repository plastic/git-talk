# git
Guia de referência sobre GIT

## git init
Cria um repositório, também podemos criar um repositorio sem o working directory utilizando --bare

## git add -A ou git add . ou git add --all
Adiciona arquivos (untracked, modified) no staging area

## git status
Retorna o status dos arquivos do working directory

## git commit 
Adiciona os arquivos rastreados no repositório

## git log --oneline --decorate
Usamos para visualizar a arvoré de commits
-p <file>

## git show
Mostra as alterações realizadas no ultimo commit

## git rm
Remove um arquivo da stage area

## git reset
Comando responsável 
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

branches obrigatórios
master - código em produção
develop - código para a próxima versão do projeto/desenvolvimento

branches de suporte
feature - a partir da branch develop, criaremos as features necessárias
bugfix - a partir da branch master, bug para ser solucionado em breve
hotfix - a partir da master, bug crítico em produção que devemos resolver com prioridade
release - branch para lançamento de uma feature/versão

![figure] (https://leanpub.com/site_images/git-flow/git-workflow-release-cycle-3release.png)

passos iniciais:
```shellscript
git init
git checkout -b develop
git add -A && git commit -m 'commit message'


git checkout -b feature/task develop


git checkout -b hotfix/1.1.0 master

git checkout -b release/1.2.0 develop
git add -A && git commit -m 'commit new version'
git checkout master
git merge --no-ff release/1.2.0
git tag -a v1.0.0
```


