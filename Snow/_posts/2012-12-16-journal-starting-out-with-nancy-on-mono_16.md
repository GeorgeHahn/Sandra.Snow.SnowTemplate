---
layout: post
title: Journal: Starting out with Nancy on Mono Pt.3 
---
In the last blog post, I had some trouble finding an ORM layer I could tolerate. Since then, I have built mono 3.0.3 from source (master/df22423 Sat Dec 15 04:31:04 EST 2012). It wasn't easy - there was a lot of black magic involved. Even once I had the mono compiler and libraries built, I was unable to build Entity Framework from source. My solution was to get the EF5 binary from NuGet - so there wasn't really any point to my building mono from source!

So, if you're here and you want to use EF, don't build it from source. Take the easy way out and download the binary from NuGet! (Not that I want to discourage anyone from contributing to an OSS project, but if you're reading this, you're probably more interested in Nancy & WebDev than ORM guts.)

**I was unable to get the MySQL bindings working, so I moved into a Windows 8 VM. From here on out, I'll be using EF5 (possibly moving to EF6) on "LocalDB".**