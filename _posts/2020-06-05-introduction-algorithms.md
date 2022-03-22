---
title: Anotações sobre Algoritmos
author: João F. F. Nogueira
date: 2020-06-05 08:00:00 -0300
categories: [Estudos-faculdade]
tags: [algoritmos, lógica]
toc: true
---

Baseado no livro: Introduction to Algorithms (Cormen; Leiserson; Rivest; Stein)

## 1 O papel dos algoritmos na computação

CORMEN, Thomas H.; LEISERSON, Charles E.; RIVEST, Ronald L.; STEIN, Clifford. **Algoritmos**: teoria e prática. 3ª ed. Rio de Janeiro: Elsevier, 2012.

Um algoritmo é qualquer procedimento computacional bem definido que toma algum valor ou conjunto de valores como entrada e produz algum valor ou conjunto de valores como saída. Portanto, um algoritmo é uma sequência de etapas computacionais que transformam a entrada na saída.

Também podemos considerar um algoritmo como uma ferramenta para resolver um problema computacional bem especificado.

Em geral, uma instância de um problema consiste na entrada.

Uma estrutura de dados é um modo de armazenar e organizar dados com o objetivo de facilitar acesso e modificações.

## 2 Dando a partida

### Ordenação por inserção

Um algoritmo eficiente para ordenar um número pequeno de elementos.

INSERTION-SORT(A) 

```javascript
for j = 2 to A.comprimento
	chave = A[j]
	//Inserir A[j] na sequência ordenada A[1...j-1].
	i=j-1
	while i>0 e A[i]>chave
		A[i+1]=A[i]
		i=i-1
	A[i+1]=chave
```

Se o arranjo estiver ordenado em ordem inversa — ou seja, em ordem decrescente —, resulta o pior caso.

### Análise de Algoritmos

· Analisar um algoritmo significa prever os recursos de que o algoritmo necessita. Ocasionalmente, recursos como memória, largura de banda de comunicação ou hardware de computador são a principal preocupação, porém mais frequentemente é o tempo de computação que desejamos medir. Em geral, pela análise de vários algoritmos candidatos para um problema, pode-se identificar facilmente um que seja o mais eficiente. Essa análise pode indicar mais de um candidato viável, porém, em geral, podemos descartar vários algoritmos de qualidade inferior no processo.

· O tempo de execução do algoritmo é a soma dos tempos de execução para cada instrução executada; uma instrução que demanda ci passos para ser executada e é executada n vezes contribuirá com cin para o tempo de execução total.

· O tempo de execução do pior caso de um algoritmo estabelece um limite superior para o tempo de execução para qualquer entrada. Conhecê-lo nos dá uma garantia de que o algoritmo nunca demorará mais do que esse tempo. Não precisamos fazer nenhuma suposição sobre o tempo de execução esperando que ele nunca seja muito pior.

· Para alguns algoritmos, o pior caso ocorre com bastante frequência. Por exemplo, na pesquisa de um banco de dados em busca de determinada informação, o pior caso do algoritmo de busca frequentemente ocorre quando a informação não está presente no banco de dados. Em algumas aplicações, a busca de informações ausentes pode ser frequente.

· Muitas vezes, o “caso médio” é quase tão ruim quanto o pior caso. Suponha que escolhemos n números aleatoriamente e aplicamos ordenação por inserção.

· Em geral, consideramos que um algoritmo é mais eficiente que outro se seu tempo de execução do pior caso apresentar uma ordem de crescimento mais baixa. Devido a fatores constantes e termos de ordem mais baixa, um algoritmo cujo tempo de execução tenha uma ordem de crescimento mais alta pode demorar menos tempo para pequenas entradas do que um algoritmo cuja ordem de crescimento seja mais baixa.

### Projeto de Algoritmos

· Muitos algoritmos úteis são recursivos em sua estrutura: para resolver um dado problema, eles chamam a si mesmos recursivamente uma ou mais vezes para lidar com subproblemas intimamente relacionados. Em geral, esses algoritmos seguem uma abordagem de divisão e conquista: eles desmembram o problema em vários subproblemas que são semelhantes ao problema original, mas de menor tamanho, resolvem os subproblemas recursivamente e depois combinam essas soluções com o objetivo de criar uma solução para o problema original.

· O paradigma de divisão e conquista envolve três passos em cada nível da recursão:

1. Divisão do problema em determinado número de subproblemas que são instâncias menores do problema original.

2. Conquista os subproblemas, resolvendo-os recursivamente. Porém, se os tamanhos dos sub-problemas forem pequenos o bastante, basta resolver os subproblemas de maneira direta.

3. Combinação as soluções dadas aos subproblemas na solução para o problema original.

· O algoritmo de ordenação por intercalação a seguir obedece rigorosamente ao paradigma de divisão e conquista. Intuitivamente, ele funciona do modo ilustrado a seguir.

4. Divisão: Divide a sequência de n elementos que deve ser ordenada em duas subsequências de n/2 elementos cada uma.

5. Conquista: Ordena as duas subsequências recursivamente, utilizando a ordenação por intercalação.

6. Combinação: Intercala as duas subsequências ordenadas para produzir a resposta ordenada.

MERGE(A, p, q, r) 

```javascript
n1=q-p+1
n2=r-q
sejam L[1..n1+1] e R[1..n2+1] novos arranjos
for i=1 to n1
	L[i]=A[p+i-1]
for j=1 to n2
	R[j]=A[q+j]
L[n1+1]=infinite
R[n2+1]=infinite
i=1
j=1
for k=p to r
	if L[i]<=R[j]
		then A[k]=L[i]
			i=i+1
		else A[k]=R[j]
			j=j+1
```

MERGE-SORT(A, p, r) 

```javascript
if p<r
	then q=[(p+r)/2]
		merge-sort(A,p,q)
		merge-sort(A,q+1,r)
		merge(A,p,q,r)
```



O bubblesort é um algoritmo de ordenação popular, porém ineficiente. Ele funciona permutando repetidamente elementos adjacentes que estão fora de ordem.