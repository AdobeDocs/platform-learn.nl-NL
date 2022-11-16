---
title: Adobe Experience Platform Data Collection & Real-time Event Forwarding Side Forwarding - Create an Adobe Experience Platform Data Collection Event Forwarding property
description: Een Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen maken
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 2ca908a3-28b9-48d4-b96e-00951de530ba
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# 14.1 Een Adobe Experience Platform Data Collection Event Forwarding-eigenschap maken

>[!NOTE]
>
>De mobiele Adobe Experience Platform Edge-extensie bevindt zich momenteel in BETA. Gebruik van deze extensie is alleen op uitnodiging. Neem contact op met uw Adobe Customer Success Manager voor meer informatie en toegang tot de materialen voor deze zelfstudie.

## 14.1.1 Wat is een Adobe Experience Platform Data Collection Event Forwarding-eigenschap?

Wanneer gegevens worden verzameld met behulp van Adobe Experience Platform Data Collection, worden deze doorgaans verzameld op het tabblad **Client-zijde**. De **Client-zijde** is een omgeving zoals een website of een mobiele toepassing. In Module 0 en Module 1, werd de configuratie van een bezit van de Cliënt van de Gegevensverzameling van Adobe Experience Platform diepgaand besproken en u uitvoerde dat het bezit van de Cliënt van de Gegevensverzameling van Adobe Experience Platform op uw website en mobiele toepassing, zodat de gegevens daar konden worden verzameld wanneer een klant met de website en de mobiele toepassing communiceerde.

Wanneer die interactiegegevens worden verzameld door de Adobe Experience Platform Data Collection Client-eigenschap, wordt een aanvraag verzonden door de website of mobiele app naar Adobe Edge. De rand is de omgeving van de gegevensverzameling van entry-gegevens en is het punt voor klikstream in het ecosysteem van Adobe. Van Edge worden die verzamelde gegevens vervolgens verzonden naar toepassingen zoals Adobe Experience Platform, Adobe Analytics, Adobe Audience Manager of Adobe Target.

Met de toevoeging van een Adobe Experience Platform Data Collection Event Forwarding-eigenschap, is het nu mogelijk om een Adobe Experience Platform Data Collection-eigenschap te configureren die luistert naar binnenkomende gegevens op de Edge. Als de Adobe Experience Platform Data Collection Event Forwarding-eigenschap die op de Edge wordt uitgevoerd binnenkomende gegevens ziet, kan deze de gegevens gebruiken en naar een andere locatie doorsturen. Dat elders nu ook een externe webhaak zonder Adobe kan zijn, waardoor het mogelijk wordt om die gegevens naar bijvoorbeeld uw gegevens te verzenden, een meer van keuze, een beslissingstoepassing of een andere toepassing die de mogelijkheid heeft om een webhaak te openen.

De configuratie van een gebeurtenis die van de Gebeurtenis van de Inzameling van Adobe Experience Platform door:sturen kijkt vertrouwd aan een bezit van de Cliënt, met de capaciteit om gegevenselementen en regels te vormen enkel als in het verleden met de eigenschappen van de Cliënt van de Inzameling van Gegevens van Adobe Experience Platform. De manier waarop gegevens worden benaderd en gebruikt, is echter iets anders, afhankelijk van uw gebruiksscenario.

Laten we beginnen met het maken van de Adobe Experience Platform Data Collection Event Forwarding-eigenschap.

## 14.1.2 Een Adobe Experience Platform Data Collection Event Forwarding-eigenschap maken

Ga naar [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Klik in het linkermenu op **Gebeurtenis doorsturen**. Vervolgens ziet u een overzicht van alle beschikbare eigenschappen voor het doorsturen van Adobe Experience Platform-gegevensverzamelingsgebeurtenissen. Klik op de knop **Nieuwe eigenschap** knop.

![Adobe Experience Platform Data Collection SSF](./images/launchhome.png)

U moet nu een naam voor uw Adobe Experience Platform-eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen invoeren. Gebruik als naamgevingsconventie `--demoProfileLdap-- - Demo System (DD/MM/YYYY) (Edge)`. In dit voorbeeld is de naam bijvoorbeeld **vangeluw - Demo System (22-02-2022) (Edge)**. Klikken **Opslaan**.

![Adobe Experience Platform Data Collection SSF](./images/ssf1.png)

U zult dan terug in de lijst van de Gebeurtenis door:sturen van de Gebeurtenis van de Gegevensverzameling van Adobe Experience Platform zijn. Klik om de eigenschap te openen die u net hebt gemaakt.

![Adobe Experience Platform Data Collection SSF](./images/ssf2.png)

## 14.1.2 De extensie Adobe Cloud Connector configureren

Ga in het linkermenu naar **Extensies**. U zult zien dat de **Kern** extensie is al geconfigureerd.

![Adobe Experience Platform Data Collection SSF](./images/ssf3.png)

Ga naar **Catalogus**. U ziet de **Adobe Cloud Connector** extensie. Klikken **Installeren** om het te installeren.

![Adobe Experience Platform Data Collection SSF](./images/ssf4.png)

De extensie wordt vervolgens toegevoegd. Er is geen configuratie voor deze stap. U wordt teruggestuurd naar het overzicht van geïnstalleerde extensies.

![Adobe Experience Platform Data Collection SSF](./images/ssf5.png)

## 14.1.3 Implementeer de eigenschap Adobe Experience Platform Data Collection Forwarding

Ga in het linkermenu naar **Publishing Flow**. Klikken **Bibliotheek toevoegen**.

![Adobe Experience Platform Data Collection SSF](./images/ssf6.png)

Voer de naam in **Hoofd**, selecteert u de omgeving **Ontwikkeling (ontwikkeling)** en klik op **+ Alle gewijzigde bronnen toevoegen**.

![Adobe Experience Platform Data Collection SSF](./images/ssf7.png)

Dan zie je dit. Klikken **Opslaan en bouwen voor ontwikkeling**.

![Adobe Experience Platform Data Collection SSF](./images/ssf8.png)

Uw bibliotheek wordt dan gemaakt, wat 1 tot 2 minuten kan duren.

![Adobe Experience Platform Data Collection SSF](./images/ssf9.png)

Tot slot wordt uw bibliotheek gemaakt en klaar.

![Adobe Experience Platform Data Collection SSF](./images/ssf10.png)

Volgende stap: [14.2 Werk uw DataStream bij om gegevens ter beschikking te stellen van uw Gebeurtenis die van de Inzameling van Gegevens door:sturen bezit](./ex2.md)

[Ga terug naar module 14](./aep-data-collection-ssf.md)

[Terug naar alle modules](./../../overview.md)
