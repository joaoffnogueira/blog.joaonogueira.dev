---
title: Organização do código Java
author: João F. F. Nogueira
date: 2020-10-23 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# Pacotes

* As classes podem ser organizadas em pacotes

* Objetivos

– Organização

– Possibilitar que classes possam ter o mesmo nome

* O nome do pacote é mapeado para um diretório no sistema de arquivos

`com.treinamento.java.Exemplo` -> com/treinamento/java/Exemplo.java

## Classes dentro de um pacote

* Devem estar na estrutura correta no sistema de arquivos

* O seu pacote deve ser declarado usando o `package`

– Esta declaração deve ser feita na primeira linha

```java
package com.treinamento.java;

public class Exemplo {
...
}
```

## Convenção de Nome dos Pacotes

* Contém apenas letras minúsculas

* Normalmente é definido um nome que não terá conflito com pacotes criados por terceiros

## Como encontrar as Classes

* Usar o `fully qualified name`

```java
com.java.Exemplo e = new com.java.Exemplo();
```

* Usar o import

```java
import com.java.Exemplo;
...
Exemplo e = new Exemplo();

```

# O uso do `import`

* Os imports devem ser usados logo após o uso do package (caso exista)

* É possível importar todas as classes de um pacote

```java
import com.java.*;
```

* Importar classe por classe é preferível por questões de organização de código

# Visibilidades `package` e `protected`

## Visibilidade `package`

* Quando não definimos modificadores para classes, atributos, métodos ou construtores, eles assumem a visibilidade package por padrão

* Package significa que todas as classes do mesmo pacote possuem o acesso

## Visibilidade `protected`

* Quando um método, atributo ou construtor possui o modificador protected

– As subclasses têm acesso ao atributo

– Outras classes do mesmo pacote também têm acesso

# Javadoc

* O Javadoc é a documentação do seu projeto

– Classes, construtores, métodos, pacotes, etc.

* Gerado a partir de comentários no código

* O Java possui uma ferramenta para exportar o Javadoc

* A própria API do Java é gerada a partir da ferramenta Javadoc

# Criação de arquivos JAR

* Java ARchive

* Conjunto de classes compactadas no padrão ZIP, mas com extensão JAR

* O JAR é um componente de software

– Agrupa código comum

– Possui relativa independência

* O JDK possui um utilitário para gerar arquivos JAR

# Convenções do código Java

* Códigos escritos em Java devem seguir algumas convenções

– Esta padronização ajuda na manutenção do código

– Facilita a leitura do código por outros desenvolvedores

* Classe e interface

– Deve ser um substantivo

– Começa com letra maiúscula e segue a notação camel case

```java
class Estado
interface DVDPlayer
class CasaDeMadeira
```

* Método

– Deve ser um verbo

– Começa com letra minúscula e segue a notação camel case

```java
void comer()
int getIdade()
void processarPagamento()
```

* Variável

– Deve ter um nome que descreva seu propósito de forma clara

– Começa com letra minúscula e segue a notação camel case

```java
double nota
int qtdeItens
Casa casaDaPraia
```

* Constante

– Todas as letras são maiúsculas e o caractere "_" é usado para separar as palavras

– A regra se aplica a elementos de enums e atributos com os modificadores static final

```java
int VALOR
String ARQUIVO_CONFIG
enum Prioridade {
	ALTA,
	MEDIA,
	BAIXA
}
```

* Blocos de código

- Convenção para estruturas que usam "{" e "}" para delimitar um bloco de código

```java
if (valor > 10) {
	...
}

public class Caneta {
	...
}
```