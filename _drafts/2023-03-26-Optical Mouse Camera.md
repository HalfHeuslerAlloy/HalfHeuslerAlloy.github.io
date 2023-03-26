---
layout: post
title:  "Optical Mouse Camera"
date:   2023-03-26
categories: Electronics, Optical
---

Intro

I extracted the PCB from the mouse and trimmed the board down to remove (and salvage) unnecessary components. If The USB interface IC was left in the circuit it may interfer with our attempts to communicate with the sensor so it was disabled by cutting off the power, ground and data pins.

The case is a basic design made in OpenSCAD. The sensor is on the centerline of the PCB so we only need a slding slot to position the sensor below the lens. The lens itself is taken from an old smartphone camera, focusing is done by a 3D printed thread to move the lens closer or further from the sensor. The endcap holds the pi pico and capture button, it is a friction fit to close the device.