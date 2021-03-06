# REST API: aanmaken van een profiel

Als je een profiel wilt aanmaken, dien je een HTTP POST request te sturen
naar de volgende URL.

`https://api.copernica.com/v1/database/$id/profiles?access_token=xxxx`

De code $id moet je vervangen door de numerieke identifier of de naam van de 
database waar je het profiel in wilt opslaan. De veldwaardes van het profiel
kun je in de body van het HTTP request plaatsen.

Zorg ervoor dat je hier een POST request stuurt en geen PUT request. Hoewel deze vaak niet verschillen zou je in dit geval een methode aanroepen om meerdere profielen te bewerken, zie [meerdere profielen te bewerken](rest-put-database-profiles).

## Beschikbare parameters

De parameters die je in de body van het HTTP POST request plaatst, zijn de
velden van het aan te maken profiel. De volgende informatie kan meegegeven worden aan het profiel.

- **fields**: associatieve array/object van veldnamen en waardes
- **interests**: array van interesses van een profiel
- **database**: ID van de database waar het profiel staat
- **secret**: de "geheime" code die aan een profiel gelinkt is 
- **created**: tijdstip waarop het profiel werd gemaakt, YYYY-MM-DD hh:mm:ss formaat
- **modified**: tijdstip waarop het profiel laatst werd aangepast, YYYY-MM-DD hh:mm:ss formaat

## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen:

    // vereiste scripts
    require_once('copernica_rest_api.php');
    
    // verander dit naar je access token
    $api = new CopernicaRestApi("your-access-token");

    // data voor de methode
    $data = array(
        'database' =>  database_id
    );
    
    // voer het verzoek uit
    $api->post("database/1234/profiles", $data);

Voor bovenstaand voorbeeld heb je de [CopernicaRestApi klasse](rest-php) nodig.

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Opvragen van alle profielen](rest-get-database-profiles)
* [Profiel bijwerken](rest-put-profile-fields)
* [Profiel verwijderen](rest-delete-profile)
* [Velden aanmaken](rest-put-profile-fields)
* [Interesses aanmaken](rest-post-profile-interests)
