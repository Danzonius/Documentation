# REST API: adding an interest to a database

The HTTP POST method to add an interest to an existing database is available at the following address:

`https://api.copernica.com/v1/database/$id/interests?access_token=xxxx`

In this, $id should be replaced by the numerical identifier, the ID, of the database you want to add an interest to. 
The name of the interest field and other values need to be added to the message body of the HTTP request.

## Available parameters

The following variables can be set in the message body:

- **name**: the title of the new interest field (mandatory)
- **group**: the group the field belongs to. Interests that belong to the same group are put together in the user interface

## PHP example

The following script demonstrates how to use the API method:

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// data to pass to the call
	$data = array(
	    'name'      =>  'Football',
	    'group'     =>  'Sport'
	);

	// do the call
	$api->post("database/1234/interests", $data);

This example uses the [CopernicaRestAPi class](rest-php).

## More information:

- [Overview of all API calls](rest-api)
- [Request all interests in a database](rest-get-database-interests)
- [Updating an interest](rest-put-profile)
- [Deleting an interest](rest-delete-profile)
