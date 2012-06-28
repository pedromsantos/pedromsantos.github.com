---
layout: default
published: false
title: DCPU16.Net and ObjC-DCPU-16-ASM
categories: [Software crafting]
tags: [OpenSource, C#, Objective-C, DCPU16]
---
#DCPU16.Net and ObjC-DCPU-16-ASM

[DCPU16.Net](https://github.com/pedromsantos/DCPU16.Net) is a software implementation of DCPU16 according to the specs @notch published [here](http://0x10c.com/doc/dcpu-16.txt). Thr project is developed in C# and uses the .Net framework.

[ObjC-DCPU-16-ASM](https://github.com/pedromsantos/ObjC-DCPU-16-ASM) also implements DCPU16 according to the same specs, but instead of using C# it's developed in Objective-C and CocoaTouch. 

It has been great fun and a great learning experience implementing an assembler and emulator from scratch.

The Objcetive-C implementations is a bit more mature regarding end to end functionality. It even has a barely functional UI :) Regarding code, the C# implementation is much more mature, I was able to implement it using a much pure OO approach. 

It was quite a chalange implementing the project using an OO aproach since in all my previous implementations of Lexers and Parsers, used a procedural aproach. Also most of the implementations for DCPU16, I found, where using mostly a procedural implementation, even the ones developed with OO languages.

##DCPU16.Net

###Project structure

* Lexer
	* Responsible for source code tokenization.
    * Implementation details
    	* A Lexer converts source code in text format into a set of defined tokens. A typical parser usualy exposes peek token and a consume next token. The first reads the next token without cosuming it and the second reads and consumes a token. The DCPU16.Net Lexer is no exception it exposes NextToken and a ConsumeTokenUsingStrategy. The behaviour of NextToken can be defined at contruct time or at run time by defining the IgnoreTokenStrategy and the ConsumeTokenStrategy. The IgnoreTokenStrategy allows client code the define behaviour regarding any tokens that it wants to be ignored by the Lexer. The ConsumeTokenStrategy allows client code to define behaviour regarding token consuption. DCPU16.Net implements IgnoreWhiteSpaceTokenStrategy, PeekTokenStrategy and ConsumeTokenStrategy.
        
* Model
	* Resposible for cross project data.
    
* Parser
	* Responsible for parsing tokens from Lexer into Statments.
    
* Assembler
	* Responsible for code generation from parser Statments.
    
* Emulator
	* Responsible for instruction execution.
    
* DCPU16Assembler
	* Console program that converts DCPU16 source code into an executable machine language program.



##ObjC-DCPU-16-ASM
