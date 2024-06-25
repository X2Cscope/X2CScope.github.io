---
layout: default
title: Demos/Downloads
nav_order: 5
---

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Supported Hardware

X2Cscope firmware side library is written in standard C. Therefore the whole [Microchip](https://www.microchip.com/) 8bit*, 16bit, 32bit MCU portfolio is supported.

## Plug and play demos

All of the demos are hosted on github: <a href="https://github.com/x2cscope">https://github.com/x2cscope</a>

| MCU | Arch. | Demo board | Configurator | link |
| --- | ----- | ---------- | ---- |--------- |
|  dsPIC33CK256MP508 | 16bit dsPIC33C | Curiosity | [Bare/Custom](firmware/baremetal.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33CK_CURIO_customHAL.X"> Download</a>{: .btn .btn-purple}|
|  dsPIC33CK256MP508 | 16bit dsPIC33C | LVMC | [MCC](firmware/mcc.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33CK_LVMC.X"> Download</a>{: .btn .btn-purple}|
|  dsPIC33CK256MP508 | 16bit dsPIC33C | LVMC | [Bare/Custom](firmware/baremetal.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33CK_LVMC_customHAL.X"> Download</a>{: .btn .btn-purple}|
| dsPIC33EP256MC502  | 16bit dsPIC33E | X2C Dev Board | [MCC](firmware/mcc.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33EP_X2CDevBoard.X"> Download</a>{: .btn .btn-purple}|
| ATSAME51J20A | 32bit Cortex-M4 | SAME51 Curiosity nano | [Harmony](firmware/harmony.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_SAME51_CNANO"> Download</a>{: .btn .btn-purple}|


## Prepared libraries

<a href="https://github.com/X2Cscope/X2Cscope_library_make/releases"> Download</a>{: .btn .btn-purple}

The package contains the precompiled X2Cscope libraries for the most popular [Microchip MCUs](https://www.microchip.com/mcu). You can use these libs to integrate X2Cscope tool to your custom/bare metal application. (See X2Cscope firmware tutorial [page](firmware/baremetal.md))

* PIC32MM
* PIC32MX
* PIC32MZ
* SAMD2x	32bit Cortex-M0
* SAME5x	32bit Cortex-M4
* SAME70	32bit Cortex-M7
* dsPIC33CH Main core
* dsPIC33CH Secondary core
* dsPIC33CK_MP
* dsPIC33CK_MC
* dsPIC33EP
* dsPIC33FJ
* PIC24FJ
* PIC24EP



## * 8bit limitation

X2Cscope implementation is using dynamic function pointers. Some of our low-end 8bit MCUs does not support it.
Contact us for more details: [https://www.microchip.com/support](https://www.microchip.com/support)