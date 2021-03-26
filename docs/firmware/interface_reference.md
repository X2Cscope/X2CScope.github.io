---
layout: default
title: API reference
parent: X2Cscope firmware
nav_order: 4
---

# X2Cscope firmware library interface reference

There are 4 public interface available at the precompiled library.

## X2CScope_Initialise
```c
void X2CScope_Initialise(void);
```
This must be called befure using X2Cscope.
This initialise the buffer and LNET protocol. 
**Example**
```c

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
void X2Cscope_init(void){ //Call this ar init section
    X2CScope_HookUARTFunctions(
        sendSerial, 
        receiveSerial, 
        isReceiveDataAvailable, 
        isSendReady
        );
    X2CScope_Initialise(); // Library built in function for buffer and LNET protocol initialise
}
```

## X2Cscope_update

**Example**
```c

```


## X2Cscope_communicate;

X2Cscope_update(); must be called with exact same periodicity to have proper scope sampling. Therefore I will use the timer interrupt in my application with 1 ms. This will provide me 1kHz sampling. Of course you can go faster, if you need more details of the analog signals.

**Example**
```c

```