---
title: Java Insider
author: João F. F. Nogueira
date: 2021-11-26 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Do webinar da Softblue

# Inside the Stack & Heap

- A Stack e o Heap são áreas alocadas de memória RAM

![Stack & Heap](/posts/2021-11-26-1.png){: width="100" height="100" }

## Passagem de Parâmetro

- No Java, a passagem de parâmetros é sempre feita por cópia!
  
– Nunca por referência

– O conteúdo é sempre copiado

## Garbage Collector (Coletor de Lixo)

- Serviço da JVM

- A JVM decide quando ele vai executar

- Libera a área de memória do Heap que não é mais acessível

![Garbage Collector](/posts/2021-11-26-2.png){: width="100" height="100" }

# Inside the String Pool

## Strings

- Armazenam conjuntos de caracteres

- String é uma classe

– Objetos String são armazenados no Heap

```java
String s = new String(“java”);//Praticamente não se usa
String s = “java”;//Esta sintaxe só existe em Strings!
```

- Pool (Área do Heap)

## A Imutabilidade das Strings

- Strings no pool são compartilhadas

- E se a String mudasse? Confusão total!

- Solução:

– Strings são imutáveis!

– A classe String é definida como final

- Para mudar uma String, só criando outra

- Para evitar a criação desnecessária de Strings (e sobrecarregar o GC), uma alternativa é usar a classe StringBuilder

# Inside the Collections API

![Collections API](/posts/2021-11-26-3.png){: width="100" height="100" }

## Listas

Interface List

Elementos ordenados

Permitem elementos duplicados

Podem aumentar ou diminuir sob demanda

## ArrayList

Usa um array pra armazenar os elementos

Novos arrays são criados para acomodar novos elementos

* Inserção

– Insere rapidamente na posição corrente do array

– Se for preciso redimensionar o array, demora um pouco mais

– Para inserção que não seja no final, é preciso mexer na estrutura do array

* Exclusão

– Todos os elementos são movidos para a esquerda para não deixar“buraco” no array

* Busca

– A busca por índice é rápida, pois vai direto na posição do array

– Na busca por objeto, é preciso iterar sobre cada elemento

## LinkedList

Usa uma lista duplamente encadeada para armazenar os elementos

* Inserção

– A inserção é rápida e pode ser feita no começo, no fim ou no meio da lista com a mesma performance

– Implica na correção das referências de elementos vizinhos, feita rapidamente

* Exclusão

– Implica na correção das referências de elementos vizinhos, feita rapidamente

* Busca

– Tanto na busca por índice como na busca pelo objeto é preciso iterar sobre cada um dos elementos da lista

## Vector

* Foi substituído pelo ArrayList

* O problema do Vector são suas operações sincronizadas (synchronized)

– Diminui a performance da coleção

* Se você deseja usar uma coleção com operações sincronizadas, use os métodos synchronized*() da classe Collections

## Conjuntos

Interface Set

Conjuntos como na matemática

Não permitem elementos duplicados

A ordem dos elementos pode não ser a mesma da inserção

## HashSet

Os elementos são organizados na memória usando um algoritmo de hashing (espalhamento)

* Inserção

– É feito o cálculo do hash do elemento, que é adicionado no local correto dentro da tabela hash

* Exclusão

– É eficiente, pois a busca é feita rapidamente na tabela hash

* Busca

– A busca feita por objeto é muito eficiente, pois o conhecimento do local na tabela hash onde o elemento está concentra a busca

### Métodos equals() e hashCode()

O algoritmo de hashing deve retornar valores bem distribuídos

hashCode() - Encontra o índice
equals() - Encontra o elemento dentro do índice

## LinkedHashSet

* Funcionamento semelhante ao do HashSet

* A diferença é que o LinkedHashSet usa uma lista duplamente encadeada para guardar a ordem de inserção

– Isso garante que a ordem de iteração será a mesma de inserção

## TreeSet

* Funcionamento semelhante ao do HashSet

* A diferença é que o TreeSet classifica os elementos na hora da inserção

* Ao iterar sobre os elementos, a ordem será a ordem de classificação

* Existe um passo a mais na inserção, que é a execução do algoritmo de ordenação Red/Black Tree (árvore rubro-negra)

Comparator e Comparable - Interfaces usadas para determinar o critério de ordenação em elementos de coleções

Coleções com “Hash” no nome: usam equals() e hashCode()
Coleções com “Tree” no nome: usam as interfaces Comparable ou Comparator

## Mapas

Interface Map

Mapeamento de uma chave a um valor

Chaves e valores podem ser de qualquer tipo

Existe uma equivalência com as implementações dos conjuntos

As regras das implementações de conjuntos são aplicadas nas chaves do mapa

HashMap -> HashSet
LinkedHashMap -> LinkedHashSet
TreeMap -> TreeSet

As implementações dos conjuntos usam as implementações dos mapas no código!

## Hashtable

* Foi substituída pelo HashMap

* O problema da Hashtable são suas operações sincronizadas (synchronized)

– Diminui a performance da coleção

* Se você deseja usar uma coleção com operações sincronizadas, use os métodos synchronized*() da classe Collections
