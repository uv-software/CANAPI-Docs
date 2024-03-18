### NAME

> *can_exit* - teardown a CAN channel

### SYNOPSIS

<a id="can_exit"></a>
**C Interface**
```C
int can_exit(int handle);
```
<a id="teardownchannel"></a>
**C++ Method**
```C++
CANAPI_Return_t TeardownChannel();
```
<a id="func_teardownchannel"></a>
**Swift Method**
```Swift
public func TeardownChannel() throws
```

### DESCRIPTION

The function [can_exit()](#can_exit) stops any operation of the CAN channel given by the *handle* argument and sets the operation state of the CAN controller to [STOPPED](/reference/status_register#status_bit_can_stopped) (aka INIT state).
All allocated resources of that CAN channel will be released.
The channel handle is invalid after that.

With the value `CANKILL_ALL` for the *handle* argument, all used CAN channels of an application can be torn down at once.

The method [TeardownChannel()](#teardownchannel) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_exit()](#can_exit) respectively [TeardownChannel()](#teardownchannel) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit) - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - invalid channel handle \
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
[Status Register](/reference/status_register#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')