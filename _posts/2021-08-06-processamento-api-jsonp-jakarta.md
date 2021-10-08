---
title: Processamento com a API JSON-P - Jakarta EE
author: João F. F. Nogueira
date: 2021-08-06 09:00:00 -0300
categories: [Português, Estudos]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# O Formato JSON

• Formato de troca de dados

– Muito usado em web services e outras aplicações que se comunicam pela internet

• Inspirado no JavaScript

– JavaScript Object Notation

• Baseado em texto

• Possui 2 estruturas de dados

– Objetos {}

• Conjunto de pares de chave e valor

– Arrays []

• Lista de valores

• Possui 2 tipos de dados

– string

– number

• JSON x XML

– JSON é mais compacto

– XML possui recursos para validação de dados (XML Schema e DTD)

```json
{
  "nome": "João",
  "sobrenome": "Alencar",
  "idade": 33,
  "endereco" : {
    "rua" : "Rua. dos Limões",
    "numero" : 200,
    "cidade" : "São Paulo"
  },
  "telefones": [
    { "Celular": "22 2222-2222" },
    { "Residencial": "11 1111-1111" }
  ]
}
```

# JSON-P

• API do Java EE para processamento de documentos JSON (geração e parsing)

• 2 APIs

– Object Model API

• Cria uma árvore do documento inteiro em memória

– Streaming API

• Baseado em eventos

## JSON-P: Object Model API

• Criar um documento JSON

```java
JsonObject rootObj = Json.createObjectBuilder()
  .add("nome", "João Almeida")
  .add("idade", 30)
  .add("endereco", Json.createObjectBuilder()
  .add("rua", "Rua dos Abacates")
  .add("numero", 50).build()
  .build();
```

• Gravar em uma saída

```java
StringWriter out = new StringWriter();

try (JsonWriter jsonWriter = Json.createWriter(out)) {
  jsonWriter.writeObject(rootObj);
}
```

• Parse de um documento JSON

```java
JsonObject rootObj;
StringReader in = new StringReader(jsonStr));
try (JsonReader jsonReader = Json.createReader(in)) {
  rootObj = jsonReader.readObject();
}
String nome = rootObj.getString("nome");
int idade = rootObj.getInt("idade");
```

## JSON-P: Streaming API

• Criar um documento JSON

```java
StringWriter out = new StringWriter();
try (JsonGenerator g = Json.createGenerator(out)) {
  g.writeStartObject()
    .write("nome", "Pedro Silva")
    .write("idade", 32)
    .writeStartObject("endereco")
      .write("rua", "Rua do Java")
      .write("numero", 100)
    .writeEnd()
  .writeEnd();
}
```

• Parse de um documento JSON

```java
JsonParser parser = Json.createParser(new StringReader(jsonStr));
while (parser.hasNext()) {
  Event event = parser.next();
  switch (event) {
    case KEY_NAME: /* ... */ break;
    case VALUE_STRING: /* ... */ break;
    case VALUE_NUMBER: /* ... */ break;
    case VALUE_TRUE: /* ... */ break;
    case VALUE_FALSE: /* ... */ break;
    case VALUE_NULL: /* ... */ break;
    case START_ARRAY: /* ... */ break;
    case END_ARRAY: /* ... */ break;
    case START_OBJECT: /* ... */ break;
    case END_OBJECT: /* ... */ break;
  }
}
```

# Object Model API x Streaming API

• Object Model API

– Vantagens

  • Manipulação dos dados é mais fácil e intuitiva

– Desvantagem

  • É mais lenta e ocupa mais memória

• Streaming API

– Vantagem

  • E mais rápida e não ocupa tanta memória

– Desvantagem

  • A manipulação dos dados é pouco intuitiva e mais complexa
  