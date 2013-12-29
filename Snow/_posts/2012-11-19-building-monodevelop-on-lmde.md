---
layout: post
title:  Building MonoDevelop on LMDE 
---

I had a fair bit of trouble installing MonoDevelop on my LMDE machine the first time around. As I write this, the current version is 3.0.5 (commit [5542f6c0aa](https://github.com/mono/monodevelop/commit/5542f6c0aaa19e016f627f8bb202494c1db68888))

**Warning: This goes against Mono best practices; if you want do be safe with your system, you should do this in a parallel mono environment. By building on top of your main environment, you risk breaking Mono on your machine.** If you want to know more about setting up a parallel environment, [read this](http://www.mono-project.com/Parallel_Mono_Environments).

1. Install some prereqs

		sudo apt-get install git autoconf automake mono-devel mono-gmcs libmono-addins-cil-dev libmono-addins-gui-cil-dev libmono-addins-gui0.2-cil libmono-addins-msbuild-cil-dev libmono-addins-msbuild0.2-cil libmono-addins0.2-cil mono-addins-utils libglade2-dev gtk-sharp2 gnome-sharp2


2. Get the source

		git clone git://github.com/mono/monodevelop.git
		git submodule init
		git submodule update


3. Configure the build - I built main, MonoDevelop.Database and MonoDevelop.Debugger.Gdb; that is, options 1, 4, and 5. Other packages may have prerequisites not outlined here.

		./configure


4. Build the code

		make


5. Install the built binaries

		sudo make install