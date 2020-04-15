# DOCS
> Documentações feitas por mim (pra ajudar a galera).

## Conteúdo
1. [Git](#git)
2. [Level Design (Games)](#level-design)
3. [Redes](#redes)

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


## Level Design

### Introdução

- criar oportunidades/desafios para usar as mecânicas do jogo
- o level tem que fazer sentido com o contexto do jogo

### Pesquisa, referências e blocagem

- toda referência vale
- referências do mercado de jogos
- analisar soluções interessantes de outros jogos para o seu
- validar a ideia antes de se comprometer
- blocagem -> dividir em blocos e ver se faz sentido as coisas
- blocagem -> testar e validar antes de produzir

### Level design: Linear

- levar o jogador de um ponto A a um ponto B
- nível de qualidade alto (por conta do jogador só ver o caminho sem variações)
- gráfico de Jesse Shell (relaxamentos e climax variados durante a fase)

### Level design: Grid

- forma matemática/precisa para construir levels
- usado em jogos de estratégia (ex: civilization, kingdom rush)
- a fase é toda segmentada (como um grid)
- o que se deve fazer ou não é muito explícito

### Level design: Teia

- usado nos jogos estilo metroidvania (ex: hollow knight, castlevania)
- mais liberdade pro jogador pelo mapa
- personaliza a gameplay do jogador (direita ou esquerda)
- cada fase precisa ser interessante (por conta da liberdade de escolha)

### Level design: Pontos no espaço

- jogos que normalmente tem uma área central/hub com vários níveis colocados
- jogador escolhe pra qual fase vai
- jogador pode ver todas as opções que tem ao mesmo tempo (fases disponíveis ou não, etc)
- ex: Destiny 2

### Level design: Espaços divididos

- forma interessante de trabalhar com jogos de sandbox (mundo aberto)
- jogos que trabalham com áreas em escala (ex: GTA, Red Dead Redemption)
- consegue transitar pelas áreas sem loadings
- passa credibilidade (como num mundo real/experiência imersiva)

### Marcos

- referência dentro do espaço onde estamos (ex: banespa em sp)
- ferramenta de navegação
- área de destaque
- ajuda o jogador a se posicionar no espaço

- funções: facilitar a localização dos jogadores
- funções: fornecer objetivos do que pode ser feito
- funções: informações da partida

### Tornando cada nível único

- tenha em mente o nível antes de começar

- paleta de design
[o level design pega todos os "ingredientes" (game design, variações, jogador),
e ele mistura. sempre procurando a forma mais interessante pros jogadores utilizarem
o que foi criado]

- ex: poder ser stealth ou inconsequente no mesmo jogo
- conheça as habilidades adquiridas (mostrando aos poucos sem sobrecarregar o jogador)
- fazer com que o jogador se lembre do nível depois de ter terminado o jogo (ex: warp zones do super meat boy)

### Iteração

- usar o tempo de produção, pra gradativamente ir melhorando os níveis
- nessa fase o ideal é gastar tempo jogando/testando o jogo
- processo demorado
- testar todas as possibilidades criadas
- usar outras pessoas para testar o nível (receber feedbacks)


## Redes

### Protocolo

Série de regras que fazem com que as comunicações em uma rede
sejam mais eficientes.

### Arquitetura em camadas (Comunicação)

- LAN: Local Area Network
- DAN: Departamental Area Network
- MAN: Metropolitan Area Network
- WAN: Wide Area Network
- GAN: Global Area Network

### Modelo OSI (Open System Interconnection)

> Tem 7 Níveis/Camadas Funcionais

#### 7. Aplicação
- Tudo que aparece na tela do seu PC

#### 6. Apresentação
- Ajuda a camada de APLICAÇÃO a mostrar as informações
EX: ZIP, APLICAÇÕES DE SEGURANÇA (SSL).

#### 5. Sessão
- Camada que faz a interface entre seu PC e a rede de TRANSPORTE DE DADOS.
(Sincronismo entre o cliente e o servidor - Controle de Diálogo)

#### 4. Transporte
- Comunicação fim-a-fim.
PORTA - Onde cada PROTOCOLO tem sua porta específica.
EX: PORTA 80 - PROTOCOLO HTTP

#### 3. Rede
- Endereçamento Lógico -> Endereço IP (Internet Protocol)

#### 2. Enlace
- Endereçamento Físico -> Endereço MAC

#### 1. Física
- Especificar tipo de fibra ótica/fio/onda eletromagnética.

### Modelo TCP/IP (Transmission Control Protocol | Internet Protocol)

- 4. Aplicação (7,6,5 do modelo OSI)
- 3. Transporte
- 2. Internet | Rede
- 1. Acesso a rede (2,1 do modelo OSI)

### O protocolo UDP (Seja o que Deus quiser)

O UDP é um protocolo voltado para a não conexão. Simplificando, quando uma máquina A envia pacotes para uma máquina B, o fluxo é unidirecional. Na verdade, a transmissão de dados é feita sem prevenir o destinatário (a máquina B) que, por sua vez, recebe os dados sem avisar ao transmissor (máquina A). Isso se deve ao fato de o encapsulamento dos dados enviados pelo protocolo UDP não permitir transmitir informações sobre o emissor. Portanto, o destinatário não conhece o emissor dos dados, apenas seu IP.

### O protocolo TCP (Confiável)

Ao contrário do UDP, o TCP é voltado para a conexão. Quando a máquina A envia dados para a máquina B, a máquina B é notificada da chegada dos dados e confirma a boa recepção dos mesmos. Aqui, intervém o controle CRC dos dados, baseado em uma equação matemática para verificar a integridade dos dados transmitidos. Assim, se os dados recebidos estiverem corrompidos, o TCP permite que os destinatários peçam ao emissor que reenvie-os.

### Principais dispositivos de Rede

- Repetidor{HUB} (Repeater) - L1 - Camada Física
- Ponte(Bridge) - L2 - Camada de Enlace (Endereçamento MAC)
- Switch - L2 - Camada de Enlace (Endereçamento MAC)
- Roteador (Router) - L3 (Endereçamento Lógico - IP)
- Gateway - L7 (Interconexão entre tecnologias)
