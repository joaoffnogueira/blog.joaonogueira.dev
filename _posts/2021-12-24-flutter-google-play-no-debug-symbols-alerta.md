---
title: Lançar app Flutter na Google Play - alerta de ausência de debug symbols
author: João F. F. Nogueira
date: 2021-12-24 08:00:00 -0300
categories: [Português, Solução de problemas]
tags: [android, flutter]
toc: false
---

Se você está tentando lançar seu app flutter na Google Play e está recebendo o seguinte alerta: `Este App Bundle contém código nativo e você não carregou símbolos de depuração. Recomendamos que você carregue um arquivo de símbolo para tornar suas falhas e ANRs mais fáceis de analisar e depurar.` veja a seguir a solução.

Alguma documentação recomenda a inclusão, no `app/build.gradle` do seu projeto, da instrução `android.buildTypes.release.ndk.debugSymbolLevel = 'FULL'`, para que o gradle inclua os símbolos de depuração no app bundle, no entanto esta solução não é compatível com o flutter no momento.

Você pode pegar os arquivos diretamente para fazer o envio para o Google Play.

Vá para `[seu projeto]\build\app\intermediates\merged_native_libs\release\out\lib`.

Selecione as pastas `arm64-v8a`, `armeabi-v7a`, `x86_64` e compacte-as em um arquivo zip.

Faça o upload desse arquivo zip como arquivo de símbolos de depuração, esta opção vai estar junto com o pacote que você incluiu como app bundle na Google Play.

Com isso, o alerta vai desaparecer!