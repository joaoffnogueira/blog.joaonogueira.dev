---
title: Conversores e Validadores - Jakarta EE
author: João F. F. Nogueira
date: 2021-05-07 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# Processos de Conversão e Validação

* Os processos de conversão e validação são necessários para garantir que os dados que chegam ao bean sejam consistentes

```java
public class LivroBean implements Serializable {
  private String titulo;
  private Date dataPublicacao;
  private Integer numPaginas;
  private Double preco;
  ...
}
```

## Conversão Automática

* Algumas conversões são feitas de forma automática pelo JSF

– Tipos de dados primitivos e classes wrappers correspondentes

– Datas

– Enums

* É possível especificar a formatação dos dados durante o processo de conversão

## Formatação de Dados

* Datas e números podem ser formatados, a fim de indicar como a conversão será realizada

```xml
<h:inputText value="#{livro.dataPublicacao}">
  <f:convertDateTime pattern="MM/yyyy" />
</h:inputText>

<h:inputText value="#{livro.preco}">
  <f:convertNumber minFractionDigits="2" maxFractionDigits="2" groupingUsed="false" />
</h:inputText>
```

## Exibindo Mensagens de Erro

* Quando um erro de conversão ou validação ocorre, o JSF exibe a mesma tela novamente, com os dados do formulário já preenchidos

* A tag `h:message` é utilizada para exibir o erro ocorrido

```xml
<h:inputText id="numPaginas" value="#{livro.numPaginas}" />
<h:message for="numPaginas" />
```

* A tag `h:messages` pode ser utilizada para exibir todas as mensagens de erro

* Mais utilizada durante o desenvolvimento

### Mensagens Resumidas e Detalhadas

* Uma mensagem de erro a ser exibida tem duas partes

– Summary: mensagem resumida

– Detail: mensagem detalhada

* É possível controlar qual parte exibir

```xml
<h:message for="comp" showSummary="true" showDetail="false" />
```

* Para `h:message`, o padrão é exibir o detail

* Para `h:messages`, o padrão é exibir o summary

### Customizando Mensagens de Erro

* É necessário criar um arquivo de recursos na aplicação, que vai sobrescrever as mensagens do arquivo de recursos padrão do JSF

MyMessages.properties
Deve ficar no classpath da aplicação
O arquivo deve ter a extensão .properties
Devem ser definidas as mensagens summary e detail

* O próximo passo é configurar a aplicação para ler as informações deste arquivo

* Isto é feito referenciando o arquivo no faces-config.xml

```xml
<faces-config>
  <application>
    <message-bundle>app.MyMessages</message-bundle>
  </application>
</faces-config>
```

* O arquivo da aplicação será consultado primeiro, antes do arquivo de recursos do JSF

* Outra opção é fornecer a mensagem de erro de conversão diretamente na tag do componente

```xml
<h:inputText value="#{livro.preco}" converterMessage="Erro de conversão" />
```

## Conversores Customizados

* Algumas vezes os conversores padrão do JSF não atendem as necessidades da aplicação

* É possível criar conversores customizados

```java
@FacesConverter(forClass = Estado.class)
public class EstadoConverter implements Converter {
  public Object getAsObject(FacesContext context, UIComponent component, String value) {
    //...
  }
  public String getAsString(FacesContext context, UIComponent component, Object value) {
  //...
  }
}
```

* No momento da conversão, um conversor customizado pode avisar sobre erros de conversão

* É preciso lançar uma `ConverterException`

```java
public Object getAsObject(FacesContext context, UIComponent component, String value) {
  //...
  FacesMessage msg = new FacesMessage("Erro!");
  throw new ConverterException(msg);
}
```

## Validação de Dados

* O JSF possui mecanismos de validação de dados

| Tag                   | O que valida                                                         |
|-----------------------|----------------------------------------------------------------------|
| f:validateRequired    | A presença de uma informação                                         |
| f:validateLength      | O tamanho do texto fornecido                                         |
| f:validateLongRange   | Se o número é do tipo long e está dentro de  determinado intervalo   |
| f:validateDoubleRange | Se o número é do tipo double e está dentro de  determinado intervalo |
| f:validateRegex       | Uma expressão regular                                                |

* Exemplos de validação

```xml
<h:inputText value="#{livro.titulo}">
  <f:validateRequired />
  <f:validateLength minimum="5" maximum="30" />
</h:inputText>

<h:inputText value="#{livro.titulo}" required="true" />

<h:inputText value="#{livro.numPaginas}">
  <f:validateLongRange minimum="10" maximum="9999" />
</h:inputText>
```

### Exibindo Mensagens de Erro

* Os erros de validação são exibidos da mesma forma que os erros de conversão

– Tags h:message e h:messages

* É possível mudar as mensagens de erro padrão do JSF através da definição de um arquivo de recursos na aplicação

* Também é possível utilizar o atributo `validatorMessage` no componente

### Validadores Customizados

* Assim como nos conversores, é possível criar validadores customizados
* O primeiro passo é criar uma classe que implemente `Validator`

```java
@FacesValidator("app.validator.Date")
public class DateValidator implements Validator {
  public void validate(FacesContext context, UIComponent component, Object value) throws ValidatorException {
    //...
  }
}
```

* Depois de criado, o validador pode ser referenciado por componentes JSF

```xml
<h:inputText value="#{livro.dataPublicacao}">
  <f:validator validatorId="app.validator.Date" />
</h:inputText>
```

### Validando com Métodos no Bean

* O JSF permite a implementação de métodos de validação, que podem ser referenciados por componentes

```xml
<h:inputText value="#{livro.preco}"
  validator="#{livro.validarPreco}">
</h:inputText>
```

```java
public void validarPreco(FacesContext context, UIComponent component, Object value) throws ValidatorException {
  //...
}
```

### Ignorando a Validação

* Em algumas situações, ignorar a validação dos dados é necessário

* Para ignorar a validação, definir o atributo `immediate` do botão/link como true

```xml
<h:commandButton action="#{doc.processar}" value="Processar" immediate="true" />
```
