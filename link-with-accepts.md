# 'accepts' property for link

Add an optional property,  <code>accepts</code>, to the <code>link</code> object whose purpose is to allow the server to indicate the representations available for the indicated resource. If present, the value MUST be a string and SHOULD contain a comma separated list of valid media types. 

##example
```json
{
	"collection": {
		"version":"1.0",
		"href":"/members/pending",
		"items": {
			{
				"href":"/members/1",
				"data": [
					{"prompt":"name", "name":"full-name", "value":"john doe"},
					{"prompt":"enrollment date", "name":"enrollment-date", "value":"2015-06-01"},
				],
				"links" : [
					{"href":"/members/1/contract", "rel":"/rels/contract", "prompt":"contract", "name":"contract", "accepts":"application/pdf, text/html"}
				]
			},
			{
				"href":"/members/2",
				"data": [
					{"prompt":"name", "name":"full-name", "value":"homer"},
					{"prompt":"enrollment date", "name":"enrollment-date", "value":"2015-05-29"},
				],
				"links" : [
					{"href":"/members/2/contract", "rel":"/rels/contract", "prompt":"contract", "name":"contract", "accepts":"application/pdf, text/html"}
				]
			}
		}
	}
}

```

##References
[https://groups.google.com/forum/#!topic/collectionjson/C1GB4UC7_mc](https://groups.google.com/forum/#!topic/collectionjson/C1GB4UC7_mc)