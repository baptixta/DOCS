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
```
git merge nome-branch
```

- Pega apenas um commit de outra Branch
```
git cherry pick nome-hash
```

### Desfazendo coisas
- Remover arquivos e diretórios que estão "untracked"
```
git clean -fd
```

- Retornar o arquivo pra antes da mudança
```
git checkout nome-arquivo
```

- Retornar o arquivo pra um commit específico
```
git checkout nome-hash nome-arquivo
```

- Retornar o arquivo pra um commit específico e criar um commit registrando essa alteração
```
git revert HEAD~(hash)
```

- Retornar o arquivo quando já foi dado "git add"
```
git reset HEAD nome-arquivo
```

- Retornar o arquivo quando já foi "commitado"
```
git reset --soft --mixed --hard
ex: git reset --soft b4a885d321a(hash)
```


## Redes

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
