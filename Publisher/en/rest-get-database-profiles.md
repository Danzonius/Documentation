# REST API: requesting profiles in a database
The method to request profiles in a database is an HTTP GET request and available at the following address:

`https://api.copernica.com/v1/database/$id/profiles?access_token=xxxx`

In this, $id should be replaced by the numerical identifier, the ID, of the database you want to request profiles from.

## Available parameters
The following parameters can be added to the URL as variables:

- **start**: the first profile to be requested
- **limit**: the length of the batch that is requested
- **total**: whether or not the total number of profiles in the database should be counted
- **fields**: optional parameter to set conditions for profiles that should be returned
- **orderby**: name or id of the field you want to use to sort the returned profiles
- **order**: whether the profiles should be ordered in ascending or descending order.

More information on the meaning of start, limit and total parameters can be found in the [article on paging](rest-paging).

The *fields* parameter can be used to select profiles. For example, if you only want to request profiles where the field “country” equals “The Netherlands”, you can do so using “fields”. More information on this parameter can be found in the [article on the “fields” parameter](rest-fields-parameter).

The *order* variable can have the name or the ID of a field assigned to it. When you do so, profiles are sorted by the value in that field. 
Instead of a field to sort on, you can also assign one of the following special values to “order”:
- **id**: this is the default value, profiles are sorted by ID.
- **random**: profiles are returned in random order
- **modified**: profiles are sorted on the timestamp they were last modified on.

## Returned fields
The method returns a list of profiles. For each profile, the following properties are returned:

- **ID**: numerical ID of the profile
- **fields**: associative array/object of field names and values
- **interests**: array of  the interests the profile has
- **database**: ID of the database the profile is stored in
- **secret**: the “secret” code that is linked to a profile
- **created**: the timestamp on which the profile was created, in YYYY-MM-DD hh:mm:ss format.
- **modified**: the timestamp on which the profile was last modified,, in YYYY-MM-DD hh:mm:ss format.

## PHP example
The following script demonstrates how to use this method. Because we use the CopernicaRestApi class, you don’t have to worry about escaping special characters in the URL; it is done automatically.

	// dependencies
	require_once('copernica_rest_api.php');

	// change this into your access token
	$api = new CopernicaRestApi("your-access-token");

	// parameters to pass to the call
	$parameters = array(
	    'limit'     =>  100,
	    'orderby'   =>  'country',
	    'fields'    =>  array("age>16", "age<=65")
	);

	// do the call, and print result
	print_r($api->get("database/1234/profiles", $parameters));`

This example uses the [CopernicaRestApi class](rest-php).

## More information

- [Overview of all API calls](rest-api)
- [Requesting profile IDs](rest-get-database-profileids)
- [Adding a profile to a database](rest-post-database-profiles)
- [Editing a profile](rest-put-profile-fields)
- [Delete profile](rest-delete-profile)
