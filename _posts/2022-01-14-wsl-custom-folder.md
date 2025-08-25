---
title: How to install your Linux distro on Windows+WSL in a custom disk/directory
author: João F. F. Nogueira
date: 2022-01-14 08:00:00 -0300
categories: [Misc]
tags: [windows, wsl]
toc: false
---

If you want to use WSL but your computer, like mine, has Windows installed on a tiny SSD and space left on the HD, you should already know that installing a Linux distro from the Microsoft Store or from the instructions in the official documentation always occurs on the same system drive, with no option. Here's a way for you to install your distro on the disk/directory you want:

If you haven't enabled WSL yet, start here: <https://docs.microsoft.com/en-us/windows/wsl/install-manual>

WSL enabled, you can download the distro of your choice here: <https://docs.microsoft.com/en-us/windows/wsl/install-manual#downloading-distributions>

The downloaded file will be an 'appx', which you can rename as 'zip' and extract to the location where the installation should be (`D:/wsl` for example):

At Terminal/PowerShell:

```bash
Rename-Item .\Ubuntu.appx Ubuntu.zip
Expand-Archive .\Ubuntu.zip -Verbose
```

After it finishes extracting, locate the executable `.exe` in the folder and run it. You will now be able to create your username and set the password:

```bash
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: joao
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Installation successful!
```

It is ready! You can remove the `.zip` you downloaded to save even more space ;)

Oh, and if you already have a distro installed and want to try moving it, I haven't tried it (so I can't say if it's ok) but I found it how here:

<https://avinal.space/posts/development/wsl1.html>

Sources:

<https://docs.microsoft.com/pt-br/windows/wsl/install-manual>

<https://damsteen.nl/blog/2018/08/29/installing-wsl-manually-on-non-system-drive>

<https://avinal.space/posts/development/wsl1.html>
