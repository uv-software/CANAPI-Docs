### NAME

> *can_write* - send a CAN message on a CAN channel

### SYNOPSIS

<a id="can_write"></a>
**C Interface**
```C
int can_write(int handle, const can_message_t *message, uint16_t timeout);
```
<a id="writemessage"></a>
**C++ Method**
```C++
CANAPI_Return_t WriteMessage(const CANAPI_Message_t &message, uint16_t timeout = 0U);
```
<a id="func_writemessage"></a>
**Swift Method**
```Swift
public func WriteMessage(message: Message, timeout: UInt16 = 0) throws
```

### DESCRIPTION

The function [can_write()](#can_write) sends a CAN message on the CAN bus via the CAN controller associated with the CAN channel given by the *handle* argument.

The [CAN message](/reference/message_format#can_message_t) to be send, will be given by the variable pointed to by the *message* argument.

The parameter *timeout* determines the time to wait for the operation to complete:
- 0 means the function returns immediately,
- 65535 means blocking operation, and any other
- timeout value means the time to wait in milliseconds

The CAN controller must be in operation state '[running](/reference/status_register#status_bit_can_stopped)'
and the operation mode flag [MON](/reference/operation_modes#mode_bit_mon) must be cleared to send CAN messages.

It depends on the used CAN driver whether the transmission of CAN messages is acknowledged or buffered, or not at all.

The method [WriteMessage()](#writemessage) behaves exactly like the C function.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [*InitializeChannel()*](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_write()](#can_write) respectively [WriteMessage()](#writemessage) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit) - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - invalid channel handle \
[CANERR_NULLPTR](/reference/error_codes#error_nullptr) - null-pointer assignment \
[CANERR_ILLPARA](/reference/error_codes#error_illpara) - invalid parameter (dlc or flags) \
[CANERR_OFFLINE](/reference/error_codes#error_online)  - controller not started \
[CANERR_TX_BUSY](/reference/error_codes#error_tx_busy) - transmitter busy \
[CANERR_QUE_OVR](/reference/error_codes#error_que_ovr) - transmit queue overrun \
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
[Bit-rate Settings](/reference/bitrate_settings#name) \
[Operation Modes](/reference/operation_modes#name) \
[Status Register](/reference/status_register#name) \
[Message Format](/reference/message_format#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')