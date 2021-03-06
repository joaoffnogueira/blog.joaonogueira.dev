---
title: Impedindo que uma barra de navegação fixa role sobre o conteúdo quando você clica em links internos
author: João F. F. Nogueira
date: 2020-09-11 11:15:00 -0300
categories: [Estudos-faculdade]
tags: [web, css]
toc: false
---

Se você tem uma barra de navegação na sua página marcada como `position: fixed;` no topo da tela, e você adiciona links internos para rolar a mesma página, você pode acabar com uma situação em que a barra de navegação sobrepõe o conteúdo da página. 

Para resolver isso você pode aplicar ao elemento de conteúdo que está sendo sobreposto a propriedade `scroll-margin-top`:

```css
section {
scroll-margin-top: 1em;
}
```

Como o nome sugere, essa propriedade adiciona uma margem top válida apenas para o ato de rolar a página.

Então você pode testar um valor compatível com a altura da sua barra de navegação, para que não sobreponha o conteúdo quando a página rolar.