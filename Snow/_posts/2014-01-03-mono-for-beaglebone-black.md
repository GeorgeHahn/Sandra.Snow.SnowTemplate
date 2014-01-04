---
layout: post
title: Building Mono on a BeagleBone Black (Hard Float)
category: software
---

I performed this on [Ubuntu Saucy 13.10 from ARMhf](http://www.armhf.com/index.php/boards/beaglebone-black/) (running from an 8Gb SD card)

1. Launch a terminal window/ssh into your BBB
1. sudo apt-get update
1. sudo apt-get install mono-complete git automake libtool
1. Wait a long time (hours)
1. git clone git://github.com/mono/mono.git
1. cd mono
1. git submodule init
1. git submodule update
1. `./autogen.sh --prefix=/usr/local --enable-nls=no --with-sgen=yes --with-xen-opt=no --with-ikvm-native=no`  
1. make
1. Wait a long time (hours again)
1. Ignore the errors and hope they don’t mean anything
1. sudo make install
1. Wait some more
1. Ignore the errors and hope they don’t mean anything

Post based off of: [http://neildanson.wordpress.com/2013/12/10/building-mono-on-a-raspberry-pi-hard-float/](http://neildanson.wordpress.com/2013/12/10/building-mono-on-a-raspberry-pi-hard-float/)