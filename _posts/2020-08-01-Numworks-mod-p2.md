---
layout: post
title: "Numworks modding - Part 2 : N0100++"
comments: true
---

This article is a follow-up on [that one]({{ site.baseurl }}/Numworks-mod-p1/). After taking a look inside my calculator,
I wanted to add something to it. So, I decided to revisit [TiPlanet's N0100++ challenge](https://tiplanet.org/forum/viewtopic.php?f=97&t=20557).

## Why ?

Epsilon is getting bigger and bigger, and Omega goes with it. You can see the evolution on the graph below.
We had to use a clever trick to get Omega 1.20 into the N0100: Making the user select its language at install-time.

<img src="{{ site.baseurl }}/images/2020-08-01-Numworks-mod-p2/stonks.png" alt="Evolution of the sizes of Epsilon and Omega"/>

We hope to add support to Omega before Numworks drops the support of the N0100, to make it live longer. But first,
the mods have to be made.

## Getting the Hardware

I bought a SOIC-8 socket to be able to swap flashes easily. I also bought a FTSH-105-01-F-DV-P as a debug port, and the
corresponding female ribbon cable, FFSD-05-D-03.50-01-N. I had a STLink v2 laying around, with the corresponding ribbon.
I started by creating the debug cable, by soldering the two ribbons together. Critor from TiPlanet also sent me two flash
chips: an Adesto AT25SF641 and a Winbond W25Q128JV, the first one being the one used on the N0110.

## Time to solder

My soldering skills aren't the best, but I managed to end up with something somewhat clean.
After that, I put holes trough the case of the device, to access it from the outside.

<img src="{{ site.baseurl }}/images/2020-08-01-Numworks-mod-p2/solder.jpg" alt="SOIC-8 Socket soldered to the N0100's PCB" style="display: inline-block; width: 58%;"/>
<img src="{{ site.baseurl }}/images/2020-08-01-Numworks-mod-p2/hole.jpg" alt="Holes in my N0100" style="display: inline-block; width: 38%;"/>

## Software

As A first test, I used [the steps zardam put together](https://zardam.github.io/post/numworks-giac/) to put GIAC on the N0100, and it works well.
I plan to adapt the newest versions of Epsilon to work with the N0100++.

## What's next ?
In the next episode on these hardware mods, we'll add support of the external flash on the latest version of Omega, and PR Epsilon.

