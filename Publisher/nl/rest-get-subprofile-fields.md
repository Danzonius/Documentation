# REST API: opvragen van alleen de velden van een subprofiel

Om alleen de velden van een subprofiel op te vragen, kun je een HTTP GET
request sturen naar de volgende URL:

`https://api.copernica.com/v1/subprofile/$id/fields?access_token=xxxx`

De code $id moet je vervangen door de numerieke identifier van het subprofiel
dat je opvraagt.


## Geretourneerde velden

De methode retourneert de velden van een subprofiel.


## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen.

    // dependencies
    require_once('copernica_rest_api.php');
    
    // change this into your access token
    $api = new CopernicaRestApi("your-access-token");

    // do the call, and print result
    print_r($api->get("subprofile/1234/fields"));

Voor bovenstaand voorbeeld heb je de [CopernicaRestApi klasse](rest-php) nodig.
    

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Opvragen van alle gegevens van een profiel](rest-get-profile)
* [Opvragen van alle gegevens van een subprofiel](rest-get-subprofile)
