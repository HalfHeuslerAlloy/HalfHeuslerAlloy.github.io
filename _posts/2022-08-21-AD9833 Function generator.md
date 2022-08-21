---
layout: post
title:  "AD9833 Function Generator"
date:   2022-08-21
categories: Electronics
---

Instead of simply buying a nice function generator for £100-200 with lots of important features such as variable amplitude, DC offset,  arbitrary functions, etc. We can build one with maybe £25 of materials and a lot more labor without those very useful features.

![Inside the unit](/assets/AD9833/outside.jpg)

The original goal of this project was to see if I could get an Arduino to output a sinewave using IO pins and a voltage ladder. Which did work, but even converting assembly was too slow. Capping out at 100-200KHz, depending on how much resolution you were willing to give up.

I then default to a standard solution of using a dedicated IC for the task. The AD9833 is a programmable waveform generator, with sinusoidal, triangular, and square wave generation at a maximum frequency of 25Mhz. It communicates over a simple SPI interface.

![Inside the unit](/assets/AD9833/inside.jpg)

The internal layout is very simple. The key components are mounted inside removable panels for ease of construction. Importantly the AD9833 is fully enclosed in an EMI shielding box made of a 3D print cover in plenty of aluminum tape. the box probably only has ok shield properties but at 25Mhz and low power that will be enough.

The control software running on the Arduino nano is very simple. Two mechanical and one rotary switch allow digit selection and modifier respectively. It does have a USB port on the back to allow SCPI commands over a simple serial interface. Of course, it doesn't truly support SCPI commands and only supports two commands in the style of SCPI and nothing else. At some point I should and *IDN and *RST command support.

[Here](https://github.com/HalfHeuslerAlloy/AD9833-Function-Generator) is a link to GitHub if you want to print out the case and even make it yourself, There isn't a wiring diagram yet, but the Arduino code will let you know what goes where. I added a voltage regulator and smoothing capacitors.