---
layout: post
title: Force DPI Scaling on Windows
category: tools, bugs
---

Windows exposes a number of ways to disable DPI scaling, but no way to forcefully enable it. This is a problem when apps tell windows they support high DPI but then go on to render at exactly the same size - making for unreadable text and unclickable buttons.

I tried editing the application's manifest to set DpiAware to false, but that had no effect. Rather than switch my laptop's resolution every time I needed to use Cadence OrCAD, I did a little debugging with Ollydbg. Turns out, at some point, [SetProcessDPIAware](http://msdn.microsoft.com/en-us/library/windows/desktop/ms633543%28v=vs.85%29.aspx) is called. I already had an idea on how to solve it, so I didn't stick around to find the offending library (though I suspect it was being set by gdiplus).

I probably could have patched OrCAD (less so gdiplus), but there is a far more flexible solution. All we need to do is hook the SetProcessDPIAware function as a program is starting, and we gain the ability to block the function call, leaving the target application no way to tell windows not to scale it.

I used the [minhook](https://github.com/RaMMicHaeL/minhook) library to build a DLL that will do just that. When it is loaded by an application, the code replaces SetProcessDPIAware with an implementation that does nothing.

The DLL must be present right as the app is initializing, else it won't be able to block the function call. Rather than inject the DLL per se, I just used CFF Explorer to add it to the misbehaving application's import table. This causes it to be loaded as the application is starting up.

To maintain Windows 8 compatibility, I didn't hook [SetProcessDpiAwareness](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302122%28v=vs.85%29.aspx).

# Using the tool

To use DPIMangler yourself, get the [binaries here](https://github.com/GeorgeHahn/DPIMangler/releases/tag/v1.0.0). Next, get [CFF Explorer](http://www.ntcore.com/exsuite.php) or a similar tool. Open the target executable in CFF Explorer, go to the Import Adder, and click Add. Select the appropriate DPIMangler binary, then choose any exported function and click Import By Name. Next, click Rebuild Import Table and save the application. That's it! Next time you run the program, calls to SetProcessDPIAware will be blocked.

If this isn't working for you, make sure the application doesn't declare DpiAware in its manifest. Additionally, it's possible the program is calling SetProcessDPIAwareness, which I haven't hooked here. If that's the case, feel free to [contact me on Twitter](https://twitter.com/George_Hahn/), and I'll try to get a new release out.

# Results

Before; OrCAD on high DPI is practically unusable with no scaling

![][0]

After; much more usable with forced scaling

![][1]

[0]: /images/OrCADNoScaling.png
[1]: /images/OrCADScaled.png

