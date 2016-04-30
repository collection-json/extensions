# Title Property

Add the OPTIONAL `collection.title` property. 

The `title` property MAY be a child of the `collection` object. If it exists, it MUST be treated as a simple STRING. 
Clients MAY use the value of this property for display in user interfaces or for other purposes.

## Example

```json
{
  "collection": {
    "version": "1.0",
    "href": "http://api.example.org/tasks/",
    "title": "Tasks Collection",
    "links": [ ],
    "items": [ ],
    "queries":[ ],
    "template: { }
  }
}
```

## Discussion

????
