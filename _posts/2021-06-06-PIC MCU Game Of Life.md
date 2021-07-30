---
layout: post
title:  "Smallest Physical Implementation of Conway's Game of Life... Probably"
date:   2021-06-06
categories: Electronics
---

Did you know you can get a microcontroller in a 6-pin SOT-23 format? Well several MCU manufactures make them including Microchip's PIC series, of these PIC10F320 are smaller than a grain of rice and not nearly as tasty. As to be expected you don't get much in them with only 256 words of program space and 64 bytes of general memory storage. But with an instruction speed of 4MHz we are just fast enough to output PAL/NTSC video by bit bashing a tristate IO pin connected to a couple of resistors. So lets try to implement Conway's game of life (GOL) in the smallest physical space!

Now we only get 256 words and we'll need every last bit of it to fit everything in. Even worst, before now I've never programmed in assembly and while PICs can be programmed in embedded C like Arduino it is even more unlikely we can fit everything in. Actually this whole project started as a fun way to learn assembly in an interesting and functional environment, and without learning x86 or bricking my PC.

{% comment %}
FYI, it is words and not bytes of program space since each instruction in PIC10 series is 12 bits so the actual program size is 384 bytes, but since each instruction is indivisible it is better expressed as a word for each instruction.
{% endcomment %}


Aficionados of the Atari and other early home game consoles will be familiar with racing the beam. Old game consoles were played on CRTs which have an electron beam racing across the screen and to update the display you had to change video memory at the right time as the beam was moving across the screen. Now the Atari had dedicated hardware to read from a very limited video memory to draw to the screen which left the main processor free to update the video memory and other game logic while that hardware did all the analog output and sync pulse timings to get the video in the right format to work on a CRT.

![PAL video timings](/assets/PIC_GOL/PAL video.svg)

The PICs don't have such hardware so we need to both race the beam and do bit-bashing to generate the correct waveform. Now each instruction takes 0.25us to execute and the visible portion of each scan line is 52us long, which is a maximum horizontal resolution of 208 pixels. And that's only if we use 1 instruction, in most cases, we need multiple instructions to read from some defined video memory and managing loops counters. Again only 256 words so we can't waste them unrolling loops. Thankfully that won't matter much as the limited PICs memory space caps our max grid space for our GOL to 16 by 16 cells.

![Circuit diagram](/assets/PIC_GOL/GOL PIC10F320.svg)

Add a diagram of PAL video here for timing and voltage references. 0V is used for sync pulse timing and voltage between 0.33V-1V are shades of grey. So to get just black and white we need to set the video pin to either 0, 0.33V or 1V. While we could use two pins, we can do it with only 1 tristate IO pin. A tristate IO pin as three states high, low or high impedance when set as input. With a voltage divide and knowing that the resistance across the video in terminal of most TVs is 75 Ohms we can setup a voltage divide to give us 0V, 0.33V and 1V (approximately) and assign them to the low , high impedance and High level respectively.


{% comment %}
Harvested SMD resistors from old circuit boards. The whole circuit fit on the end of a video plug. This may also be the smallest physical implementation of GOL.
{% endcomment %}

![Inside the unit](/assets/PIC_GOL/PIC_MCU_GOL_Inside.jpg)

I got this small enough to fit on the end of the plug itself by forgoing the need of a circuit board and directly soldering the resistors and connections to the PIC. Thus possibly making this the smallest physical implementation of GOL (not including the screen). If you know of or have made a smaller one I'd love to see it.

<iframe width="420" height="315" src="https://www.youtube.com/embed/dDvYMWH5eS4" frameborder="0" allowfullscreen></iframe>

Well here's it running! The image isn't quite centered on the display and the internal clock's instability is likely causing so jitter but it does work. I'll link the assembly code [here](/assets/PIC_GOL/GameOfLife-16wide.7z) if you want to make it yourself or improve on my horrible code!
