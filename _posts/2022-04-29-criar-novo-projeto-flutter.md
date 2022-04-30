---
title: Criar novo projeto Flutter não está aparecendo no assistente do Android Studio
author: João F. F. Nogueira
date: 2022-04-29 11:15:00 -0300
categories: [Flutter, IDE]
tags: [android, android-studio, solução-de-problemas]
toc: false
---

Se você faz questão de utilizar o Android Studio para criar o seu projeto, talvez você se depare com este problema (principalmente se estiver utilizando uma versão antiga do Android Studio):

Você instalou o Flutter, o Android Studio e dentro dele os plugins do Dart e do Flutter, e mesmo assim, quando você reinicia a IDE, não aparece a opção de criar um novo projeto Flutter.

Normalmente, o problema é que o plugin `Android APK Support` está desativado e habilitando-o deve resolver o problema.

   ![android-studio-print](/posts/2021-06-11-01.png){: width="400" height="398" }
_Assistente do Android Studio, com a opção "Criar novo Projeto Flutter" em destaque._

Tente isso:

1. Em `Configurar -> Plugins` verifique se:

   a. Os plugins do `Dart` e `Flutter` estão habilitados.

   b. `Android APK Support` está habilitado.

2. Reinicie o Android Studio.

Se ainda não estiver aparecendo, remova e reinstale os plugins do `Dart` e `Flutter`.
