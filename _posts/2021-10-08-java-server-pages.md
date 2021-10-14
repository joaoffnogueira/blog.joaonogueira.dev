---
title: Java Server Pages
author: João F. F. Nogueira
date: 2021-10-08 09:00:00 -0300
categories: [Português, Estudos]
tags: [java, web]
toc: true
---

# O Que É

• Um documento HTML é estático

• Para criar respostas dinâmicas em Java, existem os servlets

– Dependendo da resposta, é bastante difícil codificá-la usando servlets

• Surgiram os JSPs

– Java Server Pages

– HTML + Código Java

```html
<%@ page language="java" contentType="text/html; harset=ISO-8859-1"
  pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
  "http://www.w3.org/TR/html4/loose.dtd">
<%@page import="java.util.List"%>
<%@page import="java.util.ArrayList"%>
<% 
  List<String> l = new ArrayList<String>();
  l.add("Arroz");
  l.add("Feijão");
  l.add("Batata");
%>
<html>
<body>
<H1>Lista de Compras</H1>
<ul>
<% for (String item : l) { %>
<li><%= item %></li>
<% } %>
</ul>
</body>
</html>
```

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
  "http://www.w3.org/TR/html4/loose.dtd">
<html>
<body>
<H1>Lista de Compras</H1>
<ul>
  <li>Arroz</li>
  <li>Feijão</li>
  <li>Batata</li>
</ul>
</body>
</html>
```

Na resposta que chega ao cliente, o documento é 100% HTML

## Um JSP é na verdade um servlet

![Um JSP é na verdade um servlet](/posts/2021-10-08-1.png){: width="100" height="100" }

# Scriptlets

• São códigos Java inseridos no JSP 

• Não estão presentes no HTML resultante 

• Um scriptlet deve começar com <% e terminar com %>

```java
<% 
  List<String> l = new ArrayList<String>();
  l.add("Arroz");
  l.add("Feijão");
  l.add("Batata");//O ponto-e-vírgula é necessário aqui
%>
```

# Expressions

• Também são códigos Java inseridos no JSP 

• São convertidas em texto no HTML resultante

• Uma expression deve começar com <%= e terminar com %>

```java
<ul>
<% for (String item : l) { %>
<li><%= item %></li>
<% } %>
</ul>
```

Uma expression deve sempre resultar numa string

Expressions não recebem ponto-e-vírgula

# Declarations

• Também são códigos Java inseridos no JSP 

• Usadas para declarar atributos e métodos de instância

• Uma declaration deve começar com <%! e terminar com %>

```java
<%! int id = 0; %>

<%!
  int getId() {
    return id;//Não esqueça de colocar ponto-e-vírgula

  }
%>
```

Scriptets são traduzidos da forma como são escritos

Expressions são traduzidas como parâmetros para o out.print()

Declarations são traduzidas como atributos e métodos

# Comentários em JSP

• Dentro de scriptlets, os comentários seguem o padrão do Java

```java
<%
  //este é um comentário
  int x = 0;
%>

<%
  /* este é um comentário */
  int x = 0;
%>
```

• Fora dos scriptlets, deve ser usada outra notação

```html
<%-- este é um comentário %>
```

# Diretivas do JSP

• JSP possui 3 tipos de diretivas (directives)

• Elas são identificadas por começarem por <%@ e terminarem por %>

| Diretiva | Descrição                                  |
|----------|--------------------------------------------|
| include  | Inclui código de um arquivo externo no JSP |
| taglib   | Define uma tag library                     |
| page     | Define propriedades da página              |

## A Diretiva Include

• Permite incluir um arquivo externo na criação do JSP

• A inclusão é feita durante a fase de tradução

– O servlet gerado já contém o conteúdo incluído

```java
<%@ include file="inc/header.jsp" %>
```

## A Diretiva Taglib

• Permite referenciar tag libraries na página

– Tag libraries são bibliotecas de tags

– Utilizadas para simplificar algumas tarefas e esconder o código Java

```java
<%@ taglib uri="http://www.jsp.org/tags" prefix="jsp" %>
<jsp:loop id="item" value="lista">
  ...
</jsp:loop>
```

## A Diretiva Page

• Define propriedades específicas da página JSP

• É composta por diversos atributos

– language

– contentType

– pageEncoding

– import

– isErrorPage

– errorPage

• Os atributos language, contentType e pageEncoding definem a linguagem e codificação

```java
<%@ page language="java" 
  contentType="text/html; charset=ISO-8859-1"
  pageEncoding="ISO-8859-1" %>
```

• O atributo import é utilizado para importar classes e/ou pacotes que serão usados no JSP

• Funciona de forma bastante semelhante ao import do Java

```java
<%@ page import="java.util.List" %>
<%@ page import="java.util.List, java.util.ArrayList" %>
<%@ page import="java.util.*" %>
```

• Por padrão, alguns imports já são realizados

– java.lang.*

– javax.servlet.*

– javax.servlet.jsp.*

– javax.servlet.http.*

# JSP Actions

• Funcionalidades para melhorar a produtividade no desenvolvimento

• São definidas pelas tags no formato `<jsp:action>`

| Action            | Descrição                                          |
|-------------------|----------------------------------------------------|
| <jsp:include>     | Inclui outro JSP para renderização                 |
| <jsp:forward>     | Redireciona a requisição para outro local          |
| <jsp:param>       | Cria parâmetros no JSP                             |
| <jsp:getProperty> | Recupera a propriedade de um Java Bean             |
| <jsp:setProperty> | Atribui um valor a uma propriedade de um Java Bean |
| <jsp:useBean>     | Referencia um Java Bean no JSP                     |

## A action `<jsp:include>`

• Inclui o conteúdo de outro arquivo (HTML, JSP, servlet, etc.)

• A inclusão é feita durante a renderização

– A diretiva <%@ include %> faz a inclusão na fase de tradução

```java
<html>
<body>
<jsp:include page="header.jsp" />//Inclui o arquivo header.jsp na geração do HTML de retorno
...
</body>
</html>
```

## A action `<jsp:forward>`

• Permite redirecionar a requisição para outro local

– HTML, JSP, servlet, etc

```java
<jsp:forward page="result.jsp" /> //Redireciona para o arquivo result.jsp
```

# Objetos Implícitos

• Como um JSP é um servlet, ele possui acesso à objetos que um servlet acessaria

• Estes objetos existem de forma implícita no JSP

| Objeto Implícito |  Classe do Objeto   |                             |
|------------------|---------------------|-----------------------------|
| out              | JspWriter           | Dados na saída              |
| application      | ServletContext      | Configuração                |
| config           | ServletConfig       | Configuração                |
| exception        | JspException        | Apenas para páginas de erro |
| request          | HttpServletRequest  | Escopo de dados             |
| response         | HttpServletResponse | Escopo de dados             |
| session          | HttpSession         | Escopo de dados             |
| pageContext      | PageContext         | Escopo de dados             |
| page             | Object              | Escopo de dados             |

# Páginas de Erro

• Os atributos isErrorPage e errorPage possibilitam o direcionamento para uma página de erro caso alguma exceção inesperada ocorra

• isErrorPage deve ser usado pela página que representa a página de erro

• errorPage deve indicar uma página de erro para que haja o redirecionamento no caso de erro

```java
<%@ page errorPage="error.jsp" %>//atributo errorPage define qual JSP chamar em caso de exceção
<html>
<body>
<%
  Object o = null;
  o.toString();//Este código vai gerar uma NullPointerException
%>
</body>
</html>
```

```java
<%@ page isErrorPage="true" %>
<html>
<body>
<H1>Erro no Sistema</H1>
<STRONG>Mensagem: </STRONG><%= exception.toString() %>//Uma página de erro possui um objeto implícito chamado exception, que representa a exceção ocorrida
</body>
</html>
```

# Inicialização e Destruição de JSPs

• Em servlets, o container chama os métodos 

– init(): ao inicializar o servlet 

– destroy(): ao destruir o servlet 

– service(): ao atender uma requisição 

• Como um JSP é um servlet, o container também chama métodos semelhantes 

– jspInit(): ao inicializar o JSP 

– jspDestroy(): ao destruir o JSP 

– _jspService(): ao atender uma requisição

• É possível sobrescrever os métodos jspInit() e jspDestroy()

• O método _jspService() não deve ser sobrescrito

```java
<%!//Usar declaration
  public void jspInit() {
    //inicializar o que for necessário
  }
  public void jspDestroy() {
    //destruir o que for necessário
  }
%>
```

# Passando Parâmetros para JSPs

• Assim como servlets, JSPs também podem receber parâmetros de inicialização

```xml
<servlet>
  <servlet-name>ListaCompras</servlet-name>
  <jsp-file>/lista_compras.jsp</jsp-file>
  <init-param>
    <param-name>moeda</param-name>
    <param-value>R$</param-value>
  </init-param>
</servlet>
<servlet-mapping>
  <servlet-name>ListaCompras</servlet-name>
  <url-pattern>/lista_compras.jsp</url-pattern>
</servlet-mapping>
```

```java
<html>
<body>
  Moeda: <%= config.getInitParameter("moeda") %>//O objeto implítico config acessa o ServletConfig do servlet
</body>
</html>
```

# Não use código Java em JSPs

• Apesar de JSPs terem sido criados para possibilitar a mistura de HTML e código Java, escrever código Java em JSPs não é uma boa prática

– Dificulta o trabalho de web designers, que não são programadores

– Para páginas complexas, o código fica confuso

– Dificuldade de manutenção

• Qual a alternativa?

– EL (Expression Language)

– JSTL (Java Server Pages Standard Tag Library)

– Tag libraries customizadas

> Baseado nos cursos da Softblue