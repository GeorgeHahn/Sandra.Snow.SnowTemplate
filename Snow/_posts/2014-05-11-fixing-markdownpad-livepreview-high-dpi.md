---
layout: post
title: Fixing MarkdownPad live preview on Lenovo Yoga 2 Pro (and other high DPI screens)
category: tools, bugs
---

Here's a quick and dirty font size fix I applied to the Markdownpad-github.css file. I just switched all font-size items to use `em` instead of `px`. It probably formats some things totally incorrectly, but it's good enough for me for the moment.

To use, open Tools -> Options -> Stylesheets and replace the contents of `markdownpad-github.css` (or create a new stylesheet)

[See gist](https://gist.github.com/GeorgeHahn/46d809262f3be67ea13e)