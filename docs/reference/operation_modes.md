### NAME

> *can_mode_t* - operation mode selector of a CAN channel 

### SYNOPSIS

**C/C++ Defines**
```C++
#define CANMODE_FDOE     0x80U
#define CANMODE_BRSE     0x40U
#define CANMODE_NISO     0x20U
#define CANMODE_SHRD     0x10U
#define CANMODE_NXTD     0x08U
#define CANMODE_NRTR     0x04U
#define CANMODE_ERR      0x02U
#define CANMODE_MON      0x01U
#define CANMODE_DEFAULT  0x00U
```
<a id="can_mode_t"></a>
**C/C++ Typedef**
```C++
typedef union can_mode_t_ {
    uint8_t byte;
    struct {
        uint8_t mon : 1;
        uint8_t err : 1;
        uint8_t nrtr : 1;
        uint8_t nxtd : 1;
        uint8_t shrd : 1;
        uint8_t niso : 1;
        uint8_t brse : 1;
        uint8_t fdoe : 1;
    };
} can_mode_t;
```
**C/C++ Alias**
```C++
typedef can_mode_t CANAPI_OpMode_t;
```
**Swift Type**
```Swift
public struct Mode: OptionSet {
    // operation modes as option set
    public static let DefaultOperationMode = Mode([])
    public static let FdOperationEnabled = Mode(rawValue: 0x80)
    public static let BitrateSwitchingEnabled = Mode(rawValue: 0x40)
    public static let NonIsoOperationEnabled = Mode(rawValue: 0x20)
    public static let SharedAccessEnabled = Mode(rawValue: 0x10)
    public static let ExtendedFramesDisabled = Mode(rawValue: 0x08)
    public static let RemoteFramesDisabled = Mode(rawValue: 0x04)
    public static let ErrorFramesEnabled = Mode(rawValue: 0x02)
    public static let MonitorModeEnabled = Mode(rawValue: 0x01)
    // operation mode from C interface
    public init(rawValue: UInt8) {
        self.rawValue = rawValue
    }
    public let rawValue: UInt8
    // operation mode bits as predicates
    public var isFdOperationEnabled: Bool { get { return 0x80 == self.rawValue & 0x80 } }
    public var isBitrateSwitchingEnabled: Bool { get { return 0x40 == self.rawValue & 0x40 } }
    public var isNonIsoOperationEnabled: Bool { get { return 0x20 == self.rawValue & 0x20 } }
    public var isSharedAccessEnabled : Bool { get { return 0x10 == self.rawValue & 0x10 } }
    public var areExtendedFramesDisabled: Bool { get { return 0x08 == self.rawValue & 0x08 } }
    public var areRemoteFramesDisabled: Bool { get { return 0x04 == self.rawValue & 0x04 } }
    public var isErrorFramesEnabled: Bool { get { return 0x02 == self.rawValue & 0x02 } }
    public var isMonitorModeEnabled: Bool { get { return 0x01 == self.rawValue & 0x01 } }
}
```

### DESCRIPTION

The 8-bit wide [operation mode selector](/reference/operation_modes#can_mode_t) is used to determine the operation mode of a CAN channel (see *can_init()* respectively *InitializeChannel()*).
The operation mode selector is also used to probe if a specific operation mode is supported by the CAN controller associated with a CAN channel (see *can_test()* respectively *ProbeChannel()*).

<a id="mode_bit_fdoe"></a>
**Mode bit 7 (*FDOE*)** enables or disables CAN FD operation mode.
If the bit is set, the CAN controller operates in CAN FD mode (long frames).
If cleared, the CAN controller operates in Classic CAN mode (CAN 2.0).

<a id="mode_bit_brse"></a>
**Mode bit 6 (*BRSE*)** enables or disables bit-rate switching in CAN FD operation mode.
If the bit is set, the CAN controller operates in CAN FD mode with bit-rate switching enabled (fast frames).
If cleared, the CAN controller operates without bit-rate switching.
This bit can only be set in conjunction with bit 7 ([FDOE](/reference/operation_modes#mode_bit_fdoe)), otherwise it must be set to 0.

<a id="mode_bit_niso"></a>
**Mode bit 5 (*NISO*)** enables or disables Non-ISO CAN FD operation mode.
If the bit is set, the CAN controller operates in Non-ISO CAN FD mode.
If cleared, the CAN controller operates in ISO CAN FD mode.
This bit can only be set in conjunction with bit 7 ([FDOE](/reference/operation_modes#mode_bit_fdoe)), otherwise it must be set to 0.

<a id="mode_bit_shrd"></a>
**Mode bit 4 (*SHRD*)** enables or disables shared access operation mode.
If the bit is set, the CAN channel can be accessed by other client application.
If cleared, the CAN application requests an exclusive access to the CAN driver.

<a id="mode_bit_nxtd"></a>
**Mode bit 3 (*NXTD*)** enables or disables the transmission and reception of extended frames (29-bit identifier).
If the bit is set, extended frames can neither be sent nor received.
If cleared, extended frames can be received as well as transmitted.

<a id="mode_bit_nrtr"></a>
**Mode bit 2 (*NRTR*)** enables or disables the transmission and reception of remote frames (remote transmit requests).
If the bit is set, remote frames can neither be requested nor received.
If cleared, remote frames can be received as well as requested.

<a id="mode_bit_err"></a>
**Mode bit 1 (*ERR*)** enables or disables the reception of error frames[^1].
If the bit is set, error frames will be stored in the receive queue.
If cleared, error frames will not be stored in the receive queue.

<a id="mode_bit_mon"></a>
**Mode bit 0 (*MON*)** enables or disables listen-only operation mode (monitor mode).
If the bit is set, CAN messages cannot be sent (the transmitter of the CAN controller is off).
If cleared, CAN messages can be received as well as transmitted.

It depends on the CAN adapter or on the current version of the CAN API V3 wrapper library if a selected operation mode is supported or not.
Use function *can_test()* respectively method *ProbeChannel()* to probe if a specific operation mode is supported.

#### FOOTNOTE

[^1] Error frames will be inserted into the receive queue as vendor-specific status messages (see CAN message flag [sts](/reference/message_format#message_flag_sts))

### SEE ALSO

[can_init()](/reference/can_init#can_init) respectively [InitializeChannel()](/reference/can_init#initializechannel) \
[can_test()](/reference/can_test#can_test) respectively [ProbeChannel()](/reference/can_test#probechannel)


[copyright](../copyright.md ':include')