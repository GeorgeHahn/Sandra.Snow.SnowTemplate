---
layout: post
title: MQTT to 430MHz RF bridge
category: MQTT, Internet of Things, CC3200
---

For this project, I wanted a way to control my wireless power outlets from [Etekcity](http://www.amazon.com/gp/product/B0087DAW46/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B0087DAW46&linkCode=as2&tag=generi0c-20&linkId=FVZKHDNL5ZGAY5CN) with MQTT messages. [MQTT](http://www.mqtt.org/)  is an excellent publish-subscribe protocol designed to power the internet of things; I use it along with [Node-Red](http://nodered.org) to control devices around my apartment.

These outlets are controlled with a very simple protocol over ASK 433MHz RF. The protocol is documented pretty well [elsewhere](https://code.google.com/p/rc-switch/), so I won't cover it in depth.

Months ago, I created an identical device using a Netduino 2 Pro, but it wasn't fast enough to handle the radio protocol, so I had to pair it with a second microprocessor (I used a TI Tiva C Launchpad). This iteration of the project was created to simplify my setup and to let me attach the device to my network via Wifi rather than wired ethernet.

To create this device, I wired a TI CC3200 Launchpad to a [433MHz ASK transmitter](http://www.amazon.com/gp/product/B00INTI8R2/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00INTI8R2&linkCode=as2&tag=generi0c-20&linkId=IIDQZVD4UDU3VRI7). These transmitters are super simple - you have to supply 5v, ground, and a transmit signal.

Once the device was wired up, all it needed was some code. I used [knolleary/pubsubclient](https://github.com/knolleary/pubsubclient) to communicate over MQTT. The application code is pretty simple - it subscribes to one topic and repeats any messages it receives over the RF link.

Initially, I attempted to write the RF communications routine using the Energia supplied delay functions. Sadly, the microsecond delay function didn't work very well. When I measured the pulse timings with my logic analyzer, I saw that the delays were off, sometimes by a factor of 5x or more. Rather than troubleshoot a function I'm totally unfamiliar with, I took the easy way out - loop iteration based delays. With the help of my logic analyzer, I was easily able to create delays that perfectly matched my requirements. In a more complicated system, this wouldn't be a reasonable option, but this device is simple enough that it's not an issue.

I've now been using this device for a few months and haven't had any issues with it. It's super reliable and can be hidden away anywhere USB power is available.

My code is available on [Github](https://github.com/GeorgeHahn/MQTT_RF_Bridge) along with a wiring diagram.