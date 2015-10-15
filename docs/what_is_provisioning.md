# What is the mbed Provisioning App?

Devices, whether connected or not, usually require configuration to make them work. This configuration process can present a real challenge for users that are less confident with technology, and is a recurring annoyance for those that are. Today, each product implements a different system, with a different user interface, using different conventions, different button combinations, with different flashing lights and different bleeps. This is bad for users, constraining for designers and complex for developers.

The mbed Provisioning App provides a simple, flexible system for a device to ask for input from the user. The same simple system can be reused between different devices from different manufacturers ensuring the same conventions and the same experience across all of a user's devices. It eliminates re-entry of common data such as WiFi credentials. We think this creates a great user experience and makes more products more accessible to more people.


### What do I need to use the mbed Provisioning App with my product?

The mbed Provisioning App uses Bluetooth Low Energy (BLE) technology to communicate configuration information from a smartphone, tablet or wearable device to a device that needs configuration. This means that to use the app to set up your product you need to make sure BLE is designed in. We provide a set of libraries for use with mbed OS to make building connected devices fast and scalable.

### What do my customers need to setup their devices?

Your users will need to have the mbed Provisioning App installed on their smartphone or tablet. The application is available for [free](faqs.md#how-do-i-get-the-envoy-app). 
