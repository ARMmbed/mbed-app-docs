# Design Principles

This section is intended to give you an overview and some rationale for the design decisions we made when developing Envoy. It’s not essential to read this to use Envoy but may be interesting.
RESTful

The objects we deal with during an Envoy interaction are all modeled as resources, very similar to the practices used in RESTful web service design. Similarly, Envoy interactions use GET, PUT, POST and DELETE for retrieval and modification of these resources. 

All resources, including certificates, have a URI. Often this will be addressable, but this is not a requirement. There’s lots of great information about RESTful design on the [web](http://en.wikipedia.org/wiki/Representational_state_transfer). The only things that don't have URIs are POSTed interaction elements, such as invocations or codas.

## Asynchronous

Intents and Invocations are self contained, i.e. they encapsulate enough information for an Envoy to perform a requested action without further information or context. 

Often, resources will have a URI in the cloud. This can make things more power-efficient in some cases, as the Envoy may then access the cloud version of these resources instead of using a transport that incurs a high power or latency cost (e.g. BLE).

Because these resources are self contained, they allow for an efficient caching and proxying system to create store-and-forward semantics for Invocations. For example, a web service could accept an Invocation on behalf of a device; when the Invocation can be performed the web service can take full responsibility, making sure the action is performed without further interaction with the device. 

## Distributed

Every device is a server, even if fairly passive. Devices advertise a "home URL" (via BLE for example), and everything from that point on is driven by an Envoy browsing the resources offered by that server. This is how the Envoy can discover the Intents that a device is serving.

The home URL must offer a home resource which contains:

`name` - the name of the device described by the home resource.

`intents` - a list of Intents currently offered by the device.

## Security & Privacy

Security is enforced by cryptographically signing resources. Each Envoy user identity has one or more associated key pairs, which must form part of a certificate chain for a device to allow an action to be performed (if the device requires authentication). Public key cryptography is preferred over shared keys.
