---
layout: post
title:  "Internet Controlled Xylophone"
date:   2016-05-13 21:40:00 -0400
category: projects
---

I've been looking around for a few weeks for some sort of cool summer
hack project. Something fun and cheap to work on on the weekends. I've
had a few different ideas, primarily based around different technologies
I'd like to learn (like PLCs) or about "important" problems I'd like to
solve (like agriculture). What I've finally decided to work on is something
more fun, a robotic, internet controlled xylophone robot.

So far the plan is to buy a kid's xylophone (~$20) and 8 solenoids (~$5 - $10 a
piece). The solenoids will be positioned such that they hit the keys of the
xylophone and play pretty music.

I'm not sure what I want to do support wise to hold the solenoids. It will
almost definitely be wood based, and made of flat panels, so I can take
advantage of the laser cutter in the lab. (I need to do some research about
places you can get parts to order, for when the lab isn't available.) I'm
also thinking about maybe going PVC, and cutting out stuff with my dremel?

I'm thinking for doing the 3D design, I'd like to try out Autodesk Fusion,
since I could use it for free at home. If that doesn't work, I
can always move on to SolidWorks using the school's computers.

Controller wise, I'm not sure exaclty what I want to do. I definitely want
to make the device be controlled over the internet. I'm thinking about
setting up a DigitalOcean droplet to host the web page for control. The device
would periodically grab instructions from the droplet via a REST API.
People could give instructions via a website also hosted from the Droplet.

For this to work, the controller needs to be able to make HTTP requests over
the internet, preferrably over WiFi. A BeagleBone could definitely do this,
with very little problems. Plus, I already have one free. My main concern is
the timing critical nature of this project. I'm concerned that the BeagleBone
would add unneccessary complications when it comes to timing, cmapred to a
boring old microcontroller. I also have a number of mbed enabled devices
I'm not doing anything with that would be cool to play with. If I can find
an easy why to add internet to them, I may go with that.

I've also thought about not connecting the device itself to the internet, but
to connect it to a separate computer over serial that would then be
connected to the internet and the Droplet I've described previously. I have
a number of old computers that I could thow Linux on and then use permanently
for this task. Alternatively, for demos and such, I could use my laptop and
its screen to play middleware between the internet and the microcontrollers.
There is a lot to consider here.

Obviously this idea is *really* premature. I'll keep this page updated as I
continue.
