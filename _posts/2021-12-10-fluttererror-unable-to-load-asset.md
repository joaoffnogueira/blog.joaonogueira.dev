---
title: FlutterError - Unable to load asset
author: João F. F. Nogueira
date: 2021-12-10 11:14:00 -0300
categories: [English, Troubleshoot]
tags: [android, flutter]
toc: false
---

If you created your flutter project using the Android Studio wizard and you are getting the following error `FlutterError: Unable to load asset` when trying to use an image as `asset`, check your file `pubspec.yaml`.

This is where you indicate the path to folders and files that should be included as assets in the project.

I had created the base project with the Android Studio wizard and the `pubspec.yaml` had an indentation error, which is the source of the error.

Incorrect indentation (newly generated project file):
```yaml
flutter:

uses-material-design: true

assets:
  - images/test.png
```

Correct indentation:
```yaml
flutter:

   uses-material-design: true

   assets:
      - images/test.png
```

Note that indentation is necessary to demarcate the envelopment of dependencies (since there are no tags that mark the closing).

So each asset must be indented as a child of `assets:`, and it must be indented as a child of `flutter:`
