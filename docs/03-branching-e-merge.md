# Branching e Merge

<!-- Este arquivo explica como trabalhar com branches e fazer merge no Git -->

## 📋 Objetivos de Aprendizagem

- Compreender o que são branches e como funcionam
- Criar, listar, trocar e deletar branches
- Entender o papel do HEAD
- Trabalhar com múltiplas linhas de desenvolvimento paralelas
- Aplicar boas práticas de nomenclatura

## 🎯 Introdução

Branches são fundamentais para o desenvolvimento de software moderno. Eles permitem trabalhar em paralelo sem interferir no código principal, facilitando experimentação segura, correção de bugs e desenvolvimento de novas funcionalidades de forma organizada.

## O que são Branches?

Uma **branch** (ramificação) é uma referência leve que aponta para um commit específico no histórico do repositório. Em termos técnicos, um branch é simplesmente um ponteiro (pointer) para um hash SHA-1 de um commit.

### Analogia Visual

Pense em uma árvore:

- O **tronco** representa a branch principal (main)
- Os **galhos** são branches secundárias
- Cada commit é um ponto na história onde você tomou um caminho diferente

### Como Funcionam

```
Commit:    A        B        C        D        (main)
              ↓        ↓        ↓        ↓
            1a2b3c   4d5e6f   7g8h9i   0j1k2l   (hash dos commits)
              │
              └─ Another-branch (ponteiro para C)
```

Cada branch armazena apenas o hash do commit mais recente. O Git então segue a cadeia de commits pais para construir o histórico completo.

### Por que Usar Branches?

| Benefício                         | Descrição                                                                            |
| ---------------------------------- | -------------------------------------------------------------------------------------- |
| **Isolamento**               | Cada feature ou correção pode ser desenvolvida isoladamente                          |
| **Desenvolvimento Paralelo** | Multiple desenvolvedores podem trabalhar em diferentes funcionalidades simultaneamente |
| **Experimentação Segura**  | Alterações experimentais não afetam o código em produção                         |
| **Organização**            | Separação clara entre trabalho em andamento e código estável                       |

### Ciclo de Vida de uma Branch

1. **Criar** - Iniciar uma nova linha de desenvolvimento
2. **Trabalhar** - Fazer commits com alterações
3. **Merge** - Integrar as mudanças à branch destino
4. **Deletar** - Remover a branch após a integração

### Visualizando Branches

Um branch é simplesmente um ponteiro (reference) que aponta para um commit específico. O Git usa essa referência para navegar pelo histórico de commits.

#### Diagrama de Múltiplas Branches

```
       main:     A---B---C---D---E
                │
                └─ feature/login:       F---G---H
                           │
                           └─ bugfix/error:        I---J
```

- **A, B, C, D, E**: Commits na branch main
- **F, G, H**: Commits na branch feature/login (começa a partir de E)
- **I, J**: Commits na branch bugfix/error (começa a partir de H)

#### HEAD: O Ponteiro Atual

O **HEAD** é uma referência especial que indica o commit (e branch) atual onde você está trabalhando.

```
HEAD -> main -> D (você está na branch main, no commit D)
```

Quando você muda de branch, o HEAD é atualizado para apontar para a nova branch.

## Branch Principal (main/master)

A branch **main** (anteriormente chamada de **master**) é a branch padrão do repositório. Ela representa a linha principal de desenvolvimento e, geralmente, contém o código que está em produção.

### Características

- É criada automaticamente ao inicializar um repositório Git
- Geralmente contém o código mais estável e deployável
- Frequentemente protegida em repositórios remotos (não permite push direto)
- Serve como base para criar outras branches

### Histórico: master → main

Recentemente, a comunidade Git mudou de **master** para **main** como nome padrão, adotando uma linguagem mais inclusiva. Repositórios novos já usam **main** por padrão.

## Trabalhando com Branches

### Listar Branches

Para ver quais branches existem no seu repositório local:

```bash
# Listar branches locais
git branch

# Listar todas as branches (locais e remotas)
git branch -a

# Listar branches com último commit
git branch -v

# Listar branches que já foram mescladas na branch atual
git branch --merged

# Listar branches que ainda não foram mescladas
git branch --no-merged
```

### Criar uma Nova Branch

Para criar uma ramificação a partir do ponto atual onde você está:

```bash
# Criar uma nova branch (sem trocar para ela)
git branch <nome-da-branch>

# Exemplo
git branch feature/login
```

#### Boas Práticas de Nomenclatura

Use nomes descritivos e consistentes para suas branches:

| Prefixo                 | Uso                   | Exemplo                    |
| ----------------------- | --------------------- | -------------------------- |
| `feature/`            | Novas funcionalidades | `feature/login-social`   |
| `fix/` ou `bugfix/` | Correção de bugs    | `fix/bug-login-123`      |
| `hotfix/`             | Correções urgentes  | `hotfix/erro-producao`   |
| `docs/`               | Documentação        | `docs/readme-atualizado` |
| `refactor/`           | Refatoração         | `refactor/auth-service`  |
| `experiment/`         | Experimentos          | `experiment/nova-api`    |

### Dicas

- Use letras minúsculas e hifens para separar palavras
- Inclua o número da issue quando aplicável: `feature/login-#123`
- Mantenha nomes curtos mas descritivos

### Trocar de Branch

Para navegar entre as linhas do tempo (branches):

```bash
# Trocar para uma branch existente
git checkout <nome-da-branch>

# OU (comando mais moderno)
git switch <nome-da-branch>

# Exemplo
git checkout feature/login
git switch feature/login
```

> **Nota:** O `git switch` é recomendado pois é mais específico que `git checkout` (que também serve para outras coisas).

### Criar e Trocar em Um Comando

Na prática, quase sempre que criamos uma branch, queremos ir imediatamente para ela. Existem atalhos para isso:

```bash
# Criar e trocar para nova branch em um comando
git checkout -b <nome-da-branch>

# OU (comando mais moderno)
git switch -c <nome-da-branch>

# Exemplo
git checkout -b feature/login
git switch -c feature/login
```

> `-c` significa "create" (criar)

## Estados do Working Directory

Quando você troca de branch, o Git altera o conteúdo do seu diretório de trabalho para refletir o estado da branch selecionada.

### O que Acontece ao Trocar de Branch

1. O Git identifica o commit pela nova branch
2. Os arquivos no diretório de trabalho são atualizados para esse commit
3. O ponteiro HEAD é atualizado para apontar para a nova branch

### Cenário Comum

```
1. Você está na branch main com arquivos da versão 1.0
2. Troca para feature/nova-func
3. Seus arquivos agora mostram a versão com a nova funcionalidade
4. Trabalha e faz commits nessa versão
5. Troca de volta para main
6. Seus arquivos voltam para a versão original
```

### Mudanças Não Commitadas

Se você tiver alterações não salvas (não commitadas) e tentar trocar de branch, o Git impedirá a troca para evitar perda de trabalho.

```bash
# Você está em main com mudanças não commitadas
$ git status
On branch main
Changes not staged for commit:
  modified:   arquivo.txt

# Tentando trocar de branch
$ git checkout feature/nova
error: Your local changes would be overwritten by checkout.
Please commit them or stash them before you switch branches.
```

#### Soluções

1. **Fazer commit** das mudanças antes de trocar
2. **Stash** (salvar temporariamente): `git stash`

```bash
# Salvar mudanças temporariamente
git stash

# Trabalhar na nova branch
git checkout feature/nova
# ... fazer trabalho ...

# Voltar para a branch anterior
git checkout main

# Restaurar as mudanças salvas
git stash pop
```

## Merge: Unindo Branches

### O que é Merge?

Merge é a operação de pegar as mudanças desenvolvidas em uma branch separada (ex: `feature`) e aplicá-las em outra branch (ex: `main`). É como dizer: "Ok, o código do universo paralelo está pronto, agora vamos trazê-lo para a realidade principal".

### Sintaxe Básica

Para fazer um merge, você **sempre deve estar na branch de destino** (a branch que vai receber as mudanças).

```bash
# 1. Troque para a branch que vai receber as alterações
git switch main

# 2. Execute o merge trazendo a branch desejada
git merge <nome-da-branch-feature>
```

### Exemplo de Merge

```bash
# Criar e ir para nova branch
git switch -c feature/nova-tela

# ... faço edições no código ...
git add .
git commit -m "feat: adiciona nova tela de perfil"

# Volto para a branch principal
git switch main

# Incorporo a nova funcionalidade à main
git merge feature/nova-tela
```

## Tipos de Merge

### Fast-Forward Merge

<!-- TODO: O que é fast-forward -->

<!-- Quando acontece: quando não há commits divergentes -->

### Fast-Forward Merge

Acontece quando a branch de destino (`main`) **não teve nenhum commit novo** desde que a branch de `feature` foi criada. Como o caminho é direto, o Git simplesmente move o ponteiro da `main` "para frente" (fast-forward) até o commit mais recente da `feature`.

```mermaid
gitGraph
   commit id: "A"
   commit id: "B"
   branch feature
   checkout feature
   commit id: "C"
   commit id: "D"
   checkout main
   merge feature type: FAST_FORWARD
```

### Three-Way Merge

<!-- TODO: O que é three-way merge -->

<!-- Quando acontece: quando há commits em ambas as branches -->

```
Antes:
main:    A---B---C
              \
feature:       D---E

Depois (merge commit):
main:    A---B---C---F
              \     /
feature:       D---E
```

### Merge Commit

<!-- TODO: O que é um merge commit -->

<!-- Tem dois parents -->

## Estratégias de Merge

Na linha de comando, podemos forçar o comportamento do merge através de opções (flags):

### --ff (Fast-Forward)

É o comportamento padrão do Git se for possível fazer um fast-forward. Não cria um commit de merge.

```bash
git merge feature-nome # Usa --ff por padrão
```

### --no-ff (No Fast-Forward)

Força o Git a **sempre** criar um merge commit, mesmo que um fast-forward fosse possível. É muito usado em equipes para manter um registro visual de onde uma feature começou e terminou.

```bash
git merge --no-ff feature-nome
```

### --squash

O `squash` pega todos os commits da branch de `feature` e os comprime em uma única alteração no Working Directory, sem comitá-los automaticamente. Você então faz um único commit na branch principal com todas as novidades agregadas.

```bash
git merge --squash feature-nome
git commit -m "feat: pacote de funcionalidades finalizado"
```

## Deletando Branches

### Deletar uma Branch Local

```bash
# Deletar branch local (apenas se já foi merged)
git branch -d <nome-da-branch>

# Forçar deleção (use com cuidado)
git branch -D <nome-da-branch>

# Exemplo
git branch -d feature/login
git branch -d bugfix/erro-correcao
```

### Deletar uma Branch Remota

```bash
# Deletar branch remota
git push origin --delete <nome-da-branch>

# Exemplo
git push origin --delete feature/nova-funcionalidade
```

### Quando Deletar Branches

- Após fazer merge na branch principal
- Quando a funcionalidade foi abandonada
- Para manter o repositório limpo

> **Nota:** Use `-d` (minúsculo) apenas se a branch já foi mesclada. Use `-D` (maiúsculo) para forçar a deleção.

## Visualizando o Grafo

O terminal pode desenhar o histórico das branches e seus merges de forma bastante ilustrativa:

```bash
git log --graph --oneline --all
```

## Branch Tracking

### Upstream Branch

Quando você envia uma branch local para o GitHub pela primeira vez, o Git precisa saber qual é a branch "gêmea" dela lá no servidor. Esse link é chamado de configuração de *upstream*.

```bash
# Ao fazer push pela primeira vez, cria a branch no remoto e vincula as duas
git push -u origin <nome-da-branch>

# A partir daí, basta digitar:
git push
```

## Exemplos Práticos

### Exemplo 1: Feature Branch Workflow

```bash
# Atualiza localmente
git pull origin main

# Cria a nova branch
git switch -c feature/dark-mode

# Trabalha...
git add .
git commit -m "feat: adiciona tema escuro"

# Retorna e integra
git switch main
git merge feature/dark-mode

# Limpa a casa
git branch -d feature/dark-mode
```

### Exemplo 2: Desfazendo um Merge

Se você fez o merge na branch errada antes de enviar pro servidor:

```bash
# Remove o último commit (o do merge indesejado) da branch atual
git reset --hard HEAD~1
```

## Boas Práticas

- **Mantenha branches pequenas:** Elas devem durar pouco tempo, de preferência dias, não meses.
- **Commits frequentes:** Salve o progresso regularmente.
- **Merge com frequência:** Traga mudanças da `main` para a sua branch (`git merge main`) frequentemente para evitar um acúmulo gigante de alterações conflitantes no final.
- **Delete após usar:** Fez o merge, apague a branch.
- **Não comite na main:** Em times profissionais, o fluxo natural é sempre criar branch, aprovar e mergiar.

## Workflows Comuns

### Feature Branch Workflow

O fluxo mais clássico: a `main` é sagrada. Todo o novo desenvolvimento de qualquer funcionalidade, correção ou teste é feito numa branch dedicada (`feature/...`). Quando pronto, abre-se um Pull Request no GitHub para revisar e fundir à `main`.

### Gitflow

<!-- TODO: Introdução básica ao Gitflow -->

<!-- (Detalhado no capítulo 07) -->

## Conflitos de Merge

<!-- TODO: Introdução básica a conflitos -->

<!-- (Detalhado no capítulo 06 - Resolução de Conflitos) -->

### O que São

Conflitos são apenas o Git pedindo a intervenção humana para escolher qual código deve prevalecer. O Git insere marcações visuais (`<<<<<<<`, `=======`, `>>>>>>>`) no código conflitante para que você leia, decida, edite o arquivo apagando os marcadores e depois faça um commit para concluir o merge. (Esse processo é detalhado no Capítulo 06).

## git stash

Se você estiver no meio de um trabalho confuso e precisar trocar de branch urgentemente para arrumar um bug rápido na `main`, você pode usar a "gaveta" do Git: o `stash`.

### Quando Usar Stash

O comando `stash` pega todas as suas alterações não comitadas e as guarda temporariamente, limpando seu diretório. Assim, você pode trocar de branch livremente. Quando voltar, você as retira da gaveta.

```bash
# Guarda mudanças temporariamente na gaveta
git stash

# Tira a última coisa guardada da gaveta e aplica nos arquivos
git stash pop

# Vê o que tem guardado
git stash list
```

## Comparando Branches

Para ver o que tem de diferente no código da sua branch em relação à `main` antes do merge:

```bash
# Mostra o código diferente (diff) entre duas branches
git diff main..minha-branch
```

## Erros Comuns

### Erro 1: Merge na Branch Errada

Você queria fundir na `main`, mas sem perceber estava na branch `teste` e fez o merge nela.
**Solução:** Use o `git status` ou olhe a indicação no seu terminal para sempre ter certeza de qual branch está (`git switch`) antes de invocar o `git merge`. Se errar, pode ser revertido via `git reset`.

### Erro 2: Deletar Branch Sem Merge

Tentar apagar uma branch com código não finalizado usando `git branch -D` (forçado).
**Solução:** Sempre tente usar `-d` (minúsculo), o Git só permitirá deletar se tiver certeza de que as alterações já estão salvas na branch principal.

### Erro 3: Não Atualizar a Main Antes de Criar Branch

Criar uma branch a partir de uma `main` antiga na sua máquina, resultando em dezenas de conflitos na hora de integrar meses depois.
**Solução:** Sempre rode `git pull origin main` e certifique-se de ter os arquivos atualizados antes de dar o `git switch -c`.

## Exercícios

1. Crie uma nova branch chamada `docs/primeiro-teste` e troque para ela.
2. Adicione ou altere um arquivo. Faça o `git add` e o `git commit`.
3. Volte para a branch principal (`git switch main`). Observe que as suas alterações "sumiram" dos arquivos!
4. Realize a união usando `git merge docs/primeiro-teste` para que a `main` incorpore as mudanças.
5. Delete a branch usando `git branch -d docs/primeiro-teste`.

## Tabela de Referência

| Comando | Descrição |
| --- | --- |
| `git branch` | Lista as branches locais. |
| `git switch <branch>` | Troca para a branch especificada. |
| `git switch -c <branch>` | Cria uma nova branch e já troca para ela. |
| `git merge <branch>` | Junta a branch informada para dentro da branch atual. |
| `git branch -d <branch>` | Deleta a branch local (se já tiver sido mergiada). |
| `git stash` | Guarda alterações não comitadas temporariamente na gaveta. |

## Recursos Adicionais

- [Learn Git Branching (Game interativo incrível!)](https://learngitbranching.js.org/)
- [Atlassian Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)

## Resumo

- **Branches** são universos paralelos de desenvolvimento que isolam as alterações.
- Use **`git switch`** para viajar entre esses universos.
- Use **`git merge`** a partir da branch de destino (ex: `main`) para fundir as alterações de outra branch.
- Sempre tente atualizar sua branch local antes de criar novos trabalhos paralelos para evitar dores de cabeça no futuro.
- Acostume-se a **deletar** as branches após os merges para manter a organização do time.

---

## 👥 Contribuidores

Este conteúdo é colaborativo. Contribuidores deste arquivo:

- [@daniballester](https://github.com/daniballester) - Issue #19 - Seção "O que são Branches"
