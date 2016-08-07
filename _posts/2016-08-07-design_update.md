---
layout: post
title:  "Xylophone: Design Update"
date:   2016-08-07 14:00:00 -0400
category: projects
---

Hi! This weekend I made a chunk of progress on the Xylophone, which I'll
describe below. The first bit of the effort went into finalizing the solenoid
interface circuit. I also built a v.1 cardboard mechanical lay out for the
final design. I'm currently working on figuring out what the final feature set
is going to be, so I can figure out what microcontroller I'm going to use.

## Electrical ##

Last time I worked on this project, I tested a MOSFET circuit to interface
the microcontroller with the solenoid. I also talked about the potentially
trying to use a BJT instead of the MOSFET. I tried a single BJT this week and
the solenoid didn't have enough force to overcome the spring when I powered
the solenoid. This is fairly likely due to the lack of current I can supply
from the microcontroller, leaving the BJT in the linear region, as I predicted
in my last post. If I really wanted to use BJTs, I could use a Darlington Pair
to correct this issue. Because I'm already getting good performance from the
MOSFETs, I'm going to stick with them for now.

The "sluggish" behavior I was seeing last time from the solenoid only happens
with one of the solenoids I bought for testing, so I'm assuming it is caused
by a defect in that solenoid, not the circuit. I'm ok now ordering the full
eight solenoids that I need for the final design.

I've decided for v1, I'm going to stick to perf board instead of etching a
PCB. When I was looking to order perf boards, I noticed Adafruit has these
awesome [Perma-Proto Breadboard PCBs](https://www.adafruit.com/product/571)
that are perf boards, but layed out identically to breadboards, making it
super easy to port over breadboard circuits to something more permanent.
I could see my self picking these up for a different hobby project in the
future.

For power, I've estimated I need approximately 10A (1.1A x 8 solenoids, plus
plenty of headspace for LEDs, etc.) Luckily, Adafruit sells a nifty 10A, fixed
5V supply [here](https://www.adafruit.com/products/658) for $25. It's basically
a laptop charger, with a 2.1mm jack on the end. For testing today, I used a fix
5V 2A supply that used the same jack. Based on my current casing plan, I'm
probably going to expose the 2.1mm out the side of the case, and let the
regulator be hidden by the user somewhere else.

## Mechanical ##

I've also built my v0.1 cardboard prototype of the mechanical case/design,
shown below. The goal of this version was to get an idea of what scale I
want to use, and also give me something I could touch and play with as I
nailed down final features. Forgive the clearly rough construction, I'm using
this in place of a sketch, since I've found I've had better luck designing
this kind of stuff when I can *actually* touch it, not just imagine touching
it...

![Front View of cardboard protoype](/images/2016-08-07/FrontView.jpg)

The design is split into two vertically, with the open area on bottom housing
the Xylophone taking about half the vertical space and the tall wall taking
up the other half. The solenoids are going to be mounted to a small vertical
wall off the tall wall. The step behind the vertical wall will house
LEDs/lights that will add some kinetics to the design when it is playing.
Hopefully these lights will bounce of the tall wall.

![Top View of cardboard protoype](/images/2016-08-07/TopView.jpg)

One the very top, there are two buttons and 4 LEDs, used for song selection.
I'll probably use one of the buttons as a scroll through the song options
and the other to select the song. The LEDs can play the role as indicators,
as well as debugging later. The power switch and plug will be off the right
side of the case.

## Microcontroller ##

I'm still not sure whether I want to stick with the mbed microcontroller or
move over to the Beaglebone Black. The decision ultimately comes down to what
I want to do with the Xylophone at the end of all of this. Originally, the goal
was to make it cell phone controlled. This can be done either over the internet
or using BLE. The Penetrometer DAQ I designed for work uses the same internet
control stuff I would use here with a Beaglebone Black. This makes this
solution a little boring. I've never played with BLE before, but mbed has a
really good support for it. The phone side is what scares me about this
solution. Phonegap looks like it has decent support for BLE, and the more
research I've done, the more it looks perfectly technically feasible. The only
concern I have is that it requires a recent version of XCode, and I
haven't updated my Mac from OSX 10.7 ever, so I can't run any version of XCode
greater than what I have... I may be able to get around this using Phonegap
Build?

The nontechnical downside I see to using BLE is that it requires users
to download an App. This increases the cost to get strangers to use the
Xylophone which makes it less interactive of an experience.

Right now, I'm going to plan on using the mbed, without any wireless
communication, only the physical buttons. I can add the interaction later,
either with BLE or by dropping in a Beaglebone and having the Beaglebone
host the webstuff, but otherwise send the mbed commands via serial. From a
hardware side, this simplifies stuff since I can connect everything to the
mbed. From a software side, this just makes it important that I have
the concerns split well, such that I can flip between using buttons and
serial without too much concern. On the hardware side, I need to make sure
I have some sane plan to connect an extra board at some point.

## Connectors ##

The solenoids come with 2 pin PH connectors at the end. For standardization
purposes, I'm going to stick with PH connectors everywhere else in the circuit
as well. I'll be ordering these from Digikey or Mouser, pending what else
I decide I want to buy. 
