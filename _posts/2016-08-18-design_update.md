---
layout: post
title:  "Xylophone: Design Update 2"
date:   2016-08-18 16:00:00 -0400
category: projects
---

My order from Adafruit came in, and I'm currently waiting on the order from
Digikey. (It should be here by tonight.) The Adafruit order contained
everything but the connectors that will go between the various PCBs.
While I wait for the Digikey order, I've been working on designing the
body in Fusion 360.

Fusion 360 is a cloud CAD program by Autodesk. It's free for students,
hobbyists, and startups who make under a certain dollar amount. I wanted
to start with it because it's something I'll have available after graduation.
So far, I've liked it pretty well, especially its "direct modeling" approach,
which lets you make all of your parts in what ProE would consider an Assembly
view. I don't think the learning curve from ProE is all that bad.

Before I ordered everything from Adadfruit, I decided to put each solenoid
interface circuit and its correponding LED on their own shared perf board, and
then run connectors between each of the little board and the MCU. When
I selected the connectors, I made them all the same size as the connector
already at the end of the solenoid. Unfortunately, the pitch for these
connectors is different than the standard pitch on perf boards. To fix this,
I'm going to have to cut a small slot in the perf board and then use jumpers
to connect the connector's headers to the perf board. This is kind of
hacky... I still think using the connectors and separating the circuits on
multiple perf boards will simplify wiring. I also decided to go with RGB LEDs,
so I'll have more options when I'm programming on how I want things to look.

As mentioned above, I'm currently waiting for the Digikey order and
otherwise working the CAD model for the body.

