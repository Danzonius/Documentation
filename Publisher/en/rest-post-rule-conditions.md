# REST API: edit rule conditions
A method to edit conditions for a rule. This method does not 
support parameters. It is called by sending an HTTP POST request to the following URL:

`https://api.copernica.com/v1/rule/$id/conditions?access_token=xxxx`

In this, $id needs to be replaced by the numerical identifier or the name of the rule you wish to edit the conditions of.

## Available parameters

The message body can hold the following properties for a condition:

- **type**: type of condition
- **rule**: numeric ID of the rule the condition belongs to

Based on the condition type, specific properties are set. For an overview
of the supported conditions and the properties that they support, check
the specific articles:

- [Change conditions](./rest-condition-type-change.md)
- [Date conditions](./rest-condition-type-date.md)
- [DoubleField conditions](./rest-condition-type-doublefield.md)
- [Email conditions](./rest-condition-type-email.md)
- [Fax conditions](./rest-condition-type-fax.md)
- [Field conditions](./rest-condition-type-field.md)
- [Interest conditions](./rest-condition-type-interest.md)
- [LastContact conditions](./rest-condition-type-lastcontact.md)
- [Miniview conditions](./rest-condition-type-miniview.md)
- [SMS conditions](./rest-condition-type-sms.md)
- [Todo conditions](./rest-condition-type-todo.md)
- [Survey conditions](./rest-condition-type-survey.md)
- [Part conditions](./rest-condition-type-part.md)
- [ReferView conditions](./rest-condition-type-referview.md)

## PHP example

The following example demonstrates how to use this method:

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// parameters to pass to the call
	$data = array(
		'type' = 'date'
	)

	// do the call, and print result
	$api->post("rule/1234/conditions", array(), $data);

This example uses the [CopernicaRestAPi class](rest-php).

## More information

* [Overview of all REST API methods](./rest-api)
* [Fetch rules](./rest-get-rules)
* [Get rule by ID](./rest-get-rule)
* [Create rule](./rest-post-rule)
