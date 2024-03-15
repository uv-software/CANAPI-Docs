### NAME

> *can_property* - get or modify a property value of a CAN channel or of the CAN API library

### SYNOPSIS

<a id="can_property"></a>
**C Interface**
```C
int can_property(int handle, uint16_t param, void *value, uint32_t nbyte);
```
<a id="getproperty"></a>
<a id="setproperty"></a>
**C++ Methods**
```C++
CANAPI_Return_t GetProperty(uint16_t param, void *value, uint32_t nbyte);

CANAPI_Return_t SetProperty(uint16_t param, const void *value, uint32_t nbyte)
```
<a id=""></a>
**Swift Properties**
```Swift
...
```

### DESCRIPTION

The function [can_property()](#can_property) retrieves or modifies a property value of the CAN channel given by the *handle* argument.

The [id.](/reference/property_ids#property_defines) of the property to read or to write is determined by the *param* argument. The property value and its size (in byte) are specified by the *value* argument respectively the *nbyte* argument.

To read or to write a property value of the CAN API V3 library itself, the value ***-1*** can be given as *handle*.

The method [GetProperty()](#getproperty) retrieves a property value of a CAN channel.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [*InitializeChannel()*](/reference/can_init#initializechannel) from that instance.

The method [SetProperty()](#setproperty) modifies a property value of a CAN channel.
The class instance from which the method is called must be associated with a CAN channel by a previous successful call of [*InitializeChannel()*](/reference/can_init#initializechannel) from that instance.

### RETURN VALUE

Upon successful completion, the C function and the C++ method will return 0. On error, a negative value will be returned (see [errors](#errors)).

In case of an error, the Swift method will throw an exception with a corresponding error code as exception object (see [errors](#errors)).

### ERRORS

Under the following conditions, [can_property()](#can_property) respectively [GetProperty()](#getproperty) and [SetProperty()](#setproperty) will fail and return the appropriated error code:

[CANERR_NOTINIT](/reference/error_codes#error_notinit) - channel not initialized \
[CANERR_HANDLE](/reference/error_codes#error_handle)   - invalid channel handle \
[CANERR_NULLPTR](/reference/error_codes#error_nullptr) - null-pointer assignment \
[CANERR_ILLPARA](/reference/error_codes#error_illpara) - invalid parameter (id., value, or nbyte) \
[CANERR_NOTSUPP](/reference/error_codes#error_notsupp) - property or function not supported \
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
[Property IDs](/reference/property_ids#name) \
[Error Codes](/reference/error_codes#name)


[copyright](../copyright.md ':include')