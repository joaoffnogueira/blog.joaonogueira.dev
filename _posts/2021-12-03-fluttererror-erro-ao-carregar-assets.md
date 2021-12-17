---
title: FlutterError - erro ao carregar assets
author: João F. F. Nogueira
date: 2021-12-03 11:15:00 -0300
categories: [Português, Solução de problemas]
tags: [android, flutter]
toc: false
---

Se você criou seu projeto flutter usando o assistente do Android Studio e está recebendo o seguinte erro `FlutterError: Unable to load asset` ao tentar utilizar uma imagem como `asset`, verifique o seu arquivo `pubspec.yaml`.

É lá onde você indica o caminho para pastas e arquivos que deverão ser inclusos como assets no projeto.

Eu havia criado o projeto-base com o assistente do Android Studio e o `pubspec.yaml` estava com erro de indentação, sendo esta a origem do erro.

Indentação incorreta (arquivo recém gerado para o projeto):
```yaml
flutter:

uses-material-design: true

assets:
  - images/test.png
```

Indentação correta:
```yaml
flutter:

   uses-material-design: true

   assets:
      - images/test.png
```

Perceba que a indentação é necessária para demarcar o envelopamento das dependências (já que não há tags que marquem o fechamento).

Então cada asset precisa estar indentado como filho de `assets:`, e este deve estar indentado como filho de `flutter:`
