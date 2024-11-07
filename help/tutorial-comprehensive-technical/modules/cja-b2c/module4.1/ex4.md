---
title: Customer Journey Analytics - Gegevensvoorbereiding in Analysis Workspace
description: Customer Journey Analytics - Gegevensvoorbereiding in Analysis Workspace
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# 4.1.4 Gegevensvoorbereiding in Analysis Workspace

## Doelstellingen

- De gebruikersinterface van Analysis Workspace in CJA begrijpen
- Begrijp de concepten van gegevensvoorbereiding in Analysis Workspace
- Leer hoe u gegevensberekeningen uitvoert

## 4.1.4.1 Analysis Workspace-gebruikersinterface in CJA

Analysis Workspace verwijdert alle typische beperkingen van één Analytics-rapport. Het verstrekt een robuust, flexibel canvas voor de bouw van projecten van de douaneanalyse. Sleep een willekeurig aantal gegevenstabellen, visualisaties en componenten (afmetingen, Metriek, segmenten en tijdgranulariteit) naar een project. Creëer meteen onderverdelingen en segmenten, creeer cohorts voor analyse, creeer alarm, vergelijk segmenten, stroom en reserveanalyse, en curate en planningsrapporten voor het delen met iedereen in uw zaken.

Customer Journey Analytics brengt deze oplossing bovenop de gegevens van het Platform. We raden u aan deze overzichtsvideo van vier minuten te bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

Als u Analysis Workspace nog niet eerder hebt gebruikt, raden we u aan deze video te bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Uw project maken

Nu is het tijd om uw eerste CJA-project te maken. Ga naar het projectlusje binnen van CJA.
Klik **creëren nieuw**.

![ demo ](./images/prmenu.png)

Dan zie je dit. Selecteer **Leeg project** en klik dan **creeer**.

![ demo ](./images/prmenu1.png)

Dan zie je een leeg project.

![ demo ](./images/premptyprojects.png)

Selecteer eerst de juiste gegevensweergave in de rechterbovenhoek van het scherm. In dit voorbeeld is de gegevensweergave die moet worden geselecteerd `vangeluwe - Omnichannel Data View` .

![ demo ](./images/prdv.png)

Vervolgens slaat u uw project op en geeft u het een naam. U kunt de volgende opdracht gebruiken om op te slaan:

| OS | Korte snede |
| ----------------- |-------------| 
| Windows | Control + S |
| Mac | Command + S |

U ziet deze pop-up:

![ demo ](./images/prsave.png)

Gebruik deze naamgevingsconventie:

| Naam | Beschrijving |
| ----------------- |-------------| 
| `--demoProfileLdap-- - Omnichannel Analysis` | `--demoProfileLdap-- - Omnichannel Analysis` |

Daarna, klik **sparen**.

![ demo ](./images/prsave2.png)

## 4.1.4.2 Berekende cijfers

Hoewel wij alle componenten in de Mening van Gegevens hebben georganiseerd, moet u nog enkele hen aanpassen, zodat de bedrijfsgebruikers bereid zijn om hun analyse te beginnen. Ook, tijdens om het even welke analyse kunt u berekende metrisch tot stand brengen om dieper op de inzichten het vinden te gaan.

Als voorbeeld zullen wij tot een berekend **Tarief van de Omzetting** gebruikend de **Aankopen** metrisch/gebeurtenis leiden wij op de Mening van Gegevens bepaald.

### Conversiesnelheid

Laten we beginnen met het openen van de berekende metrische builder. Klik op **+** om uw eerste Berekende Metrisch in Analysis Workspace tot stand te brengen.

![ demo ](./images/pradd.png)

**Berekende Metrische Bouwer** zal omhoog verschijnen:

![ demo ](./images/prbuilder.png)

Vind de **Aankopen** in de lijst van Metriek in het linkerzijmenu. Onder **Metriek** klik **tonen allen**

![ demo ](./images/calcbuildercr1.png)

Nu sleep en laat vallen de **Steekproeven** binnen aan de berekende metrische definitie.

![ demo ](./images/calcbuildercr2.png)

Typisch, betekent de omzettingspercentage **Conversies/Sessies**. Laten we dezelfde berekening uitvoeren in het berekende metrische definitiekanvas. Vind de **metrische Zittingen** en sleep en laat vallen het in de definitiebouwer, onder de **Aankopen** gebeurtenis.

![ demo ](./images/calcbuildercr3.png)

De operator voor delen wordt automatisch geselecteerd.

![ demo ](./images/calcbuildercr4.png)

De omrekeningskoers wordt gewoonlijk uitgedrukt in een percentage. Dus, veranderen wij het formaat om percentage te worden en ook 2 decimalen selecteren.

![ demo ](./images/calcbuildercr5.png)

Ten slotte wijzigt u de naam en beschrijving van de berekende metrische waarde:

| Titel | Beschrijving |
| ----------------- |-------------| 
| Conversiesnelheid | Conversiesnelheid |

U zult iets als dit op uw scherm hebben:

![ demo ](./images/calcbuildercr6.png)

Vergeet niet om **** te sparen Berekend Metrisch.

![ demo ](./images/pr9.png)

## 4.1.4.3 Berekende Dimensionen: filters (segmentatie) en datumbereiken

### Filters: berekende Dimensionen

Berekeningen zijn niet alleen bedoeld voor Metriek. Alvorens om het even welke analyse te beginnen is het ook interessant om sommige **Berekende Dimensionen** tot stand te brengen. Dit betekende eigenlijk **segmenten** terug in Adobe Analytics. In Customer Journey Analytics, worden deze segmenten genoemd **Filters**.

![ demo ](./images/prfilters.png)

Het creëren van filters zal bedrijfs gebruikers helpen om de analyse met sommige waardevolle berekende afmetingen te beginnen. Dit zal sommige taken automatiseren evenals aan het adoptiedeel helpen. Hier volgen enkele voorbeelden:

1. Eigen media, betaalde media,
2. Nieuwe of terugkerende bezoeken
3. Klanten met Verlaten winkelwagen

Deze filters kunnen voor of tijdens het analysegedeelte worden gemaakt (dat u in de volgende oefening zult doen).

### Datumbereik: Dimensionen voor berekende tijd

De Dimensionen van de tijd zijn een ander type berekende afmetingen. Sommige zijn reeds tot stand gebracht, maar u hebt ook de capaciteit om uw eigen Dimensionen van de douanetijd bij de fase van de gegevensvoorbereiding te creëren.

Deze berekende Dimensionen van de Tijd zullen wij analisten en bedrijfsgebruikers helpen om belangrijke data te herinneren en hen te gebruiken om de rapporttijd te filtreren en te veranderen. Typische vragen en twijfels die ons bij analyses opkomen:

- Wanneer was Zwarte Vrijdag vorig jaar? 21e-29e?
- Wanneer hebben we die tv-campagne in december gevoerd?
- Van wanneer tot wanneer deden we de zomerverkoop van 2018? Ik wil het vergelijken met 2019. Weet je trouwens de exacte dagen in 2019?

![ demo ](./images/timedimensions.png)

U hebt nu de gegevensvoorbereidingsoefening met CJA Analysis Workspace voltooid.

Volgende Stap: [ 4.1.5 Visualisatie gebruikend Customer Journey Analytics ](./ex5.md)

[Terug naar module 4.1](./customer-journey-analytics-build-a-dashboard.md)

[Terug naar alle modules](./../../../overview.md)
