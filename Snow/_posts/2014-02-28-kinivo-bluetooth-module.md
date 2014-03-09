---
layout: post
title: Kinivo Bluetooth module
category: hardware
---

## Module Overview
[![][0]](http://www.amazon.com/Kinivo-BTC450-Bluetooth-Hands-Free-Input/dp/B009NLTW60/ref=sr_1_1?s=electronics&ie=UTF8&tag=generi0c-20&qid=1393638641&sr=1-1&keywords=btc450)

[Kinivo BTC 450](http://www.amazon.com/Kinivo-BTC450-Bluetooth-Hands-Free-Input/dp/B009NLTW60/ref=sr_1_1?s=electronics&ie=UTF8&tag=generi0c-20&qid=1393638641&sr=1-1&keywords=btc450)

- Held together with four T6 screws
- Contains a [KMBT007A bluetooth module](http://www.k-mate.com/en/displayproduct001.html?proID=101813595&proTypeID=100128337&fid=100128337)
- Runs at 3.3v


![][1]

### Wiring

Audio wire colors: Left: blue, Gnd: red/copper twist, Right: green

Power wire colors: Positive: red, Negative: copper (both are in thin plastic sheaths)

### IO

All switches are NO with 10k pullups to 3.3v

Has exposed SPI and UART ports

----------

## Remote Overview
[![][2]](http://www.amazon.com/Metra-Universal-Steering-Control-Interface/dp/B0052HXPAI/?_encoding=UTF8&tag=generi0c-20&camp=1789&creative=9325&linkCode=ur2)

[Axxess RF remote](http://www.amazon.com/Metra-Universal-Steering-Control-Interface/dp/B0052HXPAI/?_encoding=UTF8&tag=generi0c-20&camp=1789&creative=9325&linkCode=ur2)

Been running for almost two years on the same battery! Surprisingly, the plastic is visibly worn where it's been rubbing under my radio.

- 8 buttons
- Powered by a coin cell
- uC is an rfPIC
- Receiver uses a PIC18F2520

I used a custom firmware to toggle test points on the receiver when buttons are pressed. I preserved all radio communications so I can still control the radio station or CD track (as if I'd ever want to).


[0]: /images/kinivomodule.jpg
[1]: /images/usbbtpcb.jpg
[2]: /images/axxessmodule.jpg