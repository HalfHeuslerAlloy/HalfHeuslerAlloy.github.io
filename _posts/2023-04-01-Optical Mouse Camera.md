---
layout: post
title:  "ADNS-2610 Optical Mouse 'Camera'"
date:   2023-04-01
thumbnail: "assets/ADNS-2610/thumbnail.png"
categories: Electronics Optical
---

What camera do you give to someone who already has too many? A camera that should exist! An optical mouse is essentially a high frame rate, a low-resolution camera designed to track features on the surface of a desk/mouse pad. A quick raid of my parent's home turned up an old dirty optical mouse. Inside was a ADNS-2610 mouse sensor featuring a tiny 18*18 pixel array. 

I extracted the PCB from the mouse and trimmed the board down to remove (and salvage) unnecessary components. The ADNS-2610 can't communicate directly with the PC and instead uses a separate USB interface IC that also handles button and scroll wheel inputs. If The USB interface IC was left in the circuit it may interfere with our attempts to communicate with the sensor so it was disabled by cutting the power, ground and data pins.

![Mouse PCB](/assets/ADNS-2610/Cut_Mouse_Board.jpeg)

A Raspberry pi pico was used to interface with the ADNS-2610. For communication the sensor uses a two wire serial port, with the pico having full control over the clock speed. A little bit of micropython writes and reads to the sensor. Unfortunately, while the sensor normally runs at 1500fps for its internal feature tracking and normal computer mouse use, but it can only return 1 pixel at a time. Plus extra time is needed to send data over serial, so the frame rate is limited to about 2-3fps.

![Open Case](/assets/ADNS-2610/Open_assembly.jpg)

The case is a basic design made in OpenSCAD. The sensor is on the centerline of the PCB so we only need a sliding slot to position the sensor below the lens. The lens itself is taken from an old smartphone camera, adjustable focus is done by a 3D-printed thread to move the lens closer or further from the sensor. The end cap holds the pico and capture button in place. The end cap snaps into place closing the camera.

![Closed case](/assets/ADNS-2610/Closed_assembly.jpg)

The pico reads image data and sends it over serial to the PC as bytes where it is received by a python program and decoded. The pico also sends the state of the capture button. The image data is plotted on a matplotlib graph and displayed in a simple tkinter GUI.

![Closed case](/assets/ADNS-2610/window.png)

Overall the image quality is terrible. It's a 0.3 kilopixel 6-bit grey scale camera with very poor light sensitivity and a worse refresh rate. Selfies look barely recognizable, which I suspect is helped by our natural hypersensitivity to all things face-shaped.