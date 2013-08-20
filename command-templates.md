# Command Templates

Clients that support the [Collection+JSON](http://amundsen.com/media-types/collection/) media type MAY be able to recognize and parse command templates found within responses. Command templates MAY consist of a `data` array associated with an `href` property. The `commands` arrary supports command templates.

For command templates, the name/value pairs of the `data` array set are appended to the `URI` found in the `href` property associated with the `commands` arrary (with a question-mark ["?"] as separator) and this new `URI` is sent to the processing agent via an HTTP POST.

```json
{
  "commands": [
    {
      "href": "/users/1/disable",
      "rel": "disable",
      "prompt": "Enter number of days to disable (0 means indefinite)",
      "data": [
        {"name": "days", "value": ""}
      ]
    }
  ]
}
```
