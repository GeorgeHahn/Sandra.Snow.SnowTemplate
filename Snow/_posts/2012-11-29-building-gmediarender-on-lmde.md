---
layout: post
title: Building GMediaRender on LMDE   
category: linux
---
Note: I don't know that this will work for you. It builds fine on my system, but *gmediarender --list-outputs* shows only "Dummy output module (default)". If you have better luck, let me know!


This is a short tutorial for building GMediaRender on Linux Mint Debian Edition.

I used Henner Zeller's *gmrender-resurrect* project: he has taken the time to add some great features, for example, volume control and seeking support.


You'll want to grab the source for LibUPNP
LibUPNP: [http://sourceforge.net/projects/pupnp/files/latest/download](http://sourceforge.net/projects/pupnp/files/latest/download)

First, extract LibUPNP to an accessible directory

Build it and install the binary to your system directory

	cd libupnp-1.6.17
	./configure
	make
	sudo make install


Get the source for *gmrender-resurrect*

	git clone git://github.com/hzeller/gmrender-resurrect.git
	cd gmrender-resurrect


**Edit configure.in, add "-lm" to CFLAGS (near line 22)**

Build and install

	./autogen.sh
	./configure
	make
	sudo make install  