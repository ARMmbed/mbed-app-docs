# Intents

[IMAGE: ICON TO REPRESENT INTENTS? MAYBE REUSUABLE IN OTHER PLACES?]

An Intent encapsulates an action that a device can perform, contains the information that allows an Envoy to determine if it has the permissions to perform the action, and details any parameters the Envoy must collect to invoke the action. For example, the Intent with action com.arm.connectivity.wifi tells the device to connect to a WiFi network and has parameters for ssid and key.

A devices advertises a set of Intents that can currently be performed. Specifically, an Intent contains the following fields:

`action` - a globally namespaced identifier for the type of action, of the form `<action-id>:<version>` (e.g. `com.arm.connectivity.wifi:1`). Action identifiers are generic, so there should be one action identifier for "opening a door", and so on. 

`constraints` - (optional) a description of the parameters required for the action, including constraints on possible values, such as type, minimum value and maximum value.
Each action ID is associated with some standard set of constraints (and services exist for looking up such constraints), and any constraints in the Intent are in addition to this. See the API docs for full details [LINK].

`authority` - (optional) a list of possible authorities that must authorize the invocation of the action. See the API docs for authority [LINK TO API DOCS].

`endpoint` - the address at which the action can be invoked. This is a URL specifying where the parameters should be sent to make the action being advertised happen. It doesn’t necessarily have to be an address on the device that is advertising the Intent, but often will be. This is analogous to the webhook model often found in web service development.

`url` - (optional) the address at which the Intent is being advertised. This is the URL of the resource that represents the Intent.

`knownParameters` - (optional) a list of (possibly partial) parameter sets that might help the Envoy to generate a UI. You can think of these as auto-fill fields that you might find when filling in a form in a web browser. They are intended to provide the user with a fast way to fill out forms with known or pre-entered values. The Envoy may cache values provided via known parameters. 


In order to promote reuse of Intents and to reduce the size of Intents that the device must store and advertise, the Envoy will also fetch any Intent with a matching action from the Intent registry [LINK TO REGISTRY] and merge the constraints of the Intent provided by the device with the Intent from the registry. Read more about the Intent registry, including how to add new Intents to the registry, here [LINK TO MORE DETAILS REGISTRY SECTION].

Intents are immutable once published to the registry. To make changes to a published Intent a new version with a higher version number must be created. Version numbers are a monotonically increasing integer value. 

*Example* (using JSON encoding)
```json
{
    "url": "http://example.com/intents/wifi",
    "action": "com.arm.connectivity.wifi:1",
    "endpoint": "/invocations",
    "constraints: { ... },
    "authority": [ ... ],
    "knownParameters": [
        { "ssid": "MiWiFi" },
        { "ssid": "OtherWiFi", "key":"supersecretpassword"}
    ]
}
```
