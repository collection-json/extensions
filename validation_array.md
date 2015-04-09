# Validations Array

Clients that support the [Collection+JSON](http://amundsen.com/media-types/collection/) media type MAY be able to recognize and parse an array of validations found in a template's data array. The validations array MAY be included within a data element of the data array.

The validations array is an OPTIONAL property of an individual data element within the data array.

The validations array SHOULD contain one or more anonymous objects. Each object composed of four possible properties: 

* `name` (REQUIRED) - The name of the validator. If the `name` is missing, clients MUST ignore that validation rule.
* `prompt` (OPTIONAL) - The description of the validator as documentation for the developer.
* `arguments` (VALIDATOR-SPECIFIC) - An array of anonymous objects consisting of a `name` and `value` that will act as arguments for the validator. If the array is missing a `name` or `value` argument, clients should ignore that item. If a validator has required arguments and the array is missing or incomplete, clients MUST ignore that validation rule.
* `message` (OPTIONAL) - A message to pass to the user in the event that the validation failed. If this item is missing, clients SHOULD assume a `message` of "Validation failed".

Clients that support the validations array SHOULD accept, parse and process all common validators defined below.

## Common Validators

### Inclusion

Inclusion validates a value to ensure it is within a list of allowed values.

* Name: `inclusion`
* Arguments
  * (REQUIRED) one or more `option` elements.

```json
"validations": [{
  "name": "inclusion",
  "prompt": "The list of allowed background colors",
  "message": "The background color can be red, green or blue",
  "arguments": [{
    "name": "option",
    "value": "red"
  },{
    "name": "option",
    "value": "green"
  },{
    "name": "option",
    "value": "blue"
  }]
}]
```

### Exclusion

Exclusion validates value to ensure it is not within a list of values.

* Name: `exclusion`
* Arguments:
  * (REQUIRED) one or more `option` elements.

```json
"validations": [{
  "name": "exclusion",
  "prompt": "The list of allowed background colors",
  "message": "The background color cannot be black, white or orange",
  "arguments": [{
    "name": "option",
    "value": "black"
  },{
    "name": "option",
    "value": "white"
  },{
    "name": "option",
    "value": "orange"
  }]
}]
```

### Format

Format validates a string String to ensure it matches a specified regex pattern.

* Name: `format`
* Arguments:
  * `regex` (REQUIRED) - a regular expression as a string to match against.

```json
"validations": [{
  "name": "format",
  "prompt": "regex pattern for an email address",
  "message": "The background color must be red, green or blue.",
  "arguments": [{
    "name": "regex",
    "value": "\\b[A-Z0-9._%+-]+@[A-Z0-9.-]+\\.[A-Z]{2,4}\\b"
  }]
}]
```

### Length

Length validates a String against an upper and lower bound.

* Name: `length`
* Arguments:
  * `upper_bound` (REQUIRED) - a numeric value to provide the upper limit of the length.
  * `lower_bound` (REQUIRED) - a numeric value to provide the lower limit of the length.


```json
"validations": [{
  "name": "length",
  "prompt": "The allowed length of the label",
  "message": "The label must be less than 50 characters.",
  "arguments": [{
    "name": "lower_bound",
    "value": "0"
  },{
    "name": "upper_bound",
    "value": "50"
  }]
}]
```

### File Type

File Type validates a File against a list of allowed file types

* Name: `file_type`
* Arguments
  * (REQUIRED) one or more `option` elements

```json
"validations": [{
  "name": "inclusion",
  "prompt": "allowed file types",
  "message": "Only types of an image type are allowed",
  "arguments": [{
    "name": "option",
    "value": "png"
  },{
    "name": "option",
    "value": "bmp"
  },{
    "name": "option",
    "value": "jpg"
  },{
    "name": "option",
    "value": "gif"
  }]
}]
```

### File Size

File Size validates a File against an upper and lower bound file size.

* Name: `file_size`
* Arguments:
  * `upper_bound` (REQUIRED) - a numeric value to provide the upper limit of the length.
  * `lower_bound` (REQUIRED) - a numeric value to provide the lower limit of the length.


```json
"validations": [{
  "name": "file_size",
  "prompt": "The allowed size for a file",
  "message": "The file must be less that 2 MB.",
  "arguments": [{
    "name": "lower_bound",
    "value": "0"
  },{
    "name": "upper_bound",
    "value": "2097152"
  }]
}]
```

### Presence

Presence validates a value to ensure that it present (not null and not empty).

* Name: `presence`
* Arguments: None

```json
"validations": [{
  "name": "presence",
  "message": "The name must be included.",
}]
```

```json
// sample template with validation array
{
  "collection": {
    "version": "1.0",
    "href": "http://www.example.com/file_upload",
    "template":{
      "data": [{
        "name": "file",
        "value": null,
        "validations": [{
          "name": "file_size",
          "prompt": "The maximum size for a file",
          "message": "The file must be less that 2MB",
          "arguments": [{
            "name": "lower_bound",
            "value": "0"
          },{
            "name": "upper_bound",
            "value": "2097152"
          }]
        }, {
          "name": "file_type",
          "prompt": "allowed file types",
          "message": "The file must be an image.",
          "arguments": [{
            "name": "option",
            "value": "png"
          },{
            "name": "option",
            "value": "bmp"
          },{
            "name": "option",
            "value": "jpg"
          },{
            "name": "option",
            "value": "gif"
          }]
        }]
      },{
        "name": "label",
        "value": null,
        "validations": [{
          "name": "length",
          "prompt": "The allowed length of the label",
          "message": "The label cannot exceed 50 characters.",
          "arguments": [{
            "name": "lower_bound",
            "value": "0"
          },{
            "name": "upper_bound",
            "value": "50"
          }]
        }]
      },{
        "name": "background_color",
        "value": null,
        "validations": [{
          "name": "inclusion",
          "prompt": "The list of allowed background colors",
          "message": "The background color must be red, green or blue.",
          "arguments": [{
            "name": "option",
            "value": "red"
          },{
            "name": "option",
            "value": "green"
          },{
            "name": "option",
            "value": "blue"
          }]
        }]
      },{
        "name": "email_address",
        "value": null,
        "validations": [{
          "name": "format",
          "message": "The background color must be red, green or blue.",
          "prompt": "regex pattern for an email address",
          "arguments": [{
            "name": "regex",
            "value": "\\b[A-Z0-9._%+-]+@[A-Z0-9.-]+\\.[A-Z]{2,4}\\b"
          }]
        }]
      }]
    }
  }
}
```

