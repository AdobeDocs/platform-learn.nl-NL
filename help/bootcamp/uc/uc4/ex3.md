---
title: Bootkamp - Customer Journey Analytics - Een gegevensweergave maken
description: Customer Journey Analytics - Een gegevensweergave maken
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Data Views
exl-id: e634876c-2b1c-4f7f-99e5-1940f6c87d80
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1627'
ht-degree: 0%

---

# 4.3 Een gegevensweergave maken

## Doelstellingen

- De interface voor gegevensweergave begrijpen
- De basisinstellingen van de definitie van een bezoek begrijpen
- Kenmerk en doorzettingsvermogen in een gegevensweergave begrijpen

## 4.3.1 Gegevensweergave

Als de verbinding tot stand is gebracht, kunt u nu de visualisatie beïnvloeden. Een verschil tussen Adobe Analytics en CJA is dat CJA een gegevensweergave nodig heeft om de gegevens vóór visualisatie te kunnen opschonen en voorbereiden.

Een mening van Gegevens is gelijkaardig aan het concept Virtuele Reeksen van het Rapport in Adobe Analytics, waar u context-bewuste bezoekendefinities bepaalt, filtrerend en ook, hoe de componenten worden geroepen.

U hebt minimaal één gegevensweergave per verbinding nodig. Nochtans, voor sommige gebruik-gevallen, is het groot om veelvoudige Mening van Gegevens voor de zelfde verbinding te hebben, met het doel om verschillende inzichten aan verschillende teams te geven.
Als u uw bedrijf gegevensgedreven wilt worden, zou u moeten aanpassen hoe de gegevens in elk team worden bekeken. Enkele voorbeelden:

- UX-meetgegevens alleen voor het UX-ontwerpteam
- Gebruik dezelfde namen voor KPI&#39;s en Metriek voor Googles Analytics als voor Customers Journey Analytics, zodat het digitale analyseteam slechts één taal kan spreken.
- Gegevensweergave gefilterd om bijvoorbeeld gegevens weer te geven voor één markt, of voor één merk, of alleen voor mobiele apparaten.

Voor het **scherm van Verbindingen**, controleer checkbox voor de verbinding u enkel creeerde. Klik **creëren de Mening van Gegevens**.

![ demo ](./images/exta.png)

U zult aan **worden opnieuw gericht creeer het werkschema van de Mening van Gegevens**.

![ demo ](./images/0-v2.png)

## 4.3.2 Gegevensweergavedefinitie

U kunt de basisdefinities voor uw Mening van Gegevens nu vormen.

![ demo ](./images/0-v2.png)

De **Verbinding** u in de vorige oefening creeerde is reeds geselecteerd. Uw verbinding heeft de naam `yourLastName – Omnichannel Data Connection` .

![ demo ](./images/ext5.png)

Geef vervolgens in de gegevensweergave een naam die volgt op de naamgevingsconventie: `yourLastName – Omnichannel Data View` .

Voer dezelfde waarde in voor de beschrijving: `yourLastName – Omnichannel Data View` .

| Naam | Beschrijving |
| ----------------- |-------------| 
| `yourLastName – Omnichannel Data View` | `yourLastName – Omnichannel Data View` |

![ demo ](./images/1-v2.png)

Voor de **Tijdzone**, selecteer timezone **Berlijn, Stockholm, Rome, Bern, Brussel, Wenen, Amsterdam GMT+01:00**. Dit is een heel interessante situatie, aangezien sommige bedrijven in verschillende landen en geografische gebieden actief zijn. Door de juiste tijdzone voor elk land toe te wijzen, worden typische fouten in de gegevens vermeden, zoals bijvoorbeeld het vermoeden dat in Peru de meerderheid van de mensen om 16.00 uur T-shirts koopt.

![ demo ](./images/ext7.png)

U kunt ook de namen van de belangrijkste metriek wijzigen (Person, Sessie en Gebeurtenis). Dit is niet verplicht, maar sommige klanten gebruiken graag Personen, Bezoekingen en Verzoeken in plaats van Personen, Sessie en Gebeurtenissen (standaardnaamgevingsconventie van Customer Journey Analytics).

De volgende instellingen moeten nu zijn geconfigureerd:

![ demo ](./images/1-v2.png)

Klik **sparen en ga** verder.

![ demo ](./images/12-v2.png)

## 4.3.3 Componenten voor gegevensweergave

In deze oefening, zult u de componenten vormen u de gegevens moet analyseren en het visualiseren gebruikend Analysis Workspace. In deze interface zijn er drie hoofdgebieden:

- Linkerkant: Beschikbare componenten uit de geselecteerde datasets
- Midden: componenten toegevoegd aan de gegevensweergave
- Rechterkant: Componentinstellingen

![ demo ](./images/2-v2.png)

>[!IMPORTANT]
>
>Als u geen specifieke metrisch of afmeting kunt vinden, gelieve te controleren of wordt het gebied `Contains data` verwijderd uit uw gegevensmening. Zo niet, verwijder dat veld.
>
>![ demo ](./images/2-v2a.png)

U moet nu de componenten slepen en laten vallen u voor de analyse aan de **Toegevoegde Componenten** nodig hebt. U doet dit door de componenten in het linkermenu te selecteren en ze naar het canvas in het midden te slepen.

Laten wij met de eerste component beginnen: **Naam (web.webPageDetails.name)**. Zoek naar deze component, dan belemmering en laat vallen het op het canvas.

![ demo ](./images/3-v2.png)

Deze component is de paginanaam, aangezien u uit het lezen van het schemagebied `(web.webPageDetails.name)` kunt voortkomen.

Nochtans, gebruikend **Naam** als naam is niet de beste noemende overeenkomst voor een bedrijfsgebruiker om deze dimensie snel te begrijpen.

Laten wij de naam veranderen om **Naam van de Pagina** te zijn. Klik op de component en noem het op het **gebied van de Montages van de Component** anders.

![ demo ](./images/3-0-v2.png)

Iets echt belangrijk is de **montages van de persistentie**. Het concept gebeurtenissen en prop bestaat niet in CJA maar de montages van de Persistentie maken een gelijkaardig gedrag mogelijk.

![ demo ](./images/3-0-v21.png)

Als u deze montages niet verandert, zal CJA de dimensie als a **Prop** (klapniveau) interpreteren. Ook, kunnen wij Persistence veranderen om de dimensie tot **eVar** (voorhoud de waarde over de reis) te maken.

Als u niet vertrouwd met eVars en Props bent, kunt u [ meer over hen in de documentatie ](https://experienceleague.adobe.com/docs/analytics/landing/an-key-concepts.html?lang=nl-NL) lezen.

Laten we de paginanaam als een pop-up opgeven. Als dusdanig, te hoeven u om het even welke **Persistence Montages** niet te veranderen.

| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| Naam (web.webPageDetails.name) | Paginanaam |          |

Daarna, kies de afmeting **phoneNumber** en laat vallen het op het canvas. De nieuwe naam zou **Aantal van de Telefoon** moeten zijn.

![ demo ](./images/3-1-v2.png)

Tot slot veranderen wij de montages van de Persistentie, aangezien het Mobiele Aantal op gebruikersniveau zou moeten voortbestaan.

Om persistentie te veranderen, scrol neer in het juiste menu en open **persistentie** tabel:

![ demo ](./images/5-v2.png)

Schakel het selectievakje in om de instellingen voor persistentie te wijzigen. Selecteer **Recentste Recentste** en het **Persoon (Meldend venster)** werkingsgebied, aangezien wij slechts om het laatste mobiele aantal van die persoon geven. Als de klant de mobiele telefoon niet invult bij toekomstige bezoeken, ziet u deze waarde nog steeds gevuld.

![ demo ](./images/6-v2.png)

| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| phoneNumber | Telefoonnummer | Recentste versie, Persoon (rapportagevenster) |

De volgende component is `web.webPageDetails.pageViews.value` .

Zoek in het linkerzijmenu naar `web.webPageDetails.pageViews.value` . Sleep deze metrische waarde naar het canvas.

Verander de naam om **de Meningen van de Pagina** onder de **montages van de Component** te zijn.

| Componentnaam die u wilt zoeken | Nieuwe naam | Attributie-instellingen |
| ----------------- |-------------| --------------------| 
| web.webPageDetails.pageViews.value | Paginaweergaven |         |

![ demo ](./images/7-v2.png)

Voor de toewijzingsinstellingen laten we deze leeg.

Opmerking: Persistentie-instellingen voor metriek kunnen ook worden gewijzigd in Analysis Workspace. In sommige gevallen kunt u het hier instellen om te voorkomen dat zakelijke gebruikers hoeven te bedenken wat het beste persistentiemodel is.

Daarna, zult u veel Dimensionen en Metriek moeten vormen, zoals die in de hieronder lijst wordt vermeld.

### DIMENSIONEN


| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| brandName | Merknaam | Recentste versie, sessie |
| beluisteren | Aanroepfunctie |          |
| call-id | Type oproepinteractie |          |
| callTopic | Het Onderwerp van de vraag | Recentste versie, sessie |
| ecid | ECID | Recentste versie, Persoon (rapportagevenster) |
| email | E-mailid | Recentste versie, Persoon (rapportagevenster) |
| Betalingstype | Betalingstype |          |
| Product toevoegen, methode | Product toevoegen, methode | Recentste versie, sessie |
| Type gebeurtenis | Type gebeurtenis |         |
| Naam (productListItems.name) | Productnaam |         |
| SKU | SKU (sessie) | Recentste versie, sessie |
| Transactie-id | Transactie-id |         |
| URL (web.webPageDetails.URL) | URL |         |
| Gebruikersagent | Gebruikersagent | Recentste versie, sessie |
| niveau | Loyaliteitsniveau |          |
| punten | Levensduur van klant |          |

### METRISCHE

| Componentnaam die u wilt zoeken | Nieuwe naam | Attributie-instellingen |
| ----------------- |-------------| --------------------| 
| Aantal | Aantal |          |
| commerce.order.priceTotal | Ontvangsten |         |

Uw configuratie zou dan als dit moeten kijken:

![ demo ](./images/11-v2.png)

Vergeet niet **&#x200B;**&#x200B;te bewaren uw Mening van Gegevens. Zo klik **sparen** nu.

![ demo ](./images/12-v2s.png)

## 4.3.4 Berekende cijfers

Hoewel wij alle componenten in de Mening van Gegevens hebben georganiseerd, moet u nog enkele hen aanpassen, zodat de bedrijfsgebruikers bereid zijn om hun analyse te beginnen.

Als je je herinnert, hebben we Metriek zoals &#39;Add to Cart&#39;, &#39;Product View&#39; of &#39;Purchases&#39; niet specifiek meegenomen in de Data View.
Nochtans, hebben wij een geroepen afmeting: **Type van Gebeurtenis**. Dus, laten we deze interactietypen afleiden door 3 berekende Metriek te creëren.

Laten wij met eerste Metrisch beginnen: **de Kijken van het Product**.

Voor de linkerkant, gelieve **Type van Gebeurtenis** te zoeken en de afmeting te selecteren. Dan belemmering en laat vallen binnen het **Included Componenten** canvas.

![ demo ](./images/calcmetr1.png)

Klik om het nieuwe metrische **Type van Gebeurtenis** te selecteren.

![ demo ](./images/calcmetr2.png)

Wijzig nu de naam en beschrijving van de component in de volgende waarden:

| Componentnaam | Componentbeschrijving |
| ----------------- |-------------| 
| Productweergaven | Productweergaven |

![ demo ](./images/calcmetr3.png)

Nu laat slechts **gebeurtenissen tellen van de Meningen van het 0&rbrace; Product.** Om dat te doen, scrol neer op de **Montages van de Component** tot u **omvat Exclude Waarden** ziet. Zorg ervoor om de optie toe te laten **plaats omvat/sluit waarden** uit.

![ demo ](./images/calcmetr4.png)

Aangezien wij slechts **Weergaven van het Product** willen tellen, gelieve **commerce.productViews** onder de criteria te specificeren.

![ demo ](./images/calcmetr5.png)

Uw berekende metrisch is nu klaar!

Daarna, herhaal het zelfde proces voor **toevoegt aan de gebeurtenissen van de Kar** en **Koop**.

### Toevoegen aan winkelwagentje

Eerste belemmering en laat vallen het zelfde afmeting **Type van Gebeurtenis**.

![ demo ](./images/calcmetr1.png)

Er verschijnt een pop-upwaarschuwing voor een gedupliceerd veld terwijl we dezelfde variabele gebruiken. Gelieve te klikken op **hoe dan ook toevoegen**:

![ demo ](./images/calcmetr6.png)

Volg nu hetzelfde proces als voor de metrische productweergaven:
- Wijzig eerst de naam en beschrijving.
- Tot slot voeg **commerce.productListAdds** als criteria toe om slechts te tellen toevoegt aan Kaart

| Naam | Beschrijving | Criteria |
| ----------------- |-------------| -------------|
| Toevoegen aan winkelwagentje | Toevoegen aan winkelwagentje | commerce.productListAdds |

![ demo ](./images/calcmetr6a.png)

### Aankopen

Eerste belemmering en laat vallen het zelfde afmetingstype **van de Gebeurtenis** zoals wij voor beide vorige metriek deden.

![ demo ](./images/calcmetr1.png)

Er verschijnt een pop-upwaarschuwing voor een gedupliceerd veld terwijl we dezelfde variabele gebruiken. Gelieve te klikken op **hoe dan ook toevoegen**:

![ demo ](./images/calcmetr7.png)

Volg nu hetzelfde proces als voor de metrieke productweergaven en Toevoegen aan winkelwagentje:
- Wijzig eerst de naam en beschrijving.
- Tot slot voeg **commerce.purchase** als criteria toe om slechts Aankopen te tellen

| Naam | Beschrijving | Criteria |
| ----------------- |-------------| -------------|
| Aankopen | Aankopen | commerce.purchases |

![ demo ](./images/calcmetr7a.png)

Uw definitieve configuratie zou dan gelijkaardig aan dit moeten kijken. Klik **sparen en ga** verder.

![ demo ](./images/calcmetr8.png)

## 4.3.5 Gegevensweergave-instellingen

U moet naar dit scherm worden omgeleid:

![ demo ](./images/8-v2.png)

Op dit tabblad kunt u enkele belangrijke instellingen wijzigen om de manier te wijzigen waarop gegevens worden verwerkt. Laat beginnen door de **Onderbreking van de Zitting** aan 30 min te plaatsen. Dankzij de tijdstempel van elke ervaringsgebeurtenis kunt u het concept van een sessie op alle kanalen uitbreiden. Bijvoorbeeld, wat gebeurt als een klant het vraag-centrum na het bezoeken van de website roept? Wanneer u aangepaste sessietime-outs gebruikt, hebt u veel flexibiliteit om te bepalen wat een sessie is en hoe die sessie gegevens samenvoegt.

![ demo ](./images/ext8.png)

Op dit lusje kunt u andere dingen wijzigen zoals het filtreren van de gegevens door een segment/filter te gebruiken. Dat hoef je in deze oefening niet te doen.

![ demo ](./images/10-v2.png)

Zodra u wordt gedaan, te klikken gelieve **sparen en te beëindigen**.

![ demo ](./images/13-v2.png)

>[!NOTE]
>
>U kunt later terugkeren naar deze gegevensweergave en op elk gewenst moment instellingen en componenten wijzigen. Wijzigingen zijn van invloed op de manier waarop historische gegevens worden weergegeven.

U kunt nu doorgaan met het gedeelte visualisatie en analyse!

Volgende Stap: [ 4.4 Voorbereiding van Gegevens in Customer Journey Analytics ](./ex4.md)

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Terug naar alle modules](./../../overview.md)
