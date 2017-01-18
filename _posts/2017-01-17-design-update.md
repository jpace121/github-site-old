---
layout: post
title:  "Xylophone: Design Update"
date:   2017-01-17 17:00:00 -0400
category: projects
---

Over the Fall semester and Christmas break I was able to get a number of
things moving on the Xylophone Project.

## CAD Design ##

Most of my energy during Christmas break went into "finishing" the Mechanical
Design, using Fusion 360.

![Mechanical CAD Design](/images/2017-01-17/xylophone-cad.jpg)

Before I build the real version, I'm going to cut out a cardboard version so
I can give myself a chance to make any final adjustments.

## RGB LEDs ##

In the last post I mentioned I was adding RGB LEDs to give the design some
extra visual "energy" when running. The image below shows the schematic for
the circuit I'm using to interface with the RGB LEDs and the soelnoids. (I
think I went over the math for this in a previous blog post?)

![Solenoid Schematic](/images/2017-01-17/Solenoid_Schematic.png)

![RGB LED Schematic](/images/2017-01-17/RGB_Schematic.png)

I'm currently laying out a PCB in KiCAD and double checking all of my
math to make sure everything is good to go. (One of the things I need to
do is triple check to make sure my PCB footprints line up correctly with
the schematic.)

I also went ahead and built a single set of the above on a breadboard and
wrote a quick test program to make sure everything worked. I can now certify
that the STM32 Nucleo can control a single solenoid/LED set fine.
