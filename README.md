# 🧠 Guia de Comandos Git

> Um repositório para aprender e revisar os comandos essenciais do **git**

<br>

## 📋 Índice
- [🧠 Guia de Comandos Git](#-guia-de-comandos-git)
  - [📋 Índice](#-índice)
      - [Resumo:](#resumo)
      - [Tradução Técnica:](#tradução-técnica)
  - [⚙️ Instalação](#️-instalação)
      - [Windows](#windows)
  - [Comandos Básicos](#comandos-básicos)
      - [Nomes e emails](#nomes-e-emails)
      - [Clones](#clones)
      - [Adicionar, comentar e subir para o repositório (add, commit e push)](#adicionar-comentar-e-subir-para-o-repositório-add-commit-e-push)
        - [Introdução bem básica](#introdução-bem-básica)
        - [Como é o procedimento](#como-é-o-procedimento)
      - [Atualizar Repositórios (fetch)](#atualizar-repositórios-fetch)
        - [O que é um remote?](#o-que-é-um-remote)
        - [O que é uma branch?](#o-que-é-uma-branch)
        - [Comando fetch](#comando-fetch)
          - [Como usar](#como-usar)
          - [Exemplo](#exemplo)

O **Git** é um sistema de controle de versões distribuído. Um sistema de controle de versões distribuído (como o **Git**) é como ter checkpoints compartilhados em um jogo multiplayer:

**1. Cada Jogador Tem o Jogo Completo:**
Todo mundo tem uma cópia do jogo inteiro (histórico de saves, fases, itens)

**2. Save Offline:**
Você pode criar checkpoints (commits) sem internet e sincronizar depois

**3. Colaboração Sem Bagunça:**
Se dois jogadores modificarem o mesmo nível, o sistema ajuda a juntar as mudanças sem perder progresso

#### Resumo:
É como ter poder de viajar no tempo + um assistente que resolve conflitos entre saves

#### Tradução Técnica:

- Checkpoint = Commit
- Jogo completo = Repositórios clonados
- Juntar as mudanças = Merge/Rebase

## ⚙️ Instalação

#### Windows

Vá ao [site de download](https://git-scm.com/downloads "Downloads do git") para baixar o **Git**

ou baixe o **executável** via terminal:

abra o **Powershell** copie o comando abaixo e cole no **Powershell**:
```powershell
cd ~\Downloads\ # vai para a pasta "Downloads"
winget install --id Git.Git -e --source winget # baixa o executável via terminal na pasta atual
```

Vou colocar o video futuramente com o tutorial para baixar

## Comandos Básicos

Bom, a partir daqui, é bom já ir abrindo o git e uma das primeiras coisas que tem que ser feitas é definir os nome de usuário e o email de usuário. Segue abaixo os comandos:

#### Nomes e emails

```bash
git config --global user.name "Artemiz"
```

**O que o comando acima faz?** Bom, aqui estamos configurando o nome de usuário para Artemiz globalmente, ou seja, para todos os repositórios, o nome de usuário será esse (aparece em commits). Você também pode querer que seu nome fique de outro jeito em repositórios específicos. Para isso, você só precisa tirar a flag "--global". Ficaria desse jeito:

```bash
git config user.name "Pipoca"
```

Agora vamos para o email que não muda muita coisa

```bash
git config --global user.email "artemiz@gmail.com"
```

ou

```bash
git config user.email "pipoocaah@gmail.com"
```

#### Clones

Ok, agora vamos para a parte de clonar repositórios. É basicamente aqui que todo mundo vai ter uma versão própria do repositório.

Bom, a sintaxe é desse jeito:
```bash
git clone <HTTPS|SSH>
```

Um exemplo prático de como clonar o mesmo repositório com HTTPS e SSH:

HTTPS:
```bash
git clone https://github.com/Artemis-TK/Git-Introduction.git
```

SSH:
```bash
git clone git@github.com:Artemis-TK/Git-Introduction.git
```

Acredito que só vamos usar mais o HTTPS para clonar.

---

#### Adicionar, comentar e subir para o repositório (add, commit e push)

##### Introdução bem básica
Uma introdução bem basica: sempre que a gente clona um repositório ou ou inicia um, a gente começa a fazer modificações nos arquivos. Sempre que a gente faz alguma modificação em algum arquivo, a gente pode adicionar eles para a área de stage (ou só área stage). Essa área é onde a gente pode fazer os comentários (commit) que vão aparecer no repositório. Depois disso tudo, é só subir para o repositório remoto.

##### Como é o procedimento

```bash
git add arquivo.txt # adiciona apenas o arquivo específico
git commit -m "adicionando o arquivo.txt ao remoto" # faz um comentário com a mensagem 'adicionando o arquivo.txt ao remoto'. Você pode colocar qualquer mensagem aqui, mas é bom que seja intuitiva.
git push # sobe todos os commits para o remoto
```

Entenda o nome 'remoto' como referência para o repositório remoto.

Você também adicionar desse jeito:
```bash
git add . # adiciona todos os arquivos que foram modificados
```

ou desse jeito

```bash
git add * # adiciona todos os arquivos que foram modificados
```

#### Atualizar Repositórios (fetch)

Aqui a gente vai entender um pouco do comando `git fetch`. Antes de ir pro comando, é preciso entender um pouco sobre o que são **remotes** e **branchs**

##### O que é um remote?
Bom, um remote é basicamente um nome que aponta para o link de um repositório remoto. É como se fosse um tipo de atalho, que quando você digita o nome, é como se você estivesse digitando o link onde está o repositório. Sempre que você clona um repositório, o nome padrão do remote é "origin". Tente executar o comando abaixo para fixar melhor

```bash
git clone https://github.com/Artemis-TK/Git-Introduction.git
git remote -v
```

Você vai ver algo assim
```yaml
origin https://github.com/Artemis-TK/Git-Introduction.git (fetch)
origin https://github.com/Artemis-TK/Git-Introduction.git (push)
```

o nome "origin" está apontando diretamente para o link. Você pode mudar esse nome, mas é o normal ter essa nomenclatura. Se quiser mudar o nome padrão, basta executar esse comando:

```bash
git remote rename origin repo
```
Agora, ao invés de usar o origin, você vai usar o nome repo ou o nome que você escolher.

Acho que deve ter ficado claro, agora é só tentar entender branchs pra ir pro git fetch.

---

##### O que é uma branch?
Uma **branch** (ou "ramo") é uma **linha de desenvolvimento separada** dentro do projeto.

- Imagine que o projeto é um **livro**: uma branch é como um **rascunho alternativo** do livro, onde você pode testar novas ideias sem estragar a versão principal (`main`).

- A branch padrão geralmente se chama `main` ou `master` (depende do projeto)

**Exemplo de uso:**

- Se você cria uma branch chamada feature, está fazendo alterações isolada da branch principal (`main`)

- Quando terminar, você "mescla" ([merge](#Merge) — você vai ver esse termo mais pra frente) a feature de volta para a main

Aqui está o exemplo acima em comandos (as descrições vão estar abaixo ou depois do comando):

```bash
echo "Granola" > lista-compras.txt
```
Cria um arquivo com o nome lista-compras.txt e coloca a palavra "Granola" dentro desse arquivo <br><br><br>

```bash
git add lista-compras.txt # adiciona o arquivo lista-compras.txt para a stage (área onde pode se fazer commits)
git commit -m "Adiciona Granola na lista" # fazendo o commit com a mensagem "adicionando Granola na lista". Isso aparece no repositório
```

<br><br>
Agora é só criar a outra branch

```bash
git checkout -b feature  # Cria a branch e muda para ela
```

Objetivo: "Vou trabalhar em uma cópia segura da lista (feature), sem afetar a original (main)."

<br><br>

```bash
echo "Monster" >> lista-compras.txt # Adiciona "Monster" na última linha do arquivo
echo "RedBull" >> lista-compras.txt # Adiciona "RedBull" na última linha do arquivo
```

Agora é só fazer adicionar e commitar as mudanças na branch feature:
```bash
git add lista-compras.txt
git commit -m "Adiciona Monster e RedBull"
```

Depois disso, volte para a branch `main`

```bash
git checkout main # Volta para a branch principal
```

Agora é só mesclar (merge)

```bash
git merge feature # Combina as alterações da "feature" na "main"
```

---

##### Comando fetch

Ok, esse comando do git basicamente atualiza todo o projeto local, baixando todo o conteúdo do repositório remoto. Mas esse comando em si só faz isso, ele só atualiza.

- **Não altera arquivos locais**, apenas baixa as mudanças para uma **área temporária.**
- Útil para **verificar atualizações** antes de **integrá-las** ao código.

###### Como usar

```bash
git fetch <remote> <branch> # exemplo de uso: git fetch origin main
```

###### Exemplo

1. baixa as mudanças do remoto:
```bash
git fetch origin main
```

2. Compara a branch remota com sua branch local:
```bash
git diff main origin/main # Mostra diferenças entre sua branch e o remoto
```

