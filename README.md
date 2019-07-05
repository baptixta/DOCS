# DOCS
> Documentações feitas por mim(pra ajudar a galera).

## Conteúdo
1. [Git](#git)
2. [Redes](#redes)

## Git
- Registrar user
```
git config --global user.name "Nome"
```

- Registrar e-mail
```
git config --global user.email "Email"
```

- Configurar editor
```
git config --global core.editor "(nome do editor no cmd)"
```

- "Pegar" informação específica
```
git config (user.name | user.email | core.editor)
```

- "Pegar" todas as infos
```
git config --list
```

### Repositório Local
- Inicializar repositório
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
