---
layout: post
title:  "Solid State Tesla Coil"
date:   2021-06-06
categories: Electronics
---

This is just a quick post about my old Solid State Tesla Coil (SSTC) project. This by far my most dangerous project as it uses high voltage, RF interference and mains voltage! Can produce 10-15cm arcs and scares the hell out of my housemate.

![Inside the unit](/assets/SSTC/TeslaCoil.jpg)

I don't have a detailed circuit layout you can follow since it was constructed a little ad hoc. It generally follows [this](https://www.loneoceans.com/labs/sstc2/) design with a few changes, for instance I had trouble finding a dual mosfet driver with a disable pin for PWM so instead I toggle the power to the IC with a transistor. I also added a fiber optic cable to control the PWM so it can be operated at a safe distance in in the future play some music. I'll add a video as soon as I can work up the courage to turn it on again, plus I'll get it to play some music. The main primary circuit is currently configured to run at 240V but switching some diodes around can increase that to over 400V (the original plan and spec for these parts). Maybe in the future when I'm a homeowner and have a good isolation transformer I'll increase!
