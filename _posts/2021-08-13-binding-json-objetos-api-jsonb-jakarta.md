---
title: Binding de JSON e Objetos usando a API JSON-B - Jakarta EE
author: João F. F. Nogueira
date: 2021-08-13 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# JSON-B

• A API JSON-B (JSON Binding) permite um mapeamento automático entre objetos Java e documentos JSON

```java
Cadastro c = new Cadastro();
c.setNome("Marcos");
c.setIdade(28);
```

```json
{
"nome": "Marcos",
"idade": 28
}
```

## Usando a API JSON-B

• Criar documentos JSON

```java
Cadastro c = new Cadastro();
c.setNome("Marcos");
c.setIdade(28);
Jsonb jsonb = JsonbBuilder.create();
String json = jsonb.toJson(cadastro);
```

• Parse de documentos JSON

```java
Jsonb jsonb = JsonbBuilder.create();
Cadastro cadastro = jsonb.fromJson(jsonStr, Cadastro.class);
```

## Customizando as Propriedades

• Por padrão, o JSON-B usa o nome dos atributos da classe na manipulação do documento JSON

• Esse comportamento pode ser alterado

```java
public class Cadastro {
  @JsonbProperty("nome-da-pessoa")//Define outro nome
  private String nome;
  ...
}
```
