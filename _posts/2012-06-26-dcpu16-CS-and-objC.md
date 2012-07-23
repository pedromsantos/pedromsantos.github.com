---
layout: default
published: true
title: DCPU16.Net and ObjC-DCPU-16-ASM
categories: [Software crafting]
tags: [OpenSource, C#, Objective-C, DCPU16]
---

[DCPU16.Net](https://github.com/pedromsantos/DCPU16.Net) is a software implementation of DCPU16 according to the specs @notch published [here](http://0x10c.com/doc/dcpu-16.txt). Thr project is developed in C# and uses the .Net framework.

[ObjC-DCPU-16-ASM](https://github.com/pedromsantos/ObjC-DCPU-16-ASM) also implements DCPU16 according to the same specs, but instead of using C# it's developed in Objective-C and CocoaTouch. 

It has been great fun and a great learning experience implementing an assembler and emulator from scratch.

The Objcetive-C implementations is a bit more mature regarding end to end functionality. It even has a barely functional UI :) Regarding code, the C# implementation is much more mature, I was able to implement it using a much pure OO approach. 

It was quite a chalange implementing the project using an OO aproach since in all my previous implementations of Lexers and Parsers, used a procedural aproach. Also most of the implementations for DCPU16, I found, where using mostly a procedural implementation, even the ones developed with OO languages.

##Project structure

###Lexer
<i>Responsability:</i> Source code tokenization.
    
<p><i>Implementation details:</i></p>
<p>A Lexer converts source code in text format into a set of defined tokens. A typical parser usualy exposes peek token and a consume next token. The first reads the next token without cosuming it and the second reads and consumes a token.</p>

<p>The Lexer exposes NextToken and a ConsumeTokenUsingStrategy for token consuption. The behaviour of NextToken can be defined at contruct time or at run time by defining the IgnoreTokenStrategy and the ConsumeTokenStrategy. The IgnoreTokenStrategy allows client code the define behaviour regarding any tokens that it wants to be ignored by the Lexer. The ConsumeTokenStrategy allows client code to define behaviour regarding token consuption. The project implements: IgnoreNoneTokenStrategy, IgnoreWhiteSpaceTokenStrategy, PeekTokenStrategy and ConsumeTokenStrategy.</p>

<p>The parameterless Lexer contructor creates a Lexer using the IgnoreNoneTokenStrategy and the PeekTokenStrategy.</p>

<p>As a tokenizer the Lexer uses regular expressions.</p>

* Sample usage
	* [C#](https://github.com/pedromsantos/DCPU16.Net/blob/master/LexerTests/LexerTests.cs)
	* [Objective-C](https://github.com/pedromsantos/ObjC-DCPU-16-ASM/blob/master/DCPU16EmulatorTests/LexerTests.m)
    
###Parser
<i>Responsability:</i> Parse tokens from Lexer into Statments.
    
<p><i>Implementation details:</i></p>
<p>The Parser transforms Lexer token into Model/Statments following the of rules defined by the language. A Stament is composed of an opcode folowed by Operand A and Operand B. Optionaly it can include a label and data.</p>

* Sample usage
	* [C#](https://github.com/pedromsantos/DCPU16.Net/blob/master/ParserTests/ParserTests.cs)
	* [Objective-C](https://github.com/pedromsantos/ObjC-DCPU-16-ASM/blob/master/DCPU16EmulatorTests/ParserTests.m)
    
###Assembler
<i>Responsability:</i> Generate machine code from parser Statments.

<p><i>Implementation details:</i></p>

* Sample usage
	* [C#](https://github.com/pedromsantos/DCPU16.Net/blob/master/AssemblerTests/AssemblesIntegrationTests.cs)
	* [Objective-C](https://github.com/pedromsantos/ObjC-DCPU-16-ASM/blob/master/DCPU16EmulatorTests/AssemblerTests.m)

###Emulator
<i>Responsability:</i> Instruction execution.
    
###DCPU16Assembler
<i>Responsability:</i> Console program that converts DCPU16 source code into an executable machine language program.

###Model
<i>Responsability:</i> Cross project data.