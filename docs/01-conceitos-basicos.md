# Conceitos Básicos de Git e GitHub

<!-- Este arquivo introduz os conceitos fundamentais de controle de versão, Git e GitHub -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:
- Compreender o que é um sistema de controle de versão e por que ele é essencial.
- Diferenciar claramente o Git (ferramenta) do GitHub (plataforma).
- Instalar e realizar a configuração inicial do Git no seu computador.
- Entender os conceitos fundamentais como Repositório, Commit, Branch e Histórico.
- Criar a sua própria conta no GitHub para hospedar seus projetos.

## 🎯 Introdução

O controle de versão é uma prática fundamental no desenvolvimento de software moderno. Imagine trabalhar em um documento importante e ter dezenas de cópias salvas com nomes como "projeto_final", "projeto_final_revisado" e "projeto_final_agora_vai". Isso não apenas ocupa espaço, mas também torna impossível rastrear quem alterou o que e quando. É exatamente esse problema que o controle de versão resolve. Ao aprender Git, você adquire a habilidade de registrar o histórico completo do seu código, colaborar de forma eficiente com outros desenvolvedores em qualquer lugar do mundo e ter a segurança de poder desfazer alterações indesejadas a qualquer momento.

## O que é Controle de Versão?

O controle de versão é um sistema que registra as mudanças feitas em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas mais tarde. 

Problemas que ele resolve:
- Evita a necessidade de criar várias cópias do mesmo arquivo com nomes diferentes.
- Permite que várias pessoas trabalhem no mesmo projeto simultaneamente sem sobrescrever o trabalho umas das outras.
- Fornece um histórico detalhado de todas as alterações, respondendo a perguntas como: "Quando esse bug foi introduzido?" ou "Quem adicionou essa funcionalidade?".

Exemplos do dia a dia incluem o histórico de versões do Google Docs ou o simples comando "Ctrl+Z" (Desfazer), mas com um escopo muito maior e permanente. No controle de versão local, as versões são salvas no seu próprio computador, enquanto no distribuído (como o Git), cada desenvolvedor possui uma cópia completa do histórico do projeto.

### Benefícios do Controle de Versão

- **Histórico Completo:** Registro de cada alteração feita, com a justificativa de quem e por que foi feita.
- **Colaboração Eficiente:** Diversas pessoas podem trabalhar no mesmo código ao mesmo tempo de forma organizada.
- **Backup e Restauração:** Como o histórico é mantido, é fácil voltar para uma versão anterior se algo der errado.
- **Experimentação Segura:** Possibilidade de testar novas ideias em ambientes isolados (branches) sem afetar a versão principal e funcional do projeto.

## O que é Git?

O Git é um sistema de controle de versão distribuído de código aberto, criado por Linus Torvalds em 2005 para o desenvolvimento do kernel do Linux. Atualmente, é o sistema de controle de versão mais utilizado no mundo, sendo uma ferramenta indispensável para desenvolvedores de software de todas as áreas.

### Características Principais do Git

- **Distribuído:** Cada desenvolvedor possui uma cópia local completa do repositório, incluindo todo o seu histórico.
- **Rápido:** A maioria das operações no Git é feita localmente, o que proporciona uma velocidade enorme em comparação com sistemas centralizados.
- **Integridade de Dados:** Tudo no Git é verificado por meio de um hash (SHA-1), garantindo que as informações não possam ser corrompidas sem que o Git perceba.
- **Branching Leve:** Criar e alternar entre branches (ramificações) no Git é quase instantâneo.

### Como o Git Funciona?

O Git não armazena as informações como uma lista de alterações baseada em arquivos, mas sim como uma série de *snapshots* (capturas de tela) de um mini sistema de arquivos. Toda vez que você salva, ele tira uma foto de como todos os seus arquivos estão naquele momento e armazena uma referência para ela.

O fluxo de trabalho básico do Git envolve três estados principais onde os arquivos podem residir:
1. **Working Directory (Diretório de Trabalho):** Onde você modifica os arquivos localmente.
2. **Staging Area (Área de Preparação):** Um arquivo intermediário que armazena as informações sobre o que vai entrar no seu próximo commit.
3. **Repository (Repositório/Diretório Git):** Onde o Git armazena os metadados e o banco de dados de objetos para o seu projeto de forma permanente.

## O que é GitHub?

O GitHub é uma plataforma online de hospedagem de código-fonte e arquivos com controle de versão usando o Git. Ele oferece todas as funcionalidades de controle de versão distribuído e gerenciamento de código-fonte (SCM) do Git, além de adicionar seus próprios recursos de colaboração e gerenciamento de projetos. É a maior plataforma de código aberto do mundo.

### Recursos do GitHub

- **Repositórios Remotos:** Hospedagem na nuvem para seus projetos Git.
- **Issues:** Um sistema integrado de rastreamento de bugs e planejamento de tarefas.
- **Pull Requests:** Permitem propor mudanças em um repositório, facilitando a revisão de código em equipe.
- **GitHub Actions:** Ferramenta para automatizar fluxos de trabalho, como testes e implantação contínua (CI/CD).
- **GitHub Pages:** Hospedagem gratuita de sites estáticos diretamente de um repositório GitHub.

## Diferença entre Git e GitHub

Uma confusão muito comum para iniciantes é achar que Git e GitHub são a mesma coisa, mas não são!

| Característica | Git | GitHub |
|----------------|-----|--------|
| O que é? | Ferramenta de linha de comando (software) | Plataforma de hospedagem baseada na web (serviço) |
| Onde roda? | Localmente, no seu computador | Remotamente, na nuvem |
| Função | Gerencia o controle de versão dos seus arquivos | Hospeda os repositórios Git e facilita a colaboração |
| Necessidade de internet | Não (maioria das operações é local) | Sim |

### Analogia Útil

Pense no Git e no GitHub da seguinte forma: o **Git** é o programa de edição e criação de vídeos no seu computador, enquanto o **GitHub** é o YouTube, onde você hospeda, compartilha e recebe comentários sobre os vídeos que você criou com o Git.

## Conceitos Fundamentais

### Repositório (Repository)

Um repositório (ou simplesmente "repo") é onde os arquivos do seu projeto estão armazenados, juntamente com todo o histórico de alterações. Ele pode ser **local** (uma pasta no seu computador sob o controle do Git) ou **remoto** (hospedado em servidores na internet, como no GitHub).

### Commit

Um commit é como salvar o jogo em um videogame ou tirar uma "foto" (snapshot) do estado atual dos seus arquivos. Ele registra permanentemente as alterações no histórico do Git. Todo commit precisa ter uma mensagem descritiva explicando o que foi alterado, e fica registrado com informações como o autor, a data e a hora (timestamp).

### Branch

Um branch (ramificação) é uma linha de desenvolvimento separada e paralela. Ele permite que você trabalhe em novas funcionalidades ou corrija bugs sem afetar a versão principal do projeto (geralmente chamada de `main` ou `master`). 

### Histórico

O histórico do Git é a linha do tempo de todos os commits já feitos no repositório. Ele serve para acompanhar a evolução do projeto, descobrir quem fez determinadas alterações e voltar a estados anteriores do código, se necessário. Pode ser visualizado usando o comando `git log`.

### Clone vs Fork

- **Clone:** É o ato de baixar uma cópia exata de um repositório remoto do GitHub para o seu computador local, criando um repositório local vinculado ao original.
- **Fork:** É criar uma cópia pessoal de um repositório de outra pessoa na sua própria conta do GitHub. Geralmente é o primeiro passo quando você quer contribuir para projetos de código aberto.

## Instalação do Git

### Windows

1. Acesse o link oficial: https://git-scm.com/download/win
2. Baixe o executável para o seu sistema (geralmente 64-bit).
3. Execute o instalador e siga o passo a passo mantendo as configurações padrão na maioria dos casos (Next > Next...).

### macOS

Se você usa macOS, provavelmente já tem o Git instalado se tiver o Xcode Command Line Tools.
Para instalar usando o Homebrew, abra o terminal e digite:
```bash
brew install git
```

### Linux

A instalação depende da sua distribuição. Abra o terminal e digite:

Para Ubuntu/Debian:
```bash
sudo apt update
sudo apt install git
```

Para Fedora:
```bash
sudo dnf install git
```

Para Arch Linux:
```bash
sudo pacman -S git
```

### Verificando a Instalação

Para confirmar que o Git foi instalado com sucesso, abra o terminal (ou Git Bash no Windows) e execute:

```bash
git --version
```
Isso deverá retornar a versão instalada, por exemplo: `git version 2.40.0`.

## Configuração Inicial

Após instalar o Git, é fundamental configurar sua identidade. Essas informações serão associadas a cada *commit* que você realizar, permitindo identificar quem é o autor das alterações no projeto.

#### 1. Configuração de Identidade

Você deve configurar seu nome e e-mail. Existem dois níveis principais de configuração:
* **Global:** Aplica-se a todos os repositórios do seu usuário na máquina.
* **Local:** Aplica-se apenas ao repositório específico onde você está trabalhando.

#### Configuração Global
Para configurar em toda a sua máquina, utilize o parâmetro `--global`:

```bash
# Define seu nome de exibição
git config --global user.name "Seu Nome"

# Define seu e-mail de contato
git config --global user.email "seu.email@example.com"
```

#### Configuração Local
Se precisar usar um e-mail diferente para um projeto específico (ex: e-mail corporativo em um projeto da empresa), execute o comando dentro da pasta do projeto **sem** o `--global`:

```bash
git config user.name "Seu Nome Profissional"
git config user.email "nome.sobrenome@empresa.com"
```

#### 2. Verificação das Configurações

Para conferir se as informações foram gravadas corretamente, você pode listar as configurações atuais:

```bash
# Lista todas as configurações ativas (local + global)
git config --list

# Lista apenas as configurações globais
git config --list --global
```

#### 3. Configurações Recomendadas (Opcional)

Além da identidade, é recomendável ajustar o editor de texto padrão e o comportamento de quebra de linha.

#### Editor de Texto
Define qual editor abrirá quando o Git precisar que você escreva uma mensagem (ex: VS Code, Vim ou Notepad++):

```bash
# Exemplo para configurar o VS Code como editor padrão
git config --global core.editor "code --wait"
```

#### Tratamento de Fim de Linha (autocrlf)
Isso evita problemas de compatibilidade entre Windows (que usa CRLF) e sistemas Unix/Mac (que usam LF).

```bash
# Se você usa Windows:
git config --global core.autocrlf true

# Se você usa Mac ou Linux:
git config --global core.autocrlf input
```

#### 4. Troubleshooting (Resolução de Problemas)

* **Alterar uma configuração existente:** Basta executar o comando novamente com o novo valor. O Git sobrescreverá o anterior.
* **Remover uma configuração (Reset):** Caso queira voltar ao padrão do sistema e remover uma entrada específica:

```bash
# Remove o e-mail global
git config --global --unset user.email
```


**Observação:** Lembre-se que o Git prioriza sempre a configuração **Local** sobre a **Global**. Se você configurou um e-mail dentro da pasta do projeto, ele será usado em vez do e-mail geral da sua máquina.



### Por que Configurar Nome e Email?

A configuração de nome e e-mail não é apenas burocrática; ela é o que garante a rastreabilidade do projeto. No Git, cada alteração (commit) é "assinada".

* **Identificação de Autoria:** Em uma equipe, todos precisam saber quem fez cada modificação para tirar dúvidas ou revisar o código.
* **Histórico de Contribuições:** Sites como GitHub e GitLab usam o e-mail configurado para vincular suas alterações ao seu perfil, gerando aquele gráfico de contribuições (os quadradinhos verdes).
* **Segurança e Auditoria:** Ajuda a manter um registro claro de quando e por quem uma funcionalidade foi adicionada ou um erro foi introduzido.

> **Importante:** O Git não verifica se o e-mail é real ou se você é o dono dele, mas se você usar um e-mail diferente do que está cadastrado no seu GitHub, o commit não aparecerá vinculado ao seu perfil de usuário.


## Criando uma Conta no GitHub

1. Acesse https://github.com/ e clique em **"Sign up"** no canto superior direito.
2. Insira o seu endereço de email, crie uma senha forte e escolha um nome de usuário (que será público).
3. Resolva o desafio de verificação de segurança.
4. Clique em "Create account" e verifique a sua conta através do código enviado para o seu email.

## Exemplos Práticos

### Exemplo 1: Cenário sem Controle de Versão

Imagine uma equipe de três pessoas desenvolvendo um site juntas. A pessoa A edita o arquivo `index.html` e a pessoa B também. Quando vão juntar o trabalho num pendrive, o arquivo da pessoa B sobrescreve o trabalho da pessoa A. Para evitar isso, começam a criar arquivos como `index_final.html`, `index_final_revisado_joao.html`. Fica impossível saber qual é a versão mais recente e correta.

### Exemplo 2: Mesmo Cenário com Git

Com Git, as três pessoas trabalham em seus repositórios locais. O Git acompanha linha por linha do `index.html`. Quando a pessoa A e a pessoa B enviam (push) suas alterações para o repositório central, o Git consegue unir (merge) o trabalho de ambas automaticamente na grande maioria das vezes. Se houver modificações na exata mesma linha, o Git avisará que existe um "conflito" e deixará os desenvolvedores decidirem facilmente qual alteração manter, sem perder nada.

## Erros Comuns

### Erro 1: Confundir Git com GitHub

Como vimos, Git é a ferramenta rodando na sua máquina; GitHub é o site onde o código é guardado online. Sempre lembre: você usa o *Git* para enviar seu código para o *GitHub*.

### Erro 2: Não configurar nome e email

Se você tentar fazer um commit sem configurar seu nome e email, o Git retornará um erro pedindo para configurá-los. Para corrigir, basta rodar os comandos `git config --global` mostrados anteriormente.

## Exercícios

1. Instale o Git em seu computador, abra o terminal e verifique a versão instalada rodando `git --version`.
2. Configure o Git globalmente com o seu nome completo e o seu email que será usado no GitHub.
3. Acesse o site do GitHub e crie uma conta gratuita, caso ainda não possua uma.

## Recursos Adicionais

<!-- TODO: Adicione links úteis para aprofundamento -->

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Tutorial de Configuração Git (Atlassian)](https://www.atlassian.com/br/git/tutorials/setting-up-a-repository/git-config)
- <!-- Adicione mais recursos -->

## Glossário

- **Commit**: Uma gravação permanente de um conjunto de alterações no histórico do Git.
- **Repository**: Uma pasta que contém os arquivos do seu projeto e o histórico do Git associado a eles.
- **Clone**: O processo de criar uma cópia local de um repositório remoto.
- **Fork**: Uma cópia pessoal do repositório de outra pessoa, hospedada na sua conta do GitHub.

## Resumo

- O **controle de versão** é essencial para registrar o histórico, colaborar e manter a segurança do código.
- **Git** é a ferramenta (software) que faz o controle de versão localmente de maneira rápida e distribuída.
- **GitHub** é a plataforma web que hospeda projetos Git e facilita a colaboração.
- O fluxo de trabalho básico do Git envolve o **Working Directory**, a **Staging Area** e o **Repository**.
- Conceitos-chave incluem **Commits** (snapshots), **Branches** (linhas paralelas de desenvolvimento) e **Clones/Forks**.

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
- [Rafael Ziani de Carvalho](https://github.com/steinbukken7321) - Configuração Inicial do Git
