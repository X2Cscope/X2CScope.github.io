---
layout: default
title: API reference
parent: X2Cscope firmware
nav_order: 4
---

# X2Cscope firmware library interface reference
{:.no_toc}

### There are 4 public interfaces available at the precompiled library:
{: .no_toc .text-delta }

1. TOC
{:toc}


## X2CScope_Initialise
```c
void X2CScope_Initialise(void);
```
This must be called before using X2Cscope.
This initialises the buffer and LNET protocol. 
**Example**
```c
void X2Cscope_init(void){ //Call this at HW init section
    X2CScope_HookUARTFunctions( 
        sendSerial, 
        receiveSerial, 
        isReceiveDataAvailable, 
        isSendReady
        ); //Set communication interfaces
    X2CScope_Initialise(); // Library built in function for buffer and LNET protocol initialise
}
```

## X2CScope_HookUARTFunctions
```c
void X2CScope_HookUARTFunctions(
    void (*sendSerialFcnPntr)(uint8_t), 
    uint8_t (*receiveSerialFcnPntr)(), 
    uint8_t (*isReceiveDataAvailableFcnPntr)(), 
    uint8_t (*isSendReadyFcnPntr)()
);
```
This function connects the X2Cscope library communication functions with the peripheral functions via the function pointers in the parameters.

| parameter | type | description |
|-----------|------|-------------| 
| sendSerialFcnPntr | functionPointer | function to send byte to the PC |
| receiveSerialFcnPntr | functionPointer | function to receive byte from the PC |
| isReceiveDataAvailableFcnPntr | functionPointer | function check received byte available |
| isSendReadyFcnPntr | functionPointer | function check available free space in buffer for sending byte |

**Example**
```c
// First implement communicate functions
void sendSerial(uint8_t data)
{
    U1TXREG = data;   
}
uint8_t receiveSerial()
{
    return U1RXREG; 
}
uint8_t isReceiveDataAvailable()
{
    return (U1STAbits.URXDA == 1); //Status RX data available
}
uint8_t isSendReady()
{
    return (U1STAbits.UTXBF == 0); //Status TX buffer full
}

// Then hook the functions at the init
void X2Cscope_init(void){ //Call this at HW init section
    X2CScope_HookUARTFunctions(
        sendSerial, 
        receiveSerial, 
        isReceiveDataAvailable, 
        isSendReady
        ); //Set communication interfaces
    X2CScope_Initialise(); // Library built in function for buffer and LNET protocol initialise
}
```

## X2Cscope_update

X2Cscope_update(); must be called with exact same periodicity to have proper scope sampling. Timer, PWM or any other periodic interrupt is perfect place to call it. 1kHz-50kHz is the recommended sampling period.

**Example**
```c
// 1ms fixed period timer interrupt
void __attribute__ ( ( interrupt, no_auto_psv ) ) _T1Interrupt (  )
{
    X2CScope_Update(); // SAmple point of X2Cscope
    IFS0bits.T1IF = false; // Clear interrupt flag in the end
}

```


## X2Cscope_communicate

X2Cscope_communicate(); is a sync/non blocking cooperative task, that handles the communication with the X2Cscope plugin. This can be called in low priority task. Do not starve too much this task, otherwise you might get timeout error at X2Cscope PC side.

**Example**
```c
int main(void)
{
    // initialize the device
    initHardware();
    X2CScope_Init();
    ...
    while (1)
    {
        myAppTask(); //Low priority task in the idle loop
        X2CScope_Communicate(); //Handle the communication with X2Cscope GUI
    }
}
```