# git

## git init
Cria um repositório, também podemos criar um repositorio sem o working dir utilizando --bare

## git add -A ou git add . ou git add --all
Adiciona arquivos (untracked, modified) no staging area

## git status
Retorna o status dos arquivos do working directory

## git commit 
Adiciona os arquivos rastreados no repositório

## git log --oneline --decorate
Usamos para visualizar a arvoré de commits

## git show
Mostra as alterações realizadas no ultimo commit

## git rm
Remove um arquivo da stage area

## git reset
soft - apenas altera a referencia mas mantem os arquivos na staging area
mixed - idem soft mas remove os arquivos da staging area
hard - idem ao soft e apaga os arquivos

## git reflog
desfazer um reset

## git branch
Cria uma nova linha de desenvolvimento isolada. (faz um apontamento utilizando o hash de um commit)
(.get/refs/heads/...)

## git checkout
Faz o chaveamento entre os branches
(.get/HEAD)

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

## git blame

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
develop - código para a proxima versao do projeto/desenvolvimento

branches de suporte
feature
bugfix
hotfix
release



