# What is Envoy?

**en·voy** – “accredited messenger or representative.”

Envoy is your representative in the digital world; your personal assistant in the business of device interactions; your filter on attention seeking technology. Envoy lets you focus on what’s important.

Devices, whether connected or not, usually require configuration to make them work. This configuration process can present a real challenge for users that are less confident with technology, and is a recurring annoyance for those that are. Today, each product implements a different system, with a different user interface, using different conventions, different button combinations, with different flashing lights and different bleeps. This is bad for users, constraining for designers and complex for developers. We can do better.

Envoy provides a simple, flexible system for a device to ask for input from the user. The same simple system can be reused between different devices from different manufacturers ensuring the same conventions and the same experience across all of a user's devices. It eliminates re-entry of common data such as WiFi credentials. We think this creates a great user experience and makes more products more accessible to more people.


### What do I need to use Envoy in my product?

Envoy uses Bluetooth Low Energy (BLE) technology to communicate configuration information from a smartphone, tablet or wearable device to a device that needs configuration. This means that to use Envoy to set up your product you need to make sure BLE is designed in. Envoy provides a set of libraries for use with mbed OS to make building connected devices fast and scalable.

### What do my customers need to use Envoy?

Your users will need to have the Envoy application installed on their smartphone or tablet. The Envoy application is available for free from the Apple App Store [LINK]. 


## Example Use Cases

### WiFi Configuration

[IMAGE: WIFI PROVISIOING / COFEE MACHINE USE CASE?]

A simple example of configuration data that is often required during the setup of a new device is WiFi credentials. Typing in details repeatedly, and the struggle to remember the right password, are familiar to most people.

The action of joining a WiFi network typically requires two pieces of information:

ssid - the name of the network that should be joined.
key - the ‘password’ to access the network. 

Using Envoy can simplify this process, making the selection and authentication of preferred WiFi networks as simple as a tap from a list of options. Using Envoy enables reuse of previously entered credentials, to avoid re-entry when configuring new devices for the same network.

To find out how to use Envoy to configure your WiFi-enabled device, see the WiFi tutorial [LINK TO WIFI TUTORIAL HERE].


### Complex Configuration

[IMAGE: DEVICE IN CONVERSATION TO GET CONFIGURATION?]

Configuring WiFi is great - but for most products that’s not enough. That’s why Envoy allows you to define the configuration details that you need from your users. 

Using an extensible constraint-based system, you can efficiently describe the details you need, including data types, formats, minimum and maximum values and nesting of properties. Envoy will then deal with displaying an appropriate user interface and remembering values for reuse later on.

To find out how to use Envoy for custom complex configuration see the Configuration tutorial [LINK TO CONFIGURATION TUTORIAL HERE].