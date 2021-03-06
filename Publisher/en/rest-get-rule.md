# REST API: fetch rule meta data

A method to request all metadata from a rule. This method does not 
support parameters. It is called by sending an HTTP GET request to the following URL:

`https://api.copernica.com/v1/rule/$id?access_token=xxxx`

In this, $id needs to be replaced by the numerical identifier or the name of the rule you wish to request the selections for.

## Available parameters

There are no available parameters for this method.

## Returned fields

This method returns a JSON rule object with the following properties:

- **id** ID of the rule
- **name**: name of the rule
- **description**: description of the rule
- **view**: ID of the selection that the rule belongs to
- **conditions**: array of conditions for the rule
- **inversed**: boolean value to indicate whether the rule should be inversed. 
If set to "True" only profiles *not* conforming to the conditions are selected
- **disabled**: boolean value to indicate whether the rule should be disabled or not

## PHP example

The following example demonstrates how to use this method:

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// do the call, and print result
	print_r($api->get("rule/1234"));

This example uses the [CopernicaRestAPi class](rest-php).

## More information

* [Overview of all REST API methods](./rest-api)
* [Fetch selection rules](./rest-get-view-rules)
