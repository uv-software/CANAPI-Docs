### NAME

> *can_reset* - stop the CAN controller of a CAN channel

### SYNOPSIS

<a id="can_reset"></a>
**C Interface**
```C
int can_reset(int handle);
```
<a id="resetcontroller"></a>
**C++ Method**
```C++
CANAPI_Return_t ResetController();
```
<a id="swift_resetcontroller"></a>
**Swift Method**
```Swift
public func ResetController() throws
```

### DESCRIPTION

The function [can_reset()](#can_reset) disconnects the CAN controller of the CAN channel given by the *handle* argument from the CAN bus (*bus off*).
The operation state of the CAN controller is set to [STOPPED](/reference/status_register#status_bit_can_stopped) (aka INIT state).
No CAN communication is possible in this state.

The method [ResetController()](#resetcontroller) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_reset()](#can_reset) respectively [ResetController()](#resetcontroller) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit) - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - invalid channel handle \
[CANERR_OFFLINE](/reference/error_codes#error_offline) - controller already stopped \
[others](/reference/error_codes#error_vendor)          - vendor-specific error codes

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
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')