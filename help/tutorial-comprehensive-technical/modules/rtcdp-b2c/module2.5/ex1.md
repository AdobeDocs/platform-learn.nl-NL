---
title: Adobe Experience Platform Data Collection & Real-time Event Forwarding Side Forwarding - Create an Adobe Experience Platform Data Collection Event Forwarding property
description: Een Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen maken
kt: 5342
doc-type: tutorial
exl-id: 9c64e57d-c91c-4d4c-923f-91a02edeb2ac
source-git-commit: 6485bfa1c75c43bb569f77c478a273ace24a61d4
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# 2.5.1 Een Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen maken

## Wat is een Adobe Experience Platform Data Collection Event Forwarding-eigenschap?

Typisch, wanneer het gegeven gebruikend de Inzameling van Gegevens van Adobe Experience Platform wordt verzameld, wordt het verzameld op de **cliëntkant**. De **cliëntkant** is een milieu zoals een website of een mobiele toepassing. Bij Aan de slag en Gegevensverzameling is de configuratie van een Adobe Experience Platform Data Collection Client-eigenschap uitgebreid besproken en hebt u die Adobe Experience Platform Data Collection Client-eigenschap geïmplementeerd op uw website en mobiele toepassing, zodat gegevens daar kunnen worden verzameld wanneer een klant communiceert met de website en mobiele toepassing.

Wanneer die interactiegegevens worden verzameld door de Adobe Experience Platform Data Collection Client-eigenschap, wordt een aanvraag verzonden door de website of mobiele app naar de Edge van de Adobe. De Edge is het milieu van de Inzameling van Gegevens van de Adobe en is het ingang-punt voor klikstroomgegevens in het ecosysteem van de Adobe. Vanuit de Edge worden die verzamelde gegevens vervolgens verzonden naar toepassingen zoals Adobe Experience Platform, Adobe Analytics, Adobe Audience Manager of Adobe Target.

Met de toevoeging van een Adobe Experience Platform Data Collection Event Forwarding-eigenschap, is het nu mogelijk om een Adobe Experience Platform Data Collection-eigenschap te configureren die luistert naar binnenkomende gegevens op de Edge. Als de Adobe Experience Platform Data Collection Event Forwarding-eigenschap die wordt uitgevoerd op de Edge binnenkomende gegevens ziet, kan deze de gegevens gebruiken en naar een andere locatie doorsturen. Dat elders nu ook een externe webhaak zonder Adobe kan zijn, die het mogelijk maakt om die gegevens naar bijvoorbeeld uw gegevens te verzenden, een meer van keuze, een beslissingstoepassing of een andere toepassing die de mogelijkheid heeft om een webhaak te openen.

De configuratie van een Gebeurtenis die van de Inzameling van Adobe Experience Platform door:sturen van gegevens kijkt vertrouwd aan een cliënt zijbezit, met de capaciteit om gegevenselementen en regels te vormen enkel als in het verleden met de eigenschappen van de Cliënt van de Inzameling van Gegevens van Adobe Experience Platform. De manier waarop gegevens worden benaderd en gebruikt, is echter iets anders, afhankelijk van uw gebruiksscenario.

Laten we beginnen met het maken van de Adobe Experience Platform Data Collection Event Forwarding-eigenschap.

## Een Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen maken

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). In het linkermenu, klik **Gebeurtenis door:sturen**. Vervolgens ziet u een overzicht van alle beschikbare eigenschappen voor het doorsturen van Adobe Experience Platform-gegevensverzamelingsgebeurtenissen. Klik **creeer Bezit** knoop.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/launchhome.png)

Als er al andere eigenschappen voor het doorsturen van gebeurtenissen zijn gemaakt, ziet de interface er anders uit. In dat geval, klik **Nieuw Bezit**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/launchhomea.png)

U moet nu een naam voor uw Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen invoeren. Gebruik `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)` als naamgevingsconventie. Bijvoorbeeld, in dit voorbeeld, is de naam **vangeluw - het Systeem van de Demo (22/02/2022) (Edge)**. Klik **sparen**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf1.png)

U zult dan terug in de lijst van de Gebeurtenis door:sturen van de Gebeurtenis van de Gegevensverzameling van Adobe Experience Platform zijn. Klik om de eigenschap te openen die u net hebt gemaakt.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf2.png)

## De extensie Adobe Cloud Connector configureren

In het linkermenu, ga naar **Uitbreidingen**. U zult zien dat de **uitbreiding van de Kern** reeds wordt gevormd.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf3.png)

Ga naar **Catalogus**. U zult de **uitbreiding van de Schakelaar van de Wolk van de Adobe 0&rbrace; zien, samen vele anderen.** Klik **installeren** om het te installeren.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf4.png)

De extensie wordt vervolgens toegevoegd. Er is geen configuratie voor deze stap. U wordt teruggestuurd naar het overzicht van geïnstalleerde extensies.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf5.png)

## Implementeer de eigenschap Adobe Experience Platform Data Collection Event Forwarding

In het linkermenu, ga naar **het Publiceren Stroom**. Klik **toevoegen Bibliotheek**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf6.png)

Ga de naam **Belangrijkste** in, selecteer de milieu **Ontwikkeling (ontwikkeling)** en klik **+ voeg Alle Gewijzigde Middelen** toe.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf7.png)

Dan zie je dit. Klik **sparen &amp; bouwt voor Ontwikkeling**.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf8.png)

Uw bibliotheek wordt dan gemaakt, wat 1 tot 2 minuten kan duren.

![ de Inzameling SSF van Gegevens van Adobe Experience Platform ](./images/ssf10.png)

Volgende Stap: [ 2.5.2 Werk uw DataStream bij om gegevens beschikbaar te maken aan uw Gebeurtenis van de Inzameling van Gegevens die bezit door:sturen ](./ex2.md)

[Ga terug naar Module 2.5](./aep-data-collection-ssf.md)

[Terug naar alle modules](./../../../overview.md)
