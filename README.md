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

### Comandos mais usados
```
git status
git add .
git git commit -m ""
git pull
git push origin master
```

### Branches (Ramificações)
- Criar Branch
```
git branch nome-branch
obs: apenas cria, não faz checkout pra ela
```

- Criar Branch e ir pra ela
```
git branch -b nome-branch
```

- Criar Branch a partir de outra
```
git checkout -b nome-branch
```

- Trocar de Branch
```
git checkout nome-branch
```

- Apagar Branch
```
git branch -d nome-branch
```

- Juntar Branches
git merge nome-branch
```
git branch -d nome-branch
```

- Pega apenas um commit de outra Branch
```
git cherry pick nome-hash
```

### Desfazendo coisas


## Redes

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
