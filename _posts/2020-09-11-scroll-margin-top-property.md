---
title: Preventing a fixed navbar scroll over the content when you click on an internal-anchor link
author: João F. F. Nogueira
date: 2020-09-11 11:14:00 -0300
categories: [UI, Layout]
tags: [web, css]
toc: false
---

If you have a navbar set to `position: fixed;` on top screen, and you add internal links to scroll the same page, you may end it up with the navbar overlapping the content. 

To solve this, you can apply to the content element the property `scroll-margin-top` like this:
```css
section {
scroll-margin-top: 1em;
}
```
As the name of the property suggests, it adds a margin top only to the scroll action.

Then you can test a value compatible with the height of your navbar, so it cannot overlap the content when page scrolls.