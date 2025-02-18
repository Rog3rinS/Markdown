**Git:** Software para controle de versionamento.

**Github:** Cloud para armazenamento das versoes. 

### Status do Git

- **Working:** Refere-se ao diretório onde você faz alterações nos arquivos.
- **Staged:** Quando você prepara as alterações para serem commitadas, usando o comando `git add`.
- **Commited** Quando as alteracoes sao salvas no resositorio local com `git commit`, tornando-se parte da hostoria do projeto.

### Comandos basicos do Git

- `git status`: verifica o status das alteracoes no repositorio.
- `git add <arquivo>`: Adiciona um arquivo ao "Staging area" para ser commitado.
- `git commit`: Realiza o commmit de um ou multiplos arquivos, voce pode usar:
     - `git commit -m "mensagem"`: Para adicionar uma mensagem ao commit.
     - `git commit -a`: Faz um `git add .`  sem precisar executar esse comando, e ja fazendo o commit.
- `git mv <origem> <destino>`: Como no linux o mv server para voce poder mover entre diretorios, porem tambem pode ser utilizado para a renomeacao.
- `git log`: Mostra o historico de commits.
- `git commit --amend`: Torna o commit que voce esta dando agora o antigo commit, assim fazendo com que altere o antigo commit.

### Git reset

Existem tres tipos de `git reset`: **soft**, **mixed**, e **hard**.

- Imagine que temos tres versoes de commits: `33 <- K2 <- 13`, e estamos com o HEAD na versao 13.
     - **Soft reset**: Ao executar `git reset --soft <versao>`, voce voltara para a versao indicada, mas as alteracoes feitas ate a 13 ja estao em "Staged", ou seja, ja estao prontas para serem commitadas. 
     - **Mixed reset** Ao executar `git reset --mixed <versao>`, como no soft voce voltara para a versao indicada, mas diferentemente do soft, as alteracoes estarao como "Unstaged", ou seja, nao estao prontas para serem commitadas, elas ainda precisam ser adicionadas antes de commitar.
     - **Hard reset** Ao executar `git reset --hard <versao>`, Voce voltara para a versao de indicada, porem todas as alteracoes feitas apos aquela versao indicada serao **excluidas**, ou seja nao tera como recupera-las.

### Como criar um alias

```sh
git config —global alias.log1 “log —oneline”
```

- `git config`: Para alterar as configs do git.
- `--global`: O global server para adicionar esse alias em todas as maquinas que estiverem com a conta do git logada, se o `--global` nao for adicionado as alteracoes so funcionarao na maquina local.
- `alias.<comando>`: server para adicionar o alias colocamos por exemplo alias.log1 onde apos o ponto e o nome do comando.
