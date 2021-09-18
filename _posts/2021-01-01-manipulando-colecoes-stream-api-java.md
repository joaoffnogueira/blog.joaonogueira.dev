---
title: Manipulando Coleções com a Stream API em Java
author: João F. F. Nogueira
date: 2021-01-01 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# O que é a Stream API

* API que permite combinar operações

– Usada principalmente em coleções do Java

* Introduzida no Java 8

* Aproveita o uso de expressões lambda

* Funciona bem para coleções pequenas e também para coleções muito grandes

– Usa a abordagem de lazy evaluation

* A Stream API permite encadear as operações (pipeline)

```java
List<Integer> newList = list.stream()
	.sorted()
	.filter(e -> e >= 2 && e <= 8)
	.map(e -> e * e)
	.collect(Collectors.toList());
```

# O tipo Stream<T>

* As coleções List e Set possuem o método stream()

```java
Stream<Integer> stream = list.stream();
```

* O objeto Stream<T> é a porta de entrada para a Stream API

* O tipo parametrizado T depende do tipo da coleção

* Para arrays, o código muda

```java
int[] array = new int[10];
Stream<int[]> stream = Stream.of(array);
```

# Operações

* A Stream API possui uma série de operações para manipulação de dados

- 2 tipos

* Intermediárias

- Retornam um novo objeto Stream<T>

- Possibilitam o pipeline

- Ex: sorted(), limit(), filter(), map()

* Terminais

- Geram um resultado final (redução)

- Finalizam o uso da stream

- Ex: collect(), reduce(), count(), max()

## sorted()

* Ordena os elementos da coleção

* Permite fornecer ou não um Comparator<T>

* Operação intermediária

```java
stream.sorted((e1, e2) -> e1.getNome().compareTo(e2.getNome())) //Expressão lambda que substitui uma instância de Comparator<T>
```

## limit()

* Define um tamanho máximo para a coleção

* Os elementos que excedem o limite fornecido são removidos

* Operação intermediária

```java
Só os 10 primeiros elementos são mantidos
```

## filter()

* Filtra os resultados de acordo com um critério

* Recebe um parâmetro Predicate<T>

* Operação intermediária

```java
stream.filter(e -> e > 10);//Expressão lambda que determina a filtragem de elementos maiores que 10
```

## distinct()

* Remove elementos duplicados

* Operação intermediária

```java
stream.distinct();
```

## map()

* Mapeia um elemento em outro elemento (transformação)

* Recebe um parâmetro Function<T, R>

* Operação intermediária

```java
stream.map(e -> e + 2);//Expressão lambda que incrementa 2 unidades a cada elemento
```

* Existem também mapeamentos especializados

– mapToInt() −> IntStream

– mapToDouble() −> DoubleStream

– mapToLong −> LongStream

## collect()

* Finaliza o pipeline, gerando um resultado

* Operação terminal

* A classe Collectors tem métodos estáticos que auxiliam nesta operação

* Exemplos:

```java
stream.collect(Collectors.toList())// List<T>
stream.collect(Collectors.toSet())// Set<T>
stream.collect(Collectors.counting())// Long
stream.collect(Collectors.summingInt(e -> e.getIdade()))// Integer
```

## count()

* Faz a contagem de elementos

* Operação terminal

```java
long c = stream.count();
```

# Referenciando construtores

* Além de referenciar métodos, é possível também referenciar construtores

```java
public class Pessoa {
	private String nome;
	public Pessoa(String nome) {
		this.nome = nome;
	}
}

List<String> nomes = Arrays.asList("José", "Maria", "Pedro");
List<Pessoa> pessoas = nomes.stream()
	.map(Pessoa::new) //Equivale a: .map(e -> new Pessoa(e))
	.collect(Collectors.toList());
```

# Streams paralelas

* Uma stream paralela pode ser processada simultaneamente por vários núcleos de processamento

```java
List<Integer> list = list.parallelStream()
	.sorted()
	.map(e -> e * e)
	.collect(Collectors.toList());
```

*  Para que o resultado seja consistente, as operações intermediárias precisam ser independentes
