### NAME

> *can_test* - probe if a CAN channel is available

### SYNOPSIS

<a id="can_test"></a>
**C Interface**
```C
#if (OPTION_CANAPI_LIBRARY != 0)
 int can_test(int32_t library, int32_t channel, uint8_t mode, const void *param, int *result);
#else
 int can_test(int32_t channel, uint8_t mode, const void *param, int *result);
#endif
```
<a id="probechannel"></a>
**C++ Method**
```C++
#if (OPTION_CANAPI_LIBRARY != 0)
 static CANAPI_Return_t ProbeChannel(int32_t library, int32_t channel, const CANAPI_OpMode_t &opMode, const void *param, EChannelState &state);
 static CANAPI_Return_t ProbeChannel(int32_t library, int32_t channel, const CANAPI_OpMode_t &opMode, EChannelState &state);
#else
 static CANAPI_Return_t ProbeChannel(int32_t channel, const CANAPI_OpMode_t &opMode, const void *param, EChannelState &state);
 static CANAPI_Return_t ProbeChannel(int32_t channel, const CANAPI_OpMode_t &opMode, EChannelState &state);
#endif
```
<a id="swift_probechannel"></a>
**Swift Method**
```Swift
#if (OPTION_CANAPI_LIBRARY != 0)
 public static func ProbeChannel(library: Int32, channel: Int32, mode: Mode = .DefaultOperationMode) throws -> State
#else
 public static func ProbeChannel(channel: Int32, mode: Mode = .DefaultOperationMode) throws -> State
#endif
```

### DESCRIPTION

The function [can_test()](#can_test) probes if the CAN interface (hardware and driver) given by the [*library* and] *channel* argument is present,
and if the requested operation mode given by the *mode* argument is supported by its CAN controller.

The result of the test, the [availibility state](/reference/channel_states#name), is stored in the variable pointed to by the *result* argument.

If the requested [operation mode](/reference/operation_modes#name) is not supported by the CAN controller, error [CANERR_ILLPARA](/reference/error_codes#error_illpara) will be returned.

Values for the *param* parameter are driver-specific and out of scope for this documentation.

The method [ProbeChannel()](#probechannel) behaves exactly like the C function.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

Upon successful completion, the Swift method will return the availibility state. On error, it will be `Nil`.

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_test()](#can_test) respectively [ProbeChannel()](#probechannel) will fail and return the appropriated error code:

[CANERR_LIBRARY](/reference/error_codes#error_library) - library could not be found \
[CANERR_ILLPARA](/reference/error_codes#error_illpara) - invalid operation mode \
[CANERR_NOTSUPP](/reference/error_codes#error_notsupp) - function not supported \
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
[Channel States](/reference/channel_states#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')