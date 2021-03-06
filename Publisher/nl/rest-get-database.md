# REST API: opvragen gegevens van een database

Methode om alle meta gegevens van een database op te vragen. De methode
ondersteunt geen parameters. De methode wordt aangeroepen via het volgende adres:

`GET https://api.copernica.com/v1/database/$id?access_token=xxxx`

Als $id kun je de numerieke identifier van een database opgeven, of de naam
van een database.

## Geretourneerde velden

* **ID**: Unieke numerieke identifier
* **name**: Naam van de database
* **description**: Omschrijving van de database
* **archived**: Is de database gearchiveerd of niet?
* **created**: Tijdstip waarop de database is aangemaakt
* **fields**: Array met de velden in de database
* **interests**: Array met de interesses in de database
* **collections**: Array met de collecties in de database

De velden, interesses en collecties worden teruggegeven als arrays van
objecten. Als je wilt weten hoe deze arrays zijn opgebouwd, kun je een blik 
werpen op de documentatie van de volgende API methodes. Deze methodes 
retourneren dezelfde soort gegevens:

* [Opvragen van velden](rest-get-database-fields)
* [Opvragen van interesses](rest-get-database-interests)
* [Opvragen van collecties](rest-get-database-collections) 


## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen:

    // vereiste scripts
    require_once('copernica_rest_api.php');
    
    // verander dit in je access token
    $api = new CopernicaRestApi("your-access-token");

    // voer de opdracht uit en print het resultaat
    print_r($api->get("database/1234"));

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Bewerken van een database](rest-put-database)
