---
layout: default
title: Overview
nav_order: 1
---
# X2Cscope

X2CScope is a runtime, online/live debugger for [Microchip](https://www.microchip.com/) microcontrollers. 
X2Cscope is for generic use in any embedded application and perfectly fits for signal processing related applications.

Visit Microchip University training platform to find our tutorial video: [http://microchip.com/mu](http://microchip.com/mu)

![AnimatedScope](images/Scope_Animated.gif)

## Overview

X2Cscope debugging set-up is similar to the standard ICSP/SWD/JTAG debugging session.
An IDE is used on the PC to help your software development process and the PC is connected to the target application MCU for debugging.  X2Cscope is a comprehensive package that has GUI on the PC side and a minimal firmware library on the target side.

![MCU<->PC](/images/overview_1.png)

The main difference (to ICSP/SWD/JTAG) is the X2Cscope uses builtin peripherals like UART, CAN, TCP/IP and does not need external debugger tool. (Therefore it is dirt cheap.) Additionally it supports run-time data transfers. In other words, it is possible to read **and write** variables without stopping the target MCU execution. This is very handy at motor control and power control applications. (Of course it can be used at any kind of applications.)

## Quick start

You will need:
1. X2Cscope plugin in MPLAB X [How to use the plugin](docs/MPLABX_Plugin.md)
2. HW with Microchip MCU [Supported MCUs](docs/supportedHW.md)
3. Firmware with X2Cscope library  (Guide to integrate)
4. USB-UART converter (UART interface is recommended for learning phase)

The recommended way to start is to use one of the prepared demo.

1. Download one of our prepared [demos](docs/supportedHW.md).
2. Build the demo project with MPLAB X.
3. Program the target hardware.
4. Connect USB-UART converter to the HW and the PC.
5. Open X2Cscope plugin. (MPLAB X top bar --> Tools --> X2Cscope)
6. Configure and select COM port. Baud rate is 115200 at most of the demos. (check device manager if needed for COM number)
7. Connect with X2Cscope to the hardware.
8. Use scope and watch views.

## Slow start

The X2Cscope can be used with any 8bit*, 16bit and 32bit Microchip MCUs. To integarate X2Cscope to a custom application, follow the detailed description at [X2Cscope custom firmware integration chapter.](/docs/firmware/X2CscopeFirmware.md)