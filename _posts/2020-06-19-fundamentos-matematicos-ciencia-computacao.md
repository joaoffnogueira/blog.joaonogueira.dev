---
title: Anotações sobre Fundamentos Matemáticos para a Ciência da Computação
author: João F. F. Nogueira
date: 2020-06-19 08:00:00 -0300
categories: [Estudos-faculdade]
tags: [matemática]
toc: true
math: true
---

​Baseado em Fundamentos Matemáticos para a Ciência da Computação (Gersting).
# 1 Lógica Formal

## 1.1 Sentenças, Representação Simbólica e Tautologias

Tecnicamente, uma sentença (ou proposição) é uma frase que pode ser apenas verdadeira ou falsa.

### Conectivos e Valores-Verdade

Para enriquecermos nossas conversas não nos limitamos ao uso de simples sentenças. Ao contrário, as combinamos com o uso de conectivos a fim de criarmos sentenças compostas, cujo valor-verdade depende dos valores-verdade de cada sentença que o compõe e dos conectivos usados.

Técnicas

* Construção de tabelas-verdade para wffs compostas

* Reconhecimento de tautologias e contradições

Principais Conceitos

As wffs são representações simbólicas de sentenças.

Os valores-verdade de wffs compostas dependem dos valores-verdade de seus componentes e do tipo dos

conectivos usados.

### 1.2 Quantificadores, Predicados e Validade

**Definição: Interpretação**

Uma interpretação de uma expressão envolvendo predicados consiste no seguinte:

a. um conjunto de objetos chamados o domínio da interpretação, que deve conter pelo menos um elemento;

b. a atribuição de uma propriedade dos objetos do domínio para cada predicado na expressão; e

c. a atribuição de um objeto particular no domínio a cada símbolo constante na expressão.

**Validade:**

Wffs Proposicionais

 l. Verdadeira ou falsa, de acordo com os valores atribuídos aos símbolos proposicionais;

 2. Tautologia - verdadeira para todas as atribuições de valores-verdade;

 3. Algoritmo (tabela-verdade) para determinar se uma wff é ou não uma tautologia.

Wffs Predicativas

 1. Verdadeira, falsa ou sem valor-verdade, dependendo da interpretação;

 2. Wff válida - verdadeira para todas as interpretações;

 3. Não há algoritmo para determinar se uma é ou não válida.

Técnicas

* Determinação do valor-verdade de uma wff predicativa em uma dada interpretação.

* Tradução de sentenças na língua portuguesa para wffs e vice-versa.

* Reconhecimento de uma wff válida e a justificação.

* Reconhecimento de wffs não-válidas e a construção de uma interpretação na qual ela seja falsa ou não tenha valor-verdade

Ideias Principais

O valor-verdade de wffs predicativas depende da interpretação considerada.

Wffs válidas são wffs predicativas que são verdadeiras para qualquer interpretação e, portanto, a validade é uma propriedade inerente à forma da wff propriamente dita.

### 1.3 Lógica Proposicional

Argumentos Válidos

Em português, um argumento é normalmente apresentado como uma série de sentenças que podem ser simbolizadas por $P_{1},P_{2},...,P_{n}$ seguidas de uma conclusão Q. O argumento é um argumento válido se a conclusão pode ser deduzida, do ponto de vista da lógica, da conjunção $P_{1}\wedge P_{2}\wedge ...\wedge P_{n}$ - em outras palavras, se $P_{1}\wedge P_{2}\wedge ...\wedge P_{n}\to Q$ for um teorema.