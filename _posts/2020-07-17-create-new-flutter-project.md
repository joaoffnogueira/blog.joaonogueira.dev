---
title: Create New Flutter Project is not showing on Android Studio wizard
author: João F. F. Nogueira
date: 2020-07-17 11:14:00 -0300
categories: [English, Troubleshoot]
tags: [android, flutter]
toc: false
---

Usually, the problem is that `Android APK Support` plugin is disable and enabling it should resolve the problem.

   ![android-studio-print](/posts/2021-06-11-01.png){: width="400" height="398" }
_Android Studio wizard print, with "Create New Flutter Project" option highlighted._

Try this:

1. On `Configure -> Plugins` check if:

   a. `Dart` and `Flutter` plugins are checked as enabled.

   b. `Android APK Support` is checked as enabled.

2. Restart Android Studio.

If still is not there, remove and reinstall `Dart` and `Flutter` plugins.