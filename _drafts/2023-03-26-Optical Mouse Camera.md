---
layout: post
title:  "ADNS-2610 Optical Mouse 'Camera'"
date:   2023-03-26
categories: Electronics, Optical
---

What camera do you give to someone who already has too many? A camera that should exist! An optical mouse is essentially a high frame rate, low resolution camera design to track features on the surface of a desk/mouse pad. A quick raid of my parent's home turned up an old dirty optical mouse. Inside was a ADNS-2610 mouse sensor featuring an 18*18 pixel array. 

I extracted the PCB from the mouse and trimmed the board down to remove (and salvage) unnecessary components. If The USB interface IC was left in the circuit it may interfere with our attempts to communicate with the sensor so it was disabled by cutting the power, ground and data pins.

A Raspberry pi pico was used to interface with the ADNS-2610. For communication the sensor uses a two wire serial port, with the pico having full control over the clock speed. A little bit of micropython writes and reads to the sensor. Unfortunately, while the sensor normally runs at 1500fps for feature tracking and normal computer mouse use, it can only return 1 pixel at a time. So the frame rate is limited to about 2-3fps.

The case is a basic design made in OpenSCAD. The sensor is on the centerline of the PCB so we only need a sliding slot to position the sensor below the lens. The lens itself is taken from an old smartphone camera, adjustable focus is done by a 3D printed thread to move the lens closer or further from the sensor. The end cap holds the pico and capture button in place. The end cap snaps into place closing the camera.

