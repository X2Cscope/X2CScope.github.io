---
layout: default
title: Bare/Custom project
parent: X2Cscope firmware
nav_order: 3
---

# X2Cscope firmware manual set-up
{: .no_toc}
If you are advanced programmer and do not use configurator tools like [Harmony](harmony.md) or [MCC](mcc.md), then this guide will help you to use X2Cscope with your custom application.

You can find a detailed tutorial video at [Microcipp University](https://microchip.com/mu) training platform.

### Table of contents
{: .no_toc .text-delta }

* TOC
{:toc}

---

## 1. Get X2Cscope firmware library

1. [Download the Zip package](../supportedHW.md)
2. Copy the library file (which is corresponding to your selected MCU) from the Zip package to your project's folder
3. Copy the library header and source files from the Zip API folder to your project's folder

![FileCopyInstruction](/images/BareMetalFileCopy.png)

## 2. Add the files to your MPLAB X project

1. Create X2Cscope logical folders
2. Add X2CScope.c and X2CScopeComm.c source files to the MPLAB X project
3. Add X2CScope.h and X2CScopeComm.h header files to the MPLAB X project
4. Add X2Cscope libx2cscope-****.a library file to the MPLAB X project


![CopyFilesAnimations](/images/BareMetalAddFiles.gif)

## 3. Use/call the X2Cscope APIs

This is the most tricky part. The X2Cscope library can use different serial communication peripherals. The used communication peripheral sending/receiving functions must be connected to the X2Cscope library. This blockdiagram shows a high level overview of this mechanism.

![BareMetalAPI](/images/BareMetalAPIs.png)


1. Configure your communication peripheral. (UART 115200/8-N-1 is recommended.) 
2. Implement communication interfaces in the X2CScopeComm.c file. ([API reference](interface_reference.md))
   1. void sendSerial(uint8_t data)
   2. uint8_t receiveSerial()
   3. uint8_t isReceiveDataAvailable()
   4. uint8_t isSendReady() 
3. Initialise X2Cscope with X2CScope_Init(); ([API reference](interface_reference.md))
4. Call X2CScopeCommunicate(); at the main idle loop or as a low priority task ([API reference](interface_reference.md))
5. Call X2CScope_Update(); periodically at an interrupt. ([API reference](interface_reference.md))

## 4. Compile then use X2Cscope

At this stage the project is ready to use with X2Cscope.

1. Compile and program the device
2. Connect to the HW with the [X2Cscope GUI](/docs/MPLABX_Plugin.md)
3. [Use X2Cscope](/docs/MPLABX_Plugin.md) watch and scope windows
