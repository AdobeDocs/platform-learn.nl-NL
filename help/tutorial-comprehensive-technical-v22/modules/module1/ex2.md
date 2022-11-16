---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - het Netwerk van de Rand, Gegevensstromen en de Inzameling van Gegevens van de Server
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - het Netwerk van de Rand, Gegevensstromen en de Inzameling van Gegevens van de Server
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 6f7c540f-3804-483d-90f9-b26b4a252b8b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 2%

---

# 1.2 Edge Network, DataStream en Server Side Data Collection

## Context

In deze oefening zult u tot een **DataStream**. A **DataStream** vertelt de servers van Adobe Edge waar te om de gegevens te verzenden nadat het door Web SDK wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

De gegevensstromen worden altijd geleid in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan de gegevensinzameling van Adobe Experience Platform met Web SDK. Zelfs wanneer u Web SDK met een niet-Adobe oplossing van het markeringsbeheer uitvoert, zult u nog uw DataStream in het gebruikersinterface van de Inzameling van Gegevens van Adobe Experience Platform moeten creëren.

U zult SDK van het Web op browser in de volgende oefening uitvoeren. Het zal u dan duidelijker zijn hoe de gegevens die worden verzameld eruit zien. Vooralsnog vertellen we alleen maar aan de DataStream waar we de gegevens moeten doorsturen.

## Een DataStream maken

In [Oefening 0.2](./../module0/ex2.md) Je hebt al een DataStream gemaakt, maar we hadden het niet over de achtergrond en de reden om van de DataStream te zijn.

Een DataStream vertelt de servers van Adobe Edge waar te om de gegevens te verzenden nadat het door het Web SDK wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target? De stromen van gegevens worden beheerd in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan de gegevensinzameling van het Platform met Web SDK, ongeacht of u Web SDK via de Inzameling van de Gegevens van Adobe Experience Platform uitvoert.

We controleren uw **[!UICONTROL DataStream]**:

Ga naar [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/).

Klikken **[!UICONTROL DataStreams]** of **[!UICONTROL Gegevensstromen (bèta)]** in het linkermenu.

![Klik op het pictogram DataStream in de linkernavigatie](./images/edgeconfig1.png)

Zoek naar uw DataStream, die wordt genoemd `--demoProfileLdap-- - Demo System Datastream`.

![Geef de gegevensstroom een naam en sla deze op](./images/edgeconfig2.png)

Dan zie je de details van je DataStream.

![Geef de gegevensstroom een naam en sla deze op](./images/edgecfg1.png)

Klikken **...** naast **Adobe Experience Platform** en klik op **Bewerken**.

![Geef de gegevensstroom een naam en sla deze op](./images/edgecfg1a.png)

Dan zie je dit. Op dit moment heb je alleen Adobe Experience Platform ingeschakeld. Uw configuratie zal gelijkaardig aan de hieronder configuratie kijken. (Afhankelijk van uw omgeving en Adobe Experience Platform-instantie kan de naam van de sandbox anders zijn.)

![Geef de gegevensstroom een naam en sla deze op](./images/edgecfg2.png)

U moet de onderstaande velden als volgt interpreteren:

Voor deze gegevensstroom...

- Alle gegevens die worden verzameld, worden opgeslagen in de `--aepSandboxId--` sandbox in Adobe Experience Platform
- Alle gegevens van de Gebeurtenis van de Ervaring worden verzameld door gebrek in de dataset **Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1)**
- Alle profielgegevens worden standaard verzameld in de gegevensset **Demosysteem - profielgegevensset voor website (Global v1.1)** (het opnemen van profielgegevens binnen met Web SDK momenteel wordt niet gesteund nog door Web SDK, en zal in een recentere fase beschikbaar worden gemaakt)
- Als u de **offer decisioning** de toepassingsdienst voor deze DataStream, moet u de doos voor Offer decisioning controleren. (Dit maakt deel uit van [Module 9](./../module9/offer-decisioning.md))
- Als u de **Randsegmentatie**, moet u het vakje voor de Segmentatie van de Rand controleren.
- Als u de **Aanpassingsdoelen**, moet u de doos voor de Doelen van de Aanpassing controleren.

Voor nu, is geen andere configuratie nodig voor uw DataStream.

Volgende stap: [1.3 Inleiding tot Adobe Experience Platform-gegevensverzameling](./ex3.md)

[Ga terug naar module 1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../overview.md)
