---
layout: post
title: Converting Linux Mint Debian Edition (LMDE) into Debian Testing 
---
Linux Mint Debian Edition is built on Debian Testing. After months of dealing with flaky mirrors and a not-so-impressive distro, I decided it was time to flip the switch. (Other than Cinnamon and/or MATE, Mint doesn't offer much.)

I am going to attempt to perform an in-place switch by modifying my sources.list. We'll see how it turns out - either it will work, or I'll be installing Debian Testing later tonight.

I generated a new sources.list from [http://debgen.simplylinux.ch/](http://debgen.simplylinux.ch/).

Old sources.list:
	
	deb http://packages.linuxmint.com/ debian main upstream import
	deb http://mirror.metrocast.net/linuxmint-debian/latest testing main contrib non-free
	deb http://mirror.metrocast.net/linuxmint-debian/latest/security testing/updates main contrib non-free
	deb http://mirror.metrocast.net/linuxmint-debian/latest/multimedia testing main non-free

New sources.list (for x86-64)
	
	deb http://ftp.us.debian.org/debian testing main contrib non-free
	deb http://ftp.debian.org/debian/ wheezy-updates main contrib non-free
	deb http://security.debian.org/ wheezy/updates main contrib non-free
 
	# Third Parties Repos
	 
	# deb-multimedia.org
	deb http://www.deb-multimedia.org squeeze main non-free
	 
	# Oracle VM VirtualBox # Don't care to have right now.
	# deb http://download.virtualbox.org/virtualbox/debian wheezy contrib non-free

I'll check in later and let you know how it goes! 