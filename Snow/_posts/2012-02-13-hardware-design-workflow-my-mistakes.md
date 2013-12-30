---
layout: post
title:  Hardware Design Workflow: My Mistakes 
category: hardware
---
During my recent foray into PCB layout, I made a few mistakes. Here are the most egregious:

The biggest mistake I made was starting to route traces before I was happy with part placement. I can't stress this enough, **figure out your part placement before you start routing**. Of course, if you have an autorouter available, it is acceptable to use it periodically to gauge your part placement.

**Nail down your schematic before you start laying out your board.** If your schematic is a moving target, layout will be impossible.

**If you know you are going to need small parts, use them from the start.** On my first design, I started with 0805 passives and had to switch to 0603's when I realized I wasn't going to be able to pack 0805's as tightly as I wanted to. I scrapped the entire 0805 based layout and started from scratch with 0603 parts.

**Take it one step at a time.** I may have made this point already, but it is important enough to warrant restating. Do not start placing parts until your schematic is done. Do not start routing traces until you are happy with part placement. Do not write a BOM until your PCB is complete.

**It is a good idea to know the approximate price of parts you are using.** If you use prohibitively expensive or unavailable parts on your design, you may have to make changes as far back as the schematic. Essentially, you may have to make changes to every single step. Save yourself the frustration and know the parts you use. 