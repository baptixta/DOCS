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
