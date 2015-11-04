
## WiFi Configuration

![Wifi](../IMG_Assets/IMG_WiFiConfig (envoy).png)

A simple example of configuration data that is often required during the setup of a new device is WiFi credentials. Typing in details repeatedly, and the struggle to remember the right password, are familiar to most people.

The action of joining a WiFi network typically requires two pieces of information:

`ssid` - the name of the network that should be joined.

`key` - the ‘password’ to access the network. 

Using the mbed App can simplify this process, making the selection and authentication of preferred WiFi networks as simple as a tap from a list of options. Using the app enables reuse of previously entered credentials, to avoid re-entry when configuring new devices for the same network.

To find out how to use the mbed App to configure your WiFi-enabled device, see the [provisioning example](https://github.com/ARMmbed/equip-hello-mbed).


## Complex Configuration

Configuring WiFi is great - but for most products that’s not enough. That’s why the mbed App allows you to define the configuration details that you need from your users. 

Using an extensible constraint-based system, you can efficiently describe the details you need, including data types, formats, minimum and maximum values and nesting of properties. The app will then deal with displaying an appropriate user interface and remembering values for reuse later on.

To find out how to use the mbed App for custom complex configuration see the [provisioning example](https://github.com/ARMmbed/equip-hello-mbed).
