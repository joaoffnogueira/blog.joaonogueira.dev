---
title: Conceitos e arquitetura da plataforma Jakarta EE
author: João F. F. Nogueira
date: 2021-04-09 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
mermaid: true
---

> Baseado nos cursos da Softblue e na documentação da Oracle

# Ramificações do Java

• Java SE (Standard Edition)

– Base do Java

– Ambiente de execução e bibliotecas comuns

• Java ME (Micro Edition)

– Dispositivos móveis

• Java EE (Enterprise Edition)

– Aplicações corporativas e internet

# O Java EE

• Java Enterprise Edition

– Chamado antigamente de J2EE

• Em 2019, a Oracle entregou o Java EE para a comunidade open source

– Eclipse Foundation

– Mudança de nome: Jakarta EE

## Especificação do Java EE

• É uma especificação escrita pela Oracle

– Existe a participação de uma comunidade, que dá sugestões

– Participam desta comunidade diversas pessoas e empresas

• É um documento aberto

– Qualquer empresa pode implementar o seu servidor compatível com Java EE

• A padronização permite que a mesma aplicação execute em servidores de diferentes empresas

## Separação em Camadas

![Separação em Camadas](/posts/2021-04-09-1.png){: width="100" height="100" }

## Componentes Java EE

![Componentes Java EE](/posts/2021-04-09-2.png){: width="100" height="100" }

## Containers Java EE

![Containers Java EE](/posts/2021-04-09-3.png){: width="100" height="100" }

## Estrutura de Diretórios

```mermaid
graph TD
    A[fa:fa-folder-open Browser] --- B[fa:fa-folder-open WEB-INF]
    A --- C[fa:fa-file-alt Arquivos XHTML, Arquivos HTML estáticos, Imagens, style sheets, etc.]
    B --- D[fa:fa-file-alt web.xml]
    B --- E[fa:fa-folder-open classes] --- F[fa:fa-file-alt *.class]
    B --- G[fa:fa-folder-open lib] --- H[fa:fa-file-alt *.jar]
```

## Configuração de Aplicações

• Até o Java EE 5, usar arquivo web.xml era utilizado na configuração

– Agora o web.xml é opcional

• Grande parte das configurações é feita através de annotations

## Empacotamento de Aplicações

• Uma aplicação web pode ser empacotada em apenas um arquivo

– Facilita a distribuição

– Facilita a instalação

• Este arquivo é um WAR

– Web ARchive

```mermaid
graph TD
    subgraph fa:fa-box WAR
      C[fa:fa-file-alt Arquivos XHTML, Arquivos HTML estáticos, Imagens, style sheets, etc.]
      B[fa:fa-folder-open WEB-INF] --- D[fa:fa-file-alt web.xml]
      B --- E[fa:fa-folder-open classes] --- F[fa:fa-file-alt *.class]
      B --- G[fa:fa-folder-open lib] --- H[fa:fa-file-alt *.jar]
    end
```

Servidor Java EE gratuito - WildFly
