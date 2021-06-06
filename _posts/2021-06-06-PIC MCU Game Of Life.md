---
layout: post
title:  "PIC MCU: Game of Life in 256 words"
date:   2021-06-06
---

Did you know you can get a MCU in a 6-pin SOT-23 format? PIC10F320 are smaller than a grain of rice and not nearly as tasty. As to be expect you don't get much in them with on 256 words of program space and 64 bytes of register space of which only half is usable as general memory storage. FYI, it is words and not bytes of program space since each instruction in PIC10 series is 12 bits so the actual program size is 384 bytes, but since each instruction is indivisable it is better expressed as a word for each instruction.

Unlike an arduino with its easy to use breakout board, voltage regulators, USB interface and other quality of life features; the family of PICs are single IC componemts with no such luxury. 