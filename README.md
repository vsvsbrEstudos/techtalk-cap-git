#Introdução

Isso não é um tutorial básico sobre git. Tento atacar as principais dúvidas que me surgiram quando comecei a utilizar o Git: fluxo do git, branch e merge.

Esses três assuntos eu tento demonstrar com foco no processo de desenvolvimento, não apenas no poder da ferramenta.

#Fluxo Git
Um repositório git não depende de um repositório remoto. Todo o controle das alterações está na sua mão, localmente. Então a primeira dica é ter o fluxo de um repositório git na mente: 

![Ciclo de vida dos arquivos](img/git-status-lifecycle.png)

"staging area" or "index"

![Áreas de armazenamento](img/git-working_directory-stage_area-repository.png)

Fluxo com o repositório remoto

![Fluxo com o repositório remoto](img/git-index_structure.png)

#Branch

Criar alteranando `git checkout -b nome_branch`

Para ver branches remotas: `git branch -r`

Baixar uma branch remota e ligar com uma branch local: `git checkout -t origin/nome_branch` ou `git branch -t nome_branch origin/nome_branch`

Apagar remotas: `git push origin :nome_branch`


##Diff

Para mostrar a diferença entre alterações e commits: `git diff`

Diferença entre staged e HEAD: `git diff --cached`

Mostrar a diferença entre dois branches `git diff nome_b1 nome_b2`

##Stash

Como o próprio nome diz, esconde. Esconde uma alteração, retirando-a do working directory e/ou index e colocando numa área com um label para acessá-la de novo.

Útil quando se quer salvar uma alteração urgente e voltar o código ao original antes de uma correção de emergência.

- `git stash` - esconde
- `git stash list` - mostra áreas escondidas
- `git stash pop` - recupera a última área
- `git stash apply [stash name]` - volta área específica
- `git stash drop` --> apaga uma área
- `git stash clear` --> apaga todos os estados.

#Merge

O merge, cria um commit de merge, onde pega as alterações feitas em um branch e une com outro, seja local ou remoto.

O rabase, realinha os commits no momento que estiver unindo dois branches.

Para branches remotos o pull faz merge automático, utiliza-se a opção `--rabase` para fazer rabase ao invés de merge.

É comum executar vários comandos para buscar as alterações de uma branch remota.

```
#!bash
git checkout master
git pull origin master
git checkout b1
git rebase master
```

Mas, às vezes, tudo que se quer é atualizar a branch em manutenção, para continuar um trabalho, então pode-se fazer: `git pull --rebase origin master` direto na branch.

Se houver conflitos, após arrumá-los: `git rebase --continue`


## Conflitos
Não tem jeito, tem que resolver os conflitos manualmente. Mas quais?

`git diff --name-only --diff-filter=U`




#Processo de desenvolvimento

![Git-flow](img/git-flow-overview.jpg)

![Git-workflow](img/git-workflow.png)


#Veja também
- [GitHub pages](https://pages.github.com/) - interessante para fazer blogs estáticos.
- Geradores estáticos
    - [Pelican](http://pelican.readthedocs.org/) - em python
    - [Jekyll](http://jekyllrb.com/) - em ruby
    - [outros](https://www.staticgen.com/) - site com vários que estão no github e quantas estrelas
- [Documento de introdução ao Git do Paulistano](https://goo.gl/xYNC9m)
- [GitHowTo](http://githowto.com/) - encontrado depois da apresentação - _que pena!_
- Criar Aliases para encurtar comandos do git
    - http://githowto.com/aliases

#Referências
- Documentação do Git
    - https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
    - https://git-scm.com/about/staging-area
- Tutoriais
    - https://www.sonassi.com/knowledge-base/our-magento-git-guide-and-work-flow/
- Livro - Controlando versões com Git e GitHub - Alexandre Aquiles e Rodrigo Ferreira - Casa do Código
- Curso alura de git
    - Parte 4 - Branches
    - Parte 7 - Git stash
