### NAME

> *can_start* - start the CAN controller of a CAN channel

### SYNOPSIS

<a id="can_start"></a>
**C Interface**
```C
int can_start(int handle, const can_bitrate_t *bitrate);
```
<a id="startcontroller"></a>
**C++ Method**
```C++
CANAPI_Return_t StartController(const CANAPI_Bitrate_t &bitrate);
```
<a id="func_startcontroller"></a>
**Swift Method**
```Swift
public func StartController(bitrate: Bitrate) throws

public func StartController(index: CiaIndex) throws
```

### DESCRIPTION

The function [can_start()](#can_start) initializes the operation mode and the bit-rate of the CAN controller associated with the CAN channel given by the *handle* argument
and sets its operation state to '[running](/reference/status_register#status_bit_can_stopped)'.
The CAN communication is now taking place.

The requested [operation mode](/reference/operation_modes#name) is detemined during the initialization of the CAN channel (cf. [*can_init()*](/reference/can_init#can_init) respectively [*InitializeChannel()*](/reference/can_init#initializechannel)).
The operation mode cannot be changed afterwards.

The requested [bit-rate](/reference/bitrate_settings#name), given by the *bitrate* argument,
can be specified either by CAN clock based [bit-timing settings](/reference/bitrate_settings#bitrate_frequency) (CAN 2.0 and CAN FD) or
as [index](/reference/bitrate_settings#bitrate_index) to a table with predefined bit-timing settings (CAN 2.0 only).

Upon successful completion, all statistical counters ([tx/rx/err/ovfl](/reference/property_ids#property_defines)) are reset.

The method [StartController()](#startcontroller) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [*InitializeChannel()*](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_start()](#can_start) respectively [StartController()](#startcontroller) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit)   - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)     - invalid channel handle \
[CANERR_NULLPTR](/reference/error_codes#error_nullptr)   - null-pointer assignment \
[CANERR_BAUDRATE](/reference/error_codes#error_baudrate) - invalid bit-rate settings \
[CANERR_ONLINE](/reference/error_codes#error_online)     - controller already started \
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
[Bit-rate Settings](/reference/bitrate_settings#name) \
[Operation Modes](/reference/operation_modes#name) \
[Status Register](/reference/status_register#name) \
[Property IDs](/reference/property_ids#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')