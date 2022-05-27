---
title: A arquitetura Android e componentes de aplicativo
author: João F. F. Nogueira
date: 2021-02-05 09:00:00 -0300
categories: [Português, Estudos]
tags: [android]
toc: true
---

> Baseado no material da minha disciplina da graduação

# A arquitetura Android

![A arquitetura Android](/posts/2021-02-05-11.svg){: width="100" height="100" }

## Linux Kernel

Esta camada contém os serviços essenciais. Gerenciamento de processos e de memória são feitos nesta camada. O Linux Kernel também contém os drivers de dispositivos e a Arquitetura de Permissões, que restringe o acesso a dados ou recursos somente a processos que foram autorizados. Aqui, também, encontramos componentes específicos para Android, como, por exemplo, gerenciamento de bateria, compartilhamento e gerenciamento.

## Libraries

Na camada de libraries (bibliotecas), temos as bibliotecas de sistema, normalmente escritas em C e C++, e que são utilizadas para o bom funcionamento do sistema operacional. Também encontramos bibliotecas Java criadas especificamente para Android.

Algumas das bibliotecas:

* Surface Manager – atualização da tela  
* SQLite – utilizada para acesso a dados publicados por provedores de conteúdo e que inclui também as classes de gerenciamento do banco de dados SQLite
* SSL – (Secure Sockets Layer), que é utilizada para prover segurança na internet  
* OpenGL – que dá acesso para interface Java aos gráficos 3D OpenGL/ES e a API de renderização  
* Media Framework – utilizada para fornecer acesso à diferentes codecs (programas utilizados para codificar e decodificar arquivos de mídia), que possibilitam a gravação e execução de formatos diferentes  
* WebKit – utilizada para mostrar conteúdo da internet ou conteúdo HTML  

## Android Runtime 

É o terceiro componente da arquitetura Android, e é colocado na segunda camada (a partir de baixo). Este componente é responsável por fornecer a `Core Java Library` e a `Dalvik Virtual Machine`. As aplicações Android são normalmente criadas na linguagem de programação Java e, para tornar mais simples o desenvolvimento destas aplicações, o Android fornece uma grande gama de blocos reutilizáveis Java, como por exemplo `java.*` e `javax.*`, os pacotes `android.*`, responsáveis pelo ciclo de vida dos aplicativos Android e os pacotes `org.*`, que suportam operações de rede. A `Dalvik Virtual Machine` é o software que executa as aplicações Android, e é similar ao `Java Virtual Machine` (JVM), mas desenvolvida e otimizada para esta plataforma. A Dalvik utiliza funções principais do Java, como gerenciamento de memória e multi threading, que possibilita que cada aplicação Java rode em seu próprio processo. 

## Application Framework 

A terceira camada interage diretamente com o framework de aplicação, que gerencia as funções básicas de um dispositivo Android, como gerenciamento de recursos, gerenciamento de chamadas, etc. Blocos importantes do framework de aplicação são:  
* Activity Manager – bloco utilizado para gerenciar o ciclo de vida completo das aplicações  
* Content Providers – utilizado para gerenciar o compartilhamento de dados entre as aplicações  
* Telephony Manager – utilizado para gerenciar chamadas de voz  
* Location Manager – utilizado para gerenciar as localizações obtidas utilizando-se o GPS ou uma torre de celular  
* Resource Manager – este bloco é responsável por gerenciar os tipos diferentes de recursos utilizados em uma aplicação Android

## Applications 

Nesta camada estão as aplicações criadas por diferentes fornecedores ou desenvolvedores.

# Pacote Android:  Android Application Package (APK)

Este pacote normalmente possui a seguinte estrutura:  
* META-INF 
  * MANIFEST.MF – arquivo de manifesto da aplicação 
  * CERT.RSA – O certificado da aplicação 
  * CERT.SF – Contém os hashes SHA1 para os arquivos incluídos no pacote 

* lib – diretório que contém o código compilado específico para o tipo de processador 
  * armeabi – código compilado para processadores ARM 
  * armeabi-v7a – código compilado para todos os processadores ARMv7 e acima 
  * arm64-v8a – código compilado para processadores ARMv8 e superior 
  * x86 – código compilado para processadores x86 
  * x86_64 – código compilado para processadores x86 64 
  * mips – código compilado para processadores MIPS  

* res – diretório que contém todos os recursos não compilados no diretório resources.arsc  

* assets – diretório contendo todos os arquivos de componente bruto necessários para o funcionamento da aplicação, os quais podem recuperados através do AssetManager  

* AndroidManifest.xml – um arquivo de manifesto adicional, que descreve o nome, versão, direitos de acesso e bibliotecas utilizadas pela aplicação.  

* Classes.dex – as classes compiladas para o formato dex, que é entendido pela máquina virtual Dalvik  

* Resources.arsc – arquivo pré-compilado de recursos, como por exemplo XML binário

# Componentes de aplicativo

## Atividades (Activity)

Representam uma tela única de interface de usuário. É implementada como uma subclasse de Activity. Estas fornecem a tela com a qual os usuários podem interagir. Cada atividade recebe uma janela, que representa a interface do usuário, com botões e caixas de texto, por exemplo. Aplicativos geralmente possuem várias atividades vinculadas entre si. Um aplicativo normalmente possui uma atividade principal, que é mostrada ao usuário quando este o executa pela primeira vez. Após isso, cada atividade pode iniciar uma nova atividade para executar diferentes ações.

As atividades são ordenadas em forma de pilha no formato UEPS (último a entrar, primeiro a sair). A cada nova atividade criada, a atividade anterior é interrompida, mas é armazenada na pilha, para que possa ser restabelecida quando o usuário pressionar o botão de retorno. 

## Serviços (Services) 

Componentes executados em segundo plano para realizar operações de longa duração ou executar trabalhos remotos. Não representam uma interface com o usuário. Um serviço pode ter duas formas:  

* Iniciado – um componente do aplicativo, como uma activity, por exemplo, inicia-o chamando `startService()`. Após iniciado, o serviço pode ficar em segundo plano indefinidamente, mesmo que o componente que o chamou seja destruído. Neste modelo, normalmente não temos o retorno da operação para o componente que originou a chamada.  

* Vinculado – neste caso, o componente vincula-se ao serviço, iniciando-o pela chamada `bindService()`. Ao ser vinculado, o serviço criará uma interface cliente-servidor, que permitirá que os componentes interajam com este, enviando solicitações e recolhendo resultados. Este tipo de serviço somente permanece em execução enquanto o componente que criou o vínculo mantiver o vínculo com o mesmo. Ao se destruir o componente, ou ao se desvincular o serviço, o mesmo é destruído.

## Provedores de Conteúdo (Content Providers) 

São responsáveis por prover às aplicações o conteúdo das quais elas necessitam para funcionar, ou seja, os dados. Ao utilizarmos provedores de conteúdo, tornamos a forma como os dados são gravados transparentes à aplicação, o que permite que esta mantenha o foco nas interações com os usuários. Através do provedor de conteúdo, os aplicativos acessam e até modificam os dados gerados por outros aplicativos instalados, como, por exemplo, a lista de contatos, caso o provedor de conteúdo permita seu acesso.

## Receptores de Transmissão (Broadcast Receivers) 

Este é o componente que responde (e inicia) anúncios a todo o sistema Android. Transmissões de que o sistema está com a bateria baixa ou que a tela está ligada são originados no sistema. Aplicativos podem iniciar transmissões, como, por exemplo, de que uma imagem foi capturada, informando a outros aplicativos sobre este evento, possibilitando assim que os mesmos disparem alguma ação. Ao contrário de uma Activity, um BroadcastReceiver não possui qualquer tipo de interface com o usuário, mas possibilita a criação de uma notificação na barra de status. A intenção é de que os receptores de transmissão efetuem a menor quantidade de serviços possível, delegando seu trabalho para os Services