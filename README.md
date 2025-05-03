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
        - [Video para instalar o git](#video-para-instalar-o-git)
  - [Comandos Básicos](#comandos-básicos)
      - [Nomes e emails](#nomes-e-emails)
      - [Clones](#clones)
      - [Comandos úteis](#comandos-úteis)
        - [Branch](#branch)
          - [Exemplo](#exemplo)
        - [Checkout](#checkout)
          - [Exemplo](#exemplo-1)
        - [Log](#log)
          - [Exemplo](#exemplo-2)
        - [Diff](#diff)
          - [Exemplo](#exemplo-3)
        - [Status](#status)
          - [Exemplo](#exemplo-4)
      - [Adicionar, comentar e subir para o repositório (git add; git commit; git push)](#adicionar-comentar-e-subir-para-o-repositório-git-add-git-commit-git-push)
        - [Introdução bem básica](#introdução-bem-básica)
        - [Como é o procedimento](#como-é-o-procedimento)
      - [Atualizar Repositórios (fetch)](#atualizar-repositórios-fetch)
        - [O que é um remote?](#o-que-é-um-remote)
        - [O que é uma branch?](#o-que-é-uma-branch)
        - [git fetch](#git-fetch)
          - [Pra quê serve](#pra-quê-serve)
          - [Como usar](#como-usar)
          - [Exemplo](#exemplo-5)
      - [git merge (mesclar)](#git-merge-mesclar)
        - [Pra quê serve](#pra-quê-serve-1)
        - [Como usar](#como-usar-1)
        - [Exemplo](#exemplo-6)
      - [❗Conflitos❗](#conflitos)
        - [Exemplo](#exemplo-7)
      - [git rebase](#git-rebase)
        - [Pra que serve](#pra-que-serve)
        - [Como usar](#como-usar-2)
          - [Exemplo](#exemplo-8)
      - [git pull](#git-pull)
        - [Pra que serve](#pra-que-serve-1)
        - [Como usar](#como-usar-3)
          - [Exemplo](#exemplo-9)
          - [Como finciona](#como-finciona)

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

#### <h3>Windows</h3>

Vá ao [site de download](https://git-scm.com/downloads "Downloads do git") para baixar o **Git**

ou baixe o **executável** via terminal:

abra o **Powershell** copie o comando abaixo e cole no **Powershell**:
```powershell
cd ~\Downloads\ # vai para a pasta "Downloads"
winget install --id Git.Git -e --source winget # baixa o executável via terminal na pasta atual
```

##### <h4>Video para instalar o git</h4>

<a href="https://www.youtube.com/watch?v=VmkEZ9qEPDU&t=101"><img src="https://img.youtube.com/vi/VmkEZ9qEPDU/0.jpg" alt=""></a>

## Comandos Básicos

Bom, a partir daqui, é bom já ir abrindo o git e uma das primeiras coisas que tem que ser feitas é definir os nome de usuário e o email de usuário. Segue abaixo os comandos:

#### <h3>Nomes e emails</h3>

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

#### <h3>Clones</h3>

Ok, agora vamos para a parte de clonar repositórios. É basicamente aqui que todo mundo vai ter uma versão própria do repositório.

Bom, a sintaxe é desse jeito:
```bash
git clone <HTTPS|SSH>
```

Um exemplo prático de como clonar o mesmo repositório com HTTPS e SSH:

HTTPS:
```bash
git clone https://github.com/Artemiz-TK/Git-Introduction.git
```

SSH:
```bash
git clone git@github.com:Artemiz-TK/Git-Introduction.git
```

Acredito que só vamos usar mais o HTTPS para clonar.

---

#### <h2>Comandos úteis</h2>

##### <h4>Branch</h4>

O comando `git branch` por si só mostra quantas [branches](#o-que-é-uma-branch) existe no projeto. Mas se for passado algum argumento, uma nova branch será criada

###### <h5>Exemplo</h5>

```bash
git branch # sem nenhum argumento passado, só vai mostrar quantas branches existem
```

Saída

```yaml
* main
```
<br>
Agora para criar uma nova branch

```bash
git branch master # coloque o nome que preferir ou deixe master
git branch # exibe as branches
```

Saída

```yaml
* main
  master
```

O **"*"** indica em qual branch você está atualmente. Logo abaixo você vai aprender a como navegar entre as branches.

<br>

##### <h4>Checkout</h4>

o comando `git checkout` é basicamente um comando que fica trocando de [branches](#o-que-é-uma-branch) ou voltando para alguns commits, como se estivesse viajando no tempo. Aqui, só vai ser preciso entender apenas a troca de **branches**.

Utilizando o exemplo do tópico [Branch](#exemplo), vamos trocar para a branch master

###### <h5>Exemplo</h5>

```bash
git checkout master # saindo da branch "main" para a "master"
git branch # exibe as branches
```

Saída

```yaml
M       README.md
Switched to branch 'master'
  main
* master
```

Vai ser algo similar a isso. Para voltar para a "main" é só repetir o processo:

```bash
git checkout main
git branch # exibe as branches
```

Saída

```yaml
M       README.md
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

Ou algo similar a isso.

Também dá para criar e já trocar de branch, se faz desse jeito:

```bash
git checkout -b feature # cria e já troca para a branch especificada
git branch # exibe as branches
```

Saída (pode ser algo similar também)

```yaml
Switched to a new branch 'feature'
* feature
  main
  master
```

<br>

##### <h4>Log</h4>

O comando `git log` é o comando que mostra o histórico de commits.

###### <h5>Exemplo</h5>

```bash
git log
```

Saída (similar)

```yaml
commit d9f1400d620c1b2c800c47e3ac6a7c16d72df429 (HEAD -> main, origin/main, master, feature)
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 20 20:26:02 2025 -0300

    fix: resolvendo mais um erro no arquivo

commit 8da22ce6201e9d145745707d2e858f33c40fe9d6
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 20 20:15:54 2025 -0300

    fix: resolvendo um erro no arquivo

commit 422b95da79b1766762a0a55074f0fa366962bb38
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 20 18:59:34 2025 -0300

    update: atualizando o arquivo

commit 424a9b7f83f9b929ce04181c50844353841d2aa3
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 20 18:45:12 2025 -0300

    feat: adicionando o arquivo README.md ao remoto
```

Esse laço de números e letras que vêm após o nome `commit` são a hash do commit, mas não precisa se preocupar com isso

Também tem a versão menos verbosa:

```bash
git log --oneline
```

Saída (similar)

```yaml
d9f1400 (HEAD -> main, origin/main, master, feature) fix: resolvendo mais um erro no arquivo
8da22ce fix: resolvendo um erro no arquivo
422b95d update: atualizando o arquivo
424a9b7 feat: adicionando o arquivo README.md ao remoto
```

Aqui a hash é bem mais curta

<br>

Segue abaixo outro exemplo do `git log`
```bash
git log origin/main..main # mostra os commits que estão no local e não no remoto
git log main..origin/main # mostra os commits que estão no remoto e não no local
```

Um exemplo de saída para `git log origin/main..main` é esse:

```yaml
commit 12db4fccaa3aee8a4c4fc4dde1918e50a7703216 (HEAD -> main)
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 27 00:59:54 2025 -0300

    update: adicionando mais conteúdo para o tópico 'Log'

commit 668d60d5b584b8b67d4cafd4536bb95373f74890
Author: Lucas <alanderson.lucas@escolar.ifrn.edu.br>
Date:   Sun Apr 27 00:45:10 2025 -0300

    update: adicionando o tópico 'Diff' ao arquivo
```

Sim, isso é antes de eu ter subido essa versão do arquivo para o repositório.

Se você executou o comando `git log main..origin/main` e existir algum commit no repositório que não exista no seu repositório local, atualize seu repositório usando o comando [git pull](#git-pull). E, por favor, não use a flag `--force` no comando git push. Pode gerar perda de dados. Para entender melhor sobre isso, vá para o tópico de [conflitos](#conflitos).

<br>

##### <h4>Diff</h4>
O comando `git diff` é usado para mostrar, comparar e entender melhor as mudanças feitas no projeto.

###### <h5>Exemplo</h5>


```bash
git diff
```

O comando acima vai mostrar as mudanças feitas no diretório de trabalho. Se você não tiver feito modificações, nada será exibido.

<br>
Agora um exemplo melhor: execute o comando abaixo, não precisa entender muito o `git remote` já que não vamos usar.

```bash
# adicionando um remoto com nome origin-a
git remote add origin-a https://github.com/Artemiz-TK/Motores_ProjetoFinal_SegundoAno.git

# adcionando um remoto com o nome origin-b
git remote add origin-b https://github.com/Artemiz-TK/Motores-Projeto.git

# buscando todas as atualizações
git fetch --all

# comparando dois arquivos em repositórios distintos
git diff origin-a/main:./.gitignore origin-b/main:./.gitignore
```

**Ok, o que tá acontecendo aqui?** Aqui, eu adicionei dois remotos - um com o nome `origin-a`, outro com o nome `origin-b` - que apontam para determinados repositórios distintos. Depois, eu busco todas as atualizações possivéis e, por fim, comparo dois arquivos.

Agora vamos focar na linha do comando `git diff`. **O que essa linha faz?** Vou dividir por partes:

``git diff``: esse comando — nesse caso — diz quais as mudanças que você precisa fazer para transformar o arquivo `origin-a/main:./.gitignore` no arquivo `origin-b/main:./.gitignore`

`origin-a/main:./.gitignore`: esse argumento começa com o remoto, que aponta para o link do repositório, depois vem a branch, que nesse caso é a `main`. O `./` indica que o arquivo que a gente quer encontrar está no diretório raiz do repositório. E o `.gitignore` é o arquivo que a gente quer comparar.

A mesma coisa vale para o `origin-b/main:./.gitignore`, só que o remoto `origin-b` aponta para outro repositório.

Para você tornar esses dois arquivos iguais, a linha que vier em vermelho, você precisa remover, e a linha que vier em verde, você precisa adicionar.

Saída:

```yaml
diff --git a/.gitignore b/.gitignore
index c8d4fba..84b562f 100644
--- a/.gitignore
+++ b/.gitignore
@@ -2,7 +2,6 @@
 #
 # Get latest from https://github.com/github/gitignore/blob/main/Unity.gitignore
 #
-.utmp/
 /[Ll]ibrary/
 /[Tt]emp/
 /[Oo]bj/
@@ -25,9 +24,7 @@
 /[Aa]ssets/Plugins/Editor/JetBrains*

 # Visual Studio cache directory
-.vs/
 .vscode/
-.idea/

 # Gradle cache directory
 .gradle/
@@ -73,4 +70,4 @@ crashlytics-build.properties

 # Temporary auto-generated Android Assets
 /[Aa]ssets/[Ss]treamingAssets/aa.meta
-/[Aa]ssets/[Ss]treamingAssets/aa/*
+/[Aa]ssets/[Ss]treamingAssets/aa/*
\ No newline at end of file
```

Não dá pra ver as linhas vermelhas e verdes nessa saída, mas se você executar, vai conseguir ver.


Dá para usar o comando `git diff` com arquivos, branches, commits, [conflitos não resolvidos](#conflitos) e por aí vai.

Exemplo com commit (sugiro que tenha visto o tópico [log](#log)):
```bash
git log --oneline
git diff 0d97ee9 424a9b7 # isso é só um exemplo, com certeza a hash dos seus commits vão ser diferentes dessas
```

ou comparar as mudanças de um commit antigo com o diretório de trabalho atual (onde não se adicionou e nem commitou nada):
```bash
git diff HEAD~1
```

Exemplo com branches:
```bash
git diff main master # compara as diferenças das duas branches
```

ou até melhor:
```bash
git diff main origin/main # compara as diferenças entre a branch local com a branch do repositório
```

Exemplo com [conflitos](#conflitos) não resolvidos:
```bash
git diff # mostra conflitos não resolvidos, se tiver
```

Bom, acho que é isso que vai ser usado do `git diff`
<br>

##### <h4>Status</h4>

O comando `git status` mostra em que branch você está, mas a principal funcionalidade é que esse comando exibe o estado do diretório de trabalho (onde ainda não se adicionou, ou seja, não executou o comando `git add`) e da área stage (quando você executa o comando `git add`). Também dá para ver se tem algum conflito por [merge](#mesclar-merge) com esse comando.

###### <h5>Exemplo</h5>

```bash
git status
```

Saída

```yaml
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Vai ser algo similar a isso. Aqui está aparecendo o diretório de trabalho

---

#### <h3>Adicionar, comentar e subir para o repositório (git add; git commit; git push)</h3>

##### Introdução bem básica
Uma introdução bem basica: sempre que a gente clona um repositório ou ou inicia um, a gente começa a fazer modificações nos arquivos. Sempre que a gente faz alguma modificação em algum arquivo, a gente pode adicionar eles para a área de stage (ou só stage). Essa área é onde a gente pode fazer os comentários (commit) que vão aparecer no repositório. Depois disso tudo, é só subir para o repositório remoto.

##### Como é o procedimento

```bash
# adiciona apenas o arquivo específico
git add arquivo.txt

# faz um comentário com a mensagem 'adicionando o arquivo.txt ao remoto'.
git commit -m "adicionando o arquivo.txt ao remoto" # Você pode colocar qualquer mensagem aqui, mas é bom que seja intuitiva.

# sobe todos os commits para o remoto
git push
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

#### <h3>Atualizar Repositórios (fetch)</h3>

Aqui a gente vai entender um pouco do comando `git fetch`. Antes de ir pro comando, é preciso entender um pouco sobre o que são **remotes** e **branches**

##### <h4>O que é um remote?</h4>
Bom, um remote é basicamente um nome que aponta para o link de um repositório remoto. É como se fosse um tipo de atalho, que quando você digita o nome, é como se você estivesse digitando o link onde está o repositório. Sempre que você clona um repositório, o nome padrão do remote é "origin". Tente executar o comando abaixo para fixar melhor

```bash
git clone https://github.com/Artemiz-TK/Git-Introduction.git
cd Git-Introduction
git remote -v
```

Você vai ver algo assim
```yaml
origin https://github.com/Artemiz-TK/Git-Introduction.git (fetch)
origin https://github.com/Artemiz-TK/Git-Introduction.git (push)
```

o nome "origin" está apontando diretamente para o link. Você pode mudar esse nome, mas é o normal ter essa nomenclatura. Se quiser mudar o nome padrão, basta executar esse comando:

```bash
git remote rename origin repo
```
Agora, ao invés de usar o origin, você vai usar o nome repo ou o nome que você escolher.

Acho que deve ter ficado claro, agora é só tentar entender branches pra ir pro git fetch.

---

##### <h4>O que é uma branch?</h4>
Uma **branch** (ou "ramo") é uma **linha de desenvolvimento separada** dentro do projeto.

- Imagine que o projeto é um **livro**: uma branch é como um **rascunho alternativo** do livro, onde você pode testar novas ideias sem estragar a versão principal (`main`).

- A branch padrão geralmente se chama `main` ou `master` (depende do projeto)

**Exemplo de uso:**

- Se você cria uma branch chamada feature, está fazendo alterações isolada da branch principal (`main`)

- Quando terminar, você "mescla" ([merge](#mesclar-merge) — você vai ver esse termo mais pra frente) a feature de volta para a main

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
git checkout -b feature  # cria a branch e muda para ela
```

Objetivo: "Vou trabalhar em uma cópia segura da lista (feature), sem afetar a original (main)."

<br><br>

```bash
echo "Monster" >> lista-compras.txt # adiciona "Monster" na última linha do arquivo
echo "RedBull" >> lista-compras.txt # adiciona "RedBull" na última linha do arquivo
```

Agora é só fazer adicionar e commitar as mudanças na branch feature:
```bash
git add lista-compras.txt
git commit -m "Adiciona Monster e RedBull"
```

Depois disso, volte para a branch `main`

```bash
git checkout main # volta para a branch principal
```

Agora é só mesclar (merge)

```bash
git merge feature # combina as alterações da "feature" na "main"
```

---

##### <h3>git fetch</h3>

###### <h4>Pra quê serve</h4>

Ok, esse comando do git basicamente atualiza todo o projeto local, baixando todo o conteúdo do repositório remoto. Mas esse comando em si só faz isso, ele só atualiza.

- **Não altera arquivos locais**, apenas baixa as mudanças para uma **área temporária.**
- Útil para **verificar atualizações** antes de **integrá-las** ao código.

###### <h4>Como usar</h4>

```bash
git fetch <remote> <branch> # exemplo de uso: git fetch origin main
```

###### <h5>Exemplo</h5>

1. baixa as mudanças do remoto:
```bash
git fetch origin main
```

2. Compara a branch remota com sua branch local:
```bash
git diff main origin/main # mostra diferenças entre sua branch e o remoto
```

#### <h3>git merge (mesclar)</h3>

##### <h4>Pra quê serve</h4>
O comando `git merge` é usado para **combinar/mesclar duas [branches](#o-que-é-uma-branch)**, trazendo as alterações de uma para a outra.

##### <h4>Como usar</h4>

```bash
git merge <branch> # exemplo de uso: git merge master
```

##### <h5>Exemplo</h5>

1. Criando uma branch e atualizando a branch local
```bash
git checkout -b feature # cria a branch "feature" e muda para ela
# faz algumas alterações e edições...
git checkout main # troca para a branch main
git fetch origin main # baixa o conteúdo da branch main do remoto temporariamente
git merge origin/main # combina/mescla a branch atual (main) com a branch do remoto que foi baixada.
```

1. Resolva [conflitos](#conflitos) (se houver, mas vamos fingir que não tem) e finalize:
```bash
git add .
git commit -m "Merge da feature na main"
```

#### <h2>❗Conflitos❗</h2>

Bom, esse tópico é bem importante porque pode acontecer algumas vezes, e é bom que a maioria saiba como resolver.

Bom um conflito é basicamente a consequência de várias pessoas tentarem editar o mesmo conteúdo. Se uma pessoa tentar editar o código que outra pessoa está editando, pode ocorrer um conflito. A principal responsabilidade do comando `git merge` é combinar ramificações separadas e resolver quaisquer edições que tenham conflitos.

##### <h3>Exemplo</h3>

Imagine que você criou um repositório no github, depois clonou e agora já está no repositório local. Só que você deu permissão para mais uma pessoa, ela também clonou o repositório e está te ajudando com o desenvolvimento de algo.

A primeira coisa que vai ser feita pra esse exemplo é criar um arquivo, adicioná-lo a stage, depois fazer o commit

Então você faz o seguinte processo:
```bash
echo "Tarefa 1: Revisar o conteúdo com base nas novas exigências." > merge.txt
echo "Tarefa 2: Agendar a próxima reunião." >> merge.txt
git add merge.txt
git commit -m "Adicionando tarefas com base nas exigencias"
git push origin main
```

Mas a segunda pessoa também está editando e ela faz o seguinte processo:
```bash
echo "Tarefa 1: Revisar o conteúdo com foco na clareza dos objetivos." > merge.txt
echo "Tarefa 2: Agendar a próxima reunião." >> merge.txt
git add merge.txt
git commit -m "Adicionando tarefas com foco na clareza"
git push origin main
```

E que acontece? O push é rejeitado. O Git bloqueia o push porque o histórico da sua branch local está desatualizado em relação ao remoto. Uma mensagem similar a mensagem a seguir vai aparecer:
```yaml
! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/exemplo/projeto.git'
```

O link é só para deixar mais didático

A outra pessoa tem que atualizar o repositório local:
```bash
git fetch origin # aqui vai atualizar todos as branches
git merge origin/main
```
Pausa rápida: Eu não sei se vamos usar apenas a branch `main` para o projeto ou se vamos fazer mais de uma branch, então é melhor usar o comando `git fetch origin`

Depois que o repositório local tiver sido atualizado e mesclado, o arquivo que ambas as pessoas estavam editando vai estar assim:
```yaml
<<<<<<< HEAD
Tarefa 1: Revisar o conteúdo com foco na clareza dos objetivos.
=======
Tarefa 1: Revisar o conteúdo com base nas novas exigências.
>>>>>>> origin/main
Tarefa 2: Agendar a próxima reunião.
```

O conteúdo entre <<<<<<< HEAD e ======= é a sua versão local. O conteúdo entre ======= e >>>>>>> origin/main é a versão do repositório remoto. E precisa ter alteração para resolver o conflito. Tudo o que estiver abaixo dos símbolos >>>>>>> não precisa ser alterado.

**Resolução manual:** Resolução combinando as duas sugestões:

```yaml
Tarefa 1: Revisar o conteúdo considerando as novas exigências e priorizando a clareza dos objetivos.
Tarefa 2: Agendar a próxima reunião.
```

Agora é só adicionar, commitar e subir para o repositório:

```bash
git add merge.txt
git commit -m "Resolucao do conflito na tarefa 1 combinando as duas sugestoes"
git push origin main
```

Conflito resolvido!

Sim, cê tem que tirar aqueles símbolos e escolher algo para colocar no lugar. Isso é um arquivo de texto, o que é bem simples de corrigir esses conflitos, mas isso poderia ser um código C-Sharp ou algum outro tipo de arquivo.

O importante para saber é que dá para resolver conflitos de várias formas.

- Ficar só com uma das versões (descartar a outra)
- Combinar as duas sugestões
- Escrever algo completamente diferente
- Remover tudo se quiser (não recomendado na prática, mas é possível)

Então, **não precisa combinar se não quiser** — o importante é que o arquivo **fique sem as marcações de conflito** (<<<<<<<, =======, >>>>>>>) e o Git entenda que você **resolveu o conflito.**

Sobre o Git bloquear o push porque o repositório foi atualizado, é como se o git dissesse: "Ei! Tem coisa nova lá no remoto que você ainda não viu. Você precisa atualizar seu repositório local primeiro, pra evitar sobrescrever sem querer as mudanças dos outros"

Isso é uma proteção contra perda de dados. Por isso o push é rejeitado até você fazer [pull](#git-pull), resolver conflitos se tiver, e só então pode empurrar (push) de novo.

Então é sempre necessário ficar atualizando e combinando o repositório.

#### <h3>git rebase<h3>

##### <h4>Pra que serve</h4>

- Reorganiza o histórico de commits, colocando as alterações locais em cima de uma base atualizada (por isso `rebase`).
- Mantém o histórico linear e limpo (evita commits de merge).

##### <h4>Como usar</h4>

```bash
git rebase <branch>  # exemplo: git rebase main
```

###### <h5>Exemplo</h5>

1. Crie uma branch e vá para ela:
```bash
git checkout -b base
# faça algumas mudanças e commits...
```

2. Atualize a branch principal:
```bash
git checkout main
git fetch origin main
git merge origin/main
```

3. Reaplique seus commits da branch que você está atualmente em cima da main atualizada:
```bash
git checkout base
git rebase main
```

4. [Resolva conflitos](#conflitos) — se houver — (um por um) e continue:
```bash
git add .
git rebase --continue
```

5. Envie as alterações (se necessário):
```bash
git push origin base --force  # Use a flag "--force" com cuidado
```

> [!NOTE]
> <h3>Como funciona</h3>
>
> - **Reescreve o histórico:** desconecta seus commits locais, aplica as atualizações da base e reaplica seus commits.
>
> - **Não é muito bom usar em branches públicas** (ex: `main`), até porque isso altera o histórico compartilhado.

#### <h3>git pull</h3>

Bom, agora que você já sabe como usar os comandos `git fetch`, `git merge`, `git rebase` e dentre outros, você já deve ser capaz de entender esse comando também. Finalmente já podemos tentar entender o comando `git pull`

##### <h4>Pra que serve</h4>

- Atualiza sua branch local com as mudanças do remoto.

- Combina git fetch + git merge (ou git rebase, se configurado). Por isso a introdução deles antes desse comando, pra você ter mais facilidade com esse comando.

##### <h4>Como usar</h4>

```bash
git pull <remote> <branch> # exemplo: git pull origin main
```

###### <h5>Exemplo</h5>

- Exemplo com merge (padrão):
```bash
git pull origin main # equivale a git fetch + git merge origin/main
```

- Exemplo com rebase:
```bash
git pull --rebase origin main # equivale a git fetch + git rebase origin/main
```

###### <h4>Como finciona</h4>

- Passo 1: Baixa as atualizações do remoto (git fetch).
- Passo 2: Mescla (git merge) ou reaplica (git rebase) as mudanças na branch local.