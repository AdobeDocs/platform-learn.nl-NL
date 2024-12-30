---
title: Offer decisioning - Configureer je voorstellen en besluit-id
description: Offer decisioning - Configureer je voorstellen en besluit-id
kt: 5342
doc-type: tutorial
exl-id: 1418398b-d192-4d0b-b372-4be73fc153ed
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 1%

---

# 3.3.2 Uw aanbiedingen en beslissingen configureren

## 3.3.2.1 Maak je persoonlijke aanbiedingen

In deze oefening, zult u vier **Gepersonaliseerde Aanbiedingen** creëren. Hier volgen de details waarmee u rekening moet houden bij het maken van deze aanbiedingen:

| Naam | Datumbereik | Afbeeldingskoppeling voor e-mail | Afbeeldingskoppeling voor web | Tekst | Prioriteit | Subsidiabiliteit | Taal |
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|
| `--aepUserLdap-- - Nadia Elements Shell` | vandaag - 1 maand later | https://bit.ly/3nPiwdZ | https://bit.ly/2INwXjt | `{{ profile.person.name.firstName }}, 10% discount on Nadia Elements Shell` | 25 | all - Vrouwelijke klanten | Engels (Verenigde Staten) |
| `--aepUserLdap-- - Radiant Tee` | vandaag - 1 maand later | https://bit.ly/2HfA17v | https://bit.ly/3pEIdzn | `{{ profile.person.name.firstName }}, 5% discount on Radiant Tee` | 15 | all - Vrouwelijke klanten | Engels (Verenigde Staten) |
| `--aepUserLdap-- - Zeppelin Yoga Pant` | vandaag - 1 maand later | https://bit.ly/2IOaItW | https://bit.ly/2INZHZd | `{{ profile.person.name.firstName }}, 10% discount on Zeppelin Yoga Pant` | 25 | all - Mannelijke klanten | Engels (Verenigde Staten) |
| `--aepUserLdap-- - Proteus Fitness Jackshirt` | vandaag - 1 maand later | https://bit.ly/330a43n | https://bit.ly/36USaQW | `{{ profile.person.name.firstName }}, 5% discount on Proteus Fitness Jackshirt` | 15 | all - Mannelijke klanten | Engels (Verenigde Staten) |

{style="table-layout:auto"}

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. Om van één zandbak in een andere te veranderen, klik op **Prod van de PRODUCTIE (VA7)** en selecteer de zandbak van de lijst. In dit voorbeeld, wordt de zandbak genoemd **AEP Enablement FY22**. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

In het linkermenu, klik **Aanbiedingen** en ga dan naar **Aanbiedingen**. Klik op **+ Voorstel maken** .

![ Regel van het Besluit ](./images/offers1.png)

Dan zie je deze popup. Selecteer **Gepersonaliseerde aanbieding** en klik **daarna**.

![ Regel van het Besluit ](./images/offers2.png)

U bent nu op de **mening van Details**.

![ Regel van het Besluit ](./images/offers3.png)

In dit geval moet u de aanbieding configureren `--aepUserLdap-- - Nadia Elements Shell` . Gebruik de informatie in de bovenstaande tabel om de velden in te vullen. In dit voorbeeld, is de naam van de Gepersonaliseerde Aanbieding **vangeluw - Elementen Nadia Shell**. Ook, plaats de **datum en de tijd van het Begin** aan gisteren, en plaats de **datum en de tijd van het Eind** aan een datum in een maand van nu.

Als je klaar bent, moet je dit hebben. Klik **daarna**.

![ Regel van het Besluit ](./images/offers4.png)

U moet nu **Vertegenwoordigingen** tot stand brengen. De vertegenwoordiging is een combinatie a **Plaatsing** en een echt middel.

Voor **Vertegenwoordiging 1**, selecteer:

- Kanaal: Web
- Plaatsing: Web - Afbeelding
- Inhoud: URL
- Openbare plaats: kopieer URL van de kolom **Verbinding van het Beeld voor Web** in de bovengenoemde lijst

![ Regel van het Besluit ](./images/addcontent1.png)

Alternatief, kunt u **bibliotheek van Activa** voor de inhoud selecteren en dan **klikken doorbladert**.

![ Regel van het Besluit ](./images/addcontent2.png)

U zult dan popup van de Bibliotheek van Assets zien, ga naar de omslag **enablement-activa** en selecteer het beelddossier **nadia-web.png**. Dan, klik **Uitgezocht**.

![ Regel van het Besluit ](./images/addcontent3.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/addcontentrep20.png)

Klik op **+ Weergave toevoegen** .

![ Regel van het Besluit ](./images/addrep.png)

Voor **Vertegenwoordiging 2**, selecteer:

- Kanaal: E-mail
- Plaatsing: E-mail - Afbeelding
- Inhoud: URL
- Openbare plaats: kopieer URL van de kolom **Verbinding van het Beeld voor E-mail** in de bovengenoemde lijst

![ Regel van het Besluit ](./images/addcontentrep21.png)

Alternatief, kunt u **bibliotheek van Activa** voor de inhoud selecteren en dan **klikken doorbladert**.

![ Regel van het Besluit ](./images/addcontent2b.png)

U zult dan popup van de Bibliotheek van Assets zien, ga naar de omslag **enablement-activa** en selecteer het beelddossier **nadia-email.png**. Dan, klik **Uitgezocht**.

![ Regel van het Besluit ](./images/addcontent3b.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/addcontentrep20b.png)

Klik vervolgens op **+ Voorstelling toevoegen** .

![ Regel van het Besluit ](./images/addrep.png)

Voor **Vertegenwoordiging 3**, selecteer:

- Kanaal: niet-digitaal
- Plaatsing: niet-digitaal - tekst

Vervolgens moet u inhoud toevoegen. In dit geval betekent dit dat de tekst wordt toegevoegd die moet worden gebruikt als een oproep tot actie.

Klik **toevoegen Inhoud**.

![ Regel van het Besluit ](./images/addcontentrep31.png)

Dan zie je deze popup.

![ Regel van het Besluit ](./images/addcontent3text.png)

Selecteer **de tekst van de Douane** en vul deze gebieden in:

Kijk naar het **1} gebied van de Tekst {van de bovengenoemde lijst en ga die tekst hier in, in dit geval: `{{ profile.person.name.firstName }}, 10% discount on Nadia Elements Shell`.**

U zult ook opmerken dat u om het even welk profielattribuut kunt selecteren en het als dynamisch gebied in de aanbiedingstekst opnemen. In dit voorbeeld zorgt het veld `{{ profile.person.name.firstName }}` ervoor dat de voornaam van de klant die dit aanbod ontvangt, wordt opgenomen in de aanbiedingstekst.

Dan zie je dit. Klik **sparen**.

![ Regel van het Besluit ](./images/addcontentrep3text.png)

U hebt dit nu. Klik **daarna**.

![ Regel van het Besluit ](./images/addcontentrep3textdone.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/constraints.png)

Selecteer **door bepaalde besluitvormingsregel** en klik **+** pictogram om de regel **allen toe te voegen - Vrouwelijke Klanten**.

![ Regel van het Besluit ](./images/constraints1.png)

Dan zie je dit. Vul de **Prioriteit** zoals vermeld in de bovengenoemde lijst uit. Klik **daarna**.

![ Regel van het Besluit ](./images/constraints2.png)

U zult dan een overzicht van uw nieuwe **Gepersonaliseerde Aanbieding** zien.

![ Regel van het Besluit ](./images/offeroverview.png)

Tot slot klik **sparen en keur** goed.

![ Regel van het Besluit ](./images/saveapprove.png)

Je ziet dan dat je nieuwe persoonlijke aanbieding beschikbaar komt in het Overzicht van aanbiedingen:

![ Regel van het Besluit ](./images/offeroverview1.png)

Herhaal de bovenstaande stappen om de drie andere persoonlijke aanbiedingen voor de producten Radiant Tee, Zeppelin Yoga Pant en Proteus Fitness Jackshirt te maken.

Wanneer gedaan, zouden uw **Overzichten van de Aanbieding** scherm voor **Gepersonaliseerde Aanbiedingen** al uw aanbiedingen moeten tonen.

![ Definitieve Aanbiedingen ](./images/finaloffers.png)

## 3.3.2.2 Maak je fallback-aanbieding

Na het creëren van vier Gepersonaliseerde Aanbiedingen, zou u a **Aanbieding van de Fallback** nu moeten vormen.

Zorg ervoor u in de **mening van Aanbiedingen** bent:

![ Definitieve Aanbiedingen ](./images/finaloffers.png)

Klik op **+ Voorstel maken** .

![ Regel van het Besluit ](./images/createoffer.png)

Dan zie je deze popup. Selecteer {de aanbieding van 0} Fallback **en klik** daarna **.**

![ Regel van het Besluit ](./images/foffers2.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/foffers3.png)

Voer deze naam in voor uw fallback-aanbieding: `--aepUserLdap-- - Luma Fallback Offer` . Klik **daarna**.

![ Regel van het Besluit ](./images/foffers4.png)

U moet nu **Vertegenwoordigingen** tot stand brengen. De vertegenwoordiging is een combinatie a **Plaatsing** en een echt middel.

Voor **Vertegenwoordiging 1**, selecteer:

- Kanaal: Web
- Plaatsing: Web - Afbeelding
- Inhoud: URL
- Openbare locatie: `https://bit.ly/3nBOt9h`

![ Regel van het Besluit ](./images/addcontent1fb.png)

Alternatief, kunt u **bibliotheek van Activa** voor de inhoud selecteren en dan **klikken doorbladert**.

![ Regel van het Besluit ](./images/addcontent2fb.png)

U zult dan popup van de Bibliotheek van Assets zien, ga naar de omslag **enablement-activa** en selecteer het beelddossier **spriteyogastraps-web.png**. Dan, klik **Uitgezocht**.

![ Regel van het Besluit ](./images/addcontent3fb.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/addcontentrep20fb.png)

Voor **Vertegenwoordiging 2**, selecteer:

- Kanaal: E-mail
- Plaatsing: E-mail - Afbeelding
- Inhoud: URL
- Openbare locatie: `https://bit.ly/3nF4qvE`

![ Regel van het Besluit ](./images/addcontentrep21fb.png)

Alternatief, kunt u **bibliotheek van Activa** voor de inhoud selecteren en dan **klikken doorbladert**.

![ Regel van het Besluit ](./images/addcontent2bfb.png)

U zult dan popup van de Bibliotheek van Assets zien, ga naar de omslag **enablement-activa** en selecteer het beelddossier **spriteyogastraps-email.png**. Dan, klik **Uitgezocht**.

![ Regel van het Besluit ](./images/addcontent3bfb.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/addcontentrep20bfb.png)

Klik vervolgens op **+ Voorstelling toevoegen** .

![ Regel van het Besluit ](./images/addrep.png)

Voor **Vertegenwoordiging 3**, selecteer:

- Kanaal: niet-digitaal
- Plaatsing: niet-digitaal - tekst

Vervolgens moet u inhoud toevoegen. In dit geval betekent dat het toevoegen van de Verbinding van het Beeld.

Klik **toevoegen Inhoud**.

![ Regel van het Besluit ](./images/addcontentrep21text.png)

Dan zie je deze popup.

![ Regel van het Besluit ](./images/addcontent2text.png)

Selecteer **de tekst van de Douane** en vul deze gebieden in:

Ga de tekst `{{ profile.person.name.firstName }}, discover our Sprite Yoga Straps!` in en klik **sparen**.

![ Regel van het Besluit ](./images/faddcontent3text.png)

Dan zie je dit. Klik **daarna**.

![ Regel van het Besluit ](./images/faddcontentrep3.png)

U zult dan een overzicht van uw nieuwe **Aanbieding van de Fallback** zien. Klik **Afwerking**.

![ Regel van het Besluit ](./images/fofferoverview.png)

Tot slot klik **sparen en keur** goed.

![ Regel van het Besluit ](./images/saveapprovefb.png)

In uw **Overzichten van de Aanbieding** scherm, zult u dit nu zien:

![ Definitieve Aanbiedingen ](./images/ffinaloffers.png)

## 3.3.2.3 Maak uw collectie

Een inzameling wordt gebruikt aan **filter** uit een ondergroep aanbiedingen van de gepersonaliseerde lijst van de aanbieding en gebruik dat als deel van een Besluit om het besluitvormingsproces te versnellen.

Ga naar **Inzamelingen**. Klik op **+ Verzameling maken** .

![ Regel van het Besluit ](./images/collections.png)

Dan zie je deze popup. Configureer uw verzameling op deze manier. Klik **daarna**.

- Naam van verzameling: gebruik `--aepUserLdap-- - Luma Collection`
- Selecteer **creeer statische inzameling**.

![ Regel van het Besluit ](./images/createcollectionpopup1.png)

In het volgende scherm, selecteer de vier **Gepersonaliseerde Aanbiedingen** u in de vorige oefening creeerde. Klik **sparen**.

![ Regel van het Besluit ](./images/createcollectionpopup2.png)

U ziet nu het volgende:

![ Regel van het Besluit ](./images/colldone.png)

## 3.3.2.4 Maak uw beslissing

In een besluit worden Plaatsingen, een collectie persoonlijke aanbiedingen en een terugvalaanbieding gecombineerd die uiteindelijk door de Offer decisioning-engine worden gebruikt om de beste aanbieding voor een specifiek profiel te vinden, op basis van elk van de individuele kenmerken van de gepersonaliseerde aanbieding, zoals prioriteit, geschiktheidsbeperking en totale/gebruikersbeperking.

Om uw **Besluit** te vormen, ga **Besluiten**. Klik op **+ activiteit maken** .

![ Regel van het Besluit ](./images/activitydd.png)

U zult dan dit zien:

![ Regel van het Besluit ](./images/activity1.png)

Vul de velden zo in. Klik **daarna**.

- Naam: `--aepUserLdap-- - Luma Decision`
- Begindatum en -tijd: gisteren
- Einddatum en -tijd: vandaag + 1 maand

![ Regel van het Besluit ](./images/activity2.png)

In het volgende scherm, moet u plaatsingen in besluitvormingswerkingsgebied toevoegen. U zult besluitvormingswerkingsgebieden voor het Web van plaatsen **- Beeld**, **E-mail - Beeld** en **niet-digitaal - Tekst** moeten tot stand brengen.

![ Regel van het Besluit ](./images/addplacements.png)

Eerst, creeer het besluitvormingswerkingsgebied voor **niet-digitaal - Tekst** door die plaatsing in dropdown te selecteren. Dan, klik **toevoegen** knoop om evaluatiecriteria toe te voegen.

![ Regel van het Besluit ](./images/activity3.png)

Selecteer uw inzameling `--aepUserLdap-- - Luma Collection` en klik **toevoegen**.

![ Regel van het Besluit ](./images/activity4text.png)

Dan zie je dit. Klik op de knop **-** om een nieuw beslissingsbereik toe te voegen.

![ Regel van het Besluit ](./images/activity5text.png)

Selecteer het plaatsing **Web - Beeld** en voeg uw inzameling `--aepUserLdap-- - Luma Collection` onder evaluatiecriteria toe. Klik vervolgens nogmaals op de knop **+** om een nieuw beslissingsbereik toe te voegen.

![ Regel van het Besluit ](./images/activity6text.png)

Selecteer de plaatsing **E-mail - Beeld** en voeg uw inzameling `--aepUserLdap-- - Luma Collection` onder evaluatiecriteria toe. Dan, klik **daarna**.

![ Regel van het Besluit ](./images/activity4.png)

U moet nu uw **Aanbieding van de Fallback** selecteren, die `--aepUserLdap-- - Luma Fallback Offer` wordt genoemd. Klik **daarna**.

![ Regel van het Besluit ](./images/activity10.png)

Controleer uw beslissing. Klik **Afwerking**.

![ Regel van het Besluit ](./images/activity11.png)

In popup, klik **sparen en activeer**.

![ Regel van het Besluit ](./images/activity12.png)

Tot slot zie je nu je beslissing in het overzicht:

![ Regel van het Besluit ](./images/activity13.png)

U hebt nu met succes uw besluit gevormd. Uw besluit is nu live en kan worden gebruikt om uw klanten in real-time geoptimaliseerde en gepersonaliseerde aanbiedingen te bieden.

Volgende Stap: [ 3.3.3 bereidt uw bezit van de Cliënt van de Inzameling van Gegevens en de opstelling van SDK van het Web voor Offer decisioning voor ](./ex3.md)

[Terug naar module 3.3](./offer-decisioning.md)

[Terug naar alle modules](./../../../overview.md)
