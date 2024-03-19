### NAME

> *can_status_t* - status register of a CAN channel 

### SYNOPSIS

**C/C++ Defines**
```C++
#define CANSTAT_RESET     0x80U
#define CANSTAT_BOFF      0x40U
#define CANSTAT_EWRN      0x20U
#define CANSTAT_BERR      0x10U
#define CANSTAT_TX_BUSY   0x08U
#define CANSTAT_RX_EMPTY  0x04U
#define CANSTAT_MSG_LST   0x02U
#define CANSTAT_QUE_OVR   0x01U
```
<a id="can_status_t"></a>
**C/C++ Typedef**
```C++
typedef union can_status_t_ {
    uint8_t byte;
    struct {
        uint8_t queue_overrun : 1;
        uint8_t message_lost : 1;
        uint8_t receiver_empty : 1;
        uint8_t transmitter_busy : 1;
        uint8_t bus_error : 1;
        uint8_t warning_level : 1;
        uint8_t bus_off : 1;
        uint8_t can_stopped : 1;
    };
} can_status_t;
```
**C/C++ Alias**
```C++
typedef can_status_t CANAPI_Status_t;
```
**Swift Type**
```Swift
public struct Status {
    public let isCanStopped: Bool
    public let isBusOff: Bool
    public let isWarningLevel: Bool
    public let isBusError: Bool
    public let isTransmitterBusy: Bool
    public let isReceiverEmpty: Bool
    public let isMessageLost: Bool
    public let isQueueOverrun: Bool
}
```

### DESCRIPTION

The 8-bit wide [status register](#can_status_t) of a CAN channel can be read by [can_status()](/reference/can_status#can_status) (C) respectively [GetStatus()](/reference/can_status#getstatus) (C++) or by reading the Swift property [status](/reference/get_status#var_status).

<a id="status_bit_can_stopped"></a>
**Status bit 7 (*RESET*)** indicates whether the CAN controller in reset mode (aka INIT state) or running (bus-on).
The bit is set if the CAN controller has not been started.
The bit is cleared if the CAN controller has successfully been started by [can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller).

<a id="status_bit_bus_off"></a>
**Status bit 6 (*BOFF*)** indicates whether the CAN controller is in bus-off state.
The bit is set if the CAN controller has detected a bus-off condition.
The bit is cleared if the CAN controller has successfully been (re-)started by [can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller).
It depends on the CAN driver respectively the CAN controller firmware if this bit is set while the CAN controller in reset mode (aka INIT mode).

<a id="status_bit_warning_level"></a>
**Status bit 5 (*EWRN*)** indicates whether the CAN controller has reached its warning level (e.g. error-passive).
The bit is set according to the bus error state or the bus error counter(s) read from the CAN controller.
It depends on the CAN driver respectively the CAN controller firmware how the bus error state respectively the bus error counter(s) are mapped to this bit.

<a id="status_bit_bus_error"></a>
**Status bit 4 (*BERR*)** indicates whether the CAN controller has detected a protocol error.
The bit is set according to the protocol error flag(s) read from the CAN controller (e.g. stuff error, form error, acknowledge error, recessive bit error, dominant bit error, checksum error).
It depends on the CAN driver respectively the CAN controller firmware how the protocol error flag(s) are mapped to this bit.

<a id="status_bit_transmitter_busy"></a>
**Status bit 3 (*TX_BUSY*)** indicates that the CAN controller is not able to send a requested transmit message.
The bit is set if a call to [can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage) failed with error code [CANERR_TX_BUSY](/reference/error_codes#error_tx_busy) . Otherwise, the bit is cleared.
It depends on the CAN driver respectively the CAN controller firmware if transmit messages are acknowledged or not.

<a id="status_bit_receiver_empty"></a>
**Status bit 2 (*RX_EMPTY*)** indicates that the receive queue is empty and the CAN controller has not received any new CAN message.
The bit is set if a call to [can_read()](/reference/can_read#can_read) respectively [ReadMessage()](/reference/can_read#readmessage) failed with error code [CANERR_RX_EMPTY](/reference/error_codes#error_rx_empty). Otherwise, the bit is cleared.

<a id="status_bit_message_lost"></a>
**Status bit 1 (*MSG_LST*)** indicates that a received CAN message has been lost.
The bit is set if at least one received CAN message has been overwritten in the CAN controller before it has been stored in the receive queue.
The bit is cleared if the CAN controller has successfully been (re-)started by [can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller).
It depends on the CAN driver respectively the CAN controller firmware how message lost events are handled.

<a id="status_bit_queue_overrun"></a>
**Status bit 0 (*QUE_OVR*)** indicates that the receive queue has overflowed.
The bit is set if the receive queue is full while a new CAN message has been received by the CAN controller.
The bit is cleared if the CAN controller has successfully been (re-)started by [can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller).
It depends on the CAN driver how queue overrun events are handled.

### SEE ALSO

[can_status()](/reference/can_status#can_status) respectively [GetStatus()](/reference/can_status#getstatus) \
[can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller) \
[can_reset()](/reference/can_reset#can_reset) respectively [ResetController()](/reference/can_reset#resetcontroller) \
[can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage) \
[can_read()](/reference/can_read#can_read) respectively [ReadMessage()](/reference/can_read#readmessage)


[copyright](../copyright.md ':include')
