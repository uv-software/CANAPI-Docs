### NAME

> *can_bitrate_t* - CAN bit-rate settings for arbitration phase and data phase

### SYNOPSIS

**C/C++ Defines**
```C++
#define CANBTR_INDEX_1M     (0)
#define CANBTR_INDEX_800K  (-1)
#define CANBTR_INDEX_500K  (-2)
#define CANBTR_INDEX_250K  (-3)
#define CANBTR_INDEX_125K  (-4)
#define CANBTR_INDEX_100K  (-5)
#define CANBTR_INDEX_50K   (-6)
#define CANBTR_INDEX_20K   (-7)
#define CANBTR_INDEX_10K   (-8)
```
<a id="can_bitrate_t"></a>
<a id="can_speed_t"></a>
**C/C++ Typedef**
```C++
typedef union can_bitrate_t_ {
    int32_t index;
    struct {
        int32_t frequency;
        struct {
            uint16_t brp;
            uint16_t tseg1;
            uint16_t tseg2;
            uint16_t sjw;
            uint8_t  sam;
        } nominal;
        struct {
            uint16_t brp;
            uint16_t tseg1;
            uint16_t tseg2;
            uint16_t sjw;
        } data;
    } btr;
} can_bitrate_t;

typedef struct can_speed_t_ {
    struct {
        bool _reserved;
        float speed;
        float samplepoint;
    } nominal;
    struct {
        bool _reserved;
        float speed;
        float samplepoint;
    } data;
} can_speed_t;
```
**C/C++ Alias**
```C++
typedef can_bitrate_t CANAPI_Bitrate_t;

typedef can_speed_t CANAPI_BusSpeed_t;
```
<a id="struct_bitrate"></a>
<a id="struct_speed"></a>
**Swift Type**
```Swift
public enum CiaIndex: Int {
    case Index1000kbps = 0
    case Index800kbps = 1
    case Index500kbps = 2
    case Index250kbps = 3
    case Index125kbps = 4
    case Index100kbps = 5
    case Index50kbps = 6
    case Index20kbps = 7
    case Index10kbps = 8
}

public struct Bitrate {
    public struct Nominal {
        public var brp: UInt16
        public var tseg1: UInt16
        public var tseg2: UInt16
        public var sjw: UInt16
        public var sam: UInt8
    }
    public struct DataPhase {
        public var brp: UInt16
        public var tseg1: UInt16
        public var tseg2: UInt16
        public var sjw: UInt16
    }
    public var frequency: Int32
    public var nominal: Nominal
    public var data: DataPhase
}

public struct Speed {
    public struct Nominal {
        public var busSpeed: Float
        public var samplePoint: Float
    }
    public struct DataPhase {
        public var busSpeed: Float
        public var samplePoint: Float
    }
    public var nominal: Nominal
    public var data: DataPhase
}
```

### DESCRIPTION

CAN API V3 provides the data type [can_bitrate_t](#can_bitrate_t) (**C/C++**) respectively [struct Bitrate](#struct_bitrate) (**Swift**) for adjusting the bit-rate of the CAN controller associated with a CAN channel.
The data types contain the bit-timing settings for Classic CAN operation mode as well as for CAN FD operation mode.
The bit-timing settings are based upon the CAN clock frequency of the CAN controller.
The formula to calculate the bit-rate from frequency-based bit-timing settings is given by [(1)](#formula-1)
and to calculated the sample-point within a bit by [(2)](#formula-2).

Additionally CAN API V3 provides the data type [can_speed_t](#can_speed_t) (**C/C++**) respectively [struct Speed](#struct_speed) (**Swift**) for the data transmission speed (bit-rate in [bit/s]) and the sample-point in Classic CAN operation mode as well as in CAN FD operation mode.
The data transmission speed is a read-only property that cannot be used for adjusting the bit-rate of the CAN controller.

<a id="bitrate_frequency"></a>
Field **frequency** (CAN clock) determines the operating frequency of the CAN controller in hertz (Hz).
It is a crucial parameter as it determines the overall timing and data transmission speed on the CAN bus.

<a id="bitrate_brp"></a>
Field **brp** (bit-rate prescaler) determines the devider of the CAN clock.
The division of the CAN clock by the bit-rate prescaler (BRP) results in the time quanta (TQ).
Time quanta are discrete time intervals used to define various aspects of the bit timing on the CAN bus, such as the length of synchronization segment (SYNC_SEG), propagation segment (PROP_SEG), and phase segments (PHASE_SEG1 and PHASE_SEG2).
The BRP allows for adjusting the bit-rate by dividing the CAN clock frequency accordingly.

<a id="bitrate_tseg1"></a>
Field **tseg1** (time segment 1) determines the length of the first part of the phase segment within a bit time.
Specifically, it sets the duration during which the bit can be changed (dominant to recessive or vice versa) before the sample point.
TSEG1, together with TSEG2, influences the overall bit time and bit-rate.
TSEG1 is equivalent to sum of the propagation segment PROP_SEG and the phase segment PHASE_SEG1.

<a id="bitrate_tseg2"></a>
Field **tseg2** (time segment 2) determines the length of the second part of the phase segment within a bit time.
It defines the time after the sample point where the bit level must remain stable for successful bit reception.
TSEG2 is equivalent to the phase segment PHASE_SEG2.

<a id="bitrate_sjw"></a>
Field **sjw** (synchronization jump width) determines the maximum allowable variation in the synchronization segment (SYNC_SEG) to account for synchronization errors.
In other words, SJW defines how much the bit timing can be adjusted to accommodate variations in clock synchronization between different nodes on the CAN bus.

<a id="bitrate_sam"></a>
Field **sam** (number of samples) determines how many times the CAN controller samples the bus to determine the bit's value during each bit time.
It can be set to either single (1 sample per bit) or triple (3 samples per bit) sampling.
Triple sampling is more robust in noisy environments but requires more processing resources.
It depends on the used CAN controller if triple sampling is sopported.

<a id="bitrate_index"></a>
Field **index** (C/C++ only) determines an index to the [table with predefined bit-timings](#bit-timing-table) (Classic CAN only).
The index to the bit-timing table must be given as a negative value,
or 0 for the bit-rate of 1 MBit/s.

#### CALCULATION OF BIT-RATES :id=formula-1

A bit-rate is calculated according to the following formula:

    bit-rate = frequency / (brp * (1 + tseg1 + tseg2))

#### CALCULATION OF SAMPLE-POINTS :id=formula-2

A sample-point is calculated according to the following formula:

    sample-point = (1 + tseg1) / (1 + tseg1 + tseg2)

#### BIT-TIMING TABLE

| Index |   Bit-rate | Bit time | Sample-point recommendation | Remarks |
| :---- | ---------: | -------: | :-------------------------: | :------ |
| 0     |   1 MBit/s |  1.00 µs | 75% to 90%                |         |
| 1     | 800 kBit/s |  1.25 µs | 75% to 90%                | *Not supported by all devices* |
| 2     | 500 kBit/s |  2.00 µs | 85% to 90%                |         |
| 3     | 250 kBit/s |  4.00 µs | 85% to 90%                |         |
| 4     | 125 kBit/s |  8.00 µs | 85% to 90%                |         |
| 5     | 100 kBit/s |  10.0 µs | 85% to 90%                | *Supported for compatibility* |
| 6     |  50 kBit/s |  20.0 µs | 85% to 90%                |         |
| 7     |  20 kBit/s |  50.0 µs | 85% to 90%                |         |
| 8     |  10 kBit/s | 100.0 µs | 85% to 90%                |         |

Bit-timing table according to CiA CANopen specification.

#### BIT-TIMING SETTINGS FOR CAN CONTROLLER SJA1000

| Bit-rate    | BRP | TSeg1 | TSeg2 | SJW | SAM | Sample-point |
| ----------: | --: | ----: | ----: | --: | --: | :----------- |
|    1 MBit/s |  1  |   5   |   2   |  1  |  0  | 75.0%        |
|  800 kBit/s |  1  |   7   |   2   |  1  |  0  | 80.0%        |
|  500 kBit/s |  1  |   13  |   2   |  1  |  0  | 87.5%        |
|  250 kBit/s |  2  |   13  |   2   |  1  |  0  | 87.5%        |
|  125 kBit/s |  4  |   13  |   2   |  1  |  0  | 87.5%        |
|  100 kBit/s |  5  |   13  |   2   |  2  |  0  | 87.5%        |
|   50 kBit/s |  10 |   13  |   2   |  2  |  0  | 87.5%        |
|   20 kBit/s |  25 |   13  |   2   |  2  |  0  | 87.5%        |
|   10 kBit/s |  50 |   13  |   2   |  2  |  0  | 87.5%        |
|    5 kBit/s |  64 |   16  |   8   |  2  |  0  | 68.0%        |

The CAN controller SJA1000 is running at 8.0 MHz.

#### SYNTAX FOR BIT-RATE STRINGS USED BY CAN API V3 UTILITIES

##### Classic CAN:
    f_clock_mhz=<frequency-in-MHz>,nom_brp=<brp>,nom_tseg1=<tseg1>,nom_tseg2=<tseg2>,nom_sjw=<sjw>,nom_sam=<sam>
##### CAN FD:
    f_clock_mhz=<frequency-in-MHz>,nom_brp=<brp>,nom_tseg1=<tseg1>,nom_tseg2=<tseg2>,nom_sjw=<sjw>,data_brp=<brp>,data_tseg1=<tseg1>,data_tseg2=<tseg2>,data_sjw=<sjw>

### SEE ALSO

[can_start()](/reference/can_start#can_start) respectively [StartController()](/reference/can_start#startcontroller) \
[can_bitrate()](/reference/can_bitrate#can_bitrate) respectively [GetBitrate()](/reference/can_bitrate#getbitrate) and [GetBusSpeed()](/reference/can_bitrate#getbusspeed)


[copyright](../copyright.md ':include')