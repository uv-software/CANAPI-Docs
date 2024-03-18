### NAME

> *can_kill* - signal waiting event objects of a CAN channel

### SYNOPSIS

<a id="can_kill"></a>
**C Interface**
```C
int can_kill(int handle);
```
<a id="signalchannel"></a>
**C++ Method**
```C++
CANAPI_Return_t SignalChannel();
```
<a id="func_signalchannel"></a>
**Swift Method**
```Swift
public func SignalChannel() throws
```

### DESCRIPTION

> Some CAN drivers are using waitable objects to realize blocking operations by a call of *WaitForSingleObject()* (Windows) or *pthread_cond_wait()* (POSIX),
> but these waitable objects are no cancellation points.
> This means that they cannot be terminated by `SIGINT`.

The function [can_kill()](#can_kill) signals waiting event objects of the CAN channel given by the *handle* argument.
This can be used to terminate blocking operations in progress (e.g. by means of a Ctrl-C handler or similar).

With the value `CANKILL_ALL` for the *handle* argument, all used CAN channels of an application can be signaled at once.

The method [SignalChannel()](#signalchannel) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [InitializeChannel()](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_kill()](#can_kill) respectively [SignalChannel()](#signalchannel) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit) - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - invalid channel handle \
[CANERR_NOTSUPP](/reference/error_codes#error_) - function not supported \
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
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')