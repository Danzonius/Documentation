# Sender domains

Hoewel het vroeger heel makkelijk was om het afzenderadres van een mailing te
*faken*, is het versturen van e-mail uit naam van een ander tegenwoordig lang
zo eenvoudig niet meer. Copernica kan daarom niet zomaar uit jouw naam mailings
versturen. Hiervoor moet jij, als eigenaar van het afzenderadres en van de domeinnaam, 
eerst allerlei [DNS instellingen](./dns/md) goed zetten. Dit stelt ontvangers in 
staat om te zien dat wij inderdaad toestemming hebben om uit jouw naam te mailen. 
Als je dit niet doet, zal een groot deel van de berichten die je verstuurt niet 
goed aankomen.

Het instellen van al deze [DNS records](./dns.md) kan ingewikkeld zijn, maar met 
behulp van een technologie die we *Sender Domains* hebben genoemd, maken we het 
makkelijk. Het werkt zo: om goed te kunnen mailen moet je [DNS records](./dns.md) 
aanmaken, [MX](./mx.md), [SPF](./spf.md), [DKIM](./dkim.md) en [DMARC](./dmarc.md) 
records. Om je te helpen hoef je dit echter niet zelf te doen, maar maken wij deze 
records aan in *onze* [DNS server](./dns.md). Het enige wat jij hoeft te doen is 
het plaatsen van een aantal aliassen (CNAME records) die verwijzen naar de instellingen bij ons.

Zo simpel is het. In het 
[snel-aan-de-slag artikel over het instellen van een afzenderdomein](./quick-sender-domain-guide.md)
leggen we het uitgebreid uit. We gaan daarom hier, in dit wat diepgravender
onderdeel van de documentatie, alleen in op de ingewikkelder zaken.


## Subdomein of hoofddomein?

Als je een sender-domain instelt kun je kiezen of je dat doet voor je hoofddomein,
zeg maar bedrijfsnaam.nl, of dat je dit doet voor een subdomein, zoals
nieuwsbrief.bedrijfsnaam.nl. Natuurlijk is het een stuk chiquer wanneer alle
e-mail, inclusief de transactionele e-mails en de nieuwsbrieven, worden verstuurd
vanuit het hoofdomein. Maar vermoedelijk worden er al allerlei berichten vanuit
het hoofddomein verstuurd (zoals je reguliere mail!) en zijn er daarom al allerlei 
instellingen in je DNS om dit mogelijk te maken. Als je het niet aandurft om
deze instellingen te veranderen, dan kun je er voor kiezen om een subdomein 
(zoals nieuwsbrief.bedrijfsnaam.nl) te gebruiken voor de mail vanuit Copernica.

Maar als je wel vanuit het hoofddomein wilt gaan versturen, dan moet je op een
aantal zaken goed letten. Met name de DMARC records die je moet aanmaken of 
wijzigen behoeft speciale aandacht.


## De verschillende DNS records

Als je gebruik maakt van een Sender Domain om je DNS te configuren, dan plaatsen wij,
Copernica, in onze DNS server allerlei records met de juiste DNS instellingen. In
jouw DNS hoef je alleen nog maar aliassen te maken (door middel van CNAME records)
die verwijzen naar de records in ons DNS. In het dashboard van Copernica kun je 
precies zien welke records je moet aanmaken, en tonen we een waarschuwing als je
het niet (helemaal) goed hebt gedaan.

Omdat de aliassen die je aanmaakt naar onze servers verwijzen zijn wij in staat 
om, als dat nodig is, wijzigingen aan te brengen aan jouw configuratie. Bijvoorbeeld 
als we extra IP adressen gaan gebruiken om mail te versturen of om kliks te 
registreren, of als we DKIM keys roteren, dan kunnen we dat doen zonder dat jij
iets in jouw DNS hoeft te veranderen. De aliassen verwijzen naar de records bij 
ons, en die records kunnen wij aanpassen wanneer dat nodig is.

We maken verschillende records aan, en je moet daarom ook veel aliassen (CNAME 
records) aanmaken. De volgende records worden aangemaakt:

* Een A record om kliks en opens te registreren
* Een MX record om de bounces en out-of-office replies af te vangen
* Meerdere DKIM records om mails van een digitaal DKIM dignature te voorzien
* Een SPF record om de IP addressen van Copernica toestemming te geven om te mailen
* Een DMARC record om de DMARC rapportages van ontvangers af te vangen

De A, MX en DKIM records leveren meestal niet zo veel problemen op. Het is
toegestaan om net zo veel van deze records aan te maken als je maar nodig hebt,
en ze conflicteren niet met bestaande records. Je kunt de aliassen naar deze
records dus zonder al te veel zorgen aanmaken. Ook [SPF](./spf.md) gaat goed 
omdat we een heel nieuw subdomein aanmaken voor het afvangen van bounces.


## Let op met DMARC

Het wordt wat ingewikkelder met DMARC records, met name als je wilt versturen 
vanuit het hoofddomain (vanuit @bedrijfsnaam.nl). Er kan namelijk maar één DMARC 
record per (sub)domein worden aangemaakt, en er is een goede kans dat voor jouw 
hoofddomein een dergelijk record al bestaat. Dit bestaande record kun je niet 
zomaar weghalen of overschrijven. De simpele oplossing is om er dan toch maar 
voor te kiezen om vanuit een subdomein te versturen. Als je echter wel vanuit 
het hoofddomein wilt mailen, dat is immers chiquer, dan moet je wat extra 
maatregelen treffen. Hoe dat precies werkt leggen we in een apart artikel uit:

* [DMARC configureren](./dmarc.md)

Het instellen van sender domains, en de DNS records die je moet maken, kun
je het beste doen via de Copernica Marketing Suite (en dus niet via de oude
Publisher omgeving). De wizards in de Marketing Suite werken intuïtief en door
middel van groene vinkjes of rode kruisjes kun je precies zien of je het goed
hebt gedaan.


## Handmatige instellingen in Publisher

In de oude Copernica Publisher omgeving vind je nog allerlei formulieren om met
de hand picserver en envelope domains aan te maken, en om met de hand DKIM keys
in te stellen. Dit zijn verouderde formulieren die werden gebruikt voordat we 
Sender Domains hadden. Je hebt dit niet meer nodig, en je kunt het beste de 
Sender Domain wizard in de Marketing Suite gebruiken om dit allemaal in te 
stellen. Deze formulieren zijn alleen bedoeld voor mensen die al langere tijd
gebruik maken van de Copernica software, en nog niet zijn overgestapt op
Sender Domains.

Als je zo'n gebruiker bent en nog de oude verzendinstellingen gebruikt, dan raden 
we je aan om snel over te stappen op Sender Domains. Verzenden met behulp van 
Sender Domains is veiliger en leidt uiteindelijk tot een betere aflevering van 
je berichten. Maar doe het wel rustig aan. In het algemeen is het onverstandig
om van de één op de andere dag met heel andere instellingen te gaan mailen. Dit 
geldt ook voor de overstap naar Sender Domains. Versturen met Sender Domains is 
beter, maar stap wel rustig over. In het Sender Domain dialoogvenster in Publisher
hebben we daarom een tab geplaatst waarin je een percentage kunt invoeren. Hiermee
kun je langzaam overstappen.

Hoe kun je dit het beste doen? Als je een Sender Domain hebt geconfigureerd, kun
je het deploymentpercentage in eerste instantie op, bijvoorbeeld, 10% zetten. Dit
betekent dat 10% van jouw uitgaande berichten zal worden verstuurd met de Sender
Domain instellingen, en 90% van de berichten met de oude settings. Eén op de tien
berichten zal dus een envelope- en klikadress hebben dat via het Sender Domain is
geconfigureerd, en gebruik maken van de DKIM keys van het Sender Domain. De overige
90% van de berichten wordt nog gewoon op de oude manier samengesteld en verstuurd.

Na een paar dagen mailen kun je een blik werpen op de statistieken. Is het aantal 
foutmeldingen opeens gegroeid of gaat alles goed? Meestal gaat alles gewoon goed en 
kun je het percentage verder verhogen, bijvoorbeeld naar 25%. Op deze wijze kun
je in een aantal etappes (bijvoorbeeld 10% - 25% - 50% - 75% - 100%) een Sender
Domain implementeren. De grootte van de stappen hangt af van de omvang van je 
database. Als er een paar honderd adressen in zitten kun je wat grotere
stappen zetten. Bij een paar miljoen adressen moet je wat voorzichtiger zijn en
in kleinere etappes uitrollen.

