# REST API: aanmaken van een nieuwe selectie

Om een nieuwe selectie aan te maken, moet je een HTTP POST request sturen
naar de volgende URL. De selectie wordt dan direct onder de database aangemaakt.

`https://api.copernica.com/v1/database/$id/views?access_token=xxxx`

De code $id moet je vervangen door de numerieke identifier of de naam van de 
database waar je een selectie aan wilt toevoegen. De naam van de selectie moet
als message body aan het HTTP request worden toegevoegd.

## Beschikbare parameters

De volgende variabele moet in de body van de HTTP POST call worden geplaatst.

- **name**: Naam van de nieuw aan te maken selectie (verplicht).
- **description**: Beschrijving van de nieuwe selectie
- **parent-type**: Geeft aan of de selectie onder een onder selectie of de database is geplaatst
- **parent-id**: ID van de selectie/database waar de selectie onder valt
- **has-children**: Boolean value die aangeeft of er selecties onder deze selectie vallen
- **has-referred**: Boolean value om aan te geven of andere selecties naar deze selectie refereren
- **has-rules**: Boolean value om aan te geven of deze selectie regels heeft

## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen:

    // vereiste scripts
    require_once('copernica_rest_api.php');
    
    // verander dit naar je access token
    $api = new CopernicaRestApi("your-access-token");

    // data voor de methode
    $data = array(
        'name'      =>  'mijn-selectie',
	'description'	=> 'voorbeeld selectie',
	'has-rules'	=> False
    );
    
    // voer het verzoek uit
    $api->post("database/1234/views", $data);

Voor bovenstaand voorbeeld heb je de [CopernicaRestApi klasse](rest-php) nodig.

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Opvragen selecties van een database](rest-get-database-views)
* [Selectieregels opvragen](rest-get-view-rules)
* [Selectieregel aanmaken](rest-post-view-rules)
