---
title: Annotations e a Reflection API no Java
author: João F. F. Nogueira
date: 2020-12-11 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# Annotations

* Mecanismo criado a partir do Java 5

* São declarações no código que podem ser usadas por ferramentas ou programas externos

* Não influenciam diretamente na execução do código

```java
@ClassInfo(autor = "João Nogueira", data = "11/12/2020")
public class MyClass {
	...
}

public @interface ClassInfo { //declaração
	String autor();
	String data();
	int versao() default 1; //valor padrão
}
```

* Quando a annotation possui apenas um elemento value, ele pode ser omitido quando a anotação é usada

```java
public @interface Autor {
	String value();
}

@Autor("João Nogueira")
public class MyClass() {
	...
}
```

## @Retention

* Configura como a anotação deve se comportar perante ao compilador e à JVM

* Tipos

* RetentionPolicy.RUNTIME

- A anotação pode ser lida em tempo de execução pela JVM

* RetentionPolicy.CLASS

- A anotação é lida pelo compilador mas não pode ser lida em tempo de execução

* RetentionPolicy.SOURCE

- A anotação é ignorada pelo compilador

```java
@Retention(RetentionPolicy.RUNTIME)
public @interface ClassInfo {
	String autor();
	String data();
	int versao() default 1;
}
```

## @Target

* Indica em qual elemento a annotation pode ser aplicada

* Tipos

* ElementType.TYPE

- Classe, interface ou enum

* ElementType.METHOD

- Métodos

* ElementType.FIELD

- Atributos

* etc.

```java
@Target(ElementType.TYPE)
public @interface ClassInfo {
	String autor();
	String data();
	int versao() default 1;
}
```

## @Override

* Indica que um método sobrescreve outro

* É opcional, mas quando utilizada gera erro de compilação se o método anotado não estiver sobrescrevendo um método da superclasse

```java
@Override
public String toString() { //Se o método toString() não existir na superclasse, gera erro de compilação
	return "...";
}
```

## @SuppressWarnings

* Utilizada para remover mensagens de warning do código

* O seu uso mais comum é para remover mensagens de conversão de tipos quando o generics é utilizado

* Pode anotar classes, métodos e código

```java
List<String> l = new ArrayList();
//Warning: “The expression of type ArrayList needs unchecked conversion to conform to List<String>”

@SuppressWarnings("unchecked")
List<String> l = new ArrayList();
//O warning desaparece
```

# Reflection API

*  A Reflection API do Java permite que as classes conheçam sobre suas estruturas internas

* O ponto de entrada é um objeto Class, que guarda informações sobre uma classe

```java
Class c = String.class;
Class c = Class.forName("java.lang.String");
Class<String> c = String.class;
Class<String> c = (Class<String>) Class.forName("java.lang.String");
```

## O objeto Class

* O objeto Class pode representar também outros elementos que não sejam classes, como interfaces e enums

* A partir do objeto Class, é possível descobrir quais são os atributos, construtores e métodos

| **Método**         | **Descrição**                    |
|--------------------|----------------------------------|
| getFields()        | Retorna um array de atributos    |
| getField()         | Retorna um atributo específico   |
| getConstructors()  | Retorna um array de construtores |
| getConstructor()   | Retorna um construtor específico |
| getMethods()       | Retorna um array de métodos      |
| getMethod()        | Retorna um método específico     |

## Instanciando objetos

* Com a Reflection API, é possível instanciarmos objetos quando conhecemos apenas o nome da classe

```java
Class c = Class.forName("dev.joaonogueira.MyClass");
MyClass m = (MyClass) c.getDeclaredConstructor().newInstance();
```

## Invocando métodos

* Outro uso comum da Reflection API é para invocar métodos

```java
Class c = Class.forName("dev.joaonogueira.MyClass");
MyClass o = (MyClass) c.getDeclaredConstructor().newInstance();

Method m = c.getMethod("imprimir", String.class);//Procura o método imprimir() da classe, que recebe uma String como parâmetro
m.invoke(o, "algum texto");//Invoca o método m no objeto o, passando o parâmetro para o método
```
