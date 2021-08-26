---
title: Anotações sobre Raciocínio lógico e lógica quantitativa
author: João F. F. Nogueira
date: 2021-08-13 11:15:00 -0300
categories: [Português, Estudos]
tags: [logic]
toc: true
math: true
---

Baseado no Livro: LEITE, A. E.; CASTANHEIRA, N. P. Raciocínio lógico e lógica quantitativa. Curitiba: InterSaberes, 2017.

## Capítulo 1 - Lógica matemática

Lógica clássica - intuitiva e não matemática. Diferente, portanto, da Lógica matemática.

Proposição: conjunto de palavras ou símbolos que exprime um pensamento de sentido completo, mas que assume um de dois valores lógicos (V ou F). Sentenças declarativas. Pode ser simples ou composta.

Princípio da identidade: todas as coisas são idênticas a si próprias.

Princípio da não contradição: uma proposição não pode ser verdadeira e falsa ao mesmo tempo.

Princípio do terceiro excluído: toda proposição ou é verdadeira, ou é falsa, ou seja, não há um terceiro valor.

Três formas de raciocínio: dedução para chegar a conclusão, indução para determinar a regra e abdução para determinar a premissa.

| Não    | E        | Ou     | ou... ou... | se... então... | se e somente se   |
| ------ | -------- | ------ | ----------- | -------------- | ----------------- |
| $\sim$ | $\wedge$ | $\vee$ | $\veebar$   | $\to$          | $\leftrightarrow$ |

Conectivos das operações: negação, conjunção, disjunção, disjunção exclusiva, condicional ou implicação, bicondicional ou dupla implicação.

A conjunção também é conhecida como produto lógico de preposições. A disjunção também é conhecida como soma lógica de preposições.

O valor lógico de uma proposição simples é indicado por V(p) e de uma proposição composta por V(P).

## Capítulo 2 - Tabela Verdade

Uma tabela-verdade é um dispositivo prático que mostra todos os valores lógicos de uma proposição.

O número de linhas de uma tabela-verdade é dado por 2n, onde n é o número de proposições simples que compõem a proposição composta.

Tabela-verdade do conectivo se... então($\to$)

| p   | q   | $p\to q$ |
|:---:|:---:|:--------:|
| V   | V   | V        |
| V   | F   | F        |
| F   | V   | V        |
| F   | F   | V        |

A proposição condicional, também chamada implicação, é falsa, por definição, quando p for verdadeira e q for falsa. Nos demais casos, ela é verdadeira, como mostrado na tabela-verdade.

Tabela-verdade do conectivo se e somente se ($\leftrightarrow$)

| p   | q   | $p\leftrightarrow q$ |
|:---:|:---:|:--------------------:|
| V   | V   | V                    |
| V   | F   | F                    |
| F   | V   | F                    |
| F   | F   | V                    |

A tabela-verdade nos mostra que a proposição bicondicional, também chamada de dupla implicação, é verdadeira somente quando A e B têm o mesmo valor lógico.

Duas proposições são equivalentes quando suas tabelas-verdade forem iguais. A equivalência é representada por $\Leftrightarrow$. Não confundir com $\leftrightarrow$ (bicondicional).

## Capítulo 3 - Tautologia, contradição e contingência

Quando uma proposição composta é sempre verdadeira, temos uma **tautologia**. Quando é sempre falsa, trata-se de uma **contradição**. Caso não seja nem uma tautologia, nem uma contradição, estamos diante de uma **contingência**.

## Capítulo 4 - Teoria dos conjuntos

Conjunto é todo o agrupamento de elementos com características semelhantes.

A notação de um conjunto é feita por uma letra maiúscula. O elementos são representados entre vírgulas (ponto e vírgula no caso de números não inteiros) dentro de chaves, ou por uma propriedade em linguagem matemática, ou por diagramas de Euler/Venn.

Quando falamos em pertinência, estamos nos referindo a pertencimento; ou seja, se afirmamos que determinado elemento faz parte de um conjunto, então ele pertence ao conjunto. $\in \notin $

Já a noção de inclusão refere-se a conjuntos diferentes que estão relacionados. Da relação de inclusão, surge a noção de subconjunto. Se um conjunto A possui n elementos, então esse conjunto tem 2n subconjuntos.

Representação dos símbolos:

| Símbolos      | Significado         |
|:-------------:|:-------------------:|
| $\subset$     | Está contido em     |
| $\not\subset$ | Não está contido em |
| $\supset$     | Contém              |
| $\not\supset$ | Não contém          |

Dois ou mais conjuntos são iguais quando têm exatamente os mesmos elementos. Um conjuntos unitário é aquele que contém um único elemento. Um conjunto vazio é aquele que não possui elementos, representado por {} ou $\emptyset$.

Consideremos um conjunto S. O conjunto formado por todos os subconjuntos dele é o conjunto das partes de S; nós o representamos por P(S). Importante lembrar que o conjunto vazio é um subconjunto de qualquer conjunto.

A união ou reunião de dois ou mais conjuntos é representada pelo símbolo $\cup$.

| a. $A \cup A=A$                          | Idempotência                 |
| ---------------------------------------- | ---------------------------- |
| b. $A \cup B=B\cup A$                    | Comutativa                   |
| c. $A \cup \emptyset=A$                  | Elemento neutro para a união |
| d. Se $A \subset B=A$, então $A\cup B=B$ | Inclusão relacionada         |
| e. $(A \cup B)\cup C=A\cup(B\cup C)$     | Associativa                  |

A interseção de dois ou mais conjuntos é o conjunto cujos elementos pertencem simultaneamente a cada um deles, representado por $\cap$.

| a. $A\cap A = A$                       | Idempotência                    |
| -------------------------------------- | ------------------------------- |
| b. $A\cap B =B\cap A$                  | Comutativa                      |
| c. $A\cap \emptyset = \emptyset$       | Elemento nulo para a interseção |
| d. Se $A \subset B$, então $A\cap B=A$ | Inclusão relacionada            |
| e. $(A \cap B)\cap C=A\cap(B\cap C)$   | Associativa                     |

Importante destacar que, quando interseção de dois conjuntos quaisquer é igual a um conjunto vazio, ou seja, não há qualquer elemento comum a eles, é dado o nome de conjuntos disjuntos.

Quando temos dois conjuntos, A e B, a diferença entre eles é representada por A - B, em que os elementos pertencentes ao conjunto A não fazem parte do conjunto B.

| a. $A-A=\emptyset$                         | Não verifica a idempotência |
| ------------------------------------------ | --------------------------- |
| b. $A-\emptyset=A$                         |                             |
| c. $\emptyset -A=f$                        |                             |
| d. Se $A\subset B$, então $A-B=\emptyset$  |                             |
| e. $A-B\neq B-A$                           | Não é comutativa            |
| f. $(A-B)-C\neq A-(B-C)$                   | Não é associativa           |
| g. Se $A\cap B=0$, então $A-B=A$ e $B-A=B$ |                             |

A diferença simétrica entre dois conjuntos A e B é o conjunto dos elementos que pertencem à união de A e B, mas não pertencem à interseção deles. É representada por $\Delta$.

| a. $A=\emptyset$ se e somente se $B=A\Delta B$  |                             |
| ----------------------------------------------- | --------------------------- |
| b. $A\Delta A=\emptyset$                        | Não verifica a idempotência |
| c. $A\Delta B=B\Delta A$                        | Comutativa                  |
| d. $A\cap (B\Delta C)=(A\cap B)\Delta(A\cap C)$ | Distributiva                |
| e. $(A\Delta B)\Delta C=A\Delta(B\Delta C)$     | Associativa                 |

Dados dois conjuntos A e B tais que $B\subset A$, chamamos de complementar de B em A o conjunto $\overline{B}$ constituído pelos elementos do conjunto A que não pertencem ao conjunto B, em outras palavras, $\overline{B}=A-B$.

É verdadeira a propriedade $\overline{\overline{A}}=A$ (idempotência), ou seja, o complementar do complementar de um conjunto A é o próprio conjunto A.

Leis de Augustus de Morgan:

1. O complementar da reunião de dois conjuntos A e B é a interseção dos complementares desses conjuntos $(\overline{A\cup B})=\overline{A}\cap\overline{B}$.

2\. O complementar da reunião de uma coleção finita de conjuntos é a interseção dos complementares desses conjuntos.

3. O complementar da interseção de dois conjuntos A e B é a reunião dos complementares desses conjuntos $(\overline{A\cap B})=\overline{A}\cup\overline{B}$.

4\. O complementar da interseção de uma coleção finita de conjuntos é a reunião dos complementares desses conjuntos.

Dados os conjuntos A, constituído por x elementos, e B por y elementos, chamamos produto cartesiano A x B o conjunto constituído pelos pares ordenados (x , y).

## Capítulo 5 - Operações lógicas com sentenças abertas

Resumidamente, dizemos que p(x) é uma sentença aberta em determinado conjunto se e somente se p(x) passar a uma proposição ao se substituir a variável x por um elemento desse conjunto. Essa proposição poderá ser falsa ou verdadeira. Chamemos V(p) o conjunto-verdade de uma sentença aberta.

a. Negação 

Dada a sentença aberta p, Sua negação é $\sim p$. O conjunto-verdade de $\sim p$ em A é $V(\sim p) = C(A)$ $V(p)=C(A)\{x\in A |p(x)\}$, em que C(A) é o complemento de A. 

b. Conjunção 

Dadas duas sentenças abertas p(x) e q(x) em um conjunto A, $p(x)\wedge q(x)$ será verdadeira se 
houver um elemento $a\in A$ que satisfaça ao mesmo tempo p(x) e q(x). Em outras palavras, o conjunto-verdade da sentença aberta $p(x)\wedge q(x)$ em A será a interseção dos conjuntos-verdade V(p) e V(q), que representamos por: $V(p\wedge q)=V(p)\cap V(q)=\{x\subset A|p(x)\}\cap \{x\in A|q(x)\}$. 

c. Disjunção 

Dadas duas sentenças abertas p(x) e q(x) em um conjunto A, $p(x)\vee q(x)$ serão verdadeiras se houver um elemento $x\in A$ que satisfaça pelo menos uma das sentenças abertas p(x) e q(x). Em outras palavras, o conjunto-verdade da sentença aberta $p(x)\vee q(x)$ em A será a união dos conjuntos-verdade V(p) e V(q), que representamos por: 

d. Condicional ou implicação 

Dadas duas sentenças abertas p(x) e q(x) em um conjunto A, $p(x)\to q(x)$ terá como conjunto-verdade = $V(p\to q)=V(\sim p)\cup V(q)=C(A) V(p)\cup V(q)$. Dessa definição, deduzimos que o conjunto-verdade $V(p\to q)$ é a união dos conjuntos-verdade das sentenças abertas $\sim p(x)$ e q(x). Portanto, $V(p\to q)=\{x\in A|\sim p(x)\}\cup \{x\in A|q(x)\}$. 

e. Bicondicional ou dupla implicação 

Dadas duas sentenças abertas p(x) e q(x) em um conjunto A, $p(x)\leftrightarrow  q(x)$, temos como conjunto-verdade $V(p\leftrightarrow q)=V(p\to q)\cap V(q\to p)=[V(\sim p)\cup V(q)]\cap[V(\sim q)\cup V(p)]$. Dessa definição, deduzimos que o conjunto-verdade é a interseção dos conjuntos-verdade das sentenças abertas em A,$p(x)\to q(x)$ e $q(x)\to p(x)$; ou seja $V(p\leftrightarrow q)=[\{x\in A|\sim p(x)\}\cup \{x\in A|q(x)\}]\cap[\{x\in A|\sim q(x)\}\cup \{x\in A|p(x)\}]$.

Quantificadores são utilizados para transformar sentenças abertas em proposições. $\forall$ Qualquer que seja ou para todo (universal); $\exists$ existe (existencial).

## Capítulo 6 - Implicações lógicas

Dizemos que uma proposição p implica logicamente uma proposição q quando em suas tabelas-verdade não ocorrer V e F numa mesma linha, nessa ordem. Representamos a relação de implicação lógica pelo símbolo $\Rightarrow$.

Não podemos confundir essa representação de implicação ($\Rightarrow$) com a do conectivo "se... então..." ($\to$). O símbolo $\to$ representa uma operação lógica entre as proposições simples p e q, que resulta na proposição composta $p\to q$. Então, podemos ter como resultado o valor lógico V ou o valor lógico F. Já o símbolo $\Rightarrow$ representa a não ocorrência de V e F na mesma linha, na tabela-verdade de $p\to q$, ou seja, $p\to q$ é uma tautologia.

Uma sentença aberta implica outra sentença aberta quando o conjunto-verdade da primeira está contido no conjunto-verdade da segunda. A recíproca também é verdadeira, ou seja, se a segunda sentença aberta implica a primeira sentença aberta, o conjunto-verdade da segunda está contido no conjunto-verdade da primeira.

Propriedades das implicações:

1ª) Uma implicação $p\Rightarrow q$ só é verdadeira se a condicional $p\rightarrow q$ for uma tautologia.

2ª) A propriedade reflexiva e dada por $p\Rightarrow p$.

3ª) A propriedade transitiva é dada pela relação: se $p\Rightarrow q$ e se $q\Rightarrow r$, então $p\Rightarrow r$. A transitividade se estende a qualquer quantidade de proposições.

4ª) A propriedade antissimétrica é dada pela relação: se $p\Rightarrow q$ e se $q\Rightarrow p$, então $p\iff r$. O símbolo $\iff$ representa equivalência lógica.

Entre implicações, há as seguintes relações:

1ª) $p\Rightarrow q$ e $q\Rightarrow p$ (recíprocas). Devemos observar que duas proposições recíprocas não são necessariamente equivalentes, pois uma pode ser verdadeira, e a outra, não.

2ª) $p\Rightarrow q$ e $\sim p\Rightarrow\sim q$ (inversas). Novamente é preciso observar que duas proposições inversas não são necessariamente equivalentes, pois uma pode ser verdadeira, e a outra, não.

3ª) $p\Rightarrow q$ e $\sim q\Rightarrow\sim p$ (contrapositivas). Neste caso, duas proposições contrapositivas são logicamente equivalentes, pois, se uma é verdadeira, a outra também será.

Temos as seguintes implicações básicas, também conhecidas como *regras de inferência*, pois são usadas para executar os passos de uma demonstração ou de uma dedução:

1. $p\Rightarrow p\vee q$ (adição)
2. $q\Rightarrow p\vee q$ (adição)
3. $p\wedge q\Rightarrow p$ (conjunção)
4. $p\wedge q\Rightarrow q$ (conjunção)
5. $q\wedge p\Rightarrow p$ (conjunção)
6. $q\wedge p\Rightarrow q$ (conjunção)
7. $p\wedge q\Rightarrow p$ (simplificação)
8. $p\wedge q\Rightarrow q$ (simplificação)
9. $(p\vee q)\wedge(p\vee\sim q)\Rightarrow p$ (simplificação disjuntiva)
10. $p\rightarrow q\Rightarrow p\rightarrow(p\wedge q)$ (absorção)
11. $(p\rightarrow q)\wedge p\Rightarrow q$ (regra *Modus Ponens*)
12. $(p\rightarrow q)\wedge\sim q\Rightarrow\sim p$ (regra *Modus Tollens*)
13. $(p\vee q)\wedge\sim p\Rightarrow q$ (silogismo disjuntivo)
14. $(p\vee q)\wedge\sim q\Rightarrow p$ (silogismo disjuntivo)
15. $(p\rightarrow q)\wedge(q\rightarrow r)\Rightarrow p\rightarrow r$ (silogismo hipotético)
16. $[p\rightarrow(q\vee r)]\wedge\sim q\Rightarrow p\rightarrow r$ (eliminação)
17. $[(p\rightarrow q)\wedge(r\rightarrow s)\wedge(p\vee r)]\Rightarrow q\vee s$ (dilema construtivo)
18. $[(p\rightarrow q)\wedge(r\rightarrow s)\wedge(\sim p\vee\sim s)]\Rightarrow\sim p\vee\sim r$ (dilema destrutivo)
19. $p\rightarrow q\Rightarrow p\rightarrow q\vee r$ (regra da atenuação)
20. $\sim p\rightarrow p\Rightarrow p$ (regra da retorsão)
21. $(p\rightarrow r)\wedge(q\rightarrow r)\Rightarrow(p\vee q)\rightarrow r$ (prova por casos)

Teorema contrarecíproco:

A proposição $p(x)\Rightarrow q(x)$ é verdadeira se e somente se $\sim q(x)\Rightarrow\sim p(x)$ também for verdadeira. Há, portanto, equivalência entre as implicações. Observe, entretanto, que não há equivalência entre as proposições $p\rightarrow q$ e $\sim p\rightarrow\sim q$.

## Capítulo 7 - Equivalências lógicas

Proposições são equivalentes quando suas tabelas-verdade forem iguais, fenômeno representado pelo símbolo $\Leftrightarrow$. Não podemos confundir a equivalência ($\Leftrightarrow$) com o conectivo "se, e somente se" ($\leftrightarrow$).

a. Se duas proposições são ambas tautológicas, então são proposições equivalentes.

b. Se duas proposições são ambas contradições, então são proposições equivalentes.

c. p$\Leftrightarrow$p (reflexiva).

d. Se $p\Leftrightarrow q$ então $q\Leftrightarrow p$ (simétrica).

e. Se $p\Leftrightarrow q$ e $q\Leftrightarrow r$, então $p\Leftrightarrow r$ (transitiva).

Equivalências básicas:

1. $p\wedge p\iff p$ (idempotentes) 
2. $p\vee p\iff p$ (idempotentes) 
3. $\sim\sim p\iff p$ (dupla negação) 
4. $p\wedge q\iff q\wedge p$ (comutativas) 
5. $p\vee q\iff q\vee p$ (comutativas) 
6. $p\wedge (q\wedge r)\iff(p\wedge q)\wedge r$ (associativa) 
7. $p\vee (q\vee r)\iff(p\vee q)\vee r$ (associativa) 
8. $p\leftrightarrow q\iff q\leftrightarrow p$ (comutativa) 
9. $p\leftrightarrow q\iff (p\rightarrow q)\wedge (q\rightarrow p)$ (bicondicional) 
10. $p\leftrightarrow q\iff (p\wedge q)\vee (\sim p\wedge\sim q)$ (bicondicional) 
11. $\sim(p\wedge q)\iff\sim p\vee\sim q$ (lei de De Morgan) 
12. $\sim(p\vee q)\iff\sim p\wedge\sim q$ (lei de De Morgan) 
13. $p\wedge (p\vee q)\iff p$ (absorção) 
14. $p\vee (p\wedge q)\iff p$ (absorção) 
15. $p\rightarrow q\iff p\rightarrow (p\wedge q)$ (absorção) 
16. $p\wedge (q\vee r)\iff (p\wedge q)\vee (p\wedge r)$ (distributiva) 
17. $p\vee (q\wedge r)\iff (p\vee q)\wedge (p\vee r)$ (distributiva) 
18. $(p\rightarrow q)\iff (\sim q\rightarrow\sim p)$ (contrapositiva) 
19. $(q\rightarrow p)\iff (\sim p\rightarrow\sim q)$ (recíproca da contrapositiva) 
20. $(p\rightarrow q)\iff\sim p\vee q$ (negação da condicional) 
21. $\sim(p\rightarrow q)\iff\sim(\sim p\vee q)\iff p\wedge\sim q$ (negação da condicional) 
22. $\sim(p\leftrightarrow q)\iff p\vee q$ (negação da bicondicional) 
23. $p\wedge q\rightarrow r\iff p\rightarrow(q\rightarrow r)$ (exportação-importação) 
24. $\sim p\rightarrow p\iff p$ (Regra de Clavius)

Equivalências entre implicações:

a. $p\Rightarrow q\Leftrightarrow\sim q\Rightarrow \sim p$

b. $p\Rightarrow q\Leftrightarrow\sim (p\wedge\sim q)$

c. $p\Rightarrow q\Leftrightarrow\sim p\vee q$

## Capítulo 8 - Argumentos e silogismos

Um argumento é uma afirmação de que, tendo um grupo finito de proposições com p = 1, 2, 3, ..., n teremos como consequência uma proposição final que chamaremos de q. As proposições p, são premissas do argumento, e a proposição final é a conclusão. Um argumento que tenha as premissas e a conclusão q, é representado por:

$p_1,p_2,p_3,...,p_n\vdash q$

O silogismo é todo argumento constituído por duas premissas que resultam numa conclusão.

Um sofisma ou falácia é um argumento que não é válido, ou seja, um falso raciocínio lógico com aparência de verdadeiro, que nos leva a cometer um erro.

Um paradoxo é um raciocínio que se faz a partir de premissas não contraditórias, mas que levam a uma conclusão contraditória. Também pode representar a ausência de lógica, apesar de aparentar um raciocínio correto.

Um argumento é válido quando as premissas conduzem a uma conclusão obrigatória. Isso significa dizer que a validade de um argumento é em função da sua construção, e não do seu conteúdo.

Quantificadores: todo, algum (pelo menos um) e nenhum.

Equivalência entre todo e nenhum: "Nenhum A é B" = "Todo A é não B"; "Todo A é B" = "Nenhum A é não B"

Negação para todo, algum e nenhum: "Todo A é B" - "Algum A não é B"; "Algum A é B" - "Nenhum A é B"; "Nenhum A é B" - "Algum A é B".

Dizemos que duas ou mais proposições são inconsistentes quando elas não podem ser simultaneamente verdadeiras. Assim, um argumento é inconsistente quando suas premissas não podem ser simultaneamente verdadeiras.

## Capítulo 9 - Lógica quantitativa e aplicações da lógica matemática

## Capítulo 10 - Circuitos lógicos

   ![Circuitos lógicos](/posts/2021-08-13.png){: width="400" }