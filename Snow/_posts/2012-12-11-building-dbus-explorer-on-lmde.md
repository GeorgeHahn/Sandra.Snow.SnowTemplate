---
layout: post
title:  Building DBus Explorer on LMDE  
category: linux
---
Nice easy build today. DBus Explorer is a handy C# application for probing DBus.

DBus Explorer is developed on GitHub: [https://github.com/garuma/dbus-explorer](https://github.com/garuma/dbus-explorer)

![][0]

DBus Explorer relies on DBus-Sharp-GLib, which relies on DBus-Sharp, so all three will need to be built.

	git clone https://github.com/mono/dbus-sharp.git
	git clone https://github.com/mono/dbus-sharp-glib.git
	git clone https://github.com/garuma/dbus-explorer.git 


Build and install DBus-Sharp. Expect a few warnings, but it should compile successfully.

	cd dbus-sharp
	./autogen.sh
	make
	sudo make install


Build and install DBus-Sharp-GLib. I was able to compile this library without errors.

	cd ../dbus-sharp-glib
	./autogen.sh
	make
	sudo make install


Build DBus Explorer

	cd ../dbus-explorer
	./autogen.sh
	make


If you just want to run DBus Explorer, you can launch it from the terminal right now.

	mono --runtime=v4.0 src/bin/Debug/DBusExplorer.exe


If you want a shortcut, two more steps must be performed.

Open src/bin/Debug/dbus-explorer in a text editor and change *exec mono* to *exec mono --runtime=v4.0*

The modified file should look like this:

	#!/bin/sh
	
	exec mono --runtime=v4.0 "/usr/local/lib/dbus-explorer/DBusExplorer.exe" "$@"


DBus Explorer can now be installed (Run from the dbus-explorer/ directory)

	sudo make install

[0]: /images/Screenshot-2012-12-11-23-01-40.png