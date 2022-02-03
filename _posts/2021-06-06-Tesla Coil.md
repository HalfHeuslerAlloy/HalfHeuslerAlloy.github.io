---
layout: post
title:  "Solid State Tesla Coil"
date:   2021-06-06
categories: Electronics
---

This is just a quick post about my old Solid State Tesla Coil (SSTC) project. This by far my most dangerous project as it uses high voltage, RF interference and mains voltage! Can produce 10-15cm arcs and scares the hell out of my housemate. Made in the case of an old PC PSU. Uses a few 3d printed parts to hold circuit boards up, support the primary winding and is the tube for the secondary winding. The secondary tube was printed in vase mode and then extra support was added in later for rigidity. Finally the secondary was coated in for generic clear coat varnish to give a little extra protection.

![Inside the unit](/assets/SSTC/TeslaCoil.jpg)

I don't have a detailed circuit layout you can follow since it was constructed a little ad hoc. It generally follows [this](https://www.loneoceans.com/labs/sstc2/) design with a few changes, for instance I had trouble finding a dual mosfet driver with a disable pin for PWM so instead I toggle the power to the IC with a transistor. I also added a fibre optic cable to control the PWM so it can be operated at a safe distance and in the future play some music. I'll add a video as soon as I can work up the courage to turn it on again, plus I'll get it to play some music. The primary circuit half H-bridge is currently configured to run at 240V but switching some diodes around can increase that to over 400V (the original plan and spec for these parts). Maybe in the future when I'm a homeowner and have a good isolation transformer I'll increase it!
