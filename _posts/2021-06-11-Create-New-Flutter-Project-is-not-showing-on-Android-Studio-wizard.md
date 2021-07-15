---
title: "Create New Flutter Project" is not showing on Android Studio wizard
date: 2021-06-11 11:14:00 -0300
categories: [English, Troubleshoot]
tags: [android, flutter]
---

![Android Studio wizard print, with "Create New Flutter Project" option highlighted.](/posts/2021-06-11-01.png)
_This is how should look like_

Usually, the problem is that “Android APK Support” plugin is disable and enabling it should resolve the problem.  

Try this:  

1. On Configure -> Plugins check if:

2. Dart and Flutter plugins are checked as enabled.

3. “Android APK Support” is checked as enabled.

4. Restart Android Studio.

If still is not there, remove and reinstall Dart and Flutter plugins.