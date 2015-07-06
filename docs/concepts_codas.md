# Codas

[IMAGE: ICON TO REPRESENT CODA? MAYBE REUSUABLE IN OTHER PLACES?]

A coda generally refers to "the concluding passage of music, typically forming an addition to the basic structure". In this case Coda is the receipt of a concluding transaction. When an Envoy has posted an Invocation to a device, the device generates a Coda and sends it to the `codaEndpoints` specified by the Invocation.

The Coda can be used as a verifiable receipt that a device received and performed an Invocation. The fields of a Coda are:

`invocation` - the ID from the Invocation that the coda is responding to.

`status` - an integer status code. Similar to HTTP status codes. Valid values are 200, 400, 500 with the same meanings as for HTTP.

`more` - are there more codas for this Invocation expected later? This indicates to the Envoy that it might need to hold open a connection to a device (for example, when using BLE). 

`intents` - a set of Intents that are now being offered as a result of performing the action. Often performing an action will result in a change in the device's behaviour. For example, after an unlock Intent is invoked a door might subsequently offer a lock Intent.

**Example** (using JSON encoding)
```json
{
    "invocation": 982387642302386,
    "status": 200,
    "more": false,
    "intents": [ ... ]
}
```
