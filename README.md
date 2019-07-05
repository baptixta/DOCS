# DOCS
> Documentações feitas por mim(pra ajudar a galera).

## Conteúdo
1. [Git](#git)
2. [Redes](#redes)

## Git
- REGISTRAR USER
```
git config --global user.name "Nome"
```

- REGISTRAR EMAIL
```
git config --global user.email "Email"
```

- CONFIGURAR EDITOR
```
git config --global core.editor "(nome do editor no cmd)"
```

- "PEGAR" INFORMAÇÃO ESPECÍFICA
```
git config (user.name | user.email | core.editor)
```

- "PEGAR" TODAS AS INFOS
```
git config --list
```

### REPOSITÓRIO LOCAL
- INICIALIZAR REPOSITÓRIO
```
git init
```

### CICLO DE VIDA DOS STATUS DOS ARQUIVOS
```
git status
git add .
git git commit -m ""
git pull
git push origin master
```

### BRANCHES (RAMIFICAÇÕES)
- CRIAR BRANCH
```
git branch nome-branch
obs: apenas cria, não faz checkout pra ela
```

- CRIAR BRANCH E IR PRA ELA
```
git branch -b nome-branch
```

- CRIAR BRANCH A PARTIR DE OUTRA
```
git checkout -b nome-branch
```

- TROCAR DE BRANCH
```
git checkout nome-branch
```

- APAGAR BRANCH
```
git branch -d nome-branch
```

- JUNTAR BRANCHES
git merge nome-branch
```
git branch -d nome-branch
```

- PEGA APENAS UM COMMIT DE OUTRA BRANCH
```
git cherry pick nome-hash
```

### DESFAZENDO COISAS


## Redes

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
