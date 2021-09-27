---
title: Dividindo Sistemas em Módulos no Java
author: João F. F. Nogueira
date: 2021-03-26 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# Suporte a Módulos no Java

* Introduzido a partir do Java 9

* Objetivos

– Forte encapsulamento do código

– Redução da dependência entre pacotes

– Facilidade para escalar sistemas

– Simplificar sistemas complexos

* O que é um módulo no Java?

– Grupo de pacotes que contêm códigos que implementam determinada funcionalidade

– Considerado um componente de software independente

– Módulos podem ser combinados para criar sistemas complexos

# Divisão em Módulos

![Divisão em Módulos](/posts/2021-03-26-2.png){: width="100" height="100" }

# Ativando o Uso de Módulos

* É preciso criar no projeto um `module descriptor`

– `module-info.java`

```java
module dev.joaonogueira.abc {}//nome do módulo
```

# Exportando Pacotes

* Um módulo deve exportar os pacotes que poderão ser acessados por códigos externos ao módulo

* Os pacotes que não estiverem listados, são visíveis apenas dentro do módulo

```java
module dev.joaonogueira.abc {
  exports dev.joaonogueira.abc.pack1;
  exports dev.joaonogueira.abc.pack2;
}
```

# Dependência de Outros Módulos

* Quando um módulo precisa acessar código de outro módulo, é preciso que isso seja configurado de forma explícita

```java
module dev.joaonogueira.def {
  uses dev.joaonogueira.abc;
}
```

# A Modularização do JDK

* O próprio JDK foi modularizado a partir da versão 9 do Java

– 73 módulos
* As aplicações agora podem declarar dependência apenas dos módulos que realmente precisarem

– A JVM executa de uma forma mais “leve”

![Alguns Módulos do JDK](/posts/2021-03-26-3.png){: width="100" height="100" }
