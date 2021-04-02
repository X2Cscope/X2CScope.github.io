---
layout: default
title: MPLAB Harmony
parent: X2Cscope firmware
nav_order: 2
---

# X2Cscope frimware with Harmony
{: .no_toc}
<a href="https://www.microchip.com/mplab/harmony"><img src="../../images/harmony.png" alt="LOGO" align="right" style="padding-right: 15px" width="200"/></a>

Harmony v3 is a Embedded Software Development Framework for Microchip 32-bit Microcontrollers and Microprocessors.


To install and get started with Harmony v3 you can follow [this GUIDE](https://microchipdeveloper.com/harmony3:mhc-overview).

### Table of contents
{: .no_toc .text-delta }

* TOC
{:toc}



---


## 1. Install X2Cscope package to Harmony 3:

Install X2Cscope package with the Harmony conent manager.

1. Open MPLAB X IDE.
2. Open Tools-->Embedded-->MPLAB Harmony Content Manager at the top bar.
3. Use the default content repository.
4. Search for X2C at the Remote Packages
5. Download X2C package
6. Verify the installation: X2C package should be at Local Package

![HarmonyInstall](/images/Harmony/X2CscopeharmonyInstall.gif)

## 2. Configure and generate framework

Next step is to create the framework project with the Harmony 3. If you already have a project, then just add X2Cscope component and regenerate the framework project.

1. Create a new harmony project, or use existing project. ([Demos](../supportedHW.md))
2. Open Harmony configurator (Tools->Embedded)
3. Add X2Cscope component.
4. Add UART capable communication component.
5. Connect X2Cscope component with UART component.
6. Configure UART
7. Set-up IOs
8. (Optional) Add more component as required for your application.
9. Generate framework project.

![HarmonySetup](/images/Harmony/X2CscopeharmonySetupFramework.gif)

## 3. Add X2Cscope functions

The Harmony framework project automatically calls the X2Cscope initialisation routine, howerver there are still 2 functions we have to add manually to the code:
* [X2CScope_Communicate();](interface_reference.md)
* [X2CScope_Update();](interface_reference.md)

**Example:**

![call_X2CScope_Communicate.png](/images/Harmony/call_X2CScope_Communicate.png)

![call_X2CScope_Communicate.png](/images/Harmony/call_X2CScope_Update.png)

## 4. Compile then use X2Cscope

At this stage the project is ready to use with X2Cscope.

1. Compile and program the device
2. Connect to the HW with the [X2Cscope GUI](../MPLABX_Plugin.md)
3. [Use X2Cscope](../MPLABX_Plugin.md) watch and scope windows