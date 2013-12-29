---
layout: post
title: ASP.Net Newbie Protip 
---
When building ASP.NET projects and hosting with local IIS, don't play with the build output path in Visual Studio. The issue here is that IIS Express loads libraries from the bin\ directory. Change that to something like bin\Release\, and the running code is no longer updated when Visual Studio builds.

A simple gotcha, but it may take a little coffee to get past if you haven't experienced it before.

![][0]

PS: I dug around in an attempt to find a setting related to this path, but was unable to. Apologies!

[0]: /images/aspnet_buildpath.png