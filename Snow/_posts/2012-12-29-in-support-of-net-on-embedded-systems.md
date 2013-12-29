---
layout: post
title: In Support of .Net on Embedded Systems 
---
I am going to address some of the hostility towards .Net on embedded systems - known as the .Net Micro framework, or NetMF.

Let's take a quick look at the benefits of .Net:

- Better developer productivity
- Visual Studio & plugins
- Strong debugging environment
- Huge FOSS code ecosystem

The costs:

- Loss of deterministic real time behavior
- RAM
- Flash

Judging by this quick cost-benefit analysis, NetMF doesn't make sense in an environment where hard real time is an absolute requirement. Other than that, RAM and flash are cheap. In many cases, there is a 2 to 4 dollar difference between non-NetMF capable processors and those that are. Seems like a no-brainer for any quick-turn, low quantity shop.

Let's take a look at some basic code to toggle a pin in C:
	
	#include <mfr_library.h>
	 
	int main (void)
	{
	    LED_TRIS_BIT = PIN_OUTPUT;
	 
	    while(1)
	    {
	        LED ^= 1;
	    }
	}

And in NetMF:
	
	using System;
	using Microsoft.SPOT;
	using Microsoft.SPOT.Hardware;
	 
	namespace PinToggling
	{
	    public class Program
	    {
	        public static void Main()
	        {
	            OutputPort port = new OutputPort(Cpu.Pin.GPIO_Pin1, false);
	            bool value = false;
	 
	            while (true)
	            {
	                port.Write(value);
	                value ^= true;
	            }
	        }
	    }
	}

Ignoring the header file(s) for the C code, this example shows a nearly 2x increase in the number of lines required.

Now for something that should also be pretty easy, toggling an LED every second:
	
	#include <mfr_library.h>
	 
	byte _1ms_tick;
	 
	INTERRUPT_HANDLER OneMillisecondTick (void)
	{
	    _1ms_tick = 1;
	}
	 
	void WaitOneSecond (void)
	{
	    unsigned short counter;
	    for(counter = 0; counter < 1000; counter++)
	    {
	        while(!_1ms_tick)
	            NOP();
	        _1ms_tick = 0;
	    }
	}
	 
	int main (void)
	{
	    Configure_Interrupt();
	    LED_TRIS_BIT = PIN_OUTPUT;
	 
	    while(1)
	    {
	        LED = !LED;
	        WaitOneSecond();
	    }
	}

And in NetMF:
	
	using System;
	using System.Threading;
	using Microsoft.SPOT;
	using Microsoft.SPOT.Hardware;
	 
	namespace PinToggling
	{
	    public class Program
	    {
	        public static void Main()
	        {
	            OutputPort port = new OutputPort(Cpu.Pin.GPIO_Pin1, false);
	            bool value = false;
	 
	            while (true)
	            {
	                Thread.Sleep(1000);
	                port.Write(value);
	                value ^= true;
	            }
	        }
	    }
	}

And here's where the benefits of C# start to become apparent. Adding a delay only took one extra line, whereas it took 20 in C. Here, a user would have to know how interrupts work on a specific processor. They would also have to know how the compiler has defined the various numeric types. Is it byte, BYTE, uint8, char, or something different? C# doesn't hide all of this complexity, but it does standardize it. Need eight unsigned bits? Use an unsigned byte, easy. Need 32 signed bits? Use an int. Again, easy.

Less memorization for the developer means maintainable code, written sooner, and with fewer bugs. That is why embedded systems should be developed on the .Net Micro Framework. 