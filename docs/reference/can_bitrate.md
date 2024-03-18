### NAME

> *can_bitrate* - get the CAN bit-rate settings of a CAN channel

### SYNOPSIS

<a id="can_bitrate"></a>
**C Interface**
```C
int can_bitrate(int handle, can_bitrate_t *bitrate, can_speed_t *speed);
```
<a id="GetBitrate"></a>
<a id="GetBusSpeed"></a>
**C++ Methods**
```C++
CANAPI_Return_t GetBitrate(CANAPI_Bitrate_t &bitrate);

CANAPI_Return_t GetBusSpeed(CANAPI_BusSpeed_t &speed);
```
<a id="var_bitrate"></a>
<a id="var_speed"></a>
**Swift Properties**
```Swift
public var bitrate: Bitrate?

public var speed: Speed?
```

### DESCRIPTION

The function [can_bitrate()](#can_bitrate) retrieves the bit-rate settings and data transmission speed (bus speed in [bit/s]) of the CAN channel given by the *handle* argument.

Upon successful completion, the current [bit-rate](/reference/bitrate_settings#can_bitrate_t) is stored in the variable pointed to by *bitrate*
and the current [bus speed](/reference/bitrate_settings#can_speed_t) in the variable pointed to by *speed*.
Both parameters are optional, that means NULL pointers can be passed as arguments. 

The method [GetBitrate()](#getbitrate) retrieves the bit-rate of a CAN channel
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

The method [GetBusSpeed()](#getbusspeed) retrieves the data transmission speed of a CAN channel
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

The Swift [bitrate](#var_bitrate) property contains the current [bit-rate](/reference/bitrate_settings#struct_bitrate) read from the associated CAN channel.
It is a read-only property.
The class instance from which the property is read must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

The Swift [speed](#var_speed) property contains the current [bus speed](reference/bitrate_settings#struct_speed) read from the associated CAN channel.
It is a read-only property.
The class instance from which the property is read must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

Upon successful completion, the Swift property contains the current bit-rate respectively bus speed. On error, it will be `Nil`.

### ERRORS

Under the following conditions, [can_bitrate()](#can_bitrate) respectively [GetBitrate()](#getbitrate) and [GetBusSpeed()](#getbusspeed) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit)   - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)     - invalid channel handle \
[CANERR_OFFLINE](/reference/error_codes#error_offline)   - controller not started \
[CANERR_BAUDRATE](/reference/error_codes#error_baudrate) - invalid bit-rate settings \
[CANERR_NOTSUPP](/reference/error_codes#error_notsupp)   - function not supported \
[others](/reference/error_codes#error_vendor)            - vendor-specific error codes

### EXAMPLES

#### C Example

None.

#### C++ Example

None.

#### Swift Example

None.

### SEE ALSO

[Initialize a CAN Channel](/reference/can_init#name) \
[Start the CAN Controller](/reference/can_start#name) \
[Bit-rate Settings](/reference/bitrate_settings#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')