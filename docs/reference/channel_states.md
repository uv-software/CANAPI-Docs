### NAME

> CAN API V3 channel states

### SYNOPSIS

<a id="state_defines"></a>
**C/C++ Defines**
```C++
#define CANBRD_NOT_PRESENT   (-1)
#define CANBRD_PRESENT        (0)
#define CANBRD_OCCUPIED      (+1)
#define CANBRD_NOT_TESTABLE  (-2)
```
**C++ Type**
```C++
enum EChannelState {
    ChannelOccupied = CANBRD_OCCUPIED,
    ChannelAvailable = CANBRD_PRESENT,
    ChannelNotAvailable = CANBRD_NOT_PRESENT,
    ChannelNotTestable  = CANBRD_NOT_TESTABLE
};
```
**Swift Type**
```Swift
public enum State: Int32 {
    // enum: channel state
    case ChannelOccupied = 1
    case ChannelAvailable = 0
    case ChannelNotAvailable = -1
    case ChannelNotTestable = -2
    // state description (as String)
    public var description: String {
        get {
            switch self {
            case .ChannelOccupied: return "CAN interface available, but occupied"
            case .ChannelAvailable: return "CAN interface available"
            case .ChannelNotAvailable: return "CAN interface not available"
            case .ChannelNotTestable: return "CAN interface not testable"
            }
        }
    }
}
```

### DESCRIPTION

CAN API V3 provides a function (**C**) respectively a method (**C++**/**Swift**) to test the availability of a CAN channel.

<a id="state_occupied"></a>
State **+1 (*CANBRD_OCCUPIED*)** indicates that the requested CAN channel is available, but occupied.

<a id="state_available"></a>
State **0 (*CANBRD_PRESENT*)** indicates that the requested CAN channel is available and can be used.

<a id="state_not_available"></a>
State **-1 (*CANBRD_NOT_PRESENT*)** indicates that the requested CAN channel is not available.

<a id="state_not_testable"></a>
State **-2 (*CANBRD_NOT_TESTABLE*)** indicates that the requested CAN channel is not testable.

### SEE ALSO

[Probe a CAN Channel](/reference/can_test#name)


[copyright](../copyright.md ':include')
