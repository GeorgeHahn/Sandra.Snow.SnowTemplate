---
layout: post
title: Journal: Starting out with Nancy on Mono Pt.2      
category: words
---
Hello world is great, but it's time for some real code. I plan to develop a simple flash-card style application to help me study organic chemistry.

*I'll be developing on Debian Testing/Mono with MonoDevelop.*


**FAIL. Stop reading now, I gave up with Massive and am switching over to EntityFramework. Thus, I am currently building Mono from source.**

## Setup

I don't like the XML mappings that are used with NHibernate, so I am going to use the excellent "[Massive](https://github.com/robconery/massive)" from Rob Connery. Since I'm using MySQL, I'll be working with Alexander Nyquist's [MySQL fork](https://github.com/alexandernyquist/massive-mysql) of Massive.

Why Massive?

Tiny and simple, a perfect compliment for our tiny and simple web framework.

First things first, let's fork massive-mysql. I put it into a separate project; you don't have to. Whichever route you choose, you'll have to add some references to your project.

In the project that contains your Massive.*.cs file:

- Install mysql.data from NuGet
- Add references to:
	- Microsoft.CSharp
	- System.Configuration
	- System.Core
	- System.Data
	- System.Data.Linq
	- System.Dynamic

Let's check that everything compiles and move on to some code.

![][0]

*My project after adding references*

## ORM
The first code I'll write is the ORM code. To prepare, I have drawn a rough diagram of the tables the app will need.

![][1]

[0]: /images/circuitsioVSupverter.jpg
[1]: /images/UpverterAddComponent.png