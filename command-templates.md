# Collection+JSON Extensions

## 1.0 Command Templates

Clients that support the [Collection+JSON](http://amundsen.com/media-types/collection/) media type MAY be able to recognize and parse command templates found within responses. Command templates MAY consist of a `data` array associated with an `href` property. The `commands` array supports command templates.

For command templates, the name/value pairs of the `data` array set are sent as JSON in the body (`{"id": 1, "members_to_notify": "all"}`) or multipart/form-data, both via an HTTP POST.

## 2.0 commands

The `commands` array is an OPTIONAL top-level property of the [Collection+JSON](http://amundsen.com/media-types/collection/) document.

The `commands` array SHOULD contain one or more anonymous objects. Each object composed of five possible properties: `href` (REQUIRED), `rel` (REQUIRED), `name` (OPTIONAL), `prompt` (OPTIONAL), and a `data` array (OPTIONAL).

If present, the `data` array represents command parameters for the associated `href` property of the same object. See Command Templates for details.

```json
// samples commands array

{
  "commands": [
    {
      "href": "/users/disable",
      "rel": "disable",
      "name" "Disable",
      "prompt": "Disable user",
      "data": [
        {"name": "id", "value": "", "prompt": "User id to disable"}
      ]
    },
    ...
    {"href": URI, "rel": STRING, "prompt": STRING, "name": STRING}
  ]
}
```
