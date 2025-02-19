**Git:** Software para controle de versionamento.

**GitHub:** Cloud para armazenamento das versões.

### Status do Git

- **Working:** Refere-se ao diretório onde você faz alterações nos arquivos.
- **Staged:** Quando você prepara as alterações para serem commitadas, usando o comando `git add`.
- **Committed:** Quando as alterações são salvas no repositório local com `git commit`, tornando-se parte da história do projeto.

### Comandos básicos do Git

- `git status`: Verifica o status das alterações no repositório.
- `git add <arquivo>`: Adiciona um arquivo à "Staging Area" para ser commitado.
- `git commit`: Realiza o commit de um ou múltiplos arquivos. Você pode usar:
     - `git commit -m "mensagem"`: Para adicionar uma mensagem ao commit.
     - `git commit -a`: Faz um `git add .` sem precisar executar esse comando separadamente e já realiza o commit.
- `git mv <origem> <destino>`: Como no Linux, o `mv` serve para mover arquivos entre diretórios, mas também pode ser utilizado para renomeação.
- `git log`: Mostra o histórico de commits.
- `git commit --amend`: Permite modificar o commit mais recente, alterando sua mensagem ou adicionando arquivos.
- `git merge -m "mensagem"`: Faz o merge de uma branch.
- `git branch <nome>`: Cria uma nova branch com o nome desejado.
- `git branch -d <nome>`: Deleta uma branch, desde que ela já tenha sido mesclada.

### Git reset

Existem três tipos de `git reset`: **soft**, **mixed** e **hard**.

- Imagine que temos três versões de commits: `33 <- K2 <- 13`, e estamos com o HEAD na versão 13.
     - **Soft reset**: Ao executar `git reset --soft <versão>`, você voltará para a versão indicada, mas as alterações feitas até a versão 13 permanecerão na "Staging Area", prontas para serem commitadas.
     - **Mixed reset**: Ao executar `git reset --mixed <versão>`, você voltará para a versão indicada, mas as alterações estarão como "Unstaged", ou seja, precisarão ser adicionadas antes de serem commitadas.
     - **Hard reset**: Ao executar `git reset --hard <versão>`, você voltará para a versão indicada, mas todas as alterações feitas após essa versão serão **excluídas**, sem possibilidade de recuperação.

### Como criar um alias

```sh
git config --global alias.log1 "log --oneline"
```

- `git config`: Altera as configurações do Git.
- `--global`: O `--global` serve para adicionar esse alias em todas as máquinas que estiverem com a conta do Git logada. Se `--global` não for adicionado, as alterações só funcionarão na máquina local.
- `alias.<comando>`: Serve para adicionar o alias. Por exemplo, `alias.log1`, onde o que vem após o ponto é o nome do comando.

### Conventional Commits 1.0.0
O Conventional Commits é uma convenção leve aplicada às mensagens de commit. Ele fornece um conjunto simples de regras para criar um histórico de commits explícito.

`<tipo>[escopo opcional]: <descrição>`

`[corpo opcional]`

`[rodapé(s) opcionais]`

##### Tipos básicos:

1. `fix`: Um commit do tipo `fix` corrige um bug no seu código.
2. `feat`: Um commit do tipo `feat` introduz uma nova funcionalidade no código.
3. `BREAKING CHANGE`: Um commit que possui o rodapé `BREAKING CHANGE` ou contém `!` após o tipo introduz uma mudança que pode quebrar a API.

### Exemplos de Prefixos Correto

```sh
feat: adicionar funcionalidade de login
feat(auth): adicionar login com Google
fix(button): corrigir problema com botão que não renderizava
fix(parser): corrigir erro na análise de arrays quando havia múltiplos espaços na string
fix(db): atualizar lógica de consulta para evitar SQL injection
feat(auth)!: refatorar fluxo de autenticação
```

### Exemplos:

**Mensagem de commit com rodapé de Breaking Change**
```sh
feat: permitir que o objeto de configuração fornecido estenda outras configurações  

BREAKING CHANGE: a chave `extends` no arquivo de configuração agora é usada para estender outros arquivos de configuração  
```

**Mensagem de commit com `!` para destacar uma Breaking Change**
```sh
feat!: enviar um e-mail ao cliente quando um produto for enviado  
```

**Mensagem de commit com escopo e `!` para destacar uma Breaking Change**
```sh
feat(api)!: enviar um e-mail ao cliente quando um produto for enviado  
```

**Mensagem de commit com `!` e rodapé de Breaking Change**
```sh
chore!: remover suporte para Node 6  

BREAKING CHANGE: uso de recursos de JavaScript não disponíveis no Node 6.  
```

**Mensagem de commit sem corpo**
```sh
docs: corrigir ortografia do CHANGELOG  
```

**Mensagem de commit com escopo**
```sh
feat(lang): adicionar suporte ao idioma polonês
```

### Regras dos Conventional Commits

1. Os commits **DEVEM** ser prefixados com um tipo, seguido opcionalmente por um escopo, um `!` opcional e obrigatoriamente por dois pontos e um espaço.
2. O tipo `feat` **DEVE** ser usado para novas funcionalidades.
3. O tipo `fix` **DEVE** ser usado para correções de bugs.
4. Um escopo **PODE** ser incluído e deve descrever uma seção do código entre parênteses, por exemplo, `fix(parser):`.
5. A descrição **DEVE** seguir imediatamente após os dois pontos e o espaço.
6. Um corpo mais longo **PODE** ser adicionado após a descrição.
7. O corpo do commit **PODE** conter múltiplos parágrafos.
8. Um ou mais rodapés **PODEM** ser adicionados após uma linha em branco.
9. Os rodapés **DEVEM** usar `-` no lugar de espaços, exceto `BREAKING CHANGE`.
10. Mudanças que quebram compatibilidade **DEVEM** ser indicadas no prefixo do commit ou no rodapé.
11. `BREAKING CHANGE:` deve ser seguido de uma descrição.
12. Se `!` for usado no prefixo, o `BREAKING CHANGE:` no rodapé pode ser omitido.
13. Tipos adicionais como `docs`, `chore`, `style`, `refactor` podem ser usados.
14. As regras **NÃO DEVEM** ser sensíveis a maiúsculas e minúsculas, exceto `BREAKING CHANGE`.
15. `BREAKING-CHANGE` **DEVE** ser sinônimo de `BREAKING CHANGE`.

#### 1. **Prefixo com Tipo, Escopo Opcional, ! Opcional e Dois Pontos Seguidos de Espaço (Obrigatório)**

- **Exemplo**:
    
    ```
    feat: adicionar funcionalidade de login
    ```

#### 2. **feat para Adicionar uma Nova Funcionalidade**

- **Exemplo**:
    
    ```
    feat(auth): adicionar login com Google
    ```

#### 3. **fix para Correções de Bug**

- **Exemplo**:
    
    ```
    fix(button): corrigir problema com botão que não renderizava
    ```

#### 4. **O Escopo é Opcional e Deve Descrever uma Seção do Código**

- **Exemplo**:
    
    ```
    feat(api): adicionar novo endpoint para perfil de usuário
    ```

#### 5. **A Descrição Deve Vir Imediatamente Após o Prefixo**

- **Exemplo**:
    
    ```
    fix(parser): corrigir erro na análise de arrays quando havia múltiplos espaços na string
    ```

#### 6. **Corpo do Commit Opcional para Mais Contexto**

- **Exemplo**:
    
    ```
    fix(parser): corrigir erro na análise de arrays quando havia múltiplos espaços na string
    
    O analisador falhava ao processar strings com múltiplos espaços entre palavras. Esta atualização garante que espaços extras sejam tratados corretamente.
    ```

#### 7. **Corpo do Commit Livre, com Parágrafos Separados por Quebras de Linha**

- **Exemplo**:
    
    ```
    feat(user-profile): melhorar layout da página de perfil do usuário
    
    Redesenhamos a página de perfil com um layout mais limpo e moderno. Agora inclui uma barra lateral para navegação rápida.
    
    O perfil do usuário agora é responsivo e funciona bem em dispositivos móveis.
    ```

#### 8. **Rodapés: Opcionais, Adicionados Após o Corpo**

- **Exemplo**:
    
    ```
    fix(db): atualizar lógica de consulta para evitar SQL injection
    
    Melhoramos a consulta SQL para tratar com segurança as entradas do usuário.
    
    Closes: #45
    ```

#### 9. **Tokens no Rodapé Devem Usar `-` no Lugar de Espaços**

- **Exemplo**:
    
    ```
    feat(auth): adicionar autenticação JWT
    
    Adiciona suporte para tokens JWT no fluxo de autenticação.
    
    BREAKING CHANGE: A autenticação JWT agora é obrigatória para login.
    BREAKING-CHANGE: O gerenciamento de sessões do usuário foi reformulado.
    ```

#### 10. **Os Valores do Rodapé Podem Conter Espaços ou Quebras de Linha**

- **Exemplo**:
    
    ```
    feat(api): adicionar novo endpoint de estatísticas do usuário
    
    Adiciona um endpoint para recuperar estatísticas do usuário.
    
    Reviewed-by: João Silva
    Acknowledged-by: Maria Oliveira
    ```

#### 11. **Mudanças que Quebram Compatibilidade Devem Ser Indicadas no Tipo/Escopo ou no Rodapé**

- **Exemplo**:
    
    ```
    feat(auth)!: refatorar fluxo de autenticação
    
    Refatoramos o fluxo de autenticação para suportar OAuth.
    
    BREAKING CHANGE: O fluxo de autenticação agora exige tokens OAuth.
    ```

#### 12. **Breaking Change no Rodapé**

- **Exemplo**:
    
    ```
    feat(auth): integrar autenticação OAuth
    
    Implementa autenticação OAuth no aplicativo.
    
    BREAKING CHANGE: O sistema de autenticação agora usa tokens OAuth em vez de autenticação básica.
    ```

#### 13. **Breaking Change no Prefixo Usando `!`**

- **Exemplo**:
    
    ```
    feat(auth)!: integrar autenticação OAuth
    
    Esta refatoração introduz OAuth para autenticação. O método antigo não é mais suportado.
    ```

#### 14. **Outros Tipos Como `docs`**

- **Exemplo**:
    
    ```
    docs: atualizar README com novos passos de instalação
    ```

#### 15. **Os Tipos de Commit Não Diferenciam Maiúsculas de Minúsculas, Exceto `BREAKING CHANGE`**

- **Exemplo**:
    
    ```
    FIX(button): corrigir cor do botão que não estava atualizando
    ```

#### 16. **Sinônimo de `BREAKING CHANGE` nos Rodapés**

- **Exemplo**:
    
    ```
    feat(auth): atualizar política de senhas
    
    Agora, a política de senhas exige pelo menos um caractere especial.
    
    BREAKING CHANGE: Os requisitos de senha foram alterados.
    BREAKING-CHANGE: O comprimento mínimo foi aumentado para 8 caracteres.
    ```
