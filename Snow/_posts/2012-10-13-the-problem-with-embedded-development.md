---
layout: post
title:  The Problem with Embedded Development 
---
Embedded development sits in a remarkably odd position - somewhere between electrical engineering and computer science. It is such an odd position that there isn't even a college degree for it!

There is one big problem with embedded development today - tools. On the electrical engineering side, there are great tools. An electrical design can be created by a group ranging in size from one person to hundreds, and can be thoroughly simulated, tested, and verified before it is built. Software that runs on full computers is in an even better position. Best practices exist for all common tasks; software written in any language can be thoroughly tested. Every iteration of code can be evaluated based on one metric or another - primarily: do the tests pass?

In embedded development, none of this is true. Unit testing is almost unheard of. Whether or not the code "works" is defined by (hopefully) a third party (probably, a fellow developer) putting a device through its paces.

What we need:

- Unit testing (Desktop based?)
- A way to put code through its paces on a desktop before it is deployed. I'm imagining a tiny package that defines all of a processor's registers so code will compile and run on a desktop. Bonuses would be a system to generate various interrupts and a robust plugin system that would allow for IO.

From there, it would be trivial to set up a build server to continuously check the code in a repository.
 
*Sorry for the unpolished post. Better early than never!*