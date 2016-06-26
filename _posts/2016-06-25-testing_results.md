---
layout: post
title:  "Xylophone: Testing Update"
date:   2016-06-25 20:52:00 -0400
category: projects
---

I tested the different interface circuits today that I've described
previously. I will write up a detailed analysis of the results later.
In short, I basically see very little difference between the different
types of MOSFETs I purchased. I did not test the BJT circuit at all, since
the MOSFET circuit worked nicely.

I did run into one problem. My solenoid is currently "sticking", as in
when the voltage switches to zero, instead of going up, the slug stays
down and engaged. You can see the solenoid twitch when the voltage changes
and push the slug up freely, but it does not go up on its own.
I'm thinking I may have blown the solenoid when I left
it engaged for a fairly long period of time (a few minutes probably). I've
posted a question on reddit looking for guidance, specifically if my hunch
makes any sense at all. If the solenoid is sticking because I left it engaged
too long, I'm not really worried and will go ahead with the rest of the design.
For the real application, the solenoids will never be engaged for more that a
few milliseconds, if that.

Once I get the "sticking" issue sorted out, I'm going to move forward with the
design. I also want to try to BJT interface circuit for the heck of it.
