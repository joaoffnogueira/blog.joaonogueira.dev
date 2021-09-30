---
title: Tags e Componentes do JSF - Jakarta EE
author: João F. F. Nogueira
date: 2021-04-30 09:00:00 -0300
categories: [Português, Estudos]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# Tags do JS

* Páginas JSF são compostas por tags

* JSF suporta diversas bibliotecas de tags

| Nome     | Namespace                         | Prefixo |
|----------|-----------------------------------|---------|
| HTML     | http://xmlns.jcp.org/jsf/html     | h:      |
| Core     | http://xmlns.jcp.org/jsf/core     | f:      |
| Facelets | http://xmlns.jcp.org/jsf/facelets | ui:     |

* As tags padrão do HTML também são suportadas

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" 
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"
  xmlns:h="http://xmlns.jcp.org/jsf/html"
  xmlns:f="http://xmlns.jcp.org/jsf/core">
<h:head>
  ...
</h:head>
<h:body>
  ...
<h:body>
</html>
```

O prefixo é utilizado na referência de determinada tag

## Tags sem Representação Gráfica

Cabeçalho da página

```xml
<h:head>
  ...
</h:head>
```

Corpo da página

```xml
<h:body>
  ...
</h:body>
```

Formulários

```xml
<h:form>
  ...
</h:form>
```

Referência a arquivos JavaScript

```xml
<h:outputScript name="script.js" library="script" />
```

Referência a arquivos CSS

```xml
<h:outputStylesheet name="style.css" library="css" />
```

## Textos e Imagens

Exibe texto na página

```xml
<h:outputText value="Boa tarde, #{bean.nome}!" />
```

Exibe texto na página, possibilitando a formatação do mesmo

```xml
<h:outputFormat value="{0}, {1}!">
  <f:param value="#{bean.mensagem}" />
  <f:param value="#{bean.nome}" />
</h:outputFormat>
```

Exibe uma imagem

```xml
<h:graphicImage url="/images/figura.jpg" />
```

## Caixas de Texto

Caixa de digitação de texto

```xml
<h:inputText value="#{bean.texto}" />
```

Caixa de digitação de senha

```xml
<h:inputSecret value="#{bean.texto}" />
```

Caixa de digitação de texto em múltiplas linhas

```xml
<h:inputTextarea value="#{bean.itens}" rows="3" cols="10" />
```

## Campos Hidden

Campo que pertence ao formulário mas não é exibido

```xml
<h:inputHidden value="#{bean.id}" />
```

## Seleção de Itens: Checkboxes

Checkbox para um único item Mapeado para um boolean no bean

```xml
<h:selectBooleanCheckbox value="#{bean.ativo}" />
```

Checkbox para múltiplos itens Mapeado para um array ou coleção no bean

```xml
<h:selectManyCheckbox value="#{bean.alimentos}">
  <f:selectItem itemValue="1" itemLabel="Macarrão" />
  <f:selectItem itemValue="2" itemLabel="Feijão" />
  <f:selectItem itemValue="3" itemLabel="Arroz" />
</h:selectManyCheckbox>
```

Checkbox para múltiplos itens com lista dinâmica

```xml
<h:selectManyCheckbox value="#{bean.alimentos}">
  <f:selectItems value="#{bean.listaAlimentos}" />
</h:selectManyCheckbox>
```

A lista de elementos é fornecida pelo bean...

```java
private SelectItem[] listaAlimentos = { 
  new SelectItem("1", "Macarrão"), 
  new SelectItem("2", "Feijão"), 
  new SelectItem("3", "Arroz") 
}; 
```

Checkbox para múltiplos itens com lista dinâmica de qualquer tipo

```xml
<h:selectManyCheckbox value="#{bean.alimentos}">
  <f:selectItems value="#{bean.listaAlimentos}" var="a" itemValue="#{a.id}" itemLabel="#{a.nome}" /> 
</h:selectManyCheckbox>
```

A lista de elementos é fornecida pelo bean...

```java
private List<Alimento> listaAlimentos = Arrays.asList(new Alimento[] {
  new Alimento(1, "Macarrão"), 
  new Alimento(2, "Feijão"), 
  new Alimento(3, "Arroz") 
});
```

A classe Alimento possui os atributos id e nome, e os getters/setters correspondentes

## Seleção de Itens: Radio Buttons

Radio button para seleção de um item entre vários

```xml
<h:selectOneRadio value="#{bean.alimento}">
  <f:selectItem itemValue="1" itemLabel="Macarrão" />
  <f:selectItem itemValue="2" itemLabel="Feijão" />
  <f:selectItem itemValue="3" itemLabel="Arroz" />
</h:selectOneRadio>
```

A tag f:selectItems também pode ser utilizada com radio buttons

## Seleção de Itens: Menus

Caixa de seleção de um único item

```xml
<h:selectOneMenu value="#{bean.alimento}">
  <f:selectItem itemLabel="Selecione" noSelectionOption="true" />
  <f:selectItem itemValue="1" itemLabel="Macarrão" />
  <f:selectItem itemValue="2" itemLabel="Feijão" />
  <f:selectItem itemValue="3" itemLabel="Arroz" />
</h:selectOneMenu>
```

A tag f:selectItems também pode ser utilizada com menus

## Seleção de Itens: Listboxes

Lista de seleção de um único item

```xml
<h:selectOneListBox value="#{bean.alimento}">
  <f:selectItem itemValue="1" itemLabel="Macarrão" />
  <f:selectItem itemValue="2" itemLabel="Feijão" />
  <f:selectItem itemValue="3" itemLabel="Arroz" />
</h:selectOneListBox>
```

Lista de seleção de múltiplos itens

```xml
<h:selectManyListBox value="#{bean.alimentos}">
  <f:selectItem itemValue="1" itemLabel="Macarrão" />
  <f:selectItem itemValue="2" itemLabel="Feijão" />
  <f:selectItem itemValue="3" itemLabel="Arroz" />
</h:selectManyListBox>
```

A tag f:selectItems também pode ser utilizada com listboxes

## Botões

Botão que envia uma requisição ao servidor (POST)

```xml
<h:commandButton value="Processar Pedido" action="#{bean.processar}" />
```

Botão que envia uma requisição ao servidor (GET)

```xml
<h:button value="Processar Pedido" outcome="page" />
```

## Links

Link que envia uma requisição ao servidor (POST)

```xml
<h:commandLink action="#{bean.processar}">
  Processar Pedido
</h:commandLink>
```

Link que envia uma requisição ao servidor (GET)

```xml
<h:link value="Processar Pedido" outcome="page" />
```

Link que não submete dados ao servidor

```xml
<h:outputLink value="http://joaonogueira.dev">
  João Nogueira
</h:outputLink>
```

## Painéis

* São utilizados para organizar componentes em tabelas

* Definidos pela tag `h:panelGrid`

```xml
<h:panelGrid columns="2">
  <f:facet name="header">
    <h:outputText value="Cadastro de Cliente" />
  </f:facet>
  <h:outputText value="Nome:" />
  <h:inputText value="#{bean.nome}" />
  <h:outputText value="E-mail:" />
  <h:inputText value="#{bean.email}" />
  <h:outputText value="Endereço:" />
  <h:inputText value="#{bean.endereco}" />
  <h:outputText value="Telefone:" />
  <h:inputText value="#{bean.telefone}" />
  <f:facet name="footer">
    <h:commandButton value="OK" action="#{bean.cadastrar}" />
  </f:facet>
</h:panelGrid>
```

### Agrupando Componentes

* Ao utilizar painéis, é possível agrupar componentes em uma mesma coluna

* A tag `h:panelGroup` é utilizada

```xml
<h:panelGrid columns="2">
  <h:outputText value="Nome:" />
  <h:panelGroup>
    <h:inputText value="#{bean.nome}" />
    <h:outputText value="Nome do cliente"></h:outputText>
  </h:panelGroup>
  <h:outputText value="E-mail:" />
  <h:panelGroup>
    <h:inputText value="#{bean.email}" />
    <h:outputText value="E-mail do cliente"></h:outputText>
  </h:panelGroup>
</h:panelGrid>
```

## ID de um Componente

* Todo componente pode ter um ID associado

* Um componente com ID pode ser referenciado:

– Por outros componentes JSF

– No código Java

– Em chamadas JavaScript

```xml
<h:inputText id="txtNome" value="#{bean.nome}" />
```

## Renderização de Componentes

* Todo componente pode ser renderizado ou não

* Isto é controlado pelo atributo `rendered`

É possível utilizar value expressions

```xml
<h:inputText value="#{bean.nome}" rendered="false" />
```

## JavaScript e Componentes JSF

* É possível integrar componentes JSF com código JavaScript

```xml
<h:form id="pageForm">
  <h:panelGrid columns="3">
    <h:outputText value="Nome:" />
    <h:inputText id="txtNome" value="#{bean.nome}" />
    <h:commandButton
      value="Excluir" 
      action="#{bean.processar}" 
      onclick="return excluir(this.form);"
    />
  </h:panelGrid>
</h:form>
```

O componente deve ser referenciado como `idForm:idComp`

```javascript
function excluir(form) {
  var nome = form["pageForm:txtNome"].value;
  if (confirm("Excluir o nome " + nome + "?")) {
    return true;
  }
  return false;
}
```

Se a tag `h:form` tiver o atributo `prependId=“false”`, os componentes não recebem o ID do formulário como prefixo

## Resources

* Permite referenciar recursos, que podem estar separados em bibliotecas

– Imagens, arquivos CSS, arquivos JavaScript

### Referenciando Resources

* Imagens

```xml
<h:graphicImage name="imagem.jpg" library="images" />
```

* Arquivos CSS

```xml
<h:outputStylesheet name="styles.css" library="css" />
```

* Arquivos JavaScript

```xml
<h:outputScript name="scripts.js" library="javascript" />
```
