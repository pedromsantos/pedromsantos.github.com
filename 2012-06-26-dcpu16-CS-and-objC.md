---
layout: default
published: false
---
#DCPU16.Net and ObjC-DCPU-16-ASM

[DCPU16.Net](https://github.com/pedromsantos/DCPU16.Net) is a software implementation of DCPU16 according to the specs @notch published [here](http://0x10c.com/doc/dcpu-16.txt). Thr project is developed in C# and uses the .Net framework.

[ObjC-DCPU-16-ASM](https://github.com/pedromsantos/ObjC-DCPU-16-ASM) also implements DCPU16 according to the same specs, but instead of using C# it's developed in Objective-C and CocoaTouch. 

It has been great fun and a great learning experience implementing an assembler and emulator from scratch.

The Objcetive-C implementations is a bit more mature regarding end to end functionality. It even has a barely functional UI :) Regarding code, the C# implementation is much more mature, I was able to implement it using a much pure OO approach. 

It was quite a chalange implementing the project using an OO aproach since in all my previous implementations of Lexers and Parsers, used a procedural aproach. Also most of the implementations for DCPU16, I found, where using mostly a procedural implementation, even the ones developed with OO languages.
