### NAME

> CAN API V3 property id.s

### SYNOPSIS

<a id="property_defines"></a>
**C/C++ Defines**
```C++
#define CANPROP_GET_SPEC             0U
#define CANPROP_GET_VERSION          1U
#define CANPROP_GET_PATCH_NO         2U
#define CANPROP_GET_BUILD_NO         3U
#define CANPROP_GET_LIBRARY_ID       4U
#define CANPROP_GET_LIBRARY_VENDOR   5U
#define CANPROP_GET_LIBRARY_DLLNAME  6U
#define CANPROP_GET_DEVICE_TYPE     10U
#define CANPROP_GET_DEVICE_NAME     11U
#define CANPROP_GET_DEVICE_VENDOR   12U
#define CANPROP_GET_DEVICE_DLLNAME  13U
#define CANPROP_GET_DEVICE_PARAM    14U
#define CANPROP_GET_OP_CAPABILITY   15U
#define CANPROP_GET_OP_MODE         16U
#define CANPROP_GET_BITRATE         17U
#define CANPROP_GET_SPEED           18U
#define CANPROP_GET_STATUS          19U
#define CANPROP_GET_BUSLOAD         20U
#define CANPROP_GET_NUM_CHANNELS    21U
#define CANPROP_GET_CAN_CHANNEL     22U
#define CANPROP_GET_CAN_CLOCK       23U
#define CANPROP_GET_TX_COUNTER      24U
#define CANPROP_GET_RX_COUNTER      25U
#define CANPROP_GET_ERR_COUNTER     26U
#define CANPROP_GET_RCV_QUEUE_SIZE  27U
#define CANPROP_GET_RCV_QUEUE_HIGH  28U
#define CANPROP_GET_RCV_QUEUE_OVFL  29U
#define CANPROP_GET_TRM_QUEUE_SIZE  30U
#define CANPROP_GET_TRM_QUEUE_HIGH  31U
#define CANPROP_GET_TRM_QUEUE_OVFL  32U
#define CANPROP_GET_FLT_11BIT_CODE  40U
#define CANPROP_GET_FLT_11BIT_MASK  41U
#define CANPROP_GET_FLT_29BIT_CODE  42U
#define CANPROP_GET_FLT_29BIT_MASK  43U
#define CANPROP_SET_FLT_11BIT_CODE  44U
#define CANPROP_SET_FLT_11BIT_MASK  45U
#define CANPROP_SET_FLT_29BIT_CODE  46U
#define CANPROP_SET_FLT_29BIT_MASK  47U
#if (OPTION_CANAPI_LIBRARY != 0)
/* - -  build-in bit-rate conversion  */
#define CANPROP_GET_BTR_INDEX       64U
#define CANPROP_GET_BTR_VALUE       65U
#define CANPROP_GET_BTR_SPEED       66U
#define CANPROP_GET_BTR_STRING      67U
#define CANPROP_GET_BTR_SJA1000     68U
#define CANPROP_SET_BTR_INDEX       72U
#define CANPROP_SET_BTR_VALUE       73U
#define CANPROP_SET_BTR_SPEED       74U
#define CANPROP_SET_BTR_STRING      75U
#define CANPROP_SET_BTR_SJA1000     76U
/* - -  build-in message formatter - */
#define CANPROP_GET_MSG_STRING     128U
#define CANPROP_GET_MSG_TIME       129U
#define CANPROP_GET_MSG_ID         130U
#define CANPROP_GET_MSG_DLC        131U
#define CANPROP_GET_MSG_FLAGS      132U
#define CANPROP_GET_MSG_DATA       133U
#define CANPROP_GET_MSG_ASCII      134U
#define CANPROP_SET_MSG_FORMAT     144U
#define CANPROP_SET_FMT_TIMESTAMP  145U
#define CANPROP_SET_FMT_TIEMUSEC   146U
#define CANPROP_SET_FMT_TIME       147U
#define CANPROP_SET_FMT_ID         148U
#define CANPROP_SET_FMT_XTD        149U
#define CANPROP_SET_FMT_DLC        150U
#define CANPROP_SET_FMT_LENGTH     151U
#define CANPROP_SET_FMT_BRACKETS   152U
#define CANPROP_SET_FMT_FLAGS      153U
#define CANPROP_SET_FMT_DATA       154U
#define CANPROP_SET_FMT_ASCII      155U
#define CANPROP_SET_FMT_SUBSTITUTE 156U
#define CANPROP_SET_FMT_CHANNEL    157U
#define CANPROP_SET_FMT_COUNTER    158U
#define CANPROP_SET_FMT_SEPARATOR  159U
#define CANPROP_SET_FMT_WRAPAROUND 160U
#define CANPROP_SET_FMT_EOL_CHAR   161U
#define CANPROP_SET_FMT_RX_PROMPT  162U
#define CANPROP_SET_FMT_TX_PROMPT  163U
#endif
/* - -  access to vendor and interface list */
#if (OPTION_CANAPI_LIBRARY != 0)
#define CANPROP_SET_FIRST_VENDOR   224U
#define CANPROP_SET_NEXT_VENDOR    225U
#define CANPROP_GET_VENDOR_ID      226U
#define CANPROP_GET_VENDOR_NAME    227U
#define CANPROP_GET_VENDOR_DLLNAME 228U
#endif
#define CANPROP_SET_FIRST_CHANNEL  240U
#define CANPROP_SET_NEXT_CHANNEL   241U
#define CANPROP_GET_CHANNEL_NO     242U
#define CANPROP_GET_CHANNEL_NAME   243U
#define CANPROP_GET_CHANNEL_DLLNAME 244U
#define CANPROP_GET_CHANNEL_VENDOR_ID 245U
#define CANPROP_GET_CHANNEL_VENDOR_NAME 246U
/* - -  search path for JSON configuration files */
#if (OPTION_CANAPI_LIBRARY != 0)
#define CANPROP_SET_SEARCH_PATH    253U
#endif
/* - -  access to device handle (for C++ wrapper classes) */
#define CANPROP_GET_CPP_BACKDOOR   255U
/* - -  access to vendor-specific properties */
#define CANPROP_GET_VENDOR_PROP    256U
#define CANPROP_SET_VENDOR_PROP    512U
#define CANPROP_VENDOR_PROP_RANGE  256U
#define CANPROP_DRIVER_SPECIFIC 0x8000U

#define CANPROP_MAX_BUFFER_SIZE    256U

#define CANPROP_MAX_STRING_LENGTH 1024U
```

### DESCRIPTION

CAN API V3 provides a rich set of properties that can be read either from the CAN API library, the CAN driver or the CAN controller associated with a CAN channel.

Property **GET_SPEC** : version of the wrapper specification (`uint16_t`)

Property **GET_VERSION** : version number of the library (`uint16_t`)

Property **GET_PATCH_NO** : patch number of the library (`uint8_t`)

Property **GET_BUILD_NO** : build number of the library (`uint32_t`)

Property **GET_LIBRARY_ID** : library id of the library (`int32_t`)

Property **GET_LIBRARY_VENDOR** : vendor name of the library (`char[256]`)

Property **GET_LIBRARY_DLLNAME** : file name of the library DLL (`char[256]`)

Property **GET_DEVICE_TYPE** : device type of the CAN interface (`int32_t`)

Property **GET_DEVICE_NAME** : device name of the CAN interface (`char[256]`)

Property **GET_DEVICE_VENDOR** : vendor name of the CAN interface (`char[256]`)

Property **GET_DEVICE_DLLNAME** : file name of the CAN interface DLL (`char[256]`)

Property **GET_DEVICE_PARAM** : device parameter of the CAN interface (`char[256]`)

Property **GET_OP_CAPABILITY** : supported operation modes of the CAN controller (`uint8_t`)

Property **GET_OP_MODE** : active operation mode of the CAN controller (`uint8_t`)

Property **GET_BITRATE** : active bit-rate of the CAN controller (`can_bitrate_t`)

Property **GET_SPEED** : active bus speed of the CAN controller (`can_speed_t`)

Property **GET_STATUS** : current status register of the CAN controller (`uint8_t`)

Property **GET_BUSLOAD** : current bus load of the CAN controller (`uint16_t`)

Property **GET_NUM_CHANNELS** : numbers of CAN channels on the CAN interface (`uint8_t`)

Property **GET_CAN_CHANNEL** : active CAN channel on the CAN interface (`uint8_t`)

Property **GET_CAN_CLOCK** : frequency of the CAN controller clock in [Hz] (`int32_t`)

Property **GET_TX_COUNTER** : total number of sent messages (`uint64_t`)

Property **GET_RX_COUNTER** : total number of received messages (`uint64_t`)

Property **GET_ERR_COUNTER** : total number of received error frames (`uint64_t`)

Property **GET_RCV_QUEUE_SIZE** : maximum number of message the receive queue can hold (`uint32_t`)

Property **GET_RCV_QUEUE_HIGH** : maximum number of message the receive queue has hold (`uint32_t`)

Property **GET_RCV_QUEUE_OVFL** : overflow counter of the receive queue (`uint64_t`)

Property **GET_TRM_QUEUE_SIZE** : maximum number of message the transmit queue can hold (`uint32_t`)

Property **GET_TRM_QUEUE_HIGH** : maximum number of message the transmit queue has hold (`uint32_t`)

Property **GET_TRM_QUEUE_OVFL** : overflow counter of the transmit queue (`uint64_t`)

Property **GET_FLT_11BIT_CODE** : acceptance filter code of 11-bit identifier (`int32_t`)

Property **GET_FLT_11BIT_MASK** : acceptance filter mask of 11-bit identifier (`int32_t`)

Property **GET_FLT_29BIT_CODE** : acceptance filter code of 29-bit identifier (`int32_t`)

Property **GET_FLT_29BIT_MASK** : acceptance filter mask of 29-bit identifier (`int32_t`)

Property **SET_FLT_11BIT_CODE** : set value for acceptance filter code of 11-bit identifier (`int32_t`)

Property **SET_FLT_11BIT_MASK** : set value for acceptance filter mask of 11-bit identifier (`int32_t`)

Property **SET_FLT_29BIT_CODE** : set value for acceptance filter code of 29-bit identifier (`int32_t`)

Property **SET_FLT_29BIT_MASK** : set value for acceptance filter mask of 29-bit identifier (`int32_t`)

Property **GET_BTR_INDEX** : bit-rate as CiA index (`int32_t`)

Property **GET_BTR_VALUE** : bit-rate as struct (`can_bitrate_t`)

Property **GET_BTR_SPEED** : bit-rate as bus speed (`can_speed_t`)

Property **GET_BTR_STRING** : bit-rate as string (`char[256]`)

Property **GET_BTR_SJA1000** : bit-rate as SJA1000 register (`uint16_t`)

Property **SET_BTR_INDEX** : set value for conversion form CiA index (`int32_t`)

Property **SET_BTR_VALUE** : set value for conversion form struct (`can_bitrate_t`)

Property **SET_BTR_SPEED** : set value for conversion form bus speed (`can_speed_t`)

Property **SET_BTR_STRING** : set value for conversion form string (`char[256]`)

Property **SET_BTR_SJA1000** : set value for conversion form SJA1000 register (`uint16_t`)

Property **GET_MSG_STRING** : last received or sent message as formatted string (`char[1024]`)

Property **GET_MSG_TIME** : time-stamp of last received or sent message (`char[256]`)

Property **GET_MSG_ID** : identifier of last received or sent message (`char[256]`)

Property **GET_MSG_DLC** : DLC/length of last received or sent message (`char[256]`)

Property **GET_MSG_FLAGS** : flags of last received or sent message (`char[256]`)

Property **GET_MSG_DATA** : data of last received or sent message (`char[256]`)

Property **GET_MSG_ASCII** : data as ASCII of last received or sent message (`char[256]`)

Property **SET_MSG_FORMAT** : set message output format {DEFAULT, ...} (`int`)

Property **SET_FMT_TIMESTAMP** : set formatter option: time-stamp {ZERO, ABS, REL} (`int`)

Property **SET_FMT_TIEMUSEC** : set formatter option: time-stamp in usec {OFF, ON} (`int`)

Property **SET_FMT_TIME** : set formatter option: time format {TIME, SEC, DJD} (`int`)

Property **SET_FMT_ID** : set formatter option: identifier {HEX, DEC, OCT} (`int`)

Property **SET_FMT_XTD** : set formatter option: extended identifier {OFF, ON} (`int`)

Property **SET_FMT_DLC** : set formatter option: DLC/length {DEC, OCT, HEX} (`int`)

Property **SET_FMT_LENGTH** : set formatter option: CAN FD format {DLC, LENGTH} (`int`)

Property **SET_FMT_BRACKETS** : set formatter option: DLC in brackets {'\0', '(`', '['} (`int`)

Property **SET_FMT_FLAGS** : set formatter option: message flags {ON, OFF} (`int`)

Property **SET_FMT_DATA** : set formatter option: message data {HEX, DEC, OCT} (`int`)

Property **SET_FMT_ASCII** : set formatter option: data as ASCII {ON, OFF} (`int`)

Property **SET_FMT_SUBSTITUTE** : set formatter option: substitute for non-printables (`int`)

Property **SET_FMT_CHANNEL** : set formatter option: message source {OFF, ON} (`int`)

Property **SET_FMT_COUNTER** : set formatter option: message counter {ON, OFF} (`int`)

Property **SET_FMT_SEPARATOR** : set formatter option: separator {SPACES, TABS} (`int`)

Property **SET_FMT_WRAPAROUND** : set formatter option: wraparound {NO, 8, 10, 16, 32, 64} (`int`)

Property **SET_FMT_EOL_CHAR** : set formatter option: end-of-line character {OFF, ON} (`int`)

Property **SET_FMT_RX_PROMPT** : set formatter option: prompt for received messages (`char[6+1]`)

Property **SET_FMT_TX_PROMPT** : set formatter option: prompt for sent messages (`char[6+1]`)

Property **SET_FIRST_VENDOR** : set index to the first entry in the vendor list (`NULL`)

Property **SET_NEXT_VENDOR** : set index to the next entry in the vendor list (`NULL`)

Property **GET_VENDOR_ID** : get library id at actual index in the vendor list (`int32_t`)

Property **GET_VENDOR_NAME** : get vendor name at actual index in the vendor list (`char[256]`)

Property **GET_VENDOR_DLLNAME** : get file name of the DLL at actual index in the vendor list (`char[256]`)

Property **SET_FIRST_CHANNEL** : set index to the first entry in the interface list (`int32_t or NULL`)

Property **SET_NEXT_CHANNEL** : set index to the next entry in the interface list (`NULL`)

Property **GET_CHANNEL_NO** : get channel no. at actual index in the interface list (`int32_t`)

Property **GET_CHANNEL_NAME** : get channel name at actual index in the interface list (`char[256]`)

Property **GET_CHANNEL_DLLNAME** : get file name of the DLL at actual index in the interface list (`char[256]`)

Property **GET_CHANNEL_VENDOR_ID** : get library id at actual index in the interface list (`int32_t`)

Property **GET_CHANNEL_VENDOR_NAME** : get vendor name at actual index in the interface list (`char[256]`)

Property **SET_SEARCH_PATH** : set search path for interface configuration files (`char[256]`)

Property **GET_CPP_BACKDOOR** : get device handle (`int32_t`)

Property **GET_VENDOR_PROP** : offset to get a vendor-specific property value (`void*`)

Property **SET_VENDOR_PROP** : offset to set a vendor-specific property value (`void*`)

### SEE ALSO

[can_property()](/reference/can_property#can_property) respectively [GetProperty()](/reference/can_property#getproperty) and [SetProperty()](/reference/can_property#setproperty)


[copyright](../copyright.md ':include')