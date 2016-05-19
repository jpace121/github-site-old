---
layout: post
title:  "Xylophone: Midweek Update"
date:   2016-05-16 20:41:00 -0400
category: projects

---

Last weekend, I did some research and feel I have a decent idea about what it
takes to drive solenoids and the factors that need to be considered in
choosing them. I'll definitely write this up in a longer post.

I've decided to use the [5V solenoids from Adafruit](https://www.adafruit.com/products/2776).
The interface circuit doesn't look that hard. I'm pretty sure at minimum I need
a BJT, a resistor, and a diode to act like a snubber, ala the diagram
[here](http://playground.arduino.cc/uploads/Learning/solenoid_driver.pdf).
Alternate circuits replace the BJT with a MOSFET. I've also thought
about using a relay instead, since I have little experience with relays, and
would like to learn, but I feel this is overkill for this project.
I'm not entirely sure which approach I want to take. I'll have a better idea
after I do the math.

This weekend I want to:

1. Formally orgnanize my plan and what features will be done for each
   "version" of the xylophone.
2. Do the analysis for the solenoid circuit.
3. Order one or two test solenoids and circuit parts.
