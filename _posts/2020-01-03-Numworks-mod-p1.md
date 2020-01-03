---
layout: post
title: "Numworks modding - Part 1 : openning the beasts."
comments: true
---

Since I received my first [Numworks](https://numworks.com/) calculater, in september of this year, 
I was interested in not simply using it as a calculator, but also as a dev platform. Today's 
the big day I start looking at hardware mods for that thing.

## A calculator as dev platform...? Dafuk?
Since the numworks is openhardware and it's firmware is opensource<a class="note" href="#note-1">[1]</a>,
I thought "meh, why not start doing stuff with that thing...?". And that's how I wrote my first app,
[Atom](https://github.com/M4xi1m3/nw-atom), a basic periodic table. A couple of emails and posts
on forums later, and I got involved into [Omega](https://github.com/Omega-Numworks/Omega), a fork of epsilon,
Numworks' official OS.

## But now, I want more!
Inspired by the [Numworks++ challenge](https://tiplanet.org/forum/viewtopic.php?t=20557) started on
Ti-Planet before the N0110 came out, I wanted to start hardware-modding that thing. So let's start
by openning both of my calculators (a N0100 and a N0110), see what's inside and start planning stuff...

## The N0100

I started by taking apart the old model : the n0100. After removing the four rubber pads, it exposes
six T5 screws. I only had to unscrew them and the device was open. I had to make sure to unplug the
batterie before completely removing the back cover.

<img src="{{ site.baseurl }}/images/2019-01-03-Numworks-mod-p1/n0100-close.jpg" alt="N0100 Closed" style="display: inline-block; width: 48%;"/>
<img src="{{ site.baseurl }}/images/2019-01-03-Numworks-mod-p1/n0100-open.jpg" alt="N0100 Opened" style="display: inline-block; width: 48%;"/>

As we can see, the mother-board is held in place by 4 PH00 screws. We can see the U7 trace on the mobo,
where a flash chip can go (N++ again). There is quite a lot of room to work with in the n0100.

## The N0110

Then, it was time for my daily driver : the n0110. It opens almost like the n0100, except there are some
clips to hold it in place when the screw are removed (I don't like clips, I always break them...). After
unscrewing the six T6 screws (a bit bigger than the ones on the n0100), we can work our way arround the
clips and unplug the battery.

<img src="{{ site.baseurl }}/images/2019-01-03-Numworks-mod-p1/n0110-close.jpg" alt="N0110 Closed" style="display: inline-block; width: 48%;"/>
<img src="{{ site.baseurl }}/images/2019-01-03-Numworks-mod-p1/n0110-open.jpg" alt="N0110 Opened" style="display: inline-block; width: 48%;"/>

We can see that the mobo is a little bit shorter than on the n0100. The screen isn't under the mobo anymore,
and a plastic light-pipe was added for the LED. A flash chip was also added. There is still some space left
for some modification.

## What's next, then ?

As we have seen, there is some space to work with on the two devices. What I want to do with these two calculator
is add a port on the exterior of the device for the UART, and add one of those cheap QI induction receiver,
because induction charging a calculator is kindof swag (in my opinion at least...).

## Bonus

I also had a N0110 preproduction unit, that I won from a contest on Ti-Planet, laying arround. I opened it, and it
was exactly like the normal N0110. Nothing more, nothing less. A bit disapointed to be honnest, but heh, it's a
N0110 afterall, what would you expect.

#### Notes :
 - <span id="note-1">[1] It's CC-BY-SA-NC, something that I and many peoples wouldn't consider free
software, but it's still better than the rest of the calculator industry so...</span>

