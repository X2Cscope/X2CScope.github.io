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
|  dsPIC33CK256MP508 | 16bit dsPIC33C | LVMC | [MCC](firmware/mcc.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33CK_LVMC.X"> Download</a>{: .btn .btn-purple}|
|  dsPIC33CK256MP508 | 16bit dsPIC33C | LVMC | [Bare/Custom](firmware/baremetal.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33CK_LVMC_customHAL.X"> Download</a>{: .btn .btn-purple}|
| dsPIC33EP256MC502  | 16bit dsPIC33E | X2C Dev Board | [MCC](firmware/mcc.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_dsPIC33EP_X2CDevBoard.X"> Download</a>{: .btn .btn-purple}|
| ATSAME51J20A | 32bit Cortex-M4 | SAME51 Curiosity nano | [Harmony](firmware/harmony.md) | <a href="https://github.com/X2Cscope/X2Cscope_blinky_SAME51_CNANO"> Download</a>{: .btn .btn-purple}|


## Prepared libraries

<a href="https://github.com/X2Cscope/X2Cscope_library_make/releases"> Download</a>{: .btn .btn-purple}

The package contains the precompiled X2Cscope libraries for the most popular [Microchip MCUs](https://www.microchip.com/mcu). You can use these libs to integrate X2Cscope tool to your custom/bare metal application. (See X2Cscope firmware tutorial [page](firmware/baremetal.md))

| MCU family | Architecture | default scope size [bytes] | lib name | Compiler |
| --- | ----- | ---------- | --------- | ----- |
| SAMD2x | 32bit Cortex-M0 | 5000 | libx2cscope-cm0-elf.a | XC32 v2.50 |
| SAME5x | 32bit Cortex-M4 | 5000 | libx2cscope-cm4-elf.a | XC32 v2.50 |
| SAME70 | 32bit Cortex-M7 | 5000 | libx2cscope-cm7-elf.a | XC32 v2.50 |
| dsPIC33CH Master core | 16bit dsPIC33C | 5000 | libx2cscope-33ch_master-elf.a | XC16 v1.60 |
| dsPIC33CH Slave core | 16bit dsPIC33C | 2500 | libx2cscope-33ch_slave-elf.a | XC16 v1.60 |
| dsPIC33CK MP | 16bit dsPIC33C | 5000 | libx2cscope-33ck-elf.a | XC16 v1.60 |
| dsPIC33CK MC | 16bit dsPIC33C | 5000 | libx2cscope-33ck_mc-elf.a | XC16 v1.60 |
| dsPIC33EP | 16bit dsPIC33E | 5000 | libx2cscope-33ep-elf.a | XC16 v1.60 |
| dsPIC33FJ | 16bit dsPIC33F | 5000 | libx2cscope-33fj-elf.a | XC16 v1.60 | 
| PIC24FJ | 16bit PIC24 | 5000 | libx2cscope-24fj-elf.a | XC16 v1.60 |
| PIC32MM | 32bit MIPS microAptiv | 5000 | libx2cscope-32mm-elf.a | XC32 v2.50 | 
| PIC32MX | 32bit MIPS M4K | 5000 | libx2cscope-32mx-elf.a | XC32 v2.50 |
| PIC32MZ | 32bit MIPS M-Class | 5000 | libx2cscope-32mz-elf.a | XC32 v2.50 |


## * 8bit limitation

X2Cscope implementation is using dynamic function pointers. Some of our low-end 8bit MCUs does not support it.
Contact us for more details: [https://www.microchip.com/support](https://www.microchip.com/support)