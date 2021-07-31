---
layout: post
title:  "Infinite Fractal Plane"
date:   2021-06-06
categories: OpenGL Fractal

---

This is shadertoy script is running a ray matching algorithm with a series of affine transformation to generate fractals. To get an infinite fractal plane I use transformations that leave the fractal with cubic symmetry, then using a modulos operation only the x and y coordinates I copy the fractal over an infinite grid. If transforamtions that generate the fractals are slowly modified over the x-y plane then it allows the surface to slowly change over the surface. This creates a changing fractal landscape to explore.

<iframe width="420" height="315" src="https://www.shadertoy.com/embed/wtj3Wm?gui=true&t=10&paused=true&muted=false" frameborder="0" allowfullscreen></iframe>
