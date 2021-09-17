---
title: Inner Classes em Java
author: João F. F. Nogueira
date: 2020-12-04 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# Introdução

* Inner classes são classes declaradas dentro de outras classes

```java
class MyOuter { //Outer class
	class MyInner { //Inner class
	}
}
```

* Quando compiladas, geram bytecodes diferentes

– MyOuter.class

– MyOuter$MyInner.class

* As inner classes podem ser divididas em 4 tipos

– Regular inner class

– Method-local inner class

– Anonymous inner class

– Static inner class

# Regular inner class

* Declarada como membro de uma classe

* Possui acesso aos elementos da classe dentro da qual está inserida

```java
public class MyOuter {
	private int n = 10;

	private class MyInner {
		public void imprimirN() {
			System.out.println(n); //A inner class enxerga o atributo n
		}
	}
}
```

* Uma instância de uma inner class não pode existir sem estar associada a uma instância de uma outer class

* Normalmente é a outer class que instancia a inner class

```java
public class MyOuter {
	private class MyInner {
		//...
	}

	public void criarInner() {//A instanciação é feita como se fosse com qualquer outra classe
		MyInner i = new MyInner();
	}
}
```

* O operador this referencia o próprio objeto

* Dentro de uma inner class, this referencia a instância da inner class

```java
public class MyOuter {
	private class MyInner {
		public void m() {
			System.out.println("Ref inner: " + this);
			System.out.println("Ref outer: " + MyOuter.this);//Para referenciar a outer class
		}
	}
}
```

# Method-local inner class

* Declarada dentro de um método

* Apenas o método enxerga a classe

```java
public class MyOuter {
	public void m() { 
		class MyInner {
			public void imprimirMensagem() {
				System.out.println("Mensagem!");
			}
		}

		MyInner i = new MyInner();
		i.imprimirMensagem();
	}
}
```

* A inner class pode acessar variáveis locais do método, desde que estas sejam final ou não tenham seu valor alterado

```java
public class MyOuter {
	public void m() { 
		final String msg = "Mensagem!";//final pode ser omitido

		class MyInner {
			public void imprimirMensagem() {
				System.out.println(msg);
			}
		}

		MyInner i = new MyInner();
		i.imprimirMensagem();
	}
}
```

# Anonymous inner class

* Não possui nome

* Classes anônimas são sempre subclasses de uma classe ou implementação de uma interface

* Sobrescrevem ou implementam métodos da superclasse ou interface

```java
public class Porta {
	public void abrir() {
		System.out.println("abrir");
	}
}

public class Casa {
	private Porta p = new Porta() { //Classe anônima sendo uma subclasse de Porta
		public void abrir() {
			System.out.println("porta anônima");
		}
	};

	public void m() {//O método invocado é o método sobrescrito
		p.abrir();
	}
}
```

* Exemplo:  Usando um `java.util.Comparator`

– Interface que possui o método `compare()`

```java
Comparator<String> comparator = new Comparator<String>() {
	public int compare(String o1, String o2) {
		return o1.compareTo(o2) * -1;//A classe anônima implementa a interface Comparator
	}
};

TreeSet<String> s = new TreeSet<String>(comparator);//A referência ao objeto é usada no construtor do TreeSet
```

* O exemplo pode ser simplificado ainda mais

```java
TreeSet<String> s = new TreeSet<String>(new Comparator<String>() {
	public int compare(String o1, String o2) {
		return o1.compareTo(o2) * -1;
	}
});
```

*  Neste exemplo a classe anônima é passada diretamente como parâmetro para o construtor do TreeSet

# Static inner class

* Não é realmente uma inner class porque não tem um relacionamento especial com a outer class

* Ela é apenas uma classe declarada dentro de outra classe

* Basta declarar a classe como static

```java
public class MyOuter {
	static class MyInner {
		public void imprimir() {
			System.out.println("Mensagem!");
		}
	}
}

MyOuter.MyInner i = new MyOuter.MyInner();
i.imprimir();
```

* Uma static inner class famosa no Java é a `Map.Entry`, cujos objetos são retornados quando o método `entrySet()` é invocado
