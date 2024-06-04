---
layout: default
title: X2Cscope plugin (legacy)
nav_order: 7
---
# X2Cscope plugin for MPLAB X 
{: .no_toc}

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
# New python implementation!

The Python implementation can be found at pyx2cscope: https://x2cscope.github.io/pyx2cscope/

!The documentation below is for the not maintained MPLAB X plugin!

## Install X2Cscope plugin within MPLAB X

You will need MPLAB X IDE v5.40 or newer. [www.microchip.com/mplabx](https://microchip.com/mplabx)

1. Open MPLAB X IDE.
2. Navigate to Tools-->Plugins at the top bar.
3. Slect X2Cscope for install.
4. Restart MPLAB X IDE.
5. Open X2Cscope from Tools->Embedded->X2Cscope

![X2Cscope plugin install](/images/X2CscopePluginInstall.gif)

## Connect X2Cscope to the device

1. Select project 

MPLAB X support multiple project to be open, so we have to select which one to use for X2Cscope debugging.

![selectProject](/images/GUI/select_project.png)

2. Set communication configuration

Set the communication(Serial, CAN, TCP/IP) configuration according to the HW settings. Demos are using UART (Serial) set to 115200 8N1 by default. Check the serial port at the device manager, if you have multiple COM port.

![UARTSettings](/images/GUI/uart_settings.png)

3. Program your device

At this point make sure your program is running on the target device with the integrated X2Cscope library with the same communication configuration. Build the code and program your device if needed. Connect phisical communication connectors to the PC and to the hardware. 

4. Connect to the Device

Click on the disconnected connector icon to connect to your device.

![Connect](/images/GUI/connect.png)

If you get an error message:

![Error](/images/GUI/error.png)

Then go to the project settings (Right Click on the project and select Properties menu). Select the Loading category and tick the "Load symbols when programming or build for production" option. 

![LoadSymbols](/images/GUI/load_symbols.png)

Then apply the new settings. Then do points from 1. to 4. again.


## Use the Watch window

1. Set watch sampletime. (This will be the refresh rate of the watch window)
2. Open Watch window from Data Views tab.
3. Add/Select variables to the watch list.
4. The actual values of the selected variables will be visible in run-time.
5. Values of the variables can be modified. The new assigned value will be sent to the target device in run time!
6. Scaling, offset and unit boxes can be used for easier representation. (These parameters will be automatically saved.)

![UseWatch](/images/GUI/use_watch.gif)

## Use the Scope window

1. Set sample time of scope. Attention! Set this according to the period of X2CScope_update(); function call. (See [Firmware guide](firmware/X2CscopeFirmware.md).)
2. Open Scope window from Data Views tab.
3. Click to the empty Source box to select source signal/variable.
4. Click Sample to start the scope.
5. Uncheck "Single-shot" to do continuous sampling.
6. Use trigger settings if neccesary.

![UseScope](/images/GUI/use_scope.gif)
