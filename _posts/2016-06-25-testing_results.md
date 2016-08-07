---
layout: post
title:  "Xylophone: Testing Update"
date:   2016-06-25 20:52:00 -0400
category: projects
---

I tested the different interface circuits today that I've described
previously. In short, I basically see very little difference between
the different types of MOSFETs I purchased. I did not test the BJT
circuit at all, since the MOSFET circuit worked nicely.

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

**UDPATE 7/07/16** My post on /r/Arduino was kindly answered. The poster
agreed with me that I may have blown the soleoid by keeping it engaged
too long. They also warned that I may not have been giving the solenoid
enough current. This makes sense to me, especially considering the power
supply I am currently using does not seem to react well to sudden burst
draws of current. I need to investigate alternate power supplies. I also
want to see if a BJT performs better than the MOSFET, but mainly for the
heck of it...

**UPDATE 8/06/16** I tried the BJT circuit today and it was horrible. Solenoid
clearly wasn't getting enough current to overcome the force from the spring.
I'm definitely sticking with the MOSFET circuit. Also tried the other solenoid,
and everythign worked fine. I think the issues I was seeing earlier were
primarily due to issues with solenoid I was testing with breaking when I kept
it engaged too long.
