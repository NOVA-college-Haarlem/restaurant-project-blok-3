# Project Restaurant

## Opdrachten

### Opdracht 1 - Database ontwerp

- Maak op basis van onderstaande userstories en het SQL-bestand een database ontwerp. 

### Opdracht 2 - Repository

- Maak gebruik van de repository: https://github.com/NOVA-college-Haarlem/restaurant-project-blok-3
- Fork de repository
- Clone de repository

### Opdracht 3 - Website

- Maak een website voor een restaurant.

### Opdracht 4 - Controleren

- Controleer je website door gebruik te maken van de rubric.

## Userstories

### Overzichtspagina

**Als een** bezoeker  
**Wil ik** een overzicht zien van alle beschikbare restaurants  
**Zodat ik** snel kan bladeren door verschillende eetgelegenheden

**Als een** bezoeker  
**Wil ik** basisinformatie zien van elk restaurant (naam, keuken, thumbnail afbeelding)  
**Zodat ik** een eerste indruk krijg zonder naar de detailpagina te hoeven gaan

**Als een** bezoeker  
**Wil ik** op een restaurant kunnen klikken  
**Zodat ik** naar de detailpagina kan gaan voor meer informatie

## Filtering

**Als een** bezoeker  
**Wil ik** kunnen filteren op keukentype (Italiaans, Japans, Mexicaans, etc.)  
**Zodat ik** alleen restaurants zie die passen bij mijn voorkeur

**Als een** bezoeker  
**Wil ik** kunnen filteren op prijsklasse (€, €€, €€€)  
**Zodat ik** restaurants kan vinden binnen mijn budget

## Overige Functionaliteiten

**Als een** bezoeker  
**Wil ik** kunnen sorteren op beoordeling (van hoog naar laag of laag naar hoog)  
**Zodat ik** de best beoordeelde restaurants kan vinden

**Als een** bezoeker  
**Wil ik** zien hoeveel resultaten er beschikbaar zijn binnen mijn gekozen filters  
**Zodat ik** weet hoeveel opties ik heb

```sql
-- Database schema voor Restaurant Guide met één tabel

-- Restaurants tabel
CREATE TABLE restaurants (
    id INT PRIMARY KEY AUTO_INCREMENT,
    naam VARCHAR(100) NOT NULL,
    keukentype VARCHAR(50) NOT NULL,
    prijsklasse VARCHAR(10) NOT NULL, -- €, €€, €€€
    adres VARCHAR(200),
    postcode VARCHAR(10),
    stad VARCHAR(50),
    telefoonnummer VARCHAR(20),
    openingstijden TEXT,
    beoordeling DECIMAL(3, 1), -- bijv. 4.5
    aantal_beoordelingen INT,
    bezorging BOOLEAN,
    terras BOOLEAN,
    beschrijving TEXT,
    website VARCHAR(255),
    thumbnail_url VARCHAR(255)
);

-- Voorbeelddata invoegen
INSERT INTO restaurants (naam, keukentype, prijsklasse, adres, postcode, stad, telefoonnummer, openingstijden, beoordeling, aantal_beoordelingen, bezorging, terras, beschrijving, website, thumbnail_url) VALUES 
('Bella Italia', 'Italiaans', '€€', 'Dorpsstraat 15', '1234 AB', 'Amsterdam', '020-1234567', 'Ma-Vr: 17:00-22:00, Za-Zo: 15:00-23:00', 4.5, 128, TRUE, TRUE, 'Authentieke Italiaanse keuken met verse pasta\'s en houtoven pizza\'s.', 'www.bellaitalia.nl', 'bellaitalia.jpg'),
('Sushi Palace', 'Japans', '€€€', 'Stationplein 8', '1234 CD', 'Amsterdam', '020-7654321', 'Di-Zo: 18:00-22:30, Ma: gesloten', 4.8, 95, FALSE, FALSE, 'Hoogwaardige sushi en sashimi bereid door Japanse meesterchefs.', 'www.sushipalace.nl', 'sushipalace.jpg'),
('Tapas Bar Barcelona', 'Spaans', '€€', 'Grachtenstraat 22', '1234 EF', 'Amsterdam', '020-9876543', 'Dagelijks: 17:00-01:00', 4.2, 210, FALSE, TRUE, 'Gezellige tapasbar met authentieke Spaanse sfeer en live flamenco op vrijdag.', 'www.tapasbarcelona.nl', 'tapasbar.jpg'),
('Burger & Beer', 'Amerikaans', '€', 'Winkelweg 5', '1234 GH', 'Utrecht', '030-1122334', 'Dagelijks: 12:00-23:00', 3.9, 182, TRUE, TRUE, 'Ambachtelijke hamburgers en een uitgebreide selectie speciaalbieren.', 'www.burgerbeer.nl', 'burger.jpg'),
('Thai Spice', 'Thais', '€€', 'Marktstraat 44', '5678 IJ', 'Rotterdam', '010-8877665', 'Di-Zo: 16:30-22:00, Ma: gesloten', 4.4, 156, TRUE, FALSE, 'Authentieke Thaise gerechten met verse kruiden en specerijen.', 'www.thaispice.nl', 'thai.jpg'),
('Le Bistro', 'Frans', '€€€', 'Museumplein 10', '5678 KL', 'Amsterdam', '020-3344556', 'Di-Za: 18:00-23:00, Zo-Ma: gesloten', 4.7, 88, FALSE, TRUE, 'Verfijnde Franse keuken met seizoensgebonden menu en uitgebreide wijnkaart.', 'www.lebistro.nl', 'lebistro.jpg'),
('El Sombrero', 'Mexicaans', '€€', 'Centrumplein 3', '5678 MN', 'Den Haag', '070-6677889', 'Ma-Zo: 17:00-23:00', 4.1, 134, TRUE, TRUE, 'Kleurrijk Mexicaans restaurant met pittige taco\'s en verfrissende margarita\'s.', 'www.elsombrero.nl', 'sombrero.jpg'),
('De Pizzabakkers', 'Italiaans', '€', 'Schoolstraat 15', '9012 OP', 'Utrecht', '030-9988776', 'Ma-Zo: 16:00-22:00', 4.3, 205, TRUE, FALSE, 'Houtoven pizza\'s gemaakt van biologische ingrediënten.', 'www.depizzabakkers.nl', 'pizzabakkers.jpg'),
('Golden Dragon', 'Chinees', '€€', 'Zijstraat 27', '9012 QR', 'Rotterdam', '010-5544332', 'Dagelijks: 12:00-22:30', 3.8, 176, TRUE, FALSE, 'Traditionele Chinese gerechten en dim sum specialiteiten.', 'www.goldendragon.nl', 'dragon.jpg'),
('Tandoori Express', 'Indiaas', '€', 'Hoofdweg 88', '9012 ST', 'Den Haag', '070-2233445', 'Ma-Zo: 17:00-22:00', 4.0, 145, TRUE, FALSE, 'Snelle Indiase keuken met pittige curry\'s en verse naanbroodjes.', 'www.tandooriexpress.nl', 'tandoori.jpg'),
('Brasserie Central', 'Nederlands', '€€', 'Stationsweg 1', '3456 UV', 'Amsterdam', '020-7788990', 'Ma-Zo: 10:00-23:00', 4.2, 198, FALSE, TRUE, 'Klassieke Nederlandse gerechten met een moderne twist.', 'www.brasseriecentral.nl', 'brasserie.jpg'),
('Steakhouse Texas', 'Amerikaans', '€€€', 'Vleesstraat 45', '3456 WX', 'Utrecht', '030-6655443', 'Ma-Za: 17:00-23:00, Zo: gesloten', 4.6, 110, FALSE, TRUE, 'Sappige steaks van de grill en Amerikaanse cocktails.', 'www.texassteakhouse.nl', 'steakhouse.jpg'),
('Sushi To Go', 'Japans', '€', 'Winkelcentrum 12', '3456 YZ', 'Rotterdam', '010-1324354', 'Ma-Za: 11:00-21:00, Zo: 13:00-20:00', 3.7, 95, TRUE, FALSE, 'Snelle en betaalbare sushi voor onderweg of thuisbezorgd.', 'www.sushitogo.nl', 'sushitogo.jpg'),
('Greek Islands', 'Grieks', '€€', 'Havenlaan 32', '7890 AB', 'Den Haag', '070-9876543', 'Di-Zo: 17:00-23:00, Ma: gesloten', 4.3, 127, FALSE, TRUE, 'Griekse specialiteiten in een mediterrane sfeer met live muziek in het weekend.', 'www.greekislands.nl', 'greek.jpg'),
('Café Belgique', 'Belgisch', '€€', 'Bierstraat 5', '7890 CD', 'Amsterdam', '020-1472583', 'Ma-Zo: 16:00-01:00', 4.4, 156, FALSE, TRUE, 'Belgische bieren en traditionele gerechten zoals stoofvlees en mosselen.', 'www.cafebelgique.nl', 'belgique.jpg');

```

## Beoordelingsrubric

### Overzichtspagina

| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Basisweergave van restaurants | Restaurants worden niet of nauwelijks getoond | Restaurants worden correct weergegeven | Restaurants worden aantrekkelijk weergegeven met duidelijke visuele hiërarchie |
| Filter op keukentype | Filter werkt niet of met ernstige fouten | Filter werkt, maar heeft kleine gebreken | Filter werkt perfect en is gebruiksvriendelijk |
| Filter op prijsklasse | Filter werkt niet of met ernstige fouten | Filter werkt, maar heeft kleine gebreken | Filter werkt perfect en is gebruiksvriendelijk |
| Sortering op beoordeling | Sortering werkt niet of met ernstige fouten | Sortering werkt, maar heeft kleine gebreken | Sortering werkt perfect en is gebruiksvriendelijk |
| Doorklikken naar detailpagina | Links werken niet of met ernstige fouten | Links werken, maar zijn niet optimaal geplaatst | Links werken perfect en zijn intuïtief |

### Detailpagina
| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Weergave van restaurant details | Details worden niet of nauwelijks getoond | Details worden correct weergegeven | Details worden uitgebreid en aantrekkelijk weergegeven |
| Teruglink naar overzichtspagina | Link werkt niet of is niet aanwezig | Link is aanwezig en werkt | Link is duidelijk zichtbaar en gebruiksvriendelijk |

### Algemene aspecten
| Criterium | Onvoldoende | Voldoende | Goed |
|-----------|-------------|------------|------|
| Database connectie | Query's werken niet of met ernstige fouten | Query's werken, maar zijn niet geoptimaliseerd | Query's werken goed en zijn geoptimaliseerd |
| Code kwaliteit | Rommelige code met veel fouten | Redelijk nette code met enkele fouten | Nette, goed gestructureerde code zonder fouten |
