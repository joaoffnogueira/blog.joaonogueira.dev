---
title: Programação em Rede com Sockets TCP/IP e UDP/IP
author: João F. F. Nogueira
date: 2021-01-15 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [redes, web]
toc: true
mermaid: true
---

> Baseado nos cursos da Softblue

# O que são sockets

* Mecanismo de comunicação entre dois programas que funcionam na mesma rede

* Modelo cliente/servidor

– Uma aplicação servidor é executada numa determinada máquina e tem um socket ligado a uma porta específica dessa máquina

– O servidor espera que um cliente faça um pedido de ligação através desse socket

# Sockets TCP/IP

* Existe uma conexão entre o cliente e o servidor

– Permite utilização de fluxos de dados (streams)

* A comunicação é confiável

– Sem perda de dados

– Sem inversão de ordem dos pacotes

```mermaid
graph TD
    A[O cliente tenta se conectar ao servidor por uma porta] --- B[fa:fa-desktop Cliente]
    B --- C[fa:fa-door-open Porta]
    B --- D[ ]
    D -->|requisição de conexão| E[fa:fa-door-open Porta]
    E --- F[fa:fa-server Servidor]
    F --- G[fa:fa-door-open Porta]
    G -->|dados| C
    C -->|dados| G
    F --- H[O servidor conecta o cliente numa nova porta, por onde é feito o tráfego dos dados]
```

# Sockets UDP/IP

* Não existe uma conexão entre o cliente e o servidor

– Envio de datagramas (remetente, receptor, conteúdo)

* A comunicação não é confiável

– Dados podem ser perdidos

– Datagramas podem chegar fora de ordem

* Muito mais veloz que sockets TCP/IP

```mermaid
graph TD
    A[O cliente manda datagramas para o servidor] --- B[fa:fa-desktop Cliente]
    B -->|fa:fa-file envio de datagramas| E[fa:fa-door-open Porta]
    E --- F[fa:fa-server Servidor]
```

# Multicast

* Envio de datagramas para um grupo de destinatários

* Utiliza protocolo UDP

* Grupos multicast (IPs classe “D”)

– de 224.0.0.0 a 239.255.255.255

```mermaid
graph TD
    A[O cliente manda uma mensagem para um grupo] --- B[fa:fa-desktop Cliente]
    B --> C((Grupo Multicast))
    C --> D[fa:fa-desktop] & E[fa:fa-desktop] & F[fa:fa-desktop]
    D & E & F --- G[Os computadores cadastrados no grupo recebem a mensagem]
```
