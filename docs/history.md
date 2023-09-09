## CAN Interface API by UV Software

Originally, the CAN Interface API was based on a CAN interface definition as part of a microcontroller hardware abstraction layer for an 82527-compatible on-chip CAN controller. It was developed for use by (simple hand-coded) CANopen applications and migrated to different microcontroller types (even if the CAN peripherals on that micro had a different design).

### CAN API V1

What works on microcontrollers should also work on PC. I started to use this interface definition as a wrapper specification for different CAN devices from various vendors: e.g. for IXXAT, PEAK, Vector, Kvaser, and also for Linux-CAN (aka SocketCAN).

### CAN API V2

Dealing around with 14 virtual Basic-CAN messages boxes and a FIFO upon a virtual Full-CAN message box was a little bit over-engineered and error-prone. I optimized the interface definition to have an easy to use API following an *init-start-read-write-stop-exit* pattern.

### CAN API V3

Version 3 is the latest adaption of the CAN API wrapper specification. As new features it supports CAN FD long frames and fast frames, selectable operation modes, blocking read, and is multi-channel capable. Additionally it provides companion modules for bit-rate conversion and message formatting.


[copyright](/copyright.md ':include')