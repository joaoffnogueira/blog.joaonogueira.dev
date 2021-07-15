---
title: Create New Flutter Project is not showing on Android Studio wizard
author: João F. F. Nogueira
date: 2021-06-11 11:14:00 -0300
categories: [English, Troubleshoot]
tags: [android, flutter]
toc: false
---

    ![gh-pages-sources](https://cdn.jsdelivr.net/gh/cotes2020/chirpy-images/posts/20190809/gh-pages-sources.png){: width="850" height="153" }
_This is how should look like_

Usually, the problem is that “Android APK Support” plugin is disable and enabling it should resolve the problem.  

Try this:

1. On Configure -> Plugins check if:

2. Dart and Flutter plugins are checked as enabled.

3. “Android APK Support” is checked as enabled.

4. Restart Android Studio.

If still is not there, remove and reinstall Dart and Flutter plugins.