# REST API: deleting a selection

When you send an HTTP DELETE request to the following URL, you’ll delete 
a selection of profiles:

`https://api.copernica.com/v1/view/$id?access_token=xxxx`

The $id needs to be replaced by the numerical identifier of the selection
that you want to remove. With this method you only remove the selection, and
not the profiles that are inside of it. If you want to remove the profiles
too, you will have to remove the entire database, or you can make many
individual API calls to remove profiles one by one.

## PHP example

The following example demonstrates how to make a call using this method.

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// do the call
	$api->delete("view/1234");

This example uses the [CopernicaRestAPi class](rest-php).

## More information

* [Overview of all API calls](rest-api)
* [Remove a database](rest-delete-database)
* [Fetch all profiles in a selection](rest-get-view-profiles)
* [Remove an individual profile](rest-delete-profile)
