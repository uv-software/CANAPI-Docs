## CAN Interface API by UV Software

### Abstract

> **CAN API V3** is a wrapper specification by UV Software to have a uniform CAN Interface API for various CAN interfaces from different vendors running under multiple operating systems.

### Scope

The goal of the CAN API V3 project is to have a multi-vendor, cross-platform CAN Interface API (Application Programming Interface). Each CAN adapter manufacturer provides its own CAN software SDK (Software Development Kit) for the development of CAN applications based on the provided SDK. Unfortunately, the APIs of the different manufacturers are not compatible with each other. The CAN Interface API by UV Software (CAN API V3) solves the problems arising from this incompatibility.

This documentation is a generic description of the CAN API V3 Software Development Kit. It describes all functions, methods, attributes, properties, and data types of the CAN API V3 Application Programming Interface without referencing the specifics of the individual CAN API V3 implementations.

On the other hand, this documentation serves as a requirements specification for the implementation of a CAN API V3 wrapper library based upon a vendor-specific SDK or based upon an own CAN driver implementation. You just need to add the word “shall” to each sentence in your mind.

### API

The CAN API V3 application programming interface is defined for the **C** programming language.
The wrapper implementations also provide application programming interfaces for **C++** and **Swift** (macOS&reg; only).

CAN API V3 provides the following main functions respectively methods:

[can_test()](/reference/can_test#can_test) respectively [ProbeChannel()](/reference/can_test#probechannel) - probe if a CAN channel is available

[can_init()](/reference/can_init#can_init) respectively [InitializeChannel()](/reference/can_init#initializechannel) - initialize a CAN channel

[can_exit()](/reference/can_exit#can_exit) respectively [TeardownChannel()](/reference/can_exit#teardownchannel) - teardown a CAN channel

[can_kill()](/reference/can_kill#can_kill) respectively [SignalChannel()](/reference/can_kill#signalchannel) - signal waiting event objects of a CAN channel

[can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller) - start the CAN controller of a CAN channel

[can_reset()](/reference/can_reset#can_reset) respectively [ResetController()](/reference/can_reset#resetcontroller) - stop the CAN controller of a CAN channel

[can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage) - send a CAN message on a CAN channel

[can_read()](/reference/can_read#can_read) respectively [ReadMessage()](/reference/can_read#readmessage) - read one CAN message from the receive queue of a CAN channel

[can_status()](/reference/can_status#can_status) respectively [GetStatus()](/reference/can_status#getstatus) - get the [status register](/reference/status_register#name) from the CAN controller of a CAN channel

[can_bitrate()](/reference/can_bitrate#can_bitrate) respectively [GetBitrate()](/reference/can_bitrate#getbitrate) and [GetBusSpeed()](/reference/can_bitrate#getbusspeed) - get the CAN bit-rate settings from the CAN controller of a CAN channel

[can_property()](/reference/can_property#can_property) respectively [GetProperty()](/reference/can_property#getproperty) and [SetProperty()](/reference/can_property#setproperty) - get or modify a property value of a CAN channel or of the CAN API library

### Wrapper

Several CAN API V3 wrapper implementations exist for Windows&reg;, macOS&reg; and Linux&reg;. They can be downloaded from / cloned at my GitHub repositories.

Please note the copyright and license agreements in the appropriated repository.

#### Windows&reg;

[CAN API V3 Wrapper Library for Peak-System PCAN® Interfaces](https://github.com/uv-software/PCANBasic-Wrapper)

[CAN API V3 Wrapper Library for Kvaser CAN Interfaces](https://github.com/uv-software/KvaserCAN-Wrapper)

[Library for CAN-over-Serial-Line Interfaces (SLCAN Protocol)](https://github.com/uv-software/SerialCAN)

#### macOS&reg;

[CAN API V3 Wrapper Library for PCAN-USB Interfaces from PEAK-System](https://github.com/mac-can/PCBUSB-Wrapper)

[macOS® Driver and SDK for USB CAN Interfaces from Kvaser](https://github.com/mac-can/KvaserCAN-Library)

[macOS® Driver and SDK for TouCAN USB Interfaces from Rusoku](https://github.com/mac-can/RusokuCAN.dylib)

[Library for CAN-over-Serial-Line Interfaces (SLCAN Protocol)](https://github.com/mac-can/SerialCAN)

#### Linux&reg;

[Library for CAN-over-Serial-Line Interfaces (SLCAN Protocol)](https://github.com/mac-can/SerialCAN)

### Donate

These projects are developed and maintained in my spare time.
If you like them (all of them, or just one) I would be very happy if you donate to my work.


[copyright](/copyright.md ':include')