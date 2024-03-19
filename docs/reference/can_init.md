### NAME

> *can_init* - initialize a CAN channel

### SYNOPSIS

<a id="can_init"></a>
**C Interface**
```C
#if (OPTION_CANAPI_LIBRARY != 0)
 int can_init(int32_t library, int32_t channel, uint8_t mode, const void *param);
#else
 int can_init(int32_t channel, uint8_t mode, const void *param);
#endif
```
<a id="initializechannel"></a>
**C++ Method**
```C++
#if (OPTION_CANAPI_LIBRARY != 0)
 CANAPI_Return_t InitializeChannel(int32_t library, int32_t channel, const CANAPI_OpMode_t &opMode, const void *param = NULL);
#else
 CANAPI_Return_t InitializeChannel(int32_t channel, const CANAPI_OpMode_t &opMode, const void *param = NULL);
#endif
```
<a id="swift_initializechannel"></a>
**Swift Method**
```Swift
#if (OPTION_CANAPI_LIBRARY != 0)
 public func InitializeChannel(library: Int32, channel: Int32, mode: Mode = .DefaultOperationMode) throws
#else
 public func InitializeChannel(channel: Int32, mode: Mode = .DefaultOperationMode) throws
#endif
```

### DESCRIPTION

The function [can_init()](#can_init) initializes the CAN interface (hardware and driver) given by the [*library* and ] *channel* argument.
The operation state of the CAN controller is set to [STOPPED](/reference/status_register#status_bit_can_stopped) (aka INIT state).
No CAN communication is possible in this state.

If the requested [operation mode](/reference/operation_modes#name), given by the *mode* argument, is not supported by the CAN controller, error [CANERR_ILLPARA](/reference/error_codes#error_illpara) will be returned.

Values for the *param* parameter are driver-specific and out of scope for this documentation.

The method [InitializeChannel()](#initializechannel) behaves exactly like the C function.
Upon successful completion, the CAN interface repectively its CAN controller is associated with the class instance from which the method has been called.

### RETURN VALUE

Upon successful completion, the C function returns a channel handle and the C++ function returns 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_init()](#can_init) respectively [InitializeChannel()](#initializechannel) will fail and return the appropriated error code:

[CANERR_LIBRARY](/reference/error_codes#error_library) - library could not be found \
[CANERR_YETINIT](/reference/error_codes#error_yetinit) - channel already in use \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - no free handle found \
[others](/reference/error_codes#error_vendor)          - vendor-specific error codes

### EXAMPLES

#### C Example

None.

#### C++ Example

None.

#### Swift Example

None.

### SEE ALSO

[Operation Modes](/reference/operation_modes#name) \
[Status Register](/reference/status_register#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')