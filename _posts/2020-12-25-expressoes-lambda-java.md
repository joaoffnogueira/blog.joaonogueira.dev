---
title: Expressões Lambda em Java
author: João F. F. Nogueira
date: 2020-12-25 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# Expressões Lambda

* Maior inovação da versão 8 do Java

* O nome lambda vem do conceito matemático de cálculo lambda

* Expressões lambda trazem o Java mais próximo do paradigma de programação funcional

* Uma expressão lambda pode ser considerada como um objeto

– Pode ser referenciada por uma variável

– Pode ser passada como parâmetro para métodos e utilizada como retorno

* Em Java, uma expressão lambda é utilizada em substituição a uma inner class anônima

```java
Runnable r = new Runnable() {
	@Override
	public void run() { //Inner class anônima
		System.out.println("ABC");
	}
};
new Thread(r).start();

Runnable r = () -> System.out.println("ABC");//Expressão lambda
new Thread(r).start();

new Thread(() -> System.out.println("ABC")).start();//Expressão lambda
```

Resultado: código mais simples e intuitivo

* Uma expressão lambda é representada da seguinte forma:

```
(Parâmetros) -> { Corpo } //operador arrow
```

Exemplos de sintaxe:

![Exemplos de sintaxe](/posts/2020-12-25-1.png){: width="100" height="100" }

# Interfaces funcionais

* Uma interface funcional tem duas características

1. É uma interface

2. Possui apenas 1 método

* Uma expressão lambda pode ser atribuída a uma variável de uma interface funcional

```java
Runnable r = () -> System.out.println("ABC");
Comparator<String> c = (s1, s2) -> s1.compareTo(s2);
Comparable<String> c = s -> 0;
ActionListener l = e -> System.out.println("123");
```

Interfaces que já pertenciam ao Java agora passam a ser interfaces funcionais

# @FunctionalInterface

* Esta annotation define uma interface como interface funcional

```java
@FunctionalInterface
public interface Generator {
	public String generate();
}
```

* Seu uso não é obrigatório

* Se @FunctionalInterface for utilizada, o compilador checa se a interface define apenas 1 método

# Interface funcional: Predicate<T>

```java
@FunctionalInterface
public interface Predicate<T> {
	boolean test(T t);
}

Predicate<String> p = s -> s.length() > 5; //true se o tamanho da String for maior do que 5
```

* O tipo T define o tipo a ser testado

* Retorna um boolean

# Interface funcional: Consumer<T>

```java
@FunctionalInterface
public interface Consumer<T> {
void accept(T t);
}

Consumer<Integer> c = i -> System.out.println(i);//Processa i escrevendo o seu valor no console
```

* O tipo T define o tipo a ser processado

* Não retorna informação (void)

# Interface funcional: Function<T, R>

```java
@FunctionalInterface
public interface Function<T, R> {
	R apply(T t);
}

Function<String, Integer> f = s -> Integer.parseInt(s);//Transforma uma String em um int
```

* O tipo T define o tipo de origem

* O tipo R define o tipo de destino a ser retornado

# Novas funcionalidades em coleções

* A Collections API ganhou novas funcionalidades para aproveitar o uso de expressões lambda

```java
List<Integer> l = new ArrayList<>();
l.add(1);
l.add(2);
l.add(3);

l.forEach(item -> System.out.println(item));//Consumer<T>
l.removeIf(item -> item % 2 == 0);//Predicate<T>
```

# Referências a métodos

* Permite converter métodos já existentes em expressões lambda

```java
l.forEach(item -> System.out.println(item));

l.forEach(System.out::println);//Operador double colon (::)
```

Os parâmetros da expressão lambda são repassados para o método

# Closures

* Expressões lambda têm a capacidade de acessar variáveis definidas externamente

* Este recurso é denominado closure

```java
int mult = 2;//Variável definida fora da expressão lambda
Function<Integer, Integer> f = (x -> x * mult);

System.out.println(f.apply(5));
```

Variáveis externas acessadas por expressões lambda são implicitamente definidas como final

*  No caso da variável externa ser um atributo de classe, o final implícito não se aplica

* O valor considerado é o do momento da execução

```java
public class MyClass {
	private int mult = 2;

	public void executar() {
		Function<Integer, Integer> f = (x -> x * mult);
		mult = 5;
		System.out.println(f.apply(5));//Imprime o valor 25
	}
}
```
