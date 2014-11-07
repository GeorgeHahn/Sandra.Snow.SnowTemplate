---
layout: post
title: MQTT and C#
category: MQTT, C#
published: draft
---

M2MQTT is a pretty great library - it's stable and appears to be standards compliant. However, the programming interface it exposes isn't so great:

```
CODE SAMPLE
```

To fix this, I wrote a library on top of M2MQTT. This library, GeorgeHahn\Charlotte, exposes a beautiful API to write against. Take a look:

```
PRETTY CODE SAMPLE
```

The library is pretty light, coming in at under XXX lines of C# code. It isn't mature, it may not be stable, and its codebase could use a fair bit of tweaking. That said, I'm currently using it to power a few parts of my home automation system and have had very few issues with it.

Github issues and pull requests appreciated! If you have any comments on it, feel free to ping me on Twitter!gi 