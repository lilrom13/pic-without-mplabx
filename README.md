# Pic without MPLABX

The goal is to see how far I can go with PIC development without MPLAB X.

MPLAB X is a good tool, but I've been using VScode for many years now, and I've got used to it, and it is hard for me to use something else now.
After a quick search, I haven't find any suitable solution for my problem so let dig into the feasibility of my idea.

## existing solution:

platform IO is a plugin for VScode that allows embedded development for many platforms but not the PIC33, and is it more a hobbyist tool than a professional solution.

## POC:
  - compile a project with xc16 compiler
  - program a target
  - debug a target
  - include a build tool
  - include a TDD solution 

## research:

### compilation:
In a first time, it should be possible to edit intelliSense C/C++ extension to call the xc16 compiler. An extension might be usefull later on.

### programming:
Microchip provides a command line tool for programming a pic microcontroller, I have to find how to interface it with vscode, probably with the c/c++ extension.
But the problem with this solution is that Microchip tools are written in java and need to be excuted in a jre. It's an heavy solution. Other option is to write a programming utlity with in a different language as c++ or python.
[DsPIC33E/PIC24E Flash Programming Specification](http://ww1.microchip.com/downloads/en/DeviceDoc/70619B.pdf) gives more information on the programmation process.

### debugging:

Microchip provides command line tools that should help me.

[DAP](https://microsoft.github.io/debug-adapter-protocol/) - Debug Adapter Protocol - will allow me to implement the debugging interface for vscode. All I have to do is write my debug adapter based on [MDB user guide](http://ww1.microchip.com/downloads/en/DeviceDoc/50002102D.pdf).

One of the best option to consider is create a dedicated dspic33 platform for the [platform.io](https://platformio.org/) project.

But same problem here. The debug utily provides by microchip is written is java.

### Work in progress

I've decided to start with the creation of a programmation utily first, this utily lives in [\pic33-programmer](https://github.com/lilrom13/pic-without-mplabx/edit/main/pic33-programmer\README.md)

