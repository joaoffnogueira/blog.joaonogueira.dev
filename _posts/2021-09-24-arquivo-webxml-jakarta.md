---
title: O Arquivo web.xml - Jakarta EE
author: João F. F. Nogueira
date: 2021-09-24 09:00:00 -0300
categories: [Português, Estudos]
tags: [jakarta, java]
toc: true
---

# O Arquivo web.xml

• Utilizado para configurar a aplicação web

• Não é obrigatório, mas é necessário pra alguns tipos de configurações

• Possui algumas tags para algumas configurações simples, porém importantes

– <welcome-file-list>

– <session-config>

– <error-page>

– <context-param>

## <welcome-file-list>

• Definir arquivos padrão que serão carregados caso o usuário acesse a aplicação pelo navegador diretamente no context-root

```
http://localhost:8080/curso //Vai retornar um erro 404 do HTTP
```

```xml
<web-app>
  <welcome-file-list>
    <welcome-file>index.faces</welcome-file>
    <welcome-file>primeiro.html</welcome-file>
  </welcome-file-list>
</web-app>
```

```
http://localhost:8080/curso //Vai retornar um welcome-file
```

## <session-config>

• Permite definir um tempo de expiração para a sessão de um usuário

```xml
<web-app>
  <session-config>
    <session-timeout>60</session-timeout><!--O tempo é definido em minutos. Caso não seja fornecido, um valor padrão é assumido-->
  </session-config>
</web-app>
```

## <error-page>

• Permite direcionar a requisição para uma página customizada de erro

– De acordo com algum código de retorno HTTP

– De acordo com uma determinada exceção

```xml
<web-app>
  <error-page>
    <error-code>404</error-code>
    <location>/404.faces</location>
  </error-page>
</web-app>

<web-app>
  <error-page>
    <exception-type>java.lang.Exception</exception-type><!--Qualquer exceção que ocorrer-->
    <location>/exception.faces</location>
  </error-page>
</web-app>
```

## <context-param>

• Permite definir parâmetros iniciais para a aplicação web

• Os parâmetros são visíveis para a aplicação como um todo

```xml
<web-app>
  <context-param>
    <param-name>adminEmail</param-name>
    <param-value>admin@abc.com</param-value>
  </context-param>
</web-app>
```

Bean
```java
public class MyBean implements Serializable {
  @Inject
  @InitParameterMap
  private Map<String, String> initMap;
  public void method() {
    String email = initMap.get("adminEmail");
  }
}
```

```html
#{initParam['adminEmail']}
```

### Parâmetros Importantes no JSF

• A tag <context-param> é usada para definir alguns parâmetros importantes do JSF

• Configuração de timezone

```xml
<context-param>
  <param-name>javax.faces.DATETIMECONVERTER_DEFAULT_TIMEZONE_IS_SYSTEM_TIMEZONE</param-name>
  <param-value>true</param-value>
</context-param>
```

• Define que o timezone (fuso horário) a ser usado no processo de conversão de datas é o timezone do sistema operacional

• O padrão é usar o UTC

• Configuração de estágio de projeto

```xml
<context-param>
  <param-name>javax.faces.PROJECT_STAGE</param-name>
  <param-value>Development</param-value>
</context-param>
```

• Define o estágio do projeto, o que pode influenciar em alguns aspectos do sistema

• Valores possíveis:

– Development, UnitTest, SystemTest, Production

• O padrão é Production

• Configuração de armazenamento da view

```xml
<context-param>
  <param-name>javax.faces.STATE_SAVING_METHOD</param-name>
  <param-value>server</param-value>
</context-param>
```

• Define onde o JSF irá salvar o estados das views

• Valores possíveis:

– server, client

• O padrão é server

> Baseado nos cursos da Softblue