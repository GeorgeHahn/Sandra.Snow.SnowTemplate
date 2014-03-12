---
layout: post
title: Hotend for Metal FDM 
category: 3d printing, hardware, brainstorming
---

## Hotend & nozzle metal
- Able to withstand 700-1100C
- Not going to interact badly with molten aluminum, zinc, or copper
- Hard enough that a 0.5mm hole is still 0.5mm after extruding a bunch of molten metal through it

## Hotend design
- Thermal expansion from worst metal shouldn't cause a jam
 - worst case expansion * worst case tolerance + magic extra tolerance
- Minimum amount of metal is molten at any given moment.

## Nozzle design
- Metal should extrude with minimum turbulence
 - Nozzle 10x longer than diameter of extrusion?

## Coldend design
- Thermal transfer up filament should be minimized

## Heat break design
- Heat leakage into the coldend should be minimized
- Filament must be supported enough that it won't bend under the pressure of extrusion
 - Ceramic sheath? Stainless tube?
- If the heat break can't withstand the full pressure of extrusion, the hotend will need to be anchored to the coldend externally

## Extruder design
- Filament should not be marred (eg, by a sharp gear) to minimize the risk of jamming in the cold end or damaging any components
- Filament must be pushed with enough force to extrude
 - Need to find data on how soft metals are at various temps

## Filament research
- Find filament of multiple metals in the same diameter & tolerance (at/near extrusion temperature after thermal expansion)

## Conclusion
In my mind, this hotend looks a lot like an E3d hotend made from steel or titanium, but with a directly mounted extruder and a lot more cooling (possibly water cooled?). It would be heated with a high temp heater cartridge (maybe?) and have a much heftier heat break, possibly supplemented by external thin steel wires.

## General questions
- How will molten aluminum interact with titanium? Would it be an appropriate nozzle material? How about steel?
- Any idea how to figure out a graph of extrusion force vs temperature for aluminum (w/ a given diameter nozzle)?
- How horrible is it going to be to deal with thermal expansion across this entire design? If more than one metal is used, everything needs to be matched up for expansion, yes?
- What sort of surface will be able to handle the thermal stress of being printed onto?
- How can part adhesion to the print bed be maintained with high levels of material shrinkage?
- Ceramics are exciting and could open a lot of opportunities, but I have no idea where to start with designing and specifying ceramic parts.
- **I know there are some additional issues I haven't mentioned here and certainly some I haven't even considered. Feel free to chime in an any of them!**

![][0] 

[0]: http://e3d-online.com/image/data/v5/hotside.jpg