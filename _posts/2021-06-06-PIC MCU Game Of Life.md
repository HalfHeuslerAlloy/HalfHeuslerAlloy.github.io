---
layout: post
title:  "PIC MCU: Conway's Game of Life in 256 words"
date:   2021-06-06
---

Did you know you can get a microcontroller in a 6-pin SOT-23 format? PIC10F320's are smaller than a grain of rice and not nearly as tasty. As to be expected you don't get much in them with only 256 words of program space and 64 bytes of register space of which only half is usable as general memory storage. FYI, it is words and not bytes of program space since each instruction in PIC10 series is 12 bits so the actual program size is 384 bytes, but since each instruction is indivisible it is better expressed as a word for each instruction.

Unlike an Arduino with its easy-to-use breakout board, voltage regulators, USB interface, and other quality of life features; the family of PICs are single IC components with no such luxury. But with a 4MHz instruction rate and with a single tristate IO pin it is possible to output PAL/NTSC video, so lets try to implement Conway's game of life (GOL)! Now we only get 256 words and we'll need every last bit of it to fit everything in. Even worst, before now I've never programmed in assembly and while PICs can be programmed in embedded C like Arduino it is even more unlikely we can fit everything in. Plus I'd like to learn assembly anyway.

Aficionados of the Atari and other early home game consoles will be familiar with racing the beam. Old game consoles were played on CRTs which have an electron beam racing across the screen and to update the display you had to change video memory at the right time as the beam was moving across the screen. Now the Atari had dedicated hardware to read from a very limited video memory to draw to the screen which left the main processor free to update the video memory and other game logic while that hardware did all the analog output and sync timing to get the video in the right format to work on a CRT.

The PICs don't have such hardware so we need to both race the beam and do bit-bashing to generate the correct waveform. Now each instruction takes 0.25us to execute and the visible portion of each scan line is 52us long, which is a maximum horizontal resolution of 208 pixels. And that's only if we use 1 instruction, in most cases, we need multiple instructions to read from some defined video memory and managing loops counters. Again only 256 words so we can't waste them unrolling loops. Thankfully that won't matter much as the limited PICs memory space caps our max grid space of GOL to 16 by 16 cells.


Harvested SMD resistors from old circuit boards. The whole circuit fit on the end of a video plug. This may also be the smallest physicsal implementation of GOL.
