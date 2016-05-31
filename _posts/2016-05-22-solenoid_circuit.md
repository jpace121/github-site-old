---
layout: post
title:  "Xylophone: Solenoid Interface Circuit"
date:   2016-05-22 17:45:00 -0400
categories: projects
---

## Designing the Circuit

The [solenoids I've been looking at](https://www.adafruit.com/products/2776)
source about 1.1A, way more than any microcontroller can source, hence
some sort of interfacing circuit must be used. The two interfacing
circuits I seriously considered are shown below.

![BJT Circuit](/images/2016-05-22/BJTCircuit.JPG)

![MOSFET Circuit](/images/2016-05-22/MOSFETCircuit.JPG)

Both circuits have a snubber diode next to the solenoid to prevent the kickback
voltage generated when the solenoid is turned off from frying the rest of
the circuit. This kickback happens because the solenoid is fundamentally
a big inductor, and the voltage across an inductor is

$$ V = L\frac{dI}{dt}. $$

The two circuits differ in the switching device used. The first circuit
uses a BJT, while the second circuit uses a MOSFET. The goal of the switching
element is to turn on the motor drive circuit, while having the smallest
voltage drop over the switching elements possible. For the BJT, the
smallest voltage drop will happen when the BJT is in saturation. In
saturation, $$V_{CE}$$ will be around 0.2V (where $$C$$ and $$E$$ are
labeled in the drawing.) The issue is getting the BJT into saturation.
For BJT's to be in saturation, the ratio between the current through
the collector ($$I_C$$) and the current from the base ($$I_B$$) should be approximately 10 (or lower).
For clarity,

$$ \frac{I_C}{I_B} \approx 10 $$

for saturation.

The by the solenoids I've selected source about 1.1A at 5V,
meaning that $$I_B$$ needs to be about 0.11A (or 110mA). The problem is that
the absolute maximum current an Arduino pin, for example, [can source is
40.0mA](http://playground.arduino.cc/Main/ArduinoPinCurrentLimitations),
therefore the BJT will never go in saturation and $$V_{CE}$$ will be
even greater than 0.6V.

When a MOSFET is turned on, instead of having a constant voltage drop between
it's *source* and *drain* (the names for parts of the MOSFET between ground and
the solenoid, contrasted with *collector* and *emitter* for the BJT), it
acts as if a constant resistor was added between the source and the drain.
[For the MOSFET I am looking at](https://www.adafruit.com/products/355), the
constant resistance is $$8.7m\Omega$$. **UPDATE: I messed up here.
This $$R_{DS}$$ is at 10V $$V_{GS}$$ not 5V. The graph in the data sheet
makes it looks like the resistance will be inifinite at 3.3V $$V_{GS}$$ (?)
and much higher at 4.5V. I think I'm going to spend the rest of the week
Googling stuff about MOSFETs and then repeat the math. This MOSFET may not
work. Worst case, I already ordered them, so I can always test it... Will
update this space with my prediction and actual behavior.**
**UPDATE 5/20/2016: Even though the data sheet shows an infinite $$R_{DS}$$ at
3.3V, the listed threshold voltage is 2.35V, so I think it should work. All
the parts have arrived from Adafruit, so I'll test it all this week. I've also
gone ahead and dropped a little bit of cash to pick up some more MOSFETs and
a set of BJTs to add to my collection.**
The voltage drop can be found using
Ohm's Law ($$V = IR$$). With a current of 1.1A, the voltage drop will only be
0.010V, much better than the voltage drop using the BJT. Because of this, I've
**decided to stick to the MOSFET circuit**.
If I was really concerned about price, I may deal with the higher voltage
drop to save on the unit costs. The MOSFETS I'm looking at are approximately
[$1.75 a piece](https://www.adafruit.com/product/355),
while BJTs can be purchased in
[sets of 10 for $1.95](https://www.adafruit.com/product/756).

As a sanity check, I looked in the super awesome
[PICAXE Interface Manual](http://www.picaxe.com/docs/picaxe_manual3.pdf) for
their suggested circuit. They suggest the same MOSFET circuit I'm using.
In contrast, the Arduino website (and Adafruit) suggest
[using a BJT.](http://playground.arduino.cc/uploads/Learning/solenoid_driver.pdf)

## Sourcing the Parts

To source the parts, I looked at Sparkfun and Adafruit, as they tend to be the
easiest "one stop shops" for hobby grade parts. Both have basically equivalent
5V Solenoids for $4.95, and 10 1N4001 Diodes cost $1.50 from both stores. The
MOSFETs cost less on Sparkfun, though, $0.95 a piece compared to $1.75
from Adafruit. This difference meant that the total cost on Sparkfun (for
all 8 solenoids, 10 diodes, and 10 MOSFETs) was $50.60, compared to $56.90
on Adafruit. The difference in MOSFET price is probably due to the fact that
the MOSFETs from Adafruit have a lower $$R_{DS}$$ then the the MOSFETs from
Sparkfun. **I like Adafruit's MOSFETs better enough that I'm willing to eat
the extra cost, and will go with them for this order.**

The discrete components could be found for slightly cheaper on Mouser, but the
shipping pretty much eats any savings immediately (at the quantity of items
I'm purchasing.)

To start out with, I'm only going to order two solenoids. Once I'm sure they
will work, I'll put in a second order to grab the remaining ones. I'll
also try to have the LED stuff designed by this point, so I can combine the
two orders.
