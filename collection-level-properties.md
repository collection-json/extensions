# Collection level data properties

Provide additional metadata about the collection as a whole, rather than for a specific item.

## Rationale:

The core specification doesn’t provide a way to specify metadata about the collection as a whole. This extension proposes a method to provide properties at the collection level utilising a similar approach to data entries at the item level.

 * A simple example relates to pagination. Typically, when the size of a collection is large, items will be returned in pages, with links used to allow traversal between the pages of results ([next](https://www.w3.org/TR/html5/links.html#link-type-next), [prev](https://www.w3.org/TR/html5/links.html#link-type-prev), etc.). However, it would be useful to know the total number of available results, or pages. This is a property of the collection as a whole, rather than any individual item.
 * Similarly, more detailed names, titles, and summaries of the collection can be provided. This is useful where a subset of the 'whole' collection is being returned in response to some sort of query, especially when the results are a "fuzzy" match to the query.

This extension augments the [collection](https://github.com/collection-json/spec/blob/master/README.md#21-collection) object, with an additional child property `properties` which MAY be provided in a response containing zero or more [items](https://github.com/collection-json/spec/blob/master/README.md#31-items). There may only be one instance of the [properties](#properties) property in a [collection](https://github.com/collection-json/spec/blob/master/README.md#21-collection)

#### Properties:

The value of the `properties` element MUST be an ARRAY of zero or more anonymous objects. Each object MAY have any of three possible properties: name (REQUIRED), value (OPTIONAL), and prompt (OPTIONAL). 

This mirrors the approach of the existing [data]( https://github.com/collection-json/spec/blob/master/README.md#32-data)  property of [items](https://github.com/collection-json/spec/blob/master/README.md#31-items).

```json
// Example using properties to return number of hits from a search for "Hstory" (sic)
{ "collection":
  {
    "version":"1.0",
    "href":"http://example.org/issues/?q=Hstory",  
    “properties”: [
       {
       “name” : “size”,
       “value” : 267,
       “prompt” : “Total number of results”
       },
       {
       “name” : “pages”,
       “value” : 27
       “prompt” : “Number of result pages”
       },
       {
       "name" : "subtitle",
       "value" : "Page 1 of 27"
       {
       "name" : "title",
       "value" : "No Items matched Hstory. Returning items matching History"
       }
    ]
    "items": [...]
    "template": {(...)}
  }
}
```

### References
1. https://groups.google.com/forum/#!topic/collectionjson/GzDeBUVvcgQ

