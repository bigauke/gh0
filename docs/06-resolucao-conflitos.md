Seu material já está muito bom — o problema não é “evitar conflitos no GitHub” no texto em si, e sim pequenos pontos que podem causar confusão ou inconsistência (principalmente marcações, exemplos quebrados e trechos ambíguos). Eu revisei tudo e deixei:

* Markdown limpo e consistente
* Blocos de código corrigidos
* Comentários HTML removidos onde não fazem sentido
* Estrutura mais segura para renderização no GitHub
* Pequenas melhorias de clareza técnica

Aqui está a versão pronta para colar no GitHub 👇

---

# Resolução de Conflitos

<!-- Este arquivo ensina como identificar, entender e resolver conflitos de merge no Git -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:

* Entender o que é um conflito de merge e por que ele acontece.
* Identificar rapidamente quando o Git sinaliza que ocorreu um conflito.
* Ler e compreender os marcadores visuais de conflito dentro de um arquivo.
* Utilizar estratégias e ferramentas (como o VS Code) para resolver conflitos de forma segura.
* Adotar práticas de trabalho em equipe para minimizar a ocorrência de conflitos.

---

## 🎯 Introdução

No começo, a tela do terminal indicando um **Merge Conflict** pode assustar. Parece que você quebrou o código ou fez algo muito errado.

Mas respire: **conflitos são normais e esperados**.

Eles não são erros do sistema. São um aviso do Git:

> "Duas pessoas mexeram no mesmo trecho e eu não sei qual versão manter. Preciso que você decida."

---

## O que são Conflitos de Merge?

Um conflito ocorre quando o Git não consegue resolver automaticamente diferenças entre commits.

Na maioria dos casos, o merge é automático. O conflito aparece quando existe ambiguidade.

### Por que conflitos acontecem?

Principais cenários:

1. Duas pessoas editaram a **mesma linha**.
2. Um alterou o arquivo e outro deletou.
3. Alterações em linhas próximas.
4. Refatorações estruturais simultâneas.

---

## Cenário típico

```text
Pessoa A (branch A)              Pessoa B (branch B)
        |                                |
        |--- edita linha 10              |
        |                                |--- edita linha 10
        |--- commit                      |
        |--- merge na main (OK)          |--- commit
                                         |--- merge (CONFLITO)
```

---

## Identificando Conflitos

### Mensagem do Git

```bash
git merge feature/novo-layout

Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

### Verificando com git status

```bash
git status
```

```text
Unmerged paths:
  both modified: index.html
```

---

## Anatomia de um Conflito

Quando abrir o arquivo:

```text
<h1>Bem-vindo ao Sistema</h1>
```

### Significado

* `<<<<<<< HEAD` → sua versão
* `=======` → separador
* `>>>>>>> branch` → versão que está entrando

---

## Exemplo Completo

### Criar repositório

```bash
git init
```

### Primeiro commit

```bash
git add .
git commit -m "criação do arquivo"
```

---

### Criar branch

```bash
git switch -c teste
```

### Código (branch teste)

```python
def calcular_media(valores):
    total = 0
    for v in valores:
        total += v
    
    print("Processando valores...")
    media = total / len(valores)
    
    resultado = f"Média calculada: {media}"
    
    return resultado

dados = [10, 20, 30]
print(calcular_media(dados))
```

```bash
git commit -am "mensagem média calculada"
```

---

### Alteração na main

```bash
git switch main
```

```python
resultado = f"Valor médio final: {media}"
```

```bash
git commit -am "mensagem valor médio final"
```

---

### Merge com conflito

```bash
git merge teste
```

### Resolver

Substituir por:

```python
resultado = f"Média: {media}"
```

```bash
git add .
git commit -m "conflito resolvido"
```

---

## Resolução Manual

### Passos

1. `git status`
2. Abrir arquivo
3. Ler as duas versões
4. Decidir
5. Editar
6. Remover marcadores
7. Testar
8. `git add`
9. `git commit`

---

## Resolução automática

```bash
git checkout --ours arquivo.txt
git checkout --theirs arquivo.txt

git add arquivo.txt
git commit
```

---

## Ferramentas

### VS Code

* Accept Current
* Accept Incoming
* Accept Both
* Compare Changes

### Merge tool

```bash
git config --global merge.tool meld
git mergetool
```

---

## Tipos de conflito

* Conteúdo
* Renomeação
* Deleção

---

## Prevenção

### Boas práticas

* Comunicação no time
* Atualizar branch frequentemente
* Commits pequenos
* Separar responsabilidades

```bash
git fetch origin
git merge origin/main
```

---

## Pull Requests

### Resolver localmente

```bash
git switch minha-branch
git pull origin main

# resolver conflitos

git add .
git commit -m "resolve conflitos"
git push
```

---

## Abortar merge

```bash
git merge --abort
```

---

## Dicas úteis

### Ver histórico

```bash
git log --oneline --graph --all
```

### Ver autor da linha

```bash
git blame arquivo.js
```

---

## Erros comuns

* Não remover `<<<<<<<`
* Não testar
* Aceitar tudo sem entender
* Force push indevido

---

## Exercício

1. Criar `teste-conflito-1`
2. Alterar README
3. Criar `teste-conflito-2`
4. Alterar mesma linha
5. Fazer merge e resolver

---

## Checklist

* [ ] Git avisou conflito
* [ ] Rodou `git status`
* [ ] Leu as duas versões
* [ ] Resolveu corretamente
* [ ] Removeu marcadores
* [ ] Testou
* [ ] `git add`
* [ ] `git commit`

---

## Recursos

* [https://git-scm.com/docs/git-merge](https://git-scm.com/docs/git-merge)
* [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)

---

## Resumo

* Conflitos são normais
* Git precisa da sua decisão
* Entenda antes de resolver
* Comunicação evita problemas

---

## 👥 Contribuidores

* @bigauke (Antonio Daniel de Souza Linhares)

---

Se quiser, posso ir além e transformar isso em um **material de aula nível SENAI/bootcamp**, com exercícios práticos guiados + simulação real de conflito pra você ensinar ou apresentar.
