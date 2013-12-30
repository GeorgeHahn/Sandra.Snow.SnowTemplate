---
layout: post
title: Why the PhoneBloks phone will never happen   
category: words
---

It's a physics issue. Signals in modern devices are extremely high speed; the easiest and cheapest way to combat this is to bring components closer together. For example, the wireless radios, RAM, and processor in all modern phones exist as one chip. They essentially put the CPU and wireless magic on the same silicon die (or on a separate die in the same package) and pop a RAM chip on top ("Package on Package").

It's a communication issue. All of the ICs in a phone don't communicate over a single bus - almost every one ties directly into specific processor pins. This would restrict block size and placement.

If we aim a little lower and try for a modular design, the interconnects needed to ensure signal integrity at high speed are still very expensive. This project would require serious economies of scale to succeed. Each high speed component - CPU, RAM, storage, modem - would need an expensive socket.

Technically, the storage could be put on a socket pretty easily. It's not fast enough to warrant a very expensive socket, but would still add ~$2-5 to the final design. (Keep in mind, that means the consumer would be paying $4-20 extra, just to have the option to upgrade the storage.)

It's an interoperability issue. Going a little further, even if the device could be built in some fashion - there isn't much standardization in this area. I've spent days wrestling with a display peripheral on a processor to get it to interface with a specific display or video input IC - and that's with the benefit of thousands of pages of documentation, a field application engineer on call, and a ~$15000 oscilloscope. The amount of effort in testing and debugging that would be required to ensure the compatibility of each component would be absolutely enormous.

--

All of that said, I think the modular idea is excellent and could be done right - maybe not with blocks as described and - optimally - not with electrical signals. I could see it happening with optical interconnects, but we're a few years out from that. On chip optical interconnects are still in research, but there's a lot of money being put into them. Intel has demonstrated some very impressive optical tech that should come to market within the next five years. Eventually, we may be able to tie ICs together through optical traces for extreme high speed communication.

Finally, the stated motivation for this design is to reduce electrical waste. The best way to do that in the short term is to ensure devices are more repairable. An emphasis on user-serviceable batteries would make a significant difference in how long our devices remain useful without adversely impacting their cost or limiting their design.

It's worth noting that the smartphone market is starting to mature. Phones aren't improving by the massive leaps and bounds that they were. The technological differences are trivial - few people notice the difference between a 1GHz and 1.2GHz processor or 1GB and 2GB of RAM. Now, the main thing that separates generations of phones are millimeters of extra display space, grams of saved space, and milliamphours of extra battery life.

One major driver of phone sales right now is software. This is where the problem lies, not in hardware. Users need the right to unlock our phone modems and bootloaders. Unlocking the modems to allow use on different carriers would give used phones a wider market. Unlocking bootloaders would let users completely replace the original software, adding improvements and features to otherwise uninteresting devices.

We definitely have an e-waste problem - and I give this person credit for thinking outside the box - but this isn't the solution we need.

--

One source, because I'm lazy:
[IFIXIT](http://www.ifixit.com/Info/why)