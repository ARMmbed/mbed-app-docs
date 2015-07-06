# Constraint Set

A device will often require parameters for performing an action: a thermostat might need to know the SSID and password for a network so it can get internet access; a lighting system might need to know how long to keep the lights on after you leave a room; a coffee machine might let you configure how much water you like in your coffee. The number of different configuration options is endless. Envoy provides a flexible system that allows you to describe what the valid set of parameters to your device looks like without having to enumerate everything.

This is captured by a set of constraints, which includes things like minimum and maximum values, data types, data format, title and description. See the constraints API documentation [LINK TO CONSTRAINTS DOCUMENTATION] for full details.

*Note: not all of the constraints need to be transmitted from the device. There is a central repository of Intents that devices should reuse and build upon. [LINK TO INTENT REGISTRY]*

**Example** (using JSON encoding)
```json
{
    "type": "dictionary",
    "title": "WiFi Access",
    "description": "Connect to a WiFi network",
    "icon": "../icons/wifi.svg",
    "properties": {
        "ssid": {
            "title": "Network Name",
            "description": "The name of the network.",
            "type": "string"
        },
        "key": {
            "title": "Password",
            "description": "The password for the network.",
            "type": "string"
        }
    }
}
```