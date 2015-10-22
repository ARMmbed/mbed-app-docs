# Protocol Description

This section details the protocol specifics for various types of transport that the mbed Provisioning App supports. In general, the protocol should not be tied to a single transport, e.g. HTTP or BLE GAT. Instead, the concepts detailed above are mapped to the supported transports to give an efficient yet interoperable system.

**Note: the only supported transport at the moment is CBOR encoding over Bluetooth Low Energy using the block transfer service**


## Bluetooth Low Energy

Bluetooth Low Energy is an exciting protocol that many connected devices are adopting, often in combination with a higher data rate, longer range radio. It is a short-range wireless communication technology, which, unlike the classic Bluetooth standard, is designed to reduce power consumption, allowing your BLE device to run for months or years on a coin-cell battery.

### BLE Service & Characteristic Details

mbed Provisioning App uses the service UUID 0xFE8E. The service is built on top of the BLE Block Transfer service that is already provided in mbed OS. The characteristic UUIDs used for the block transfer are:

`device_incoming` - `0x0001` is a readable, notifiable characteristic used for data heading towards the device.

`device_outgoing` - `0x0002` is a writable characteristic used for data leaving the device.

### Resource Serialisation for BLE

*Note: if you are using the mbed OS library for the mbed Provisioning App, the library will handle encoding and decoding for you - so you can skip this section.*

When an app interacts with your device over a BLE connection, the resources described in this documentation are encoded as CBOR [http://cbor.io/]. This efficient encoding uses a binary format suitable for constrained embedded devices. The encoded resources are then sent to and from your device using the BLE Block Transfer protocol.

CBOR is a document serialisation format heavily inspired by the JSON data model: numbers, strings, arrays, maps (called objects in JSON), and a few values such as false, true, and null.

To further compress the resources that are transferred from your device, mbed Provisioning App defines a mapping from string key names as used in JSON, e.g. “`action`” and “`codaEndpoints`” to a more efficient integer representation for use with CBOR. This mapping can be found in the headers for the [mbed OS library](https://github.com/ARMmbed/equip-cpp).

Unlike JSON, CBOR supports semantic tagging of values in the serialisation. Semantic tags provide a hint to the decoder as to what the intended format of value is. You can think of this as a kind of type-hint for the decoder. The mbed Provisioning App expects the following semantic tags for the resource types described above:

**Intent** - has semantic tag `16397`

**Invocation** - has semantic tag `16398`

**Coda** - has semantic tag `16399`

**ConstraintSet** - has semantic tag `16426`


