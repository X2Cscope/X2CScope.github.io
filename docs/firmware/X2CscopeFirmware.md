---
layout: default
title: X2Cscope firmware
has_children: true
nav_order: 3
---
# X2Cscope Firmware

X2Cscope is implemented in C, therefore it can be integrated into a wide range of embedded application. We provide a prepared library ([see download section](../supportedHW.md)) and it can be integrated to C based application seamlessly. It is using minimal resources from the target MCU. 

The minimal requirements:
* 6-10 kByte flash (depends on the CPU architecture)
* 0.5 kByte RAM + Scope size (Can be lower, this is just default scope windows size)
* Serial communication peripheral (UART, CAN, USB-CDC or Ethernet with TCP/IP)

![Architecture](/images/architecture.png)


There are 3 ways to integrate X2Cscope to your application:
1. [MPLAB Code Configurator](mcc.md) 
   * 16bit Microchip MCUs like dsPIC33CK
2. [Harmony 3 configurator](harmony.md)
   * 32bit MCUs like PIC32MZ or SAME54 ([Official Harmony documentation](https://microchip-mplab-harmony.github.io/x2c/))
3. [Bare matal integration for custom projects](baremetal.md)
   * If your code is already available and no configurator tool is used. 
   * Or for engineers who are believing only in their own handwritten code. 


There are 3 main interfaces, that must be integrated into your application. 
* `X2Cscope_init();`
* `X2Cscope_update();`
* `X2Cscope_communicate();`


![X2Cscope APIs](/images/X2CscopeAPIs.png)

### X2Cscope_init(); 

Must be called before using other X2Cscope interfaces. If you are using code configurator, like MCC or Harmony, this will be done automatically. In case of custom framework, then you have to call this function explicitly. The X2Cscope initialise routine connects the serial peripheral interfaces, initialises LNET protocol, buffers and functions.

### X2Cscope_communicate(); 

This function is not very time critical. This can executed in a low level task in an RTOS environment, or in the IDLE loop with OS free application. This must be done manually as it highly depends on the final application implementation. *X2Cscope_communicate();* handles the communication with the MPLAB X plugin on the PC side. Make sure there is always some time leftover to execute this function, itherwise you can get time out errors on the PC side.

### X2Cscope_update(); 

This is the sample point of the scope, therefore this must be called with same fixed periodicity as it is selected in the X2Cscope plugin settings on the PC side. Otherwise the time domain will not match in the scope view. If you select a variable for the scope channel on the PC side, then this function will start to stream the values of the selected variables to reserved RAM buffer. Once the buffer is full then it will be transferred to the PC and plotted to the scope view. 5kByte is reserved for the buffer by default, but can be changed.
