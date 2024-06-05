---
layout: default
title: Overview
nav_order: 1
---

<img src="images/X2Cscope_logo.png" alt="LOGO" align="left" style="padding-right: 15px" width="150"/>

X2CScope is a runtime, online/live debugger for [Microchip](https://www.microchip.com/) microcontrollers. 
X2Cscope is for generic use in any embedded application and perfectly fits for signal processing related applications. [pyX2Cscope](https://x2cscope.github.io/pyx2cscope/) scripting interfaces enabled the system for automated HIL tests. 

Visit Microchip University training platform for our training video: [http://microchip.com/mu](http://microchip.com/mu)

## Overview

X2Cscope is a comprehensive debugging package:
* PC side package called [pyX2Cscope](https://x2cscope.github.io/pyx2cscope/) 
* C implemented library for emebedded systems (MCUs) [demos](docs/supportedHW.md)

![MCU<->PC](/images/overview.gif)

The main difference (to ICSP/SWD/JTAG) is the X2Cscope enabled firmware uses builtin peripherals like UART, CAN, TCP/IP and does not need external debugger tool. Additionally it supports run-time data transfers. In other words, it is possible to read **and write** variables without stopping the target MCU execution. This is very handy at motor control and power control applications. (Of course it can be used at any kind of applications.)

## Quick start

You will need:
1. pyX2Cscope python package [How to use the python package](https://x2cscope.github.io/pyx2cscope/)
2. HW with Microchip MCU [Supported MCUs](docs/supportedHW.md)
3. Firmware with X2Cscope library  [Guide to integrate](docs/firmware/X2CscopeFirmware.md)
4. USB-UART converter (UART interface is recommended for learning phase)

The recommended way to start is to use one of the prepared demo.

1. Download one of our prepared [demos](docs/supportedHW.md).
2. Build the demo project with MPLAB X.
3. Program the target hardware.
4. Connect USB-UART converter to the HW and the PC.
5. Open pyX2Cscope [How to use the python package](https://x2cscope.github.io/pyx2cscope/)
    a. `pip install pyX2Cscope`
    b. `python -m pyx2cscope`
6. Configure and select COM port. Baud rate is 115200 at most of the demos. (check device manager if needed for COM number)
7. Connect with pyX2Cscope to the hardware. (Click connect button)
8. Use scope and watch views.

## Slow start

The X2Cscope can be used with any 8bit*, 16bit and 32bit Microchip MCUs. To integarate X2Cscope to a custom application, follow the detailed description at [X2Cscope custom firmware integration chapter.](/docs/firmware/X2CscopeFirmware.md)