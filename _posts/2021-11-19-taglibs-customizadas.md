---
title: Taglibs Customizadas
author: João F. F. Nogueira
date: 2021-11-19 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [java]
toc: true
---

# Criando Taglibs

• É possível que o desenvolvedor crie suas próprias taglibs

– Melhorar produtividade do desenvolvimento

– Código mais fácil de entender a manter

• Taglibs podem ser criadas de duas maneiras

– Tag files

– Tag handlers

## Tag Files

• Fragmentos de arquivos JSP

• Possuem a extensão .tag

• Estão localizados no diretório WEB-INF/tags

image.tag
```xml
<CENTER>
<IMG src="java.png"><BR>
</CENTER>
```
Este tag file adiciona uma imagem centralizada na página

### Usando um Tag File

exemplo.jsp
```xml
<%@ taglib prefix="t" tagdir="/WEB-INF/tags" %>
<html>
<body>
<t:image /><!--O image referencia o nome do tag file (image.tag)-->
</body>
</html>
```

### Passando Atributos para Tag Files

image.tag
```xml
<%@ attribute name="imgName"
required="true"
rtexprvalue="true"
%><!--A diretiva attribute define os atributos da tag-->
<CENTER>
<IMG src="${imgName}"><!--imgName é substituído pelo atributo passado-->
<CENTER>
```

exemplo.jsp
```xml
<%@ taglib prefix="t" tagdir="/WEB-INF/tags" %>
<html>
<body>
<t:image imgName="java.png" /><!--Passagem de atributo-->
</body>
</html>
```

### Informações no Corpo das Tags

image.tag
```xml
<%@ attribute name="imgName"
required="true"
rtexprvalue="true"
%>
<CENTER>
<IMG src="${imgName}"><BR>
<jsp:doBody /><!--Imprime o corpo da tag sendo chamada-->
<CENTER>
```

exemplo.jsp
```xml
<%@ taglib prefix="t" tagdir="/WEB-INF/tags" %>
<html>
<body>
<t:image imgName="java.png">
Logotipo do Java<!--Corpo da tag-->
</image>
</body>
</html>
```

## Tag Handlers

• Tag files são interessantes quando não há necessidade de envolver código Java

• Nestes casos, é melhor usar um tag handler

• O Tag Handler é uma classe Java que representa uma taglib

• A classe estende SimpleTagSupport e sobrescreve o método doTag()

### Criando um Tag Handler

```java
public class DateTag extends SimpleTagSupport {
  private String pattern;
  public void doTag() throws JspException, IOException {
    Date d = new Date();
    SimpleDateFormat sdf = new SimpleDateFormat(pattern);
    getJspContext().getOut().print(sdf.format(d));//Envio do dado para a response
  }
  public void setPattern(String pattern) {
    this.pattern = pattern;//Setter invocado pelo container
  }
}
```

### Configurando o Tag Handler

• A configuração é feita em um arquivo .tld (tag library descriptor), dentro de WEB-INF

mytags.tld
```xml
<taglib>
  <tlib-version>1.0</tlib-version>
  <short-name>MyCustomTags</short-name>
  <uri>myTags</uri>
  <tag>
    <description>Formata uma data</description>
    <name>date</name>
    <tag-class>tag.DateTag</tag-class>
    <body-content>empty</body-content>
    <attribute>
      <name>pattern</name>
      <required>true</required>
      <rtexprvalue>true</rtexprvalue>
    </attribute>
  </tag>
</taglib>
```

### Usando o Tag Handler

exemplo.jsp
```xml
<%@ taglib prefix="t" uri="myTags" %><!--Referencia a URI do arquivo mytags.tld-->
<html>
<body>
<t:date pattern="dd/MM/yyyy" /><!--O container chama o método setPattern() no handler-->
</body>
</html>
```

### Tag Handler e o Corpo da Tag

```java
public class MyTag extends SimpleTagSupport {
  public void doTag() throws JspException, IOException {
    getJspContext().invoke(null);//Imprime o conteúdo do corpo da tag na response
    //É possível passar um Writer como parâmetro
  }
}
```

## Mais Sobre Configurações

• Atributo das tags: rtexprvalue

| Valor | Significado                                                                                         |
|-------|-----------------------------------------------------------------------------------------------------|
| true  |  Strings literais e outras expressões (como EL e scriptlets) são aceitas como valor para o atributo |
| false |  Apenas strings literais são aceitas como valor para o atributo                                     |

• Atributo do corpo das tags: body-content

| Valor        | Significado                                                          |
|--------------|----------------------------------------------------------------------|
| empty        | A tag não pode ter corpo                                             |
| scriptless   | O corpo da tag não pode conter scriptlets (mas aceita expressões EL) |
| tagdependent | O corpo da tag é interpretado como texto                             |
