# Property `platforms`

The property `platforms` is a JSON array, which contains a comma seperated JSON strings, representing the names of the platforms which are used inside the `share` block.

## Example usage

The following input JSON shows how to set platforms in a share block. This is
the basic usage, showing a set of share buttons.

```javascript
{
    "from" : "info@example.com",
    "subject" : "Email with a share block",
    "content" : {
        "blocks" : [ {
            "type"      : "share",
            "label"     : "Share with friends!",
            "align"     : "left",
            "icon"      : {
                "type"      : "rounded",
                "size"      : 32
            },
            "link"      : {
                "url"       : "https://responsiveemail.com/",
                "title"     : "Post title"
            },
            "platforms" : ["facebook", "twitter", "linkedin", "googleplus"] 
        } ]
    }
}
```

For more information and more examples, please check the documentation of the `share` block.
