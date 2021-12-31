---
title: Launch Flutter app on Google Play - no debug symbols alert
author: João F. F. Nogueira
date: 2021-12-31 08:00:00 -0300
categories: [English, Troubleshoot]
tags: [android, flutter]
toc: false
---

If you're trying to launch your flutter app on Google Play and you're getting the following alert: `This App Bundle contains native code, and you've not uploaded debug symbols. We recommend you upload a symbol file to make your crashes and ANRs easier to analyze and debug.` see the solution below.

Some documentation recommends the inclusion, in the `app/build.gradle` of your project, the instruction `android.buildTypes.release.ndk.debugSymbolLevel = 'FULL'`, for gradle to include the debug symbols in the app bundle, however this solution is not currently supported with flutter.

You can get the files directly to upload them to Google Play.

Go to `[your project]\build\app\intermediates\merged_native_libs\release\out\lib`.

Select folders `arm64-v8a`, `armeabi-v7a`, `x86_64` and compress them into a zip file.

Upload this zip file as a debug symbol file, this option will be bundled with the package you included as an app bundle on Google Play.

With that, the alert will disappear!