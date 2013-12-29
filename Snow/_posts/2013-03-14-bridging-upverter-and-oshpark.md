---
layout: post
title: Bridging Upverter and OSHPark
---
[Upverter](http://upverter.com/) is the best online circuit creation platform, and OSHPark is one of the best circuit board production services. Put the two together, and you should find bliss - but you won't. Anyone who has had an Upverter-designed board built by OSHPark will be familiar with this problem. When you download gerbers from Upverter, you get a zip full of files like bottom_copper.ger and top_paste.ger. OSHPark, on the other hand, wants names like Bottom Layer.ger and Board Outline.ger.

Here are the name transformations - each pair consists of the Upverter name followed by the OSHPark name. If a file isn't listed here, it should not be uploaded to OSHPark.
	
	var filepairs = new TupleList<string, string>
	{
	 { "layers.cfg", "layers.cfg" },
	 { "hole.ger", "Drills.xln" },
	 { "mechanical_details.ger", "Board Outline.ger" },
	 
	 { "top_copper.ger", "Top Layer.ger" },
	 { "top_silkscreen.ger", "Top Silk Screen.ger" },
	 { "top_solder_mask.ger", "Top Solder Mask.ger" },
	 
	 { "bottom_copper.ger", "Bottom Layer.ger" },
	 { "bottom_silkscreen.ger", "Bottom Silk Screen.ger" },
	 { "bottom_solder_mask.ger", "Bottom Solder Mask.ger" }
	};

I wrote a quick C# command line app to do the transformation automatically. If you drop a Upverter zip onto the app, it will create an *osh_* zipfile using the OSHPark naming conventions.

You can find the source and the binary at [https://bitbucket.org/George_Hahn/upvertertooshpark](https://bitbucket.org/George_Hahn/upvertertooshpark).

BONUS: Create a shortcut to the binary in the %APPDATA%\Microsoft\Windows\SendTo directory! This will allow you to right click on an Upverter zip and choose Send to: OSHPark!