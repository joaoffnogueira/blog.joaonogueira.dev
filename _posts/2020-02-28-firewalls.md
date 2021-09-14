---
title: Tipos de firewalls e suas facilidades
author: João F. F. Nogueira
date: 2020-02-28 09:00:00 -0300
categories: [Português, Estudos]
tags: [security]
toc: true
---

# Tipos de Firewalls

•	(Stateless) Packet filtering – PF

O PF é um firewall que realiza a filtragem de pacotes IP individuais baseado em regras que determinam se cada pacote será transmitido ou descartado. Algumas das regras mais comuns de filtragem são os endereços IP de origem e destino, os endereços da camada de transporte (porta), o campo IP de protocolo e a interface (STALLINGS; BROWN, 2014).

•	Stateful packet filtering – SPF

Firewalls de filtragem de pacotes com estado verificam as mesmas informações que um filtro de pacotes IP individual, mas vai além monitorando o estado das conexões, criando um diretório de conexões TCP de saída. Com o conhecimento do contexto (a sessão por onde transitam os pacotes IP) e informações das outras camadas do protocolo TCP/IP, o filtro de pacotes com estado consegue cobrir algumas brechas de segurança deixadas pelo filtro de pacotes que não monitora o estado das conexões e torna mais rígidas as regras aplicadas (STALLINGS; BROWN, 2014).

•	Application gateways - AG

Atuando no nível da aplicação, e por isso também chamado de proxy de aplicação, o firewall do tipo application gateway retransmite segmentos TCP seguindo uma implementação específica da aplicação. Assim, conexões que não são compatíveis com a implementação do gateway não conseguem permissão para trafegar dados. Além disso, o gateway pode implementar funções específicas e códigos de proxy diferentes para aplicações específicas, garantindo mais segurança e especificidade na filtragem de conexões do firewall (STALLINGS; BROWN, 2014).

# Facilidades de Firewalls

•	Access Control Lists – ACLs

As listas de controle de acesso são facilidades dos firewalls que permitem criar regras específicas para permitir ou negar o acesso a usuários ou conexões. Podem ser do tipo White lists, onde apenas os usuários ou conexões listados e identificados podem acessar os recursos do sistema ou trafegar dados pelo firewall, rejeitando qualquer origem desconhecida. Ou podem ser do tipo Black lists, que aceitam todos os acessos desconhecidos, barrando apenas os conhecidos e identificados na lista (STALLINGS; BROWN, 2014). 

•	Intrusion Detection System (IDS)

O Sistema de detecção de intrusos é uma facilidade de firewall que visa detectar acessos não autorizados ao sistema. Existem diversos tipos, que partem da premissa de que o comportamento de um invasor é diferente de um usuário autorizado. Para monitorar esse comportamento, os IDS verificam constantemente quais conexões estão sendo estabelecidas, quais usuários estão autenticados, quais as ações que eles estão realizando, quais falhas de conexão ou de autenticação estão sendo lançadas. Comparando esse registros com logs e históricos do próprio sistema ou com registros de invasões conhecidas, o IDS pode sinalizar acessos suspeitos e interromper conexões para proteger o sistema (STALLINGS; BROWN, 2014).

# Comparação entre Firewalls baseados em Software e em Hardware

| ****                                     | **SW - (ex: Windows Firewall)**                                                                                                           | **HW - (ex: Fortiner)**                                                                                                                                              |
|:----------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Custo                                    | Baixo considerando que existem opções gratuitas. Altos em caso de licenciamento de muitas cópias.                                         | Alto para implantação e para poucas máquinas. Baixo se um único dispositivo protegerá muitas máquinas.                                                               |
| Facilidade de implementação e manutenção | Fácil, pode ser utilizado por usuários comuns.                                                                                            | Difícil, requer profissional especializado.                                                                                                                          |
| Desempenho                               | Limitado aos recursos da máquina onde está instalado.                                                                                     | Memória e processador dedicados, liberando recursos das máquinas principais.                                                                                         |
| Vantagens específicas                    | Mais opções de controle e configuração. Mais versátil.                                                                                    | Esconde as máquinas da rede local, representando para um observador externo um único dispositivo (NAT). Um único dispositivo pode proteger uma rede interna inteira. |
| Desvantagens específicas                 | O software precisa ser instalado e configurado em muitas máquinas, se houverem. Consome recursos (memórias, processamento...) do usuário. | Não é apropriado para rastreamento de tráfego de saída. Ocupa espaço físico para instalação.                                                                         |


Fonte: ABHILASH(2015), FORTINET(s. d.), TECHSAA(2021).

Referências

ABHILASH, C. R. Hardware vc Software firewall: a brief comparison. Bobcares. 13 set. 2015. Disponível em: https://bobcares.com/blog/hardware-vs-software-firewall-a-brief-comparison/ Acesso em: 19/08/2021.

FORTINET. Hardware Firewalls vs. Software Firewalls. Sem data. Disponível em: https://www.fortinet.com/resources/cyberglossary/hardware-firewalls-better-than-software#:~:text=Hardware%20vs.%20Software%20Firewalls%20At%20the%20most%20basic,ways%2C%20giving%20them%20their%20own%20set%20of%20advantages%3A Acesso em: 19/08/2021.

STALLINGS, W.; BROWN, L. Segurança de computadores: princípios e práticas. Tradução de Arlete Simille Marques. 2. ed. Rio de Janeiro: Elsevier, 2014. 

TECHSAA. Firewall Hardware And Software: Differences Everybody Needs To Know. Hackernoon. 24 mar. 2021. Disponível em: https://hackernoon.com/firewall-hardware-and-software-differences-everybody-needs-to-know-pxx3339 Acesso em: 19/08/2021.
