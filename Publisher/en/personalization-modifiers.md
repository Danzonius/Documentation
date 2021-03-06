# Variable Modifiers

You can use *modifiers* to finetune, format or filter the personalization 
variables from the database. A modifier is a sort of filter that changes
the contents of a variable. For example, there are modifiers that ensure that
names always start with an uppercase letter, or that a certain variable does
not exceed a certain length (which is useful if you want to prevent that the
layout of mailings gets messed up if someone entered unreasable long strings):

    {$name|ucfirst}
    {$city|truncate:50}

Modifiers can also be chained. If you want to apply both of the above modifiers
to a veriable, you can pass the output of the first modifier (which ensure that
the string starts with an uppercase character) to the second one (which reduced
the string to at most 50 chars): 

    {$city|ucfirst|truncate:50}

The most important modifier is the |escape modifier. This modifier is used to
convert HTML code, scripts and possible conflicting characters into safe texts. 
You need this modifier because the variables that you use for personalizing 
are often entered by people themselves. Although this data is normally correct,
you can never be 100% sure about this. People could just as well enter a piece 
of javascript as their name. To prevent that such invalid tags and scripts end
you in your mailing, you should always apply the |escape modifier to variables
inside HTML code: 

    Dear {$name|ucfirst|escape}

The above example first ensures that the first letter of the {$name} is 
converted to uppercase, and then the escape-modifier ensures that the output 
can be safely used inside HTML and that no conflicts occur.


## List of available modifiers

The Copernica personalization engine is based on Smarty. A more comprehensive
explanation of the workings of these modifiers, and a list of all built-in
modifiers can be found [on the Smarty website](http://www.smarty.net/docsv2/en/language.modifiers.tpl).
The following modifiers are supported by Copernica:

* **{$variable|[base64_encode](./personalization-modifier-base64_encode.md)}**: convert to base64 encoding
* **{$variable|[capitalize](./personalization-modifier-capitalize.md)}**: convert the first letter of each word to uppercase
* **{$variable|[cat](./personalization-modifier-cat.md)}**: append text to variable
* **{$variable|[ceil](./personalization-modifier-ceil.md)}**: round fractions up
* **{$variable|[count](./personalization-modifier-count.md)}**: number of items in a variable (useful if $variabele is an array)
* **{$variable|[count_characters](./personalization-modifier-count_characters.md)}**: number of characters in a string
* **{$variable|[count_paragraphs](./personalization-modifier-paragraphs.md)}**: number of paragraphs in a string
* **{$variable|[count_sentences](./personalization-modifier-sentences.md)}**: number of sentences in a string
* **{$variable|[count_words](./personalization-modifier-count_words.md)}**: number of words in a string
* **{$variable|[date_format](./personalization-modifier-date_format.md)}**: formatting dates and times
* **{$variable|[default](./personalization-modifier-default.md)}**: use default value in case a variable is empty
* **{$variable|[escape](./personalization-modifier-escape.md)}**: filter out scripts and html
* **{$variable|[explode](./personalization-modifier-explode.md)}**: split string into parts
* **{$variable|[htmlspecialchars_decode](./personalization-modifier-htmlspecialchars_decode.md)}**: reverse of |escape: bring back an escaped string to html
* **{$variable|[html_entity_decode](./personalization-modifier-html_entity_decode.md)}**: html entities weer terugbrengen oorspronkelijke tekens
* **{$variable|[http_build_query](./personalization-modifier-http_build_query.md)}**: convert variable to a query string
* **{$variable|[indent](./personalization-modifier-indent.md)}**: indent text with spaces
* **{$variable|[json_decode](./personalization-modifier-json_decode.md)}**: convert json to a regular variable
* **{$variable|[json_encode](./personalization-modifier-json_encode.md)}**: convert variabele to json (so you can use it inside javascript)
* **{$variable|[lower](./personalization-modifier-lower.md)}**: convert text to lowercase
* **{$variable|[md5](./personalization-modifier-md5.md)}**: md5 hash of a text
* **{$variable|[nl2br](./personalization-modifier-nl2br.md)}**: convert newlines to &lt;br/&gt; tags
* **{$variable|[number_format](./personalization-modifier-number_format.md)}**: number formatting
* **{$variable|[rand](./personalization-modifier-rand.md)}**: random number
* **{$variable|[regex_replace](./personalization-modifier-regex_replace.md)}**: replace text based on a regular expression
* **{$variable|[replace](./personalization-modifier-replace.md)}**: replace text
* **{$variable|[sha1](./personalization-modifier-sha1.md)}**: sha1 hash
* **{$variable|[spacify](./personalization-modifier-spacify.md)}**: stretch text by adding spaces
* **{$variable|[string_format](./personalization-modifier-string_format.md)}**: printf-like modifier
* **{$variable|[strip](./personalization-modifier-strip.md)}**: strip whitespace
* **{$variable|[strip_tags](./personalization-modifier-strip_tags.md)}**: remove html tags from text
* **{$variable|[strstr](./personalization-modifier-strstr.md)}**: look for a substring
* **{$variable|[strtotime](./personalization-modifier-strtotime.md)}**: parse date or time string
* **{$variable|[strval](./personalization-modifier-strval.md)}**: convert variable to a string
* **{$variable|[substr](./personalization-modifier-substr.md)}**: select substring
* **{$variable|[trim](./personalization-modifier-trim.md)}**: remove whitespace from begin and end 
* **{$variable|[truncate](./personalization-modifier-truncate.md)}**: set max length for a text
* **{$variable|[ucfirst](./personalization-modifier-ucfirst.md)}**: convert first character to uppercase
* **{$variable|[ucwords](./personalization-modifier-ucwords.md)}**: convert first letter of each character to uppercase
* **{$variable|[upper](./personalization-modifier-upper.md)}**: convert string to all uppercase
* **{$variable|[unserialize](./personalization-modifier-unserialize.md)}**: unserialize php variable
* **{$variable|[urlencode](./personalization-modifier-urlencode.md)}**: encode variable to be usable in url
* **{$variable|[wordwrap](./personalization-modifier-wordwrap.md)}**: wrap long texts over multiple lines

