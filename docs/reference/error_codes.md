### NAME

> CAN API V3 error codes

### SYNOPSIS

<a id="error_defines"></a>
**C/C++ Defines**
```C++
#define CANERR_NOERROR              (0)
#define CANERR_BOFF                (-1)
#define CANERR_EWRN                (-2)
#define CANERR_BERR                (-3)
#define CANERR_OFFLINE             (-9)
#define CANERR_ONLINE              (-8)
#define CANERR_MSG_LST            (-10)
#define CANERR_LEC_STUFF          (-11)
#define CANERR_LEC_FORM           (-12)
#define CANERR_LEC_ACK            (-13)
#define CANERR_LEC_BIT1           (-14)
#define CANERR_LEC_BIT0           (-15)
#define CANERR_LEC_CRC            (-16)
#define CANERR_TX_BUSY            (-20)
#define CANERR_RX_EMPTY           (-30)
#define CANERR_QUE_OVR            (-40)
#define CANERR_TIMEOUT            (-50)
#define CANERR_RESOURCE           (-90)
#define CANERR_BAUDRATE           (-91)
#define CANERR_HANDLE             (-92)
#define CANERR_ILLPARA            (-93)
#define CANERR_NULLPTR            (-94)
#define CANERR_NOTINIT            (-95)
#define CANERR_YETINIT            (-96)
#define CANERR_LIBRARY            (-97)
#define CANERR_NOTSUPP            (-98)
#define CANERR_FATAL              (-99)
#define CANERR_VENDOR            (-100)
```
**C/C++ Typedef**
```C++
enum EErrorCodes {
    NoError = CANERR_NOERROR,
    BusOFF = CANERR_BOFF,
    ErrorWarning = CANERR_EWRN,
    BusError = CANERR_BERR,
    ControllerOffline = CANERR_OFFLINE,
    ControllerOnline = CANERR_ONLINE,
    MessageLost = CANERR_MSG_LST,
    TransmitterBusy = CANERR_TX_BUSY,
    ReceiverEmpty = CANERR_RX_EMPTY,
    QueueOverrun = CANERR_QUE_OVR,
    Timeout = CANERR_TIMEOUT,
    ResourceError = CANERR_RESOURCE,
    InvalidBaudrate = CANERR_BAUDRATE,
    InvalidHandle = CANERR_HANDLE,
    IllegalParameter = CANERR_ILLPARA,
    NullPointer = CANERR_NULLPTR,
    NotInitialized = CANERR_NOTINIT,
    AlreadyInitialized = CANERR_YETINIT,
    InvalidLibrary = CANERR_LIBRARY,
    NotSupported = CANERR_NOTSUPP,
    FatalError = CANERR_FATAL,
    VendorSpecific = CANERR_VENDOR
};
```
**C/C++ Alias**
```C++
typedef int CANAPI_Return_t;
```
**Swift Type**
```Swift
public enum Error: Int32, Swift.Error {
    // enum: error code (as Swift error exception)
    case NoError = 0
    case BusOFF = -1
    case ErrorWarning = -2
    case BusError = -3
    case ControllerOffline = -9
    case ControllerOnline = -8
    case MessageLost = -10
    case TransmitterBusy = -20
    case ReceiverEmpty = -30
    case QueueOverrun = -40
    case Timeout = -50
    case ResourceError = -90
    case InvalidBaudrate = -91
    case InvalidHandle = -92
    case IllegalParameter = -93
    case NullPointer = -94
    case NotInitialized = -95
    case AlreadyInitialized = -96
    case NotSupported = -98
    case FatalError = -99
    case VendorSpecific = -100
    // error description (as String)
    public var description: String {
        get {
            switch self {
            case .NoError: return "no error occurred"
            case .BusOFF: return "busoff status"
            case .ErrorWarning: return "error warning status"
            case .BusError: return "bus error"
            case .ControllerOffline: return "not started"
            case .ControllerOnline: return "already started"
            case .MessageLost: return "message lost"
            case .TransmitterBusy: return "transmitter busy"
            case .ReceiverEmpty: return "receiver empty"
            case .QueueOverrun: return "queue overrun"
            case .Timeout: return "timed out"
            case .ResourceError: return "resource allocation"
            case .InvalidBaudrate: return "illegal baudrate"
            case .InvalidHandle: return "illegal handle"
            case .IllegalParameter: return "illegal parameter"
            case .NullPointer : return "null-pointer assignment"
            case .NotInitialized: return "not initialized"
            case .AlreadyInitialized: return "already initialized"
            case .InvalidLibrary: return "illegal library"
            case .NotSupported: return "not supported"
            case .FatalError: return "fatal error"
            default: return "vendor-specific or general error"
            }
        }
    }
}
```

### DESCRIPTION

Each CAN API V3 function (**C**) respectively method (**C++**) returns zero or, in rare cases, a positive number if executed successfully, and a negative number (an [error code](#error_defines)) if it fails.
Swift methods will throw an exception if they fail.

Error codes less or equal than -100 are reserved for vendor-specific error codes
and codes less or equal than -10000 are reserved for OS-specific error codes
(add 10000 to get the reported OS error code, e.g. `errno`).

<a id="error_noerror"></a>
Error code **0** (*CANERR_NOERROR*) indicates the successful completion of a function (**C**) respectively method (**C++**).

<a id="error_boff"></a>
Error code **-1** (*CANERR_BOFF*)[^1] indicates that the CAN controller has entered the bus-off error state; cf. status bit [BOFF](/reference/status_register#status_bit_bus_off).

<a id="error_ewrn"></a>
Error code **-2** (*CANERR_EWRN*)[^1] indicates that the CAN controller has reached the error warning level; cf. status bit [EWRN](/reference/status_register#status_bit_warning_level).

<a id="error_berr"></a>
Error code **-3** (*CANERR_BERR*)[^1] indicates that the CAN controller has detected a bus error (e.g. from ECC logic); cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_online"></a>
Error code **-8** (*CANERR_ONLINE*) indicates that the CAN controller is in RUNNING state (*bus on*) and cannot execute the requested operation.

<a id="error_offline"></a>
Error code **-9** (*CANERR_OFFLINE*) indicates that the CAN controller is in INIT state (*bus off*) and cannot execute the requested operation.

<a id="error_msg_lst"></a>
Error code **-10** (*CANERR_MSG_LST*)[^1] indicates that a received CAN message was overwritten before it was read by the CAN controller; cf. status bit [MSG_LST](/reference/status_register#status_bit_message_lost).

<a id="error_lec_stuff"></a>
Error code **-11** (*CANERR_LEC_STUFF*)[^1] indicates that the ECC logic of the CAN controller has detected a stuff error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_lec_form"></a>
Error code **-12** (*CANERR_LEC_FORM*)[^1] indicates that ECC logic of the CAN controller has detected a form error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_lec_ack"></a>
Error code **-13** (*CANERR_LEC_ACK*)[^1] indicates that ECC logic of the CAN controller has detected an acknowledge error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_lec_bit1"></a>
Error code **-14** (*CANERR_LEC_BIT1*)[^1] indicates that ECC logic of the CAN controller has detected a recessive bit error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_lec_bit0"></a>
Error code **-15** (*CANERR_LEC_BIT0*)[^1] indicates that ECC logic of the CAN controller has detected a dominant bit error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_lec_crc"></a>
Error code **-16** (*CANERR_LEC_CRC*)[^1] indicates that ECC logic of the CAN controller has detected a CRC error; cf. status bit [BERR](/reference/status_register#status_bit_bus_error).

<a id="error_tx_busy"></a>
Error code **-20** (*CANERR_TX_BUSY*) indicates that a transmission is pending, and a new CAN message cannot be sent; cf. status bit [TX_BUSY](/reference/status_register#status_bit_transmitter_busy).

<a id="error_rx_empty"></a>
Error code **-30** (*CANERR_RX_EMPTY*) indicates that the receive queue is empty; cf. status bit [RX_EMPTY](/reference/status_register#status_bit_receiver_empty).

<a id="error_que_ovr"></a>
Error code **-40** (*CANERR_QUE_OVR*) indicates that the receive queue has overflowed; cf. status bit [QUE_OVR](/reference/status_register#status_bit_queue_overrun). \
*Note: The bit remains latched until the CAN controller is restarted.*

<a id="error_timeout"></a>
Error code **-50** (*CANERR_TIMEOUT*) indicates that the requested operation has timed out.

<a id="error_resource"></a>
Error code **-90** (*CANERR_RESOURCE*) indicates a general resource allocation error (e.g. memory).

<a id="error_baudrate"></a>
Error code **-91** (*CANERR_BAUDRATE*) indicates that the given bit-rate settings are not valid, or not supported by the CAN controller.

<a id="error_handle"></a>
Error code **-92** (*CANERR_HANDLE*) indicates that the given *handle* argument to a C function is invalid, or that no channel handle is available to be associated with a CAN controller.

<a id="error_illpara"></a>
Error code **-93** (*CANERR_ILLPARA*) indicates that a given argument to a function respectively method is invalid (e.g. out of range).

<a id="error_nullptr"></a>
Error code **-94** (*CANERR_NULLPTR*) indicates that a NULL pointer is given as argument to a function respectively method.

<a id="error_notinit"></a>
Error code **-95** (*CANERR_NOTINIT*) indicates that the CAN channel is not initialized, and the requested operation cannot be executed.

<a id="error_yetinit"></a>
Error code **-96** (*CANERR_YETINIT*) indicates that that the CAN channel is already initialized.

<a id="error_library"></a>
Error code **-97** (*CANERR_LIBRARY*) indicates that the given *library* argument to the initialization function respectively method is invalid.

<a id="error_notsupp"></a>
Error code **-98** (*CANERR_NOTSUPP*) indicates that the requested operation is not supported by the CAN API library or the present CAN controller, or that a given argument to a function respectively method is not supported.

<a id="error_fatal"></a>
Error code **-99** (*CANERR_FATAL*) indicates that something went terribly wrong.

<a id="error_vendor"></a>
An error code less or equal than **-100** (*CANERR_VENDOR*) indicates a vendor-specific error or an OS-specific error (see above).

#### FOOTNOTES

[^1] These error codes are deprecated and not used anymore.

### SEE ALSO

[Status register](/reference/status_register#name)


[copyright](../copyright.md ':include')