### NAME

> *can_read* - read one CAN message from the receive queue of a CAN channel

### SYNOPSIS

<a id="can_read"></a>
**C Interface**
```C
int can_read(int handle, can_message_t *message, uint16_t timeout);
```
<a id="readmessage"></a>
**C++ Method**
```C++
CANAPI_Return_t ReadMessage(CANAPI_Message_t &message, uint16_t timeout = CANREAD_INFINITE);
```
<a id="func_readmessage"></a>
**Swift Method**
```Swift
public func ReadMessage(timeout: UInt16 = blocking) throws -> Message?
```

### DESCRIPTION

The function [can_read()](#can_read) reads one CAN message from the receive queue of the CAN channel given by the *handle* argument.

Upon successful completion, the read [CAN message](/reference/message_format#can_message_t) is stored in the variable pointed to by the *message* argument.

The parameter *timeout* determines the time to wait for the operation to complete:
- 0 means the function returns immediately,
- 65535 means blocking operation, and any other
- timeout value means the time to wait in milliseconds

The CAN controller must be in operation state '[running](/reference/status_register#status_bit_can_stopped)' to read CAN messages.

The size of the receive queue depends on the used CAN driver.

The method [ReadMessage()](#readmessage) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of *InitializeChannel()* from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method return 0. On error, a negative value will be returned (see [errors](#errors)).

Upon successful completion, the Swift method returns the read message. On error, it will be `Nil`.

In case of an error, the Swift method throws an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_read()](#can_read) respectively [ReadMessage()](#readmessage) fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit)   - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)     - invalid channel handle \
[CANERR_NULLPTR](/reference/error_codes#error_nullptr)   - null-pointer assignment \
[CANERR_OFFLINE](/reference/error_codes#error_online)    - controller not started \
[CANERR_RX_EMPTY](/reference/error_codes#error_rx_empty) - message queue empty \
[CANERR_QUE_OVR](/reference/error_codes#error_que_ovr)   - receive queue overrun \
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
[Operation Modes](/reference/operation_modes#name) \
[Status Register](/reference/status_register#name) \
[Message Format](/reference/message_format#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')