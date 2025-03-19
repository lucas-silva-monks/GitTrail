# GitTrail

## Introdução
Esta documentação cobre os conceitos e comandos essenciais do Git, desde o básico até técnicas avançadas, incluindo boas práticas e resolução de problemas.

## Conceitos Fundamentais

### O que é Git?
O Git é um sistema de controle de versão e tem a finalidade de gerenciar diferentes versões de um projeto ou código, armazenando versões sólidas e permitindo colaboração entre programadores, sincronizando alterações quando necessário.

### Estados dos Arquivos no Git

1. **Modified**: O arquivo sofreu modificações, mas não foi preparado para ser incluído no repositório.
2. **Staged**: O arquivo foi marcado para ser adicionado no próximo commit (`git add`).
3. **Committed**: As alterações foram registradas no repositório (`git commit`).

## Comandos Básicos

- `git init` – Inicia um repositório Git em um projeto local.
- `git clone [URL]` – Clona um repositório remoto.
- `git add [arquivo]` – Adiciona um arquivo ao staging.
- `git commit -m "Mensagem"` – Registra alterações no repositório.
- `git diff` – Compara alterações no repositório.
- `git log` – Exibe o histórico de commits.
- `git status` – Mostra o estado atual do repositório.
- `git reset` – Reverte alterações em commits.
- `git checkout -b [nome-branch]` – Cria e troca para uma nova branch.
- `git merge [branch]` – Mescla alterações de outra branch na atual.
- `git pull` – Atualiza o repositório local com as mudanças do remoto.
- `git push` – Envia commits para o repositório remoto.

## Trabalhando com Repositórios Remotos

- `git remote add origin [URL]` – Adiciona um repositório remoto.
- `git fetch` – Baixa alterações do repositório remoto sem aplicá-las.
- `git pull` – Atualiza a branch local com as alterações do remoto.
- `git push origin [branch]` – Envia mudanças da branch local para o remoto.

## Rebase no Git

O `git rebase` é utilizado para reorganizar e linearizar o histórico de commits. Ele move uma sequência de commits para um novo ponto base, tornando o histórico mais limpo e compreensível.

### Como Usar o Rebase no Terminal do VS Code no macOS

#### Passo 1: Iniciar o rebase interativo
1. No terminal do VS Code, navegue até o diretório do repositório:  
   ```sh
   cd /caminho/do/repo
   ```
2. Execute o comando:
   ```sh
   git rebase -i <hash-do-commit-base>
   ```
   - Substitua `<hash-do-commit-base>` pelo hash do commit onde deseja basear o rebase.
   - Isso abrirá um editor interativo (geralmente o Vim) com a lista de commits.

#### Passo 2: Editar os commits no Vim

1. No Vim, você verá uma lista como esta:
   ```
   pick abc1234 Commit 1
   pick def5678 Commit 2
   pick ghi9101 Commit 3
   ```
2. Para entrar no modo de edição, pressione `i`.
3. Modifique os commits conforme necessário:
   - `pick` → Mantém o commit.
   - `reword` → Permite editar a mensagem do commit.
   - `edit` → Permite modificar o commit.
   - `squash (s)` → Junta o commit com o anterior.
   - `drop (d)` → Remove o commit.
4. Pressione `Esc`, digite `:wq` e pressione `Enter` para salvar e sair.

#### Passo 3: Resolver conflitos (se houver)

1. Caso ocorra um conflito, o Git indicará os arquivos com problemas.
2. Edite os arquivos manualmente para resolver os conflitos.
3. Após resolver, execute:
   ```sh
   git add <arquivos-modificados>
   ```
4. Continue o rebase com:
   ```sh
   git rebase --continue
   ```
5. Se quiser abortar o rebase, use:
   ```sh
   git rebase --abort
   ```

#### Passo 4: Finalizar o rebase

1. Se o rebase for concluído com sucesso, o terminal exibirá uma mensagem de confirmação.
2. Para verificar as mudanças, use:
   ```sh
   git log --oneline --graph
   ```

### Dicas Extras
- **GitLens**: Extensão do VS Code que facilita a visualização do histórico do Git.
- **Git pull --rebase**: Sincroniza a branch com o repositório remoto antes do push.
- **Git merge vs. Git rebase**: O rebase mantém um histórico linear, enquanto o merge preserva a ordem original dos commits.

## Git Stash

- `git stash` – Salva temporariamente as alterações pendentes.
- `git stash pop` – Recupera as alterações armazenadas.

## Git Reset

- `git reset --soft <commit>` – Move commits sem perder as alterações.
- `git reset --mixed <commit>` – Mantém as mudanças no diretório de trabalho.
- `git reset --hard <commit>` – Desfaz todas as alterações (irreversível!).

## Resolvendo Conflitos no Git

Os conflitos ocorrem quando há alterações incompatíveis em diferentes branches. Para resolver:
1. Identifique os arquivos com conflitos.
2. Edite os arquivos para escolher quais alterações manter.
3. Adicione os arquivos resolvidos com `git add`.
4. Finalize a mesclagem com `git commit` ou `git rebase --continue`.
5. Se necessário, utilize `git merge --abort` ou `git rebase --abort` para cancelar o processo.

## Recursos Úteis
- [Oh Shit, Git!?!](https://ohshitgit.com/) - Guia rápido para sair de situações complicadas no Git.
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/?authuser=0) - Padrão para mensagens de commit bem estruturadas.

---
Esse guia fornece uma visão abrangente do Git. Para mais detalhes, consulte a [documentação oficial do Git](https://git-scm.com/doc).

