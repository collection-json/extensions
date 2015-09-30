# Deprecated Property

Clients that support the [Collection+JSON](https://github.com/collection-json/spec) media type MAY be able to recognize and parse an OPTIONAL `deprecated` property on items within the [data array](https://github.com/collection-json/spec#32-data) to indicate that the item is being removed. The value of the property SHOULD be a boolean value of `true` or `false`.

## Example

```json
data: [
  {
    "name": "old_name",
    "value": "Robert Tables",
    "prompt": "'old_name' is deprecated and will be removed in a future version, use 'new_name' instead."
    "deprecated": true
  },{
    "name": "new_name",
    "value": "Robert Tables",
    "prompt": "Name"
  }
]
```

## Discussion

[Extension Proposal] (https://groups.google.com/forum/#!topic/collectionjson/plwrVxn7fw4)
