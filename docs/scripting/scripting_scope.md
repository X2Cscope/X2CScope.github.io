---
layout: default
title: Scope API
parent: Scripting (legacy MPLAB X)
nav_order: 2
---

# Recommended to use the new python package for scripting: [https://x2cscope.github.io/pyx2cscope/](https://x2cscope.github.io/)

The MPLAB X plugin is not updated anymore.

# `x2c_scope`

Scope Control Interface variable preinitialised as: `public interface IScopeManager`

## `void setChannelConfig(int channel, String identifier, double gain, double offset) throws Exception`

Sets up channel configuration.

 * **Parameters:**
   * `channel` — Channel number
   * `identifier` — Symbol identifier
   * `gain` — Gain
   * `offset` — Offset
 * **Exceptions:** `Exception` — if invalid channel number<br>
	if invalid identifier
	 
###  Example
```python
x2c_scope.setChannelConfig(7, "myStruct.sinus", 1, 0) # Set channel 7 to monitor the sinus variable
```

## `void setTrigger(int srcChannel, double level, String edge, int delay) throws Exception`

Sets up and enables trigger configuration by channel number.

 * **Parameters:**
   * `srcChannel` — Trigger source: channel number
   * `level` — Trigger level
   * `edge` — Trigger edge (RISING or FALLING)
   * `delay` — Delay
 * **Exceptions:** `Exception` — if invalid source channel number<br>
     if selected source channel is not configured<br>
     if invalid trigger edge value<br>
     if delay is out of bounds

###  Example
```python
x2c_scope.setChannelConfig(7, "myStruct.sinus", 1, 0) # Set channel 7 to monitor the sinus variable
x2c_scope.setTrigger(7, -0.7, "RISING", 0)# Set trigger to channel 7
```

## `void setTrigger(String identifier, double level, String edge, int delay) throws Exception`

Sets up and enables trigger configuration by symbol identifier.

 * **Parameters:**
   * `identifier` — Trigger source: Symbol identifier
   * `level` — Trigger level
   * `edge` — Trigger edge (RISING or FALLING)
   * `delay` — Delay
 * **Exceptions:** `Exception` — if invalid identfier<br>
     invalid trigger edge value<br>
     if delay is out of bounds

###  Example
```python
x2c_scope.setChannelConfig(7, "myStruct.sinus", 1, 0) # Set channel 7 to monitor the sinus variable
x2c_scope.setTrigger(7, -0.7, "RISING", 0)# Set trigger to channel 7
```

## `void clearTrigger()`

Clears and disables trigger configuration.

###  Example
```python
x2c_scope.clearTrigger()
```

## `void clearChannelConfig(int channelNo) throws Exception`

Clears channel configuration.

 * **Parameters:** `channelNo` — Channel number
 * **Exceptions:** `Exception` — Invalid channel number

## `void clearChannelConfigs()`

Clears all channel configurations.

###  Example
```python
x2c_scope.clearChannelConfigs() # clear all channel
```

## `void setSampleTimeFactor(int factor) throws Exception`

Sets sample time factor.

 * **Parameters:** `factor` — Sample time factor
 * **Exceptions:** `Exception` — Invalid value (less than 1)

###  Example
```python
x2c_scope.setSampleTimeFactor(1) # sample time "divider" increases the sampling time
```

## `void sample(boolean waitForCompletion) throws Exception`

Starts sample in blocking or non-blocking kind.

 * **Parameters:** `waitForCompletion` — true to block until sample completion, false for non-blocking mode
 * **Exceptions:** `Exception` — if a communication problem occurs

###  Example
```python
x2c_scope.setChannelConfig(2, "myStruct.rad", 1, 0) #setup channel
x2c_scope.sample(False) #false-> non blocking
```

## `boolean isSampleComplete() throws Exception`

Returns Scope sampling state. Usually being used with {@link #sample(boolean)} in non-blocking mode.

 * **Returns:** true if sampling has completed, false if it's yet in progress
 * **Exceptions:** `Exception` — if a communication problem occurs

###  Example
```python
x2c_scope.sample(False) #false-> non blocking
		
print "Wait for scope sample finish"
while not x2c_scope.isSampleComplete():
	time.sleep(0.1)
```

## `void uploadData() throws Exception`

Uploads sampled data from target.

 * **Exceptions:** `Exception` — if a communication problem occurs<br>

     if a sample is in progress

###  Example
```python
x2c_scope.uploadData() #Upload the data from the hardware
data = x2c_scope.getData() #get the uploaded data
```

## `double[][] getData()`

Returns sampled data. Must be preceded by an uploadData() call for up-to-date data.

 * **Returns:** Sampled data

###  Example
```python
x2c_scope.uploadData() #Upload the data from the hardware
data = x2c_scope.getData() #get the uploaded data
```

## `void setSampleTime(double ts)`

Sets Scope sample time. Used for time vector calculation.

 * **Parameters:** `ts` — Sample time
 
###  Example
```python
#set sample time to 50us
#Should be same as X2Cscope_Update call period
x2c_scope.setSampleTime(0.00005) 
```