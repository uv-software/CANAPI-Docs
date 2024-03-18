### NAME

> *can_message_t* - CAN message with time-stamp 

### SYNOPSIS

**C/C++ Defines**
```C++
#define CAN_MAX_STD_ID  0x7FF
#define CAN_MAX_XTD_ID  0x1FFFFFFF

#define CAN_MAX_DLC  8
#define CAN_MAX_LEN  8

#define CANFD_MAX_DLC  15
#define CANFD_MAX_LEN  64
```
<a id="can_message_t"></a>
**C/C++ Typedef**
```C++
typedef struct timespec can_timestamp_t;

typedef struct can_message_t_ {
    uint32_t id;
    struct {
        uint8_t xtd : 1;
        uint8_t rtr : 1;
        uint8_t fdf : 1;
        uint8_t brs : 1;
        uint8_t esi : 1;
        uint8_t : 2;
        uint8_t sts : 1;
    };
    uint8_t dlc;
    uint8_t data[CANFD_MAX_LEN];
    can_timestamp_t timestamp;
} can_message_t;
```
**C/C++ Alias**
```C++
typedef can_timestamp_t CANAPI_Timestamp_t;

typedef can_message_t CANAPI_Message_t;
```
<a id="swift_message"></a>
**Swift Type**
```Swift
public struct Message {
     public struct Flags: OptionSet {
         // message flags as option set
         public static let StandardFrame = Flags([])
         public static let ExtendedFrame = Flags(rawValue: 0x01)
         public static let RemoteFrame = Flags(rawValue: 0x02)
         public static let CanFdLongFrame = Flags(rawValue: 0x04)
         public static let CanFdFastFrame = Flags(rawValue: 0x08)
         // message flags from C interface
         public init(rawValue: UInt8) {
             self.rawValue = rawValue
         }
         public let rawValue: UInt8
         // message flags as predicates
         public var isStandardFrame: Bool { get { return 0x00 == self.rawValue & 0xFF } }
         public var isExtendedFrame: Bool { get { return 0x01 == self.rawValue & 0x01 } }
         public var isRemoteFrame: Bool { get { return 0x02 == self.rawValue & 0x02 } }
         public var isCanFdLongFrame: Bool { get { return 0x04 == self.rawValue & 0x04 } }
         public var isCanFdFastFrame: Bool { get { return 0x08 == self.rawValue & 0x08 } }
         public var isErrorStateIndicator: Bool { get { return 0x10 == self.rawValue & 0x10 } }
         public var isStatusMessage: Bool { get { return 0x80 == self.rawValue & 0x80 } }
     }
     // CAN message
     public var canId: UInt32
     public var canDlc: UInt8
     public var flags: Flags
     public var data: [UInt8]
     public var time: TimeInterval
     public var length: UInt8 { get { return UInt8(data.count) }}
}
```

### DESCRIPTION

The [CAN message](/reference/message_format#can_message_t) data type is used for the reception as well as for the transmission of CAN messages (see [can_read()](/reference/can_read#can_read) respectively [ReadMessage()](/reference/can_read#readmessage) and [can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage)).

<a id="message_id"></a>
Field **id** contains the CAN message identifier, either as 11-bit identifier (standard frame) or as 29-bit identifier (extended frame).
11-bit identifier are in the range of 0 to `CAN_MAX_STD_ID`, and 29-bit identifier in the range of 0 to `CAN_MAX_XTD_ID`.

<a id="message_dlc"></a>
Field **dlc** contains the data length code (DLC) of the CAN message for both Classical CAN frames and CAN FD frames.
For Classical CAN frames the DLC is in the range of 0 to `CAN_MAX_DLC`, and for CAN FD frames in the range of 0 to `CANFD_MAX_DLC` (see [DLC table](#dlc_table)).
The transmission as well as the reception of CAN FD frames is only possible if the operation mode flag [FDOE](/reference/operation_modes#mode_bit_fdoe) is selected.

<a id="message_data"></a>
Field **data** contains the data bytes of the CAN message.
The field is an array to hold 0 to 8 bytes for a Classical CAN frame and 0 to 64 bytes for a CAN FD frame.
The value of data bytes beyond the number of bytes specified by the field dlc (data length code) is undefined for receive messages respectively don´t care for transmit messages.
The transmission as well as the reception of CAN FD frames is only possible if the operation mode flag [FDOE](/reference/operation_modes#mode_bit_fdoe) is selected.

<a id="message_timestamp"></a>
Field **timestamp** contains the time-stamp of a received CAN message.
It is given as `struct timespec` with field `tv_sec` (elapsed seconds since start of the epoch) and field `tv_nsec` (nanoseconds).
The timestamp field is not relevant for transmit messages and will be ignored by [can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage).

<a id="message_flag_xtd"></a>
Flag **xtd** (bit 0) indicates whether the CAN message is a standard frame or an extended frame.
If the flag is set, the CAN message is an extended frame with an 29-bit identifier (independent of the value of the CAN identifier).
If cleared, the CAN message is a standard frame with an 11-bit identifier.
If the operation mode flag [NXTD](/reference/operation_modes#mode_bit_nxtd) is selected, the transmission as well as the reception of extended frames is suppressed.

<a id="message_flag_rtr"></a>
Flag **rtr** (bit 1) indicates whether the CAN message is a “normal” frame or a remote frame (Remote Transmit Request).
If the flag is set for a transmit message, the message data are requested from a RTR capable CAN node that provides the message data.
If it is set on a received message, a remotely requested frame from another CAN node has been received.
If cleared, the CAN message is a "nsormal" CAN frame.
If the operation mode flag [NRTR](/reference/operation_modes#mode_bit_nrtr) is selected, the transmission as well as the reception of remote frames is suppressed.

<a id="message_flag_fdf"></a>
Flag **fdf** (bit 2) indicates whether the CAN message is a Classical CAN frame or a CAN FD frame.
If the flag is set, the CAN message is a CAN FD frame independent of its length (“short” frame up to 8 bytes or long frame up to 64 bytes).
If cleared, the CAN message is a Classical CAN frame even if CAN FD operating mode has been selected.
The transmission as well as the reception of CAN FD frames (independent if it is a long frame or a “short” frame) is only possible if the operation mode flag [FDOE](/reference/operation_modes#mode_bit_fdoe) is selected.

<a id="message_flag_brs"></a>
Flag **brs** (bit 3) indicates that bit-rate switching is active for CAN FD data phase (fast frames).
If the flag is set, the CAN message data bytes are transmitted or received by a potentially faster bit-rate.
If cleared, the bit-rate of the arbitration phase and the data phase are equal as in Classical CAN operation mode.
The transmission as well as the reception of CAN FD fast frames is only possible if the operation mode flags [FDOE](/reference/operation_modes#mode_bit_fdoe) and [BRSE](/reference/operation_modes#mode_bit_brse) are selected.

<a id="message_flag_esi"></a>
Flag **esi** (bit 4) indicates that the CAN message has been receive with error state indicator (ESI) set.
The flag is set according to the ESI bit in the received CAN FD frame.
The flag is ignored for transmit messages and on Classical CAN frames. 

<a id="message_flag_sts"></a>
Flag **sts** (bit 7) indicates that the CAN message is a vendor-specific status message (mainly used for error frames).
The encoding of status messages is different among the different driver vendors;
see the appropriated documentation for the encoding of status messages.
This flag can not be set for a transmit message.
If the operation mode flag [ERR](/reference/operation_modes#mode_bit_err) is selected, the reception of status message is enabled.
By default, the reception of status message is disabled.

The **Swift** [Message](#swift_message) data type defines the message flags as an *option set* for transmit messages and as *predicates* for receive messages.
Furthermore it defines the read-only property *length* to get the length of a received CAN frame in addition to the data length code ([canDlc](#message_dlc)).

#### DLC TABLE  :id=dlc_table

| DLC  | Length  | Operation mode |
| :--  | :------ | :------------- |
| 0    | 0       | Classical CAN and CAN FD |
| 1    | 1       | Classical CAN and CAN FD |
| 2    | 2       | Classical CAN and CAN FD |
| 3    | 3       | Classical CAN and CAN FD |
| 4    | 4       | Classical CAN and CAN FD |
| 5    | 5       | Classical CAN and CAN FD |
| 6    | 6       | Classical CAN and CAN FD |
| 7    | 7       | Classical CAN and CAN FD |
| 8    | 8       | Classical CAN and CAN FD |
| 9    | 12      | CAN FD only |
| 10   | 16      | CAN FD only |
| 11   | 20      | CAN FD only |
| 12   | 24      | CAN FD only |
| 13   | 32      | CAN FD only |
| 14   | 48      | CAN FD only |
| 15   | 64      | CAN FD only |


### SEE ALSO

[can_read()](/reference/can_read#can_read) respectively [ReadMessage()](/reference/can_read#readmessage) \
[can_write()](/reference/can_write#can_write) respectively [WriteMessage()](/reference/can_write#writemessage) \
[Operation Modes](/reference/operation_modes#name) (data type and defines)


[copyright](../copyright.md ':include')