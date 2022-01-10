---
title: Como instalar sua distro Linux no Windows+WSL em um disco/diretório personalizado
author: João F. F. Nogueira
date: 2022-01-07 08:00:00 -0300
categories: [Português, Solução de problemas]
tags: [windows, wsl]
toc: false
---

Se você quer usar WSl mas seu computador, assim como o meu, tem o Windows instalado em um SSD minúsculo e espaço sobrando no HD, você já deve saber que a instalação de uma distro Linux pela Microsoft Store ou pelas instruções da documentação oficial sempre ocorre no mesmo drive do sistema, sem opção. Aqui vai um modo de você instalar sua distro no disco/diretório que você quiser:

Se você ainda não habilitou o WSL comece aqui: <https://docs.microsoft.com/pt-br/windows/wsl/install-manual>

WSL habilitado, você pode baixar a distro de sua escolha aqui: <https://docs.microsoft.com/pt-br/windows/wsl/install-manual#downloading-distributions>

O arquivo baixado será um ´appx´, que você pode renomear como ´zip´ e extrair no local onde a instalação deverá ficar (`D:/wsl` por exemplo):

No terminal/PowerShell:

```bash
Rename-Item .\Ubuntu.appx Ubuntu.zip
Expand-Archive .\Ubuntu.zip -Verbose
```

Depois que terminar de extrair, localize na pasta o executável `.exe` e execute. Você já vai poder criar seu usuário e definir a senha:

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

Está pronto! Você pode remover o `.zip` que baixou pra economizar ainda mais espaço ;)

Ah, e se você já tem uma distribuição instalada e quer tentar mover ela, eu não fiz (então não posso dizer se é ok) mas encontrei como aqui:

<https://avinal.space/posts/development/wsl1.html>

Fontes:

<https://docs.microsoft.com/pt-br/windows/wsl/install-manual>

<https://damsteen.nl/blog/2018/08/29/installing-wsl-manually-on-non-system-drive>

<https://avinal.space/posts/development/wsl1.html>