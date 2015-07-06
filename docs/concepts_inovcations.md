# Invocations

When an Envoy wants to perform an action advertised as an Intent by a device, it generates an Invocation resource that encapsulates the parameters that the device should use for performing the action. It also provides some proof that the Envoy has permission to perform the action it’s requesting. More on the proof mechanism here [LINK].

The Invocation is then posted to the endpoint that was specified in the Intent (to make the action happen). An Invocation has the following properties:

`id` - a unique ID generated by the Envoy for this particular invocation of the Intent.

`action` - the action from the Intent.

`parameters` - a set of values that fulfill the constraints described by the Intent. These are the values that the device should use to perform the action.

`codaEndpoints` - a list of addresses to which the result of the action should be posted (in the form of a Coda[LINK]). This doesn’t necessarily have to be an address on the Envoy that created the invocation, but there are user experience downsides when you do not notify the Envoy directly about the result. This is analogous to the webhook model often found in web service development. 

*Example* (using JSON encoding)
```json
{
    "id": 982387642302386,
    "action": "com.arm.connectivity.wifi:1",
    "parameters": { ... },
    "codaEndpoints": [
        "/codas",
        "https://example.com/codas/32642378"
    ]
}
```