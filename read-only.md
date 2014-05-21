# Read only items

Inform the client that some collection items are read-only, while still allowing others to be updated and also new items to be created.
Rationale:
The core specification doesn't provide a way to include in the representation what collection items are read-only. This proposal extends the collection representation with this information.
Namely:
 * There are scenarios where new items can be created, some items can be updated while other are read-only. Consider for instance a issue tracking system where any authenticated user can create new issues however is only allowed to edit the issues created or owned but her.
 * For new items to be created, the representation must include a template or a link with the `template` relation type. However, the presence of any of these elements means that the items are also updatable, according to the core specification.
 * Clients should be able to know if an item is not updatable without having to do a `OPTIONS` request. Namely, for usability reasons, a user-facing client should not even show an update option to the user if an item is read-only. 

This extension introduces the new `read-only` property as an optional child property of the `items` array. When present, its value MUST be one of the following literals: `false` or `true`.
Clients SHOULD assume that an item represented by an object with a `read-only` property containing a `true` value is not updatable by that client.

Clients that are unaware of this extension still operate correctly when processing representations containing the `read-only` property: a `PUT` request to an read-only item should still not be allowed by the server (e.g. by returning a response with a `405` status code).

The non-updatability of an item can be relative to the authentication context of a client. For instance, two clients with different authenticated identities can observe the representations of the _same_ item with _different_ `read-only` properties.

Example:

```json
{ "collection":
  {
    "version":"1.0",
    "href":"http://example.org/issues/",  
    "items":[
       {
          "href":"http://example.org/issues/1",
          "read-only":true,
          "data":[
             { "name":"title", "value":"some non-updatable issue"}
          ]             
       },
       {
          "href":"http://example.org/issues/2",
          "read-only":false,
          "data":[
             { "name":"title", "value":"some updatable issue"}
          ]             
       },
       {
          "href":"http://example.org/issues/3",          
          "data":[
             { "name":"title", "value":"some other updatable issue"}
          ]             
       }
    ],
    "template": {(...)}
  }
}
```

### References
1. https://groups.google.com/forum/#!topic/collectionjson/nRpM6flESBE

