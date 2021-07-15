---
title: Criar novo projeto Flutter não está aparecendo no assistente do Android Studio
author: João F. F. Nogueira
date: 2021-06-11 11:15:00 -0300
categories: [Português, Solução de problemas]
tags: [android, flutter]
toc: false
---

Normalmente, o problema é que o plugin `Android APK Support` está desativado e habilitando-o deve resolver o problema. 

   ![android-studio-print](/posts/2021-06-11-01.png){: width="400" height="398" }
_Assistente do Android Studio, com a opção "Criar novo Projeto Flutter" em destaque._

Tente isso: 

1. Em `Configurar -> Plugins` verifique se: 

   a. Os plugins do `Dart` e `Flutter` estão habilitados. 

   b. `Android APK Support` está habilitado. 

2. Reinicie o Android Studio. 

Se ainda não estiver aparecendo, remova e reinstale os plugins do `Dart` e `Flutter`.