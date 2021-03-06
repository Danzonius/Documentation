# REST API: deleting a field from a collection

When you send an HTTP DELETE request to the following URL, you’ll delete a field from a collection:

`https://api.copernica.com/v1/collection/$id/field/$id?access_token=xxxx`

The $id needs to be replaced by the numerical identifier, the ID, of the collection. The second needs to be replaced by the ID or the name of the field you want to delete.

## PHP example
The following example demonstrates how to make a call using this method.

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// do the call
	$api->delete("collection/1234/field/firstname");

This example uses the [CopernicaRestAPi class](rest-php).

## More information
- [Overview of all API calls](rest-api)
- [Requesting all fields from a collection](rest-get-collection-fields)
- [Creating a new field in a collection](rest-post-collection-fields)
- [Editing a field in a collection](rest-put-collection-fields)
