---
title: Conhecendo os Filters - Jakarta EE
author: João F. F. Nogueira
date: 2021-09-10 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

# Filters

Os clientes fazem requisições aos diversos servlets da aplicação.

Como fazer para calcular o tempo levado em cada requisição?

A requisição passa por um filtro antes de chegar aos servlets.

O filtro implementa a lógica para calcular o tempo gasto em cada requisição.

Podem existir mais de um filter que interceptam uma requisição.

Os filters funcionam em cadeia: um filter chama o seu sucessor.

A requisição é interceptada tanto na ida quanto na volta.

Os Filters são transparentes: O filter não sabe da existência de outros filters; O cliente não sabe da existência dos filters; O servlet não sabe da existência dos filters.

• Ninguém sabe que os filters existem

– A não ser o container, que gerencia a chamada dos filters

• Isto permite um desenvolvimento totalmente desacoplado

– Filters podem ser colocados e retirados da cadeia de filters sem que seja necessário alterar código

## Exemplos de Filters

• Alguns exemplos do que pode ser feito com o uso de filters

– Log

– Auditoria

– Verificação de segurança

– Alterações na request e na response

## Criando um Filter

• A implementação de um filter é feita através da implementação da interface `javax.servlet.Filter`

| Método     | Quando é chamado...                     |
|------------|-----------------------------------------|
| init()     | Quando o filter é iniciado              |
| destroy()  | Quando o filter é removido              |
| doFilter() | Quando o filter intercepta a requisição |

• Assim como servlets, apenas uma instância de um filter existe em uma aplicação

```java
public class MyFilter implements Filter {
  private FilterConfig config;
  public void init(FilterConfig config) throws ServletException {
    //armazena o objeto FilterConfig
    this.config = config;
  }
  public void destroy() {
    //limpeza de recursos
  }
  public void doFilter(ServletRequest request, 
    ServletResponse response, 
    FilterChain chain) throws IOException, ServletException {
    //faz algo antes de repassar a request
    chain.doFilter(request, response);
    //faz algo depois de receber a response
  }
}
```

## Configurando um Filter

• O filter deve ser registrado no web.xml para que o container possa carregá-lo

```xml
<web-app> 
  <filter>
    <filter-name>LogFilter</filter-name>
    <filter-class>filter.LogFilter</filter-class>
  </filter>
  <filter>
    <filter-name>SecurityFilter</filter-name>
    <filter-class>filter.SecurityFilter</filter-class>
  </filter>
</web-app>
```

• Como o container sabe quando invocar determinado filter? 

– Através de mapeamentos de URL 

– Da mesma forma como acontece com servlets

```xml
<web-app> 
  <filter-mapping>
    <filter-name>LogFilter</filter-name>
    <url-pattern>/*</url-pattern><!--Intercepta todas as requisições-->
  </filter-mapping>
  <filter-mapping>
    <filter-name>SecurityFilter</filter-name>
    <url-pattern>/admin/*</url-pattern><!--Intercepta requisições em /admin-->
  </filter-mapping>
</web-app>
```

## Ordem de Carregamento

• Se mais de um filter for mapeado para a mesma URL, o container usa a ordem da declaração dos filters no web.xml para definir a cadeia.

## Filters e Annotations

• Filters também podem ser configurados através de annotations

```java
@WebFilter("/*")//@WebFilter define um filter e o mapeamento
public class LogFilter implements Filter {
  public void doFilter(ServletRequest request, 
    ServletResponse response, FilterChain chain) 
    throws IOException, ServletException {
    //código do filter
  }
  public void init(FilterConfig fConfig) throws
    ServletException { }
  public void destroy() { }
}
```

A definição de ordem só é possível através do web.xml

# Aspect Oriented Programming

• Programação orientada a aspectos

– AOP

• Permite plugar funcionalidades no código

– Estas funcionalidades são chamadas de aspectos

• O código não possui conhecimento a respeito dos aspectos, o que permite habilitá-los e desabilitá-los sem que seja necessária qualquer alteração no código

> Baseado nos cursos da Softblue