### NAME

> *can_status* - get the status register from the CAN controller of a CAN channel

### SYNOPSIS

<a id="can_status"></a>
**C Interface**
```C
int can_status(int handle, uint8_t *status);
```
<a id="getstatus"></a>
**C++ Method**
```C++
CANAPI_Return_t GetStatus(CANAPI_Status_t &status);
```
<a id="var_status"></a>
**Swift Property**
```Swift
public var status: Status?
```

### DESCRIPTION

The function [can_status()](#can_status) reads the [status register](/reference/status_register#name) from the CAN controller associated with the initialized channel specified by the *handle* argument into an 8-bit wide variable pointed to by *status*.
The parameter *status* is optional, that means a NULL pointer can be passed as argument.

The [GetStatus()](#getstatus) method behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of *InitializeChannel()* from that instance.

The Swift [status](#var_status) property contains the current [status register](/reference/status_register#name) read from the associated CAN channel.
It is a read-only property.
The class instance from which the property is read must be associated with a CAN channel by a previous successful call of *InitializeChannel()* from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method return 0. On error, a negative value will be returned (see [errors](#errors)).

Upon successful completion, the Swift property contains the current status register. On error, it will be `Nil`.

### ERRORS

Under the following conditions, [can_status()](#can_status) respectively [GetStatus()](#getstatus) fail and return the appropriated error code:

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