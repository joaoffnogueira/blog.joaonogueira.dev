---
title: Anotações sobre Redes de Computadores
author: João F. F. Nogueira
date: 2021-02-05 08:00:00 -0300
categories: [Português, Estudos]
tags: [network]
toc: true
---

# 1 Introdução a redes de computadores

Uma rede, network ou simplesmente net é conhecida pelo acrônimo (sigla) em inglês DCN – Data Communication Network.

Finalidade das redes de computadores:

1. Interoperabilidade;

2. Interconectividade;

3. Serviços de mensagem;

4. Serviços de telefonia;

5. Acesso remoto à informação;

6. Compartilhamento de recursos;

7. Distribuição da carga de trabalho;

8. Reforçam a confiabilidade e segurança dos sistemas, uma vez que permitem a estruturação de sistemas com tolerância a falhas;

9. Gerenciamento ou gestão de recursos, através da sua capilaridade e da sua abrangência.

Classificação das redes em função da sua abrangência geográfica:

* PAN, do Inglês Personal Area Network ou rede de área pessoal (<=10m);

* LAN, de Local Area Network ou rede de área local, ou simplesmente Rede Local;

* MAN, de Metropolitan Area Network ou rede de área metropolitana ;

* WAN, de Wide Area Network ou rede de grande área;

* E a Internet, isto é, a interconexão de redes, a rede das redes, ou rede de alcance mundial.

Classificação das redes em função da conectividade:

Redes lógicas, na qual a configuração é definida por um arranjo de software, ou redes físicas, que resultam da combinação de meios de comunicação e hardware específico em arranjos físicos e com distribuição geográfica conhecida. Uma rede também pode ser composta pelos combinação destes dois tipos. O melhor exemplo para isto é a famosa Computação na Nuvem, ou seja, o Cloud Computing.

Classificação das redes em função da forma de gerenciamento:

Públicas ou privadas

Classificação das redes quanto à arquitetura:

Cliente/servidor, ponto a ponto ou híbrida.

## Tecnologias

Ethernet: É típica de topologia do tipo Estrela, e faz uso de prevenção e detecção de colisões com o CSMA/CD. As interfaces (cartões ou placas) de rede física (MAC) possuem endereços de 48 bits, ou seja, é possível designar até 248 endereços para os dispositivos ou hosts. A ethernet usa como padrões de mídia o 10 Base-T, com cabos CAT-5 e conector RJ-45. Com estes padrões consegue atingir distâncias de até 100 metros mantendo uma velocidade de comunicação de 10 Mbps (dez megabits por segundo). Com o passar do tempo e a evolução tecnológica, a ethernet também foi evoluindo, passando a apresentar novos padrões, tais como:

* FAST ETHERNET, padrão IEEE 802.2, mídia 100 Base-T, cabo CAT-5 e conector RJ-45, que atinge até 100 Mbps em distâncias de até 100m;

* FAST ETHERNET em fibra ótica, mídia 100 Base-Fx, que atinge até 100 Mbps em até 2.000 m (ou 2 Km, dois quilômetros);

* GIGABIT ETHERNET, padrão IEEE 802.3ab, cabos CAT-5, CAT-5e e CAT-6, com velocidades até 1 Gbps (Gigabits por segundo);

* GIGABIT ETHERNET em fibra óptica, padrão IEEE 802.ah;

Token Ring: utilizada principalmente em redes de topologia ANEL em ambientes de altíssimo volume de tráfego de dados, exigência de alta disponibilidade e baixíssima taxa de erros. Geralmente é empregada para a comunicação de computadores de grande porte, os Mainframes, dispositivos de armazenamento de grande capacidade, os Storages ou dispositivos voltados para a cópia de segurança dos dados destes sistemas, o Backup. Esta rede é eficiente para ambientes que trocam grandes volumes de dados pois evita a colisão – a tentativa de comunicação simultânea entre mais de dois dispositivos. Isto porque existe um TOKEN, isto é, um sinalizador que fica de posse de apenas um host a cada momento, e somente o host que tiver a posse do token poderá transmitir seus dados através da rede.

WiFi® – Wireless Fidelity, marca registrada da WiFi Alliance. É definida pelos padrões IEEE 802.11a para a velocidade de até 2 Mbps, IEEE 802.11b para 11 Mbps, IEEE 802.11g para 54 Mbps e IEEE 802.11n de 150 até 600 Mbps.

O Bluetooth é outra tecnologia de rede sem fio, criada pela ERICSSON na década de 90, e transformada no padrão IEEE 802.15.x, é uma tecnologia voltada para a comunicação à curta distância, basicamente para as redes pessoais (PAN ou WPAN), e também associada à mobilidade e à IOT.

Mobile é composta de outras tecnologias que permitem o tráfego de dados, denominadas 2G, 3G, 4G, etc.

## Topologia (ou arquitetura)

Topologia de uma rede de computadores é a forma através da qual os computadores e demais componentes ou dispositivos da rede estão organizados, ligados ou conectados entre si. Esta ligação pode ocorrer de forma física, através dos meios de comunicação e transmissão, ou lógica, configurada por software. A topologia física expressa a aparência ou layout da rede, e a lógica representa o fluxo dos dados na rede.

* Ponto a ponto: um exemplo é a VPN;

* Barramento (BUS): todos os hosts compartilham um único meio para a comunicação. Este tipo de rede é fácil de se construir, pois o meio é único – um único cabo coaxial ou fibra ótica percorrendo toda a extensão da rede. Para evitar problemas de transmissão este tipo de rede usa um controle de acesso ao meio e de detecção de colisão do tipo CSMA/CD - Carrier Sense Multiple Access with Collision Detection ou Bus Master, ou seja, quando um host vai iniciar uma transmissão, primeiro verifica se o meio está livre.

* Estrela (Star): todos os hosts são conectados a um ponto ou nó central, normalmente um dispositivo de rede do tipo Hub ou Switch , mas também podem ser do tipo Repetidor, Bridge, Gateway, Router, etc. De fato existe uma conexão ponto a ponto entre os hosts e este nó central, pelo qual passa todo o tráfego da rede. Por isso, em caso de falha de um host os outros não são afetados, porém se o equipamento do nó central falhar, toda a rede fica inoperante.

* Anel (Ring): cada host é conectado a dois outros, seu antecessor e seu sucessor, ou o anterior e o seguinte. Desta forma há uma conexão ponto-aponto entre cada um destes dois hosts, e o tráfego da rede passa por cada um deles. Por isso mesmo, em caso de falha de um host toda a rede falha. Para evitar este tipo de falha normalmente há um anel backup no qual a informação circula em sentido contrário ao do principal.

* Mesh (Malha): Nas redes do tipo malha, cada host é conectado a todos os outros hosts (Full Mesh) ou pelo menos aos mais próximos a ele (Partially Mesh), através de uma conexão ponto a ponto entre cada host.

* Árvore (Tree): Também chamada de Hierárquica ou de Hierarquia, este tipo de rede é organizada em camadas (layers), resultado de uma combinação das redes do tipo Barramento e Estrela. Hosts vizinhos e dispositivos em nós de transição entre os níveis utilizam uma conexão ponto a ponto, resultando que, em caso de falha dos nós centrais toda a rede falha. Esta é uma configuração típica das Redes Locais.

* Daisy Chain: cada host é conectado a dois outros hosts, exceto os dois da extremidade da rede. É o resultado de uma combinação de redes do tipo barramento e anel, também fazendo uso de uma conexão ponto-a-ponto entre hosts vizinhos.

* Híbrida.

Ativos de rede: são os equipamentos ou dispositivos que, em síntese, fazem a rede funcionar.

* Concentrador ou Reforçador (Hub): É o dispositivo que centraliza a conexão de diversos hosts em um mesmo segmento da rede, ligando-os e formando uma rede de topologia estrela.

* Repetidor: É o equipamento que conecta dois segmentos de rede recuperando e reforçando ou amplificando os sinais da transmissão.

* Bridge: É um ativo de rede que conecta dois segmentos de rede, tornando-os uma única rede, ou duas redes distintas entre si.

* Comutador (Switch): É o equipamento mais comum em redes locais, pois conecta hosts de diferentes segmentos de rede. Diferentemente do HUB, o Switch retransmite os pacotes de dados apenas para o host ou nó de destino, fechando um circuito entre este e o host ou nó de origem dos dados e emulando uma rede ponto a ponto entre ambos. Também permite as transmissões simultâneas ("conversas em paralelo") e, devido à segregação dos circuitos comutados, diminui o número de colisões no segmento de rede.

* Roteador (Router): é o dispositivo que conecta - ou separa - redes distintas, evitando que pacotes de uma trafeguem de forma indiscriminada para outra, e encaminhando os pacotes destinados a hosts da outra rede. Um router é capaz de traçar a melhor rota – ou caminho - para um determinado pacote de dados, identificar o estado dos segmentos de rede quando à disponibilidade ou tráfego e ainda impor determinadas regras de segurança.

* Gateway: É o dispositivo que conecta redes com tecnologias distintas entre si, tal como as Bridges, porém com capacidade de realizar a tradução de protocolos e a conversão de dados. Proxy, Firewall e IDS (Intrusion Detection System).

Meios de transmissão: são os canais, as vias ou condutores pelos quais os computadores e os dispositivos de rede enviam e recebem os dados. Eles são capazes de transportar sinais elétricos e eletromagnéticos (ondas de rádio) e a luz, que por sua vez carregam as informações em sua menor unidade, o BIT.

* Cabos elétricos;

* Cabos óticos;

* Sinais luminosos ou ondas eletromagnéticas.

# 2 Protocolos de comunicação

 Protocolos são as regras aplicadas à comunicação de dados nas redes de computadores – às informações e aos dispositivos da rede – para possibilitar a compatibilidade entre diferentes tipos de equipamentos, redes e formatos de informação, e principalmente garantir que a informação trafegue entre origem e destino de modo efetivo, no menor tempo possível e mantendo suas qualidades.

## O modelo ISO/OSI

O modelo ISO/OSI é um padrão da ISO - International Standard Organization para a interconexão de sistemas abertos (Open Systems Interconnection). É formado por sete camadas ou níveis de tratamento da informação:

1 - Física: A camada física possibilita a ligação física de duas estações diferentes. É esta camada que trata da interação entre o hardware e os mecanismos de sinalização.

2 - Enlace ou link de dados: É a que faz a conversão do fluxo de dados recebido da camada de rede para os sinais a serem transmitidos pela camada 1, interagindo com o hardware. Do lado do receptor da transmissão a camada de enlace de dados recebe os dados de hardware, transformados de sinais elétricos em BITs pela camada 1, e os agrupa em um formato de QUADRO reconhecível, disponibilizando este quadro para a camada de rede. É dividida em: - Controle lógico do link: Cuida dos protocolos, controle de fluxo e do controle de erros. - Controle de acesso ao meio (MAC - Media Access Control): Realiza o controle dos meios de comunicação. Contém o endereço físico da mídia (“placa” ou “cartão” de rede) denominado MAC Address.

3 - Rede: É a camada ou nível que:

* Cuida da atribuição de endereços aos hosts. É nesta camada que o endereço lógico é configurado, reconhecido e tratado;

* Trata da definição do roteamento, isto é, o caminho pelo qual os pacotes de informação serão enviados até o destino;

* Faz o controle da transmissão, adequando o fluxo de dados às características do meio de transmissão (como a velocidade, por exemplo);

* Realiza o tratamento de erros de transmissão, fazendo a detecção e providenciando a correção dos erros; - Mantém as tabelas de roteamento ou rotas estáticas;

* Controla a formação dos pacotes de dados de entrada e saída e faz o encaminhamento de acordo com a qualidade e as restrições do serviço;

* Possibilita a conexão entre redes diferentes;

* Busca a entrega de pacotes para o destino com o menor esforço;

* Fornece os mecanismos para a comunicação através de conexões ou a comunicação sem conexão.

Além disso, provê os seguintes serviços e recursos:

* Gerenciamento da qualidade dos serviços (QoS – Quality of Service);

* Balanceamento de carga e gerenciamento de link de dados;

* Segurança;

* Interação entre diferentes protocolos e a comunicação entre redes diferentes;

* Configuração de uma rede lógica sobre a rede física.

* Utilização de VPN - Virtual Privative Network ou Rede Privativa Virtual nível L3

* Túneis para a conexão dedicada ponto-a-ponto.

É na camada de rede que atuam os roteadores, tratando do encaminhamento (ou roteamento) dos pacotes e da distribuição da transmissão, que pode ser: - Unicast: destinado a um único host; - Multicast: destinado a um grupo de hosts; - Broadcast: destinado a todos os hosts da rede; - Anycast: destinado aos hosts mais próximos.

4 - Transporte: É a camada que responde pela entrega dos pacotes de dados aos hosts, cuidando da comunicação de ponta a ponta, entre host que podem nem mesmo pertencer à mesma rede. Suas principais atribuições são:

* Divide os dados fornecidos pela camada de aplicação em unidades menores, chamadas segmentos, numerando-os e mantendo o registro de cada segmento.

* Assegura que os dados devem ser recebidos na mesma sequência em que foram enviados. - Além dos endereços de rede são associados aos segmentos um número de porta.

* Por sua vez estas portas estão associadas a determinados tipos de serviço e às aplicações que os utilizam.

* As portas também são numeradas e tem usos definidos.

5 - Sessão: Nesta camada são estabelecidas as sessões de comunicação entre os hosts. Sessões são definidas por intervalos de tempo nos quais um serviço é fornecido ou uma atividade é realizada. Para iniciar uma sessão é necessário realizar uma autenticação, isto é, identificar quem está solicitando o serviço ou a atividade. Esta camada também cuida do reconhecimento de nomes e do registro das atividades (log) na rede.

6 - Apresentação: Nesta camada é tratado o formato dos dados a serem apresentados pelos aplicativos. Pode-se considerá-la como o serviço tradutor da rede. Entre outros serviços, fornece a conversão de códigos de caracteres, conversão, compactação / descompactação e criptografia de dados;

7 - Aplicação: Esta camada é a que interage com os programas de aplicação ou aplicativos do usuário para que estes possam utilizar os serviços da rede.

## Protocolo TCP/IP

Transmission Control Protocol/Internet Protocol suite é um conjunto de protocolos utilizado pela Internet. Por isso também é chamado de Internet Model.

De modo análogo ao modelo ISO/OSI, é apresentado em camadas, porém, ao invés das sete camadas do modelo OSI/ISO, contém quatro camadas interdependentes, a saber:

* Interface de rede: especifica o tratamento dos bits, isto é, como a informação vai ser repassada para o meio físico por meio das interfaces eletrônicas. Nesta camada estão as tecnologias voltadas para o hardware, como o Ethernet e Token Ring.

* Inter rede ou internet: é a que contempla o IP – Internet Protocol, que trata do empacotamento dos dados (IP Datagrams) e de seu encaminhamento, isto é, do roteamento do pacote pela rede. A face mais característica é o endereço IP, um conjunto de números que representa o endereço de cada host para a rede.

* Transporte: é a responsável pelo nível de serviço e pelo controle da conexão que provê o transporte das informações pelas rotas da rede. Nela estão definidos os protocolos TCP (Transmission Control Protocol) e UDP(User Datagram Protocol, mais simples e sem garantia de entrega).

* Aplicação: cuida dos protocolos de aplicação e de como a aplicação realiza a comunicação com os serviços da camada de transporte. Nesta camada estão os protocolos como FTP, HTTP, SMTP e DHCP.

O endereço IP: É um conjunto de quatro grupos de números binários de oito bits (bytes ou octetos), podendo variar de 0 (20) a 255 (28 – 1). É o identificador único de um host (ou interface) em uma rede específica. Os grupos de números são representados por dígitos decimais separados por pontos.

O processo de comunicação por meio do TCP/IP:

1\. A comunicação pela rede por meio do TCP/IP inicia-se com o empacotamento dos dados.

2\. Os pacotes são numerados sequencialmente para manter a ordem e identificação.

3\. Os pacotes numerados são colocados no meio de transmissão pelos protocolos da suíte, e então enviados individualmente para o IP do destinatário. Cada pacote segue pela melhor rota possível no momento, até o endereço do host destino.

4\. Para cada pacote recebido o destinatário informa o seu recebimento ao remetente. Caso algum pacote não seja recebido em um determinado tempo, é enviado novamente.

5\. Os pacotes recebidos são então colocados na ordem da origem e a informação completa é reconstruída.

# 3 Internetworking

A conexão ou roteamento entre duas redes é chamada de internetworking ou conexão inter-redes, e é tratada na camada 2 do protocolo TCP/IP, principalmente pelo protocolo IP.

Os protocolos de roteamento utilizados na rede interna de da organização são chamados protocolos de gateway interior ou Interior Gateway Protocol (IGP), como por exemplo os protocolos RIP e OSPF. Roteamento entre diferentes organizações requerem o Exterior Gateway Protocol (EGP), e há apenas um EGP para cada rede, normalmente o Border Gateway Protocol (BGP).

## Internetworking no TCP/IP e no ISO/OSI

No modelo TCP/IP a camada de Rede combina as camadas de enlace de dados (link) e a física do modelo ISO/OSI (camadas 1 e 2) para que haja independência da infraestrutura de rede. A camada superior – camada 2 ou inter-rede, equivalente à camada de rede (camada 3) do modelo ISO/OSI, trata do roteamento ou encaminhamento de pacotes entre os nós das redes.

   ![OSI-TCP/IP](/posts/2021-02-05-1.png){: width="100" height="100" }

No modelo TCP/IP as camadas de Aplicação, Apresentação e Sessão - camadas 7, 6 e 5 do modelo ISO/OSI - são combinadas e formam a camada de aplicação. Nesta camada estão presentes os seguintes protocolos ou serviços, entre outros:

* DNS - Domain Name Service ou serviço de nomes do domínio;

* SMTP – Simple Mail Transfer Protocol ou protocolo simples de transferência de correio

* FTP – File Transfer Protocol ou protocolo de transferência de arquivo; -

* Ping – serviço / programa de teste de tráfego entre hosts e redes que funciona por meio de um “eco” de pacotes;

* HTTP – Hyper Text Transfer Protocol ou protocolo de transferência de hipertexto;

* NFS – Network File System ou sistema de arquivo em rede;

* POP – Post Office Protocol ou protocolo de correio;

* Telnet – Terminal Link over Network ou Terminal Virtual da Rede.

As camadas de Enlace e Física – camadas 2 e 1 do modelo ISO/OSI são unificadas na camada de Rede – camada 1 do TCP/IP. Como já visto, isto se deve à necessidade de preservar, no TCP/IP, a independência da rede.

   ![Internetworking no TCP/IP e no ISO/OSI](/posts/2021-02-05-2.png){: width="100" height="100" }

Na camada 2 do TCP/IP – camada inter-redes, são definidos os protocolos responsáveis por tratar da comunicação entre as redes, a saber:

* IP – Internet Protocol ou protocolo internet, é o mais conhecido e mais importante protocolo desta camada, responsável, entre outras funcionalidades, pelo endereçamento dos hosts na Internet, que também chamamos endereço IP. O IP faz o encaminhamento dos pacotes entre as redes utilizando o endereço IP do host, a máscara de rede e o gateway padrão. Por exemplo: endereço do host 192.168.1.25, máscara de rede 255.255.255.0 e gateway padrão 192.168.1.1;

* ARP – Address Resolution Protocol, ou protocolo de resolução de endereço, busca o endereço físico da interface de rede que corresponde a um IP. Este endereço, também chamado MAC Address, é um número de 48 bits, geralmente representado em hexadecimal, como por exemplo: 94-eb-cd-26-5d-16. O ARP cria uma tabela em memória com a equivalência entre endereço físico e endereço IP. É possível acessar esta tabela com o comando ARP –a na linha de comando do Windows.

* RARP - Reverse Address Resolution Protocol ou Protocolo de Resolução Reversa de Endereços associa um endereço físico (MAC Address) conhecido à um endereço IP. É necessário haver um servidor ou serviço RARP na rede para responder às solicitações dos hosts, retornando o IP ligado ao MAC Address fornecido. Como o próprio nome diz, faz o trabalho reverso do ARP.

* ICMP - O Internet Control Message Protocol ou Protocolo Internet de Controle de Mensagem permite informar os erros ocorridos no processo de comunicação entre hosts. O protocolo IP não trata os erros, mas os informa às camadas subjacentes que podem tratar, registrar ou comunicar os erros. Os switches e os routers utilizam o ICMP para assinalar erros (delivery problem). Um exemplo do uso do ICMP é o comando ping, que faz uso de mensagens ICMP. O comando solicita um “eco” para um host destino. Se o host destino devolver o pacote enviado à origem, então pode ser alcançado pela comunicação.

* IGMP - Internet Group Management Protocol serve para controlar os membros de um grupo de multicast controlando a entrada e a saída dos hosts deste grupo. Desta forma o protocolo otimiza os recursos de uma rede, pois os roteadores só enviam multicast para os hosts de um determinado grupo. Multicast é a transmissão de áudio e/ou vídeo de um host para um grupo ou conjunto de outros hosts previamente conhecidos. Como exemplos de uso de multicast estão os jogos em rede, as videoconferências e a distribuição de vídeo pela rede no formado de Video on Demand - VOD e IP Television – IPTV.

   ![Internetworking no TCP/IP e no ISO/OSI](/posts/2021-02-05-3.png){: width="100" height="100" }

Endereçamento IP: Todo host conectado à uma rede TCP/IP requer uma identificação exclusiva e universal perante a rede, de forma que os pacotes endereçados a ele cheguem somente até ele. Para esta identificação o host é designado por um endereço IP. O endereço é um número binário de 32 bits, que pode endereçar até 4.294.967.296 hosts. Este número, o endereço, pode ser representado em binário ou em decimal pontuado, que é a notação mais comum e mais fácil de entender e memorizar.A notação decimal é resultado da transformação de cada conjunto de oito bits (octetos ou bytes) em um número decimal, que pode variar de 0 a 255, representando um intervalo de 256 valores (28). Os endereços IPv4 contém 32 bits e são divididos em endereço da rede e endereço do host. As máscaras de subrede ou simplesmente Mask são conjuntos de bits que mostram onde o endereço de rede termina e o onde o endereço de host começa. Para isto são utilizados os bits 1 para as posições do endereço que representam a rede e os bits 0 para as posições reservadas ao endereço dos hosts da rede.

Classes: O endereço é composto de identificação da rede (endereço da rede ou NetID) e identificação do host (endereço do host ou HostID). A organização de NetID e de HostID define a classe de endereço, e a máscara de rede ajuda a identificar o NetID e o HostID, como mostrado a seguir:

   ![Endereçamento IP](/posts/2021-02-05-4.png){: width="100" height="100" }

As classes são designadas pelas letras A, B, C, D e E. Na Classe A o primeiro bit do endereço é sempre 0 (zero), resultando em 224 ou 16.777.216 possíveis endereços de hosts (7 bits para NetID e 24 para HostID). Na Classe B os primeiros bits do endereço são sempre 10 (um, zero), resultando em 216 ou 65.536 possíveis endereços de hosts (14 bits para NetID e 16 para HostID). Na Classe C os primeiros bits do endereço são sempre 110 (um, um, zero), resultando em 28 ou 256 possíveis endereços de hosts (21 bits para NetID e 8 para HostID). Na Classe D os primeiros bits do endereço são sempre 1110 (um, um, um, zero). Esta classe é conhecida por Multicast ID, dada a sua utilização padrão para grupos de multicast. Na Classe E os primeiros bits do endereço são 1111 (um, um, um, um). Esta classe é de uso reservado pelos gestores de endereços globais para uso em projetos de pesquisa e testes.

Endereços reservados:

* 127.x.x.x - Reservados para testes internos (também chamado de localhost ou loopback);

* O primeiro e o último endereço da classe ou da sub-rede: O primeiro, por exemplo 192.168.10.0, é o endereço da rede. O último, por exemplo 192.168.255.255, é o endereço de broadcast para a rede em questão.

Além disso existem os endereços específicos recomendados para as redes locais ou redes internas conectadas à Internet. As faixas recomendadas para redes locais (internas) são:

* 10.0.0.0 a 10.255.255.255

* 172.16.0.0 a 172.31.255.255

* 192.168.0.0 a 192.168.255.255

É por isto que sempre se verifica a ocorrência destes endereços nos hosts das redes locais.

Notação Standard e CIDR: Notação Standard começa com o endereço e contém o prefixo que determina o tamanho (máscara) da rede. Por exemplo, a representação 192.168.0.0 /24 corresponde a uma sub-rede que contém 254 endereços possíveis, de 192.168.0.1 até 192.168.0.254, com 192.168.0.0 sendo o endereço de rede e 192.168.0.255 sendo o endereço de broadcast para esta rede.

Na representação 192.168.0.0 /22 tem-se uma sub-rede com 1022 possíveis endereços de hosts, de 192.168.0.1 até 192.168.3.254, com 192.168.0.0 sendo o endereço de rede e 192.168.3.255 sendo o endereço de broadcast para esta rede.

Para o IPv4, uma representação alternativa usa o endereço de rede, escrito na forma decimal com pontos, seguido da máscara de sub-rede após uma barra. Desta forma o endereço 192.168.0.0 /24 pode ser escrito como 192.168.0.0 255.255.255.0, pois contando os 24 bits da esquerda para a direita temos:

11111111.11111111.11111111.00000000

Já o endereço 192.168.0.0 /22 pode ser escrito como 192.168.0.0 255.255.252.0, pois contando os 22 bits da esquerda para a direita, temos:

11111111.11111111.11111100.00000000

A representação com a barra torna mais flexível o endereçamento, liberando-o do emprego somente das classes-padrão de endereçamento. Por isto é chamada também de CIDR - Classless Inter-Domain Routing ou Roteamento inter-domínio sem uso de classes, e serve para o endereçamento e agregação de sub-redes, flexibilizando as máscaras de rede e permitindo um maior aproveitamento dos endereços.

Endereçamento IP – IPv6: O IPv6 é a versão mais atual do protocolo IP, desenvolvida em função do esgotamento de faixas de endereço do IPv4. Os endereços são representados por números de 128 bits, permitindo assim a representação de 2128 hosts. O de, normalmente escritos como oito grupos de 4 dígitos hexadecimais, como por exemplo: 2001:0db8:85a3:08d3:1319:8a2e:0370:7344

Ao escrever o endereço os grupos de vários dígitos seguidos de zeros (0000) podem ser omitidos, como por exemplo: 2001:0db8:85a3:0000:0000:0000:0000:7344 é o mesmo endereço IPv6 que 2001:0db8:85a3::7344.

Endereçamento IP – DHCP: O DHCP - Dynamic Host Configuration Protocol ou Protocolo de configuração dinâmica de host é um protocolo de serviço TCP/IP que oferece configuração dinâmica, concessão de endereços IP de host, máscara de sub-rede e Default Gateway (Gateway Padrão). Isto evita o cansativo e recorrente trabalho de atribuição de endereços aos hosts de uma rede. O DHCP funciona do seguinte modo: um host envia um pacote UDP em broadcast com uma requisição DHCP para a porta 67. Um servidor DHCP que capturar este pacote irá responder, caso o cliente se enquadrar numa série de critérios, para a porta 68 do host solicitante, com um pacote contendo um endereço IP, uma máscara de rede e outros dados, como o default gateway, servidores de DNS, etc.

Endereçamento IP – NAT: O NAT - Network Address Translation ou Tradução de Endereços de Rede é uma técnica que permite reescrever o endereço de um host de uma rede interna quando este é colocado na Internet, e vice-versa. Desta forma os endereços da rede interna (rede local), geralmente padronizados, não são publicados na internet. Desde modo o uso de NAT torna a rede interna mais protegida e reduz o número de endereços IP necessários para a rede externa. Porém só é possível utilizar NAT com os protocolos TCP e UDP. É bom ressaltar que o NAT permite um máximo de 65535 conexões ativas concorrentes, devido ao uso de 16 bits para a identificação das portas utilizadas para a conversão.

# 4 Transporte

## O protocolo TCP

O Transmission Control Protocol, ou protocolo de controle de transmissão, é um dos principais protocolos da Internet. É adequado às redes globais, pois verifica se os dados são enviados pela rede da forma correta, na sequência apropriada e sem erros. É um protocolo da camada de transporte do modelo TCP/IP (camada3), sobre o qual se assentam a maioria dos demais protocolos e aplicações, como o SSH, FTP, HTTP — e praticamente toda a World Wide Web.

O processo de transmissão nesta camada funciona da seguinte maneira: transmissor e receptor criam pontos extremos – os sockets. Os Sockets são representados pelo endereço IP e mais um número de 16 bits, denominado porta. Por exemplo: 192.168.10.1:8080. As portas com valor abaixo de 1024 são chamadas de portas conhecidas e são reservadas para serviços específicos do TCP. As portas conhecidas só podem ser inicializadas por usuários com privilégio.

O protocolo TCP tem como principal característica a garantia da entrega da informação, isto é, a confiabilidade da transmissão. As suas outras características são:

* Orientado à conexão: É necessário estabelecer uma conexão entre os hosts que pretende comunicar entre si. Para isto é necessário encaminhar, por meio da rede, informações de um para o outro de forma que se reconheçam e consigam iniciar a comunicação.

* Ponto a ponto: A comunicação acontece entre um host e outro do início ao fim, isto é, um host é a origem e outro é o destino (e vice-versa) como se estivessem fisicamente ligados.

* Confiabilidade: As informações encaminhadas por meio da rede têm a garantia da entrega durante todo o processo de comunicação, incluindo-se a identificação, o tratamento e a correção de erros.

* Full duplex: Uma vez estabelecida a conexão entre os hosts a comunicação flui nos dois sentidos, fazendo com que ambos sejam, simultaneamente, origem e destino da comunicação.

* Handshake: O processo de comunicação precisa estabelecer o reconhecimento mútuo entre os hosts antes de iniciar a transmissão/recepção das informações. O TCP usa para isso o triplo handshake com o objetivo de sincronizar algumas informações, como o número de sequência dos pacotes, por exemplo.

* Entrega ordenada: Os pacotes da informação são entregues em sequência ordenada ao destinatário, de forma que a informação original possa ser remontada ou reconstruída para ser entregue à camada de aplicação exatamente como estava na origem.

* Controle de fluxo: O processo de comunicação inclui a confirmação do recebimento de cada pacote e a avaliação da quantidade de informações recebidas e aceitas, podendo inclusive atuar sobre parâmetros da comunicação para adequar o fluxo às condições da rede naquele momento.

* O TCP não permite broadcast e tampouco multicasting.

Existem portas do TCP associadas a serviços e protocolos específicos, que não podem ser utilizadas com outro propósito. Como já mencionado, estas portas são denominadas portas conhecidas e seu valor está no limite de 1024. As mais conhecidas são as seguintes:

| Porta  | Protocolo | Uso                                |
|:------:|:---------:|:----------------------------------:|
| 20, 21 | FTP       | Transferência de arquivos          |
| 22     | SSH       | Login remoto, substituto do Telnet |
| 25     | SMTP      | Correio eletrônico                 |
| 80     | HTTP      | World Wide Web                     |
| 110    | POP-3     | Acesso remoto a correio eletrônico |
| 143    | IMAP      | Acesso remoto a correio eletrônico |
| 443    | HTTPS     | Web segura (HTTP sobre SSL/TLS)    |
| 543    | RTSP      | Controle de player de mídia        |
| 631    | IPP       | Compartilhamento de impressora     |

Transmissor e receptor trocam informações na forma de segmentos. Os Segmentos são compostos de um cabeçalho de tamanho fixo de 20 bytes e os dados da transmissão (informações que o usuário quer transmitir ou necessita receber). O software decide o tamanho do segmento, porém este é limitado ao payload do IP, que é de 64 kBytes (65.535 Bytes). O segmento também é limitado pelo MTU (Maximum Transfer Unit) do enlace de dados, isto é, a capacidade máxima de encaminhamento de segmentos e seu tamanho.

Um pacote TCP:

   ![pacote TCP](/posts/2021-02-05-6.png){: width="100" height="100" }

Os oito bits dos flags do TCP atuam no processo de comunicação com as seguintes finalidades:

* CWR - Congestion Window Reduced ou janela de congestionamento reduzida, significa que o fluxo de informação deve ser reduzido em função de perdas ou atraso na informação;

* ECE - Confirma o “echo” da conexão TCP durante um handshake;

* URG – Indica que o pacote requer tratamento de urgência (pouco utilizado);

* ACK – Reconhecimento válido;

* PSH – Envio imediato dos dados, sem aguardar o preenchimento do buffer;

* RST, SYN e FIN – Processo de estabelecimento e liberação da conexão;

## O protocolo UDP

User Datagram Protocol é um protocolo simples da camada de transporte que permite que a aplicação escreva um datagrama encapsulado num pacote (IPv4 ou IPv6), o qual é então enviado ao endereço IP do destino. Porém não há qualquer tipo de garantia que o pacote será entregue. O protocolo UDP não é confiável, e se for necessário garantir a entrega, é preciso implementar controles tais como timeouts (limite de tempo), retransmissões, acknowlegments (reconhecimento), controle de fluxo, etc.

Cada datagrama UDP tem um tamanho e pode ser considerado como um registro indivisível. O UDP é um serviço sem conexão, isto é, não há necessidade de manter uma ligação entre o cliente e o servidor (ou entre origem e destino). Isto significa que um cliente UDP pode criar um socket, enviar um datagrama para um servidor e imediatamente enviar outro datagrama com o mesmo socket para um servidor diferente. Da mesma forma, um servidor poderia ler datagramas vindos de diversos clientes, usando um único socket. O UDP também fornece os serviços de broadcast e multicast, permitindo que um único cliente envie pacotes para vários outros na rede.

O protocolo UDP é a escolha adequada para fluxos de dados em tempo real, especialmente aqueles que admitem uma certa perda ou dano de parte de seu conteúdo. Parte do desempenho obtido por comunicação com o UDP deve-se ao fato de que este não perde tempo com criação ou destruição de conexões. Em função disso, durante uma conexão o UDP troca apenas 2 pacotes, enquanto no TCP esse número é superior a 10.

O UDP também contempla portas específicas para determinados tipos de serviço ou operações, dentre as quais cabe citar:

| Porta | Protocolo  | Descrição                                     |
|:-----:|:----------:|:---------------------------------------------:|
| 7     | Echo       | Ecoa um datagram recebido de volta ao emissor |
| 9     | Discard    | Descarta qualquer datagrama recebido          |
| 11    | Users      | Usuários ativos                               |
| 13    | Daytime    | Retorna data e hora                           |
| 17    | Quote      | Retorna um comentário do dia                  |
| 19    | Chargen    | Retorna uma string de caracteres              |
| 53    | Nameserver | Domain Name Services                          |
| 67    | BOOTPs     | Servidor bootstrap                            |
| 68    | BOOTPc     | Cliente bootstrap                             |
| 69    | TFTP       | Trivial File Transfer Protocol                |
| 111   | RPC        | Remote Procedure Call                         |
| 123   | NTP        | Network Time Protocol                         |
| 161   | SNMP       | Simple Network Management Protocol            |
| 162   | SNMP       | Simple Network Management Protocol (trap)     |

O pacote UDP:

   ![pacote UDP](/posts/2021-02-05-8.png){: width="100" height="100" }

## Protocolo SCTP

Stream Control Transmission Protocol é um protocolo de transporte confiável que opera sobre um serviço de pacotes não confiável e sem conexão, como é o caso do IP. O SCTP é orientado a mensagens e utiliza o conceito de associação para estabelecer vários fluxos de comunicação. Além disso provê suporte para Multihoming. As principais características do SCTP são:

* Entrega confirmada de dados de usuário, livre de erros e não duplicados;

* Fragmentação de dados em conformidade com o MTU descoberto do caminho;

* Entrega sequencial de dados de usuário em múltiplos fluxos;

* Empacotamento opcional de múltiplas mensagens de usuário num único pacote SCTP;

* Tolerância a falhas de rede através do suporte a caminhos múltiplos (multihoming);

* O SCTP é rate adaptative, adaptando-se às variações da rede;

O SCTP é um protocolo mais adaptado às necessidades de comunicação das redes modernas, e, portanto, apresenta alguns benefícios quando comparado ao TCP e ao UDP, como segue:

* O SCTP provê transmissão confiável, e detecta quando os dados são descartados, reordenados, duplicados ou corrompidos, retransmitindo os dados quando necessário;

* O SCTP é orientado a conexão;

* O SCTP usa o conceito de associação, o que o torna mais abrangente que a conexão TCP. Enquanto uma conexão TCP estabelece apenas um único fluxo full duplex, uma associação SCTP estabelece um número arbitrário de fluxos simplex. Porém, para simular uma conexão TCP, basta criar um fluxo SCTP em cada direção;

* O SCTP tem potencial de substituir o TCP em diversas aplicações, e além disso pois todas as portas reservadas pelo IANA ao TCP são automaticamente reservadas ao SCTP.

# 5 Aplicação

| Aplicação    | Acessar recursos da rede                                              |
| ------------ | --------------------------------------------------------------------- |
| Apresentação | Traduzir, criptografar, comprimir                                     |
| Sessão       | Estabelecer, gerenciar e encerrar sessões                             |
| Transporte   | Entrega confiável ponto a ponto, correção de erros                    |
| Rede         | Encaminhamento de pacotes da origem ao destino, conectar redes        |
| Enlace       | Entrega de nó em nó, frames/quadros de bits                           |
| Física       | Transmitir bits por meio físico, especificações mecânicas e elétricas |

## DNS

O DNS – Domain Name System ou sistema de nomes de domínio é uma aplicação que realiza o serviço de identificação de computadores na rede por meio de um nome. O DNS atende as outras aplicações, permitindo o uso de endereços da camada de aplicação – URLs ou um endereço de e-mail – ao invés de endereços lógicos da camada de rede (endereço IP). Diferentemente das pessoas, a rede identifica os computadores por seu endereço IP, totalmente numérico e de difícil memorização. Por causa disto é necessário um serviço que possa relacionar um nome de domínio ou de um host à um endereço IP: este serviço é o DNS.

Os servidores DNS da internet estão organizados em uma hierarquia na forma de uma árvore invertida de nomes de domínio.

Esta “árvore” de domínios comporta até 128 níveis, partindo da raiz – nível 0 –até o nível mais baixo – nível 127. Cada nó ou subdivisão da árvore é identificado por um rótulo (label) exclusivo que não se repetirá naquele nível. Uma sequência de rótulos separadas por pontos “.” forma um nome de domínio.

Os domínios podem ser genéricos – por especialidade – como “.edu”, “.com”, “.net”, por área geográfica ou país, como “.br”, “.ch”, “.ar”.

   ![DNS](/posts/2021-02-05-10.png){: width="100" height="100" }

Os domínios contêm diversos servidores de DNS, sendo o principal chamado de servidor DNS RAIZ. Este servidor define uma ZONA, à qual estão vinculados todos os demais servidores DNS primários e secundários. O servidor primário armazena e mantém atualizada a tabela de nomes do domínio, enquanto o servidor secundário mantém uma cópia desta tabela para atuar em caso de falha do servidor primário.

Para que um nome possa figurar em um servidor de domínio é necessário que seja cadastrado em uma entidade registradora homologada pela ICANN - Internet Corporation for Assigned Names and Numbers – Corporação da Internet para Designação de Nomes e Números. No Brasil o cadastro é mantido pelo registro.br aos cuidados da FAPESP – Fundação de Amparo à Pesquisa do Estado de São Paulo. Juntamente com o nic.br – Núcleo de Informações e Coordenação do Ponto BR este cadastro define os nomes de domínio para o território brasileiro.

O DNS consiste em uma aplicação cliente/servidor. Um host executando o módulo cliente encaminha uma mensagem de consulta à um host executando o servidor – ou um servidor DNS. A mensagem compõe-se de um cabeçalho com as informações do cliente e uma seção de perguntas, que contém os nomes de domínios a serem traduzidos para endereços IP.O servidor DNS devolve uma mensagem de resposta formada pelo cabeçalho, com as informações do cliente e do servidor, a seção de perguntas, uma seção de respostas, uma seção de autoridades e uma seção de informações adicionais.

O que acontece se um servidor primário não conseguir resolver um determinado nome? Ele repassará aos nós superiores da hierarquia do domínio para que estes resolvam o nome. Caso a solicitação chegue até o servidor raiz sem a descoberta do IP, um erro será devolvido na mensagem de resposta.

O DNS pode usar tanto o TCP quanto o UDP, e faz as conexões através da porta 53. Para pacotes de mensagem de resposta cujo tamanho não exceda os 512 bytes – tamanho típico de um pacote UDP – este protocolo, o UDP, será usado. Caso o tamanho da mensagem de resposta ultrapasse os 512 bytes ou não seja conhecido o tamanho, então será usada uma conexão TCP.

## DDNS – Dynamic Domain Name System

O sistema de nomes de domínio dinâmico – DDNS é uma evolução do DNS devido às constantes mudanças nas redes, com a inclusão de novos hosts e domínios ou eliminação de hosts ou domínios. Promover uma atualização de grande escala é inviável de forma manual. No DDNS, quando um nome é resolvido as informações são enviadas por meio de DHCP para o servidor primário do domínio, que cuida da replicação deste novo conjunto para os demais servidores, incluindo os servidores de DNS secundários. Para evitar o uso inadequado o DDNS pode usar mecanismos de autenticação, garantindo que somente servidores autorizados possam publicar as mudanças.

## DNSSEC – Domain Name System Secure

O sistema de nomes de domínio seguro é uma versão de DNS que utiliza a criptografia e a assinatura digital para a manutenção e o acesso à base de dados do sistema. O uso deste tipo específico de serviço tem por objetivo evitar ataques de DNS forjado.

## TELNET

O programa aplicativo cliente/servidor TELNET – de TErminaL NETwork é uma aplicação para serviços de terminal virtual que provê uma conexão a um sistema remoto por meio da rede. É a aplicação padrão do TCP/IP para os serviços de terminal virtual de acordo com a ISO – International Standard Organization. O TELNET permite que um host crie, por meio de terminal local, uma conexão a um host remoto, fazendo com que este terminal se comporte como se fosse um terminal do sistema remoto. Um terminal, neste cenário, é um dispositivo composto de Teclado, Monitor e Mouse – ou um computador emulando terminal – que possibilita a interação do usuário com os sistemas do computador remoto. O uso de terminal é típico de sistemas operacionais de tempo compartilhado - Time sharing – como o UNIX e o LINUX. O TELNET provê uma interface universal chamada NVT – Network Virtual Terminal – que utiliza um conjunto de caracteres padrão, pois hosts diferentes podem usar diferentes conjuntos de caracteres, em função do idioma ou do sistema operacional utilizado por cada um.

Para estabelecer a comunicação com o host remoto o TELNET usa uma conexão TCP e a porta 23 do servidor. O funcionamento do TELNET ocorre de três modos de operação:

* O modo Padrão, utilizado quando nenhum outro modo for negociado, e aquele no qual o eco é local, isto é, uma vez digitado um caractere, o próprio cliente (terminal local) faz a apresentação do mesmo na tela, porém só transmite para o servidor (host remoto) a linha inteira (ou até que pressionada a tecla ).

* No modo Caractere cada vez que um caracter é digitado o mesmo é enviado ao servidor, que o retransmite de volta para que o cliente faça a apresentação na tela. Isto gera dois efeitos: em conexões mais lentas ou congestionadas, pode haver um retardo entre a digitação e a apresentação do caracter; além disso cada caracter digitado vai gerar três segmentos de TCP na rede.

* No modo Linha a edição de linhas (eco, correção, etc.) é realizada pelo cliente. Quando finalizada a edição pela tecla então toda a linha é enviada para o servidor.

## Correio Eletrônico

O serviço de correio eletrônico usa uma arquitetura com três componentes principais, a saber:

* O User Agente (UA), agente de usuário, é o serviço ou aplicação responsável pelas operações do e-mail no cliente, seja o remetente ou o destinatário;

* O Message Transfer Agent (MTA), agente de transferência de mensagens, é a aplicação cliente/servidor que responde pelo envio de mensagens à um servidor de correio eletrônico;

* Message Access Agent (MAA), agente de acesso às mensagens, é a aplicação cliente/servidor responsável por buscar as mensagens em um servidor de e-mail.

Um serviço de Correio Eletrônico pode operar de quatro modos distintos. No primeiro modo, o remetente e destinatário est\]ao conectados no no mesmo sistema. Neste caso é necessário apenas o uso dos programas User Agent (UA). O remetente faz uso do UA para preparar e encaminhar seu e-mail para o remetente que, quando usar seu UA, receberá a mensagem. É o caso típico do serviço “mail” do UNIX / LINUX.

Em um segundo modo, o remetente e destinatário estão conectados a sistemas distintos. Então é necessário o uso de dois programas User Agent (UA) e um par de programas Message Transfer Agent (MTA), que funcionam em um modelo cliente/servidor para encaminhar a mensagem de um sistema ao outro. Este é o caso de uma mensagem de e-mail trocada entre dois sistemas UNIX / LINUX conectados à rede.

Em um terceiro modo o Remetente faz parte de uma LAN / WAN e o destinatário está conectado diretamente ao serviço de correio eletrônico. Neste modo é necessário o uso de dois programas User Agent (UA) e dois pares de servidores Message Transfer Agent, cada par funcionando em modelo cliente / servidor para o encaminhamento da mensagem de um sistema até o outro.

Finalmente, no quarto modo, o remetente e destinatário estão conectados ao serviço de correio eletrônico por meio de uma LAN / WAN. É necessário o uso de dois programas User Agent (UA), dois pares de servidores Message Transfer Agent (MTA) e um par de servidores Message Access Agent (MAA). Este é o cenário típico atualmente na internet.

## SMTP – Simple Mail Transfer Protocol

O SMTP - Simple Mail Transfer Protocol ou Protocolo Simples de Transferência de Mensagem é o protocolo que define a comunicação entre cliente e servidor do Message Transfer Agent (MTA). O SMTP utiliza a porta 25 (conexão em texto plano)1 ou a porta 465 (conexão criptografada via SSL). Em um processo típico de envio de e-mail o SMTP é utilizado tanto entre o cliente (UA) e o servidor de correio quanto entre os servidores de correio MTA).

## POP3 – Post Office Protocol versão 3

O POP3 – Post Office Protocol versão 3 ou Protocolo de Posto de Correio é o protocolo que define a comunicação entre cliente e servidor Message Access Agent (MAA) para acessar as mensagens deixadas em um servidor de e-mail. O POP3 acessa as mensagens no servidor de e-mail e as disponibiliza para o UA apresentá-las ao seu destinatário. O POP3 permite o acesso em dois modos, o modo keep e o módulo delete. No modo keep as mensagens são acessadas, porém mantidas no servidor de e-mail, e, portanto, podem ser acessadas novamente a partir de outro cliente MAA. No modo delete as mensagens são acessadas e excluídas do servidor de e-mail, sendo mantidas no UA a partir deste ponto. O POP3 utiliza a porta 110 do TCP para acessar as mensagens de correio eletrônico em um servidor.

## IMAP4 – Internet Mail Access Protocol versão 4

O IMAP – Internet Mail Access Protocol ou Protocolo de Acesso a Correio pela Internet é o protocolo que define a comunicação entre cliente e servidor Message Access Agent (MAA) de forma similar ao POP3, porém com muitos recursos adicionais, como por exemplo:

* É possível acessar o assunto de um e-mail antes de transferi-lo para o UA;

* É possível pesquisar um conteúdo específico nos e-mails do servidor;

* É possível baixar parcialmente um e-mail (sem as imagens, vídeos ou anexos, por exemplo);

* Também é possível que o usuário gerencie pastas e defina o armazenamento de suas mensagens nestas pastas no servidor de e-mail.

O IMPA4 utiliza a porta 143 do TCP para as conexões cliente / servidor com o servidor de e-mail.

## TRANSFERÊNCIA DE ARQUIVOS - FTP – File Transfer Protocol

O FTP – File Transfer Protocol ou Protocolo de Transferência de Arquivos é o protocolo padrão do TCP/IP para transferência de arquivos entre hosts. É uma aplicação cliente / servidor que estabelece duas conexões entre os hosts: uma para os dados e outra para o controle da transferência, e utiliza as portas 20 e 21 para estas duas conexões. Para acessar o servidor e fazer uma transferência é necessário ter uma conta com um nome de usuário (login) e uma senha. A transmissão dos dados do FTP é feita por uma conexão TCP. É possível utilizar também o FTP Anônimo para arquivos de acesso público. Neste caso, geralmente não é necessário login e senha, porém o padrão é que sejam:

Login: anonymous

Senha: guest

Nestes casos o acesso ao sistema é restrito e poucas operações são permitidas.

Outra alternativa para o FTP é o TFPT - Trivial File Transfer Protocol , um protocolo de transferência de arquivos muito simples e muito semelhante ao FTP. É muito utilizado para transferir pequenos arquivos entre hosts de uma rede, como, por exemplo, quando um terminal remoto ou um cliente inicia o seu funcionamento, a partir do servidor.

# 6 Aplicação

A World Wide Web é um serviço cliente/servidor distribuído, no qual um cliente (browser) pode acessar serviços em um ou mais servidores distribuídos por diversas localidades. Os serviços constituem-se em sua maioria em provimento de conteúdo. O conteúdo é distribuído em sites, e cada site administra seus documentos ou páginas web, com um servidor provendo o acesso aos documentos mediante a requisição do browser do cliente.

O cliente (browser) é aplicação que viabiliza o acesso, a apresentação dos documentos e a interação com o usuário. É formado por três partes: o controlador, que provê a interface com o usuário (teclado, mouse e tela), os programas clientes, que efetivamente acessam os documentos arquivados nos servidores, e os interpretadores, que apresentam os documentos de acordo com o padra o por eles definidos.

O servidor armazena as páginas e os elementos que as compõem. Ao receber uma solicitação de um cliente, busca a página e a transfere para o cliente para que possa interpretá-las e exibi-las. O servidor também mantém as páginas solicitadas anteriormente em cache para melhorar a eficiência, pois é provável que o acesso à uma página não seja único. Um servidor é um computador que utiliza técnicas multitarefa / multithread / multiprocessamento para melhorar o desempenho, e assim providenciar o atendimento a vários clientes simultâneos.

A URL - Uniform Resource Locator ou localizadora uniforme de recursos é utilizada pelo protocolo HTTP para prover o acesso a documentos distribuídos mundo afora. Uma URL é um padrão para a especificação de qualquer tipo de informação na Internet. O formato de uma URL é: protocolo://host:porta/path, onde:

Protocolo: Identifica o tipo de aplicação utilizada para acessar o conteúdo;

Host: Nome do computador que armazena as informações. Geralmente começa com a designação www, porém isto não é obrigatório;

Porta: Número da porta (0 – 65535) para acesso ao Host

Path: O caminho para chegar até a informação na estrutura de diretórios do Host. Utiliza o mesmo modelo do sistema operacional UNIX.

A função do cookie é armazenar informações da sessão e do cliente no host utilizado para o acesso ao site. O formato de um cookie geralmente é um arquivo de texto ou sequência de caracteres contendo, na maioria dos casos: - O nome de domínio do cliente; - Informações coletadas pelo servidor relativas à sessão do cliente - Data e hora

Os documentos estáticos apresentam uma estrutura fixa. O seu conteúdo é definido na criação do documento.

Os documentos dinâmicos, ao invés disso, são criados pelo servidor à cada solicitação de um cliente.

Os documentos ativos são os que implicam na execução de um código pelo próprio cliente. Estes documentos resultam de uma interação com o usuário ou com o host do cliente. Estes códigos são geralmente formados por Applets Java ou JavaScript. O que diferencia estes códigos é que os Applets são compostos de código executável, enquanto o JavaScript é composto por texto plano.

A HTML – Hipertext Markup Language ou linguagem de marcação de hipertexto.

## HTTP – HyperText Transfer Protocol

O HTTP - HyperText Transfer Protocol ou protocolo para transferência de hipertexto é o protocolo utilizado para acessar os dados na WEB. Pode-se dizer que é uma combinação de FTP e SMTP: faz a transferência de arquivos do mesmo modo que o FTP usando conexão TCP, porém com apenas uma conexão. E utiliza mensagens para a requisição de dados como o SMTP.

O HTTP usa os serviços TCP na porta 80 por padrão. Além disso o HTTP também inclui comandos ou métodos nas mensagens, tais como GET, POST e PUT, que são interpretados pelos clientes e servidores da Web e geram respostas em formato de códigos, dentre os quais o mais conhecido é o 404 (Not Found). O HTTP requer uma conexão persistente, partindo do princípio que, uma vez transferida e exibida uma página, haverá uma interação com o usuário que resultará em nova mensagem ou consulta. Então o servidor mantém a conexão mesmo após enviar a resposta ao cliente.

O HTTP permite o uso de servidores PROXY, os quais mantém uma cópia dos documentos em seu cache. Neste caso, o cliente consulta primeiro o PROXY: se a informação não for localizada, então o próprio PROXY consulta o WEB Server para obter a informação atualizada. Isto reduz o tráfego na rede de forma significativa, especialmente em redes locais de grande porte.

## Sistema de Gerenciamento de Redes

Um sistema de gerenciamento de redes é composto de um conjunto de atividades e recursos para atender às principais funções do gerenciamento de rede, que podem ser agrupadas em:

* Gerenciamento de configuração: tem por finalidade informar o estado de cada elemento e sua relação com os demais a cada instante, incluindo as mudanças e problemas ocorridos. Geralmente estas informações são fornecidas pelos processos de reconfiguração e de documentação (software e hardware) da rede;

* Gerenciamento de falhas: trata do funcionamento adequado de cada elemento da rede, buscando o bom funcionamento da rede como um todo. O processo de gerenciamento de falhas da rede comporta duas abordagens: gerenciamento reativo e gerenciamento proativo. O gerenciamento reativo abrange as tarefas de detecção, isolamento, correção e registro de falhas. O gerenciamento proativo tem por objetivos impedir a ocorrência de falhas por meio de medidas de prevenção e identificação de sinais divergentes, ou mesmo da utilização de critérios específicos como a vida útil e a capacidade de trabalho de determinados elementos da rede;

* Gerenciamento de desempenho: busca a melhor eficiência os equipamentos e da rede como um todo, e trabalha e, conjunto com o gerenciamento de falhas. Trata-se do monitoramento e controle da rede com base em critérios quantitativos e qualitativos que analisa constantemente a capacidade (determinada pelos equipamentos e meios de transmissão), o tráfego na rede (representa a quantidade de bits ou bytes que são encaminhados e recebidos pelos nós de rede em função do tempo), o throughput (taxa de transferência medida em um nó da rede ou trecho da rede para determinar se há um gargalo ou estrangulamento no tráfego) e o tempo de resposta (intervalo de tempo entre o encaminhamento de uma solicitação de usuário e o recebimento da resposta).

* Gerenciamento de segurança: é o processo que concentra as atividades de controle de acesso à rede e aos elementos da rede. É o responsável pela aplicação da política de segurança – especialmente no que diz respeito a tráfego e acesso, e depende de todos os demais processos para fazer a aplicação, o monitoramento e o controle de uso e acesso aos recursos da rede;

* Gerenciamento de contabilização: providencia a quantificação de acessos e o uso dos recursos da rede, conhecida como Tarifação. Esta medição é necessária para efeitos de desempenho e segurança, e tem como principais objetivos evitar o monopólio de recursos escassos ou críticos da rede – como o link de internet, por exemplo - e promover o uso da forma mais eficiente possível. Além disso a contabilização provê informações para os administradores planejarem a expansão e a atualização da rede em função da demanda e do desempenho. É comum também haver o fornecimento de informações da tarifação para fins de Auditoria.

## SNMP – Simple Network Management Protocol

O protocolo simples para gerenciamento de redes é um Framework para gerenciamento de dispositivos em rede com base no TCP/IP e que usa o conceito de gerente e agente. É um protocolo do nível de aplicação, o que permite sua utilização independe das características físicas da rede e dos fabricantes do hardware. Um elemento gerente – ou gerenciador – é um host ou estação que executa uma aplicação SNMP Cliente. Um elemento agente é um equipamento de rede que executa uma aplicação SNMP Servidor. O gerenciamento é o resultado da interação entre o cliente e o(s) servidor(es). O agente é responsável por coletar as informações e mantê-las em uma base de dados, e encaminhá-las ao gerente quando solicitado, para que o gerente avalie as informações e também possa endereçar ações ao equipamento no qual o agente está em execução. Os agentes também podem transmitir mensagens de alerta, os traps, no caso de identificação de situações anômalas, falhas ou problemas de capacidade.

O SNMP geralmente é implementado em uma ferramenta mais abrangente que cuida da criação e atualização de estatísticas e de sua apresentação, geralmente em formato gráfico. Além disso o SNMP conta com dois protocolos auxiliares:

* SMI – Structure of Management Information, ou estrutura de informações de gerenciamento: é o protocolo que define as regras de atribuição de nomes, estabelece tipos de objetos e mostra como codificar os objetos e valores. Porém não define o número de objetos, não lhes dá nomes e tampouco atua na associação entre os objetos e seus valores.

* MIB – Management Information Base, ou base de informações de gerenciamento: é o protocolo que cuida da criação de um conjunto de objetos, nomes, tipos e relações entre si para um equipamento gerenciável da rede, formando um banco de dados para o equipamento. Estas informações serão solicitadas pelo SNMP e, em função delas, determinadas ações poderão ser comandas ao agente.