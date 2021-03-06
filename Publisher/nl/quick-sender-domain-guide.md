Afzenderdomain instellen
========================

De mailings die je verstuurt worden verstuurd vanuit een bepaald afzenderadres,
bijvoorbeeld nieuwsbrief@bedrijfsnaam.nl. Dit afzenderadres kun je zelf in 
Copernica instellen, maar om te zorgen dat alle ontvangers de mail ook goed 
ontvangen adviseren we je om eerst de DNS records van je domeinnaam bij te werken. 
Eenvoudig gezegd moet je zorgen dat in de DNS instellingen van jouw domeinnaam
staat dat Copernica gerechtigd is om mail vanuit jouw domeinnaam te verzenden. Als je 
dit niet doet is de kans groot dat veel van de berichten niet worden geaccepteerd.

Normaal gesproken is het bijwerken van de DNS records een complexe klus. Je
moet records aanmaken om SPF, DKIM en DMARC goed in te stellen (we leggen elders
uit wat dit allemaal betekent), en je moet subdomeinen aanmaken om de kliks,
opens en bounces te registreren. En als je het echt goed wil doen, moet je
bovendien periodiek deze DNS instellingen wijzigen om te voorkomen dat de
private key van de DKIM signatures worden gekraakt.

Copernica kent echter "Sender Domains" - of in het Nederlands: afzenderdomeinen.
Dit is een technologie waarmee het een stuk makkelijker wordt om je DNS
instellingen te beheren.


Marketing Suite
---------------
De vernieuwde interface van de Marketing Suite zorgt ervoor dat je makkelijk en snel
de sender-domain in kan stellen.

Als je een afzenderdomein hebt ingesteld, zorgt Copernica automatisch
dat alle DNS instellingen goed staan. Je hoeft wat domeinnamen betreft niks
anders meer te configuren. Dit betekent dat je, na het instellen van een sender-domain,
dus niet meer apart in hoeft te stellen welke domeinnaam moet worden gebruikt om clicks en 
bounces te registreren en om te bepalen wat de DKIM keys zijn. De instellingen van het 
sender-domain hebben prioriteit, zelfs als je mails gaat versturen met Publisher. 

Je vindt de sender-domain tool in het menu onder het kopje *configuratie*.

Hoofddomein of subdomein?
-------------------------

Als je via de Marketing Suite een sender domain instelt, dan moet je een
domeinnaam opgeven. Dit is de domeinnaam die je als afzenderadres wilt gaan
gebruiken. Als je bijvoorbeeld wilt mailen vanuit "nieuwsbrief@bedrijfsnaam.nl", 
dan moet je voor "bedrijfsnaam.nl" een sender domain aanmaken. Vervolgens
worden automatisch allerlei DNS records aangemaakt met de juiste instellingen.

Maar let op. Als er al DNS records met SPF en DMARC instellingen
voor "bedrijfsnaam.nl" bestonden, dan moet je deze configuratie overzetten
naar het sender domain. Als je dit niet wilt of niet kunt, of als je niet het risico
wilt lopen dat er door een foutje een configuratieconflict onstaat, dan kun
je het beste gebruik maken van een subdomein. Je moet je mail dan versturen
vanuit, bijvoorbeeld, "nieuwsbrief@campagnes.bedrijfsnaam.nl". Zo'n subdomein 
als afzenderadres oogt weliswaar wat minder chique, maar als je snel aan de slag 
wilt dan is dat de snelste manier om de configuratie goed te krijgen. 


Domeinnaam valideren
--------------------

Om misbruik van sender domains te voorkomen, moet je bewijzen dat jij echt de 
eigenaar bent van het domein. Nadat je een sender domain hebt aangemaakt toont de Marketing Suite
daarom een waarschuwingsbericht. Je moet eerst een TXT record aan je domein
toevoegen met daarin een speciale code die alleen door Copernica wordt begrepen. 
Pas als Copernica ziet dat je dit record aan het domein hebt toegevoegd, geloven
we dat je echt de eigenaar van het domein bent en kun je verder gaan met
het configueren van het domein.


Achtergrondinformatie
---------------------

Zoals beschreven, maakt Copernica alle relevante DNS records aan, zodat je
die records zelf niet meer hoeft te beheren. Tenminste, dat schreven we steeds.
Maar Copernica kan in werkelijkheid natuurlijk helemaal geen DNS instellingen 
van een domein wijzigen zonder dat de domeineigenaar daar expliciet toestemming
voor geeft. Alleen de eigenaar van een domein kan subdomeinen aanmaken en DNS
instellingen wijzigen. Hoe werkt dit dan?

De DNS records die Copernica aanmaakt, maakt Copernica dan ook niet aan bij 
jouw domein, maar voor een subdomein van Copernica zelf. In de Marketing Suite 
krijg je een lijstje te zien met door ons geadviseerde DNS records die je moet
kopiëren naar jouw DNS server. Deze geadviseerde DNS records zijn *aliassen* (meestal CNAME 
records) die verwijzen naar de DNS servers van Copernica. Alleen de domeineigenaar
(jij dus) kan deze aliassen toevoegen aan het domein. Maar als je dit netjes
doet en alle aliassen installeert, dan kan Copernica vervolgens wijzigingen
doorvoeren.

<pre>

    Geadviseerde DNS records die                DNS records op de server
    aan het domein moeten worden                van Copernica, met instellingen
    toegevoegd:                                 van het sender domain:

    +-------------------+                       +-------------------+
    |   SPF alias       |           --->        |   TXT record      |
    +-------------------+                       +-------------------+
    |   DKIM alias      |           --->        |   TXT record      |
    +-------------------+                       +-------------------+
    |   DMARC alias     |           --->        |   TXT record      |
    +-------------------+                       +-------------------+
    |   Tracking alias  |           --->        |   A record(s)     |
    +-------------------+                       +-------------------+
    |   Bounce alias    |           --->        |   MX record(s)    |
    +-------------------+                       +-------------------+
</pre>

Bovenstaand, versimpeld, schema legt het uit. Als je de adviezen van de 
Marketing Suite opvolgt, dan voeg je aan jouw domein een aantal aliassen toe 
die verwijzen naar DNS records van Copernica. Dit stelt ons vervolgens in staat 
om de instellingen van jouw domein te beheren.

Nadat je het sender domain hebt aangemaakt, je domein hebt gevalideerd, en
de aliassen hebt toegevoegd aan DNS, kun je mailings gaan versturen met een 
afzenderadres dat overeenkomt met het aangemaakte afzenderdomein.


De volgende stap
----------------

Om de eerste mail te kunnen versturen, heb je natuurlijk 
[een database met profielen](quick-database-guide) nodig om die mailing naar
toe te sturen.
