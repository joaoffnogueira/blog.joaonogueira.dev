---
title: Desenvolvendo com o uso do Maven em Java
author: João F. F. Nogueira
date: 2020-11-27 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# O Maven

* O Maven é um projeto da Apache

– Open source

* Objetivos principais

– Gerenciamento de build

– Geração de relatórios

– Geração de documentação

* Baseado no conceito de POM

– Project Object Model

Funcionamento do Maven:

![Funcionamento do Maven](/posts/2020-11-27-1.png){: width="100" height="100" }

## Estrutura de um projeto Maven

* O Maven define uma estrutura base para os projetos Java

![Estrutura de um projeto Maven](/posts/2020-11-27-2.png){: width="100" height="100" }

## O arquivo `pom.xml`

*  Descreve as características do projeto, dependências, plug-ins a serem executados, etc.

```xml
<project>
	<modelVersion>4.0.0</modelVersion>
	<groupId>br.com.softblue</groupId>
	<artifactId>exampleproj</artifactId>
	<version>0.0.1-SNAPSHOT</version>
</project>
```

* Conceitos

– Group ID
	
	• Normalmente referencia a empresa

– Artifact ID

	• Nome do artefato ou projeto

– Version

	• Versão do artefato

## Gerenciamento de dependências

* O Maven é capaz de gerenciar dependências de outros artefatos de forma automática

– JARs

– Projetos

* O arquivo pom.xml define a dependência

– A dependência é baixada do repositório central e fica armazenada no repositório local

– Dependências transitivas também são resolvidas automaticamente

– O projeto passa a referenciar o artefato

* Exemplo de dependência da API `Apache Commons I/O`

```xml
<project>
	<modelVersion>4.0.0</modelVersion>
	<groupId>br.com.softblue</groupId>
	<artifactId>exampleproj</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<dependencies>
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-io</artifactId>
			<version>1.3.2</version>
		</dependency>
	</dependencies>
</project>
```

## Repositório central do Maven

* O gerenciamento de dependências funciona com base em um repositório central

– Os artefatos ficam todos disponibilizados neste repositório

– Cada artefato no repositório é identificado pelo `group ID`, `artifact ID` e `versão`
