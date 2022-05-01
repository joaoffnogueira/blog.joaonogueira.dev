---
title: FlutterError - erro ao carregar assets
author: João F. F. Nogueira
date: 2022-05-01 11:15:00 -0300
categories: [Flutter, Dependências]
tags: [flutter, pubspec, yaml]
toc: false
---

![FlutterError: Unable to load asset](/posts/2022-05-01.png){: max-width="100%" height="auto" }

Se você criou seu projeto flutter usando o assistente do Android Studio e está recebendo o seguinte erro `FlutterError: Unable to load asset` ao tentar utilizar uma imagem como `asset`, verifique o seu arquivo `pubspec.yaml`.

É lá onde você indica o caminho para pastas e arquivos que deverão ser inclusos como assets no projeto.

Eu havia criado o projeto-base com o assistente do Android Studio e o `pubspec.yaml` estava com erro de indentação, sendo esta a origem do erro.

Indentação incorreta (arquivo recém-gerado para o projeto):

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

Perceba que a indentação é necessária para demarcar a hierarquia das dependências (já que não há tags que marquem o fechamento).

Então cada asset precisa estar indentado como "filho" de `assets:`, e este deve estar indentado como "filho" de `flutter:`

Outros problemas relativos ao carregamento de assets podem ser resolvidos executando um:

```bash
flutter clean
```

Tenha cuidado também com as barras ao indicar o caminho dos arquivos no `pubspec.yaml`.

O Windows utiliza barras invertidas por padrão para indicar caminhos (`\`), e isso pode fazer com que seu arquivo não seja interpretado corretamente.

Sempre utilize barras direitas (`/`) para indicar o caminho dos arquivos. No Visual Studio Code você pode configurar as preferências para que a opção "Copiar caminho relativo" dos arquivos do projeto utilize sempre a barra normal.
