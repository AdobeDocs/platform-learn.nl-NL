---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Gegevensstromen en de Inzameling van Gegevens van de Server
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Gegevensstromen en de Inzameling van Gegevens van de Server
kt: 5342
doc-type: tutorial
source-git-commit: 7d2f5f842559b2d6d9f115f3993268a4b36a0fe0
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# 1.1.2 Edge Network, gegevensstreams en gegevensverzameling op de server

## Context

In deze oefening zult u a **Datastream** creëren. A **Datastream** vertelt de servers van Adobe Edge waar te om de gegevens te verzenden nadat het door Web SDK wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

De gegevensstromen worden altijd geleid in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan de gegevensinzameling van Adobe Experience Platform met Web SDK. Zelfs wanneer u Web SDK met een niet-Adobe oplossing van het markeringsbeheer uitvoert, zult u nog uw DataStream in het gebruikersinterface van de Inzameling van Gegevens van Adobe Experience Platform moeten creëren.

U zult SDK van het Web op browser in de volgende oefening uitvoeren. Het zal u dan duidelijker zijn hoe de gegevens die worden verzameld eruit zien. Vooralsnog vertellen we alleen maar aan de DataStream waar we de gegevens moeten doorsturen.

## Een DataStream maken

In [ Uitoefening 0.2 ](./../../../modules/gettingstarted/gettingstarted/ex2.md) creeerde u reeds een Datastream, maar wij bespraken niet de achtergrond en de reden voor zijn van de Datastream.

Een DataStream vertelt de servers van Adobe Edge waar te om de gegevens te verzenden nadat het door het Web SDK wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target? De stromen van gegevens worden beheerd in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan de gegevensinzameling van het Platform met Web SDK, ongeacht of u Web SDK via de Inzameling van Gegevens van Adobe Experience Platform uitvoert.

Controleer uw **[!UICONTROL Datastream]** :

Ga naar [ https://experience.adobe.com/launch/ ](https://experience.adobe.com/launch/).

Klik op **[!UICONTROL Datastreams]** of **[!UICONTROL Datastreams (Beta)]** in het linkermenu.

![ klik het pictogram DataStream in de linkernavigatie ](./images/edgeconfig1.png)

Zoek naar uw DataStream, die `--demoProfileLdap-- - Demo System Datastream` wordt genoemd.

![ noem DataStream en bewaar ](./images/edgeconfig2.png)

Dan zie je de details van je DataStream.

![ noem DataStream en bewaar ](./images/edgecfg1.png)

Klik **...** naast **Adobe Experience Platform** en klik **uitgeven**.

![ noem DataStream en bewaar ](./images/edgecfg1a.png)

Dan zie je dit. Op dit moment heb je alleen Adobe Experience Platform ingeschakeld. Uw configuratie zal gelijkaardig aan de hieronder configuratie kijken. (Afhankelijk van uw omgeving en Adobe Experience Platform-instantie kan de naam van de sandbox anders zijn.)

![ noem DataStream en bewaar ](./images/edgecfg2.png)

U moet de onderstaande velden als volgt interpreteren:

Voor deze gegevensstroom...

- Alle verzamelde gegevens worden opgeslagen in de `--aepSandboxId--` -sandbox in Adobe Experience Platform
- Alle gegevens van de Gebeurtenis van de Ervaring worden verzameld door gebrek in het dataset **Systeem van de Demo - de Dataset van de Gebeurtenis voor Website (Globale v1.1)**
- Alle gegevens van het Profiel zullen door gebrek in het dataset **Systeem van de Manifestatie - de Dataset van het Profiel voor Website (Globale v1.1) worden verzameld** (het opnemen van profielgegevens nefend met Web SDK momenteel wordt niet gesteund nog door Web SDK, en zal in een recentere fase beschikbaar worden gemaakt)
- Als u de **de toepassingsdienst van de Offer decisioning** voor deze DataStream wilt gebruiken, moet u de doos voor Offer decisioning controleren. (Dit zal deel van [ Module 3.3 ](./../../../modules/ajo-b2c/module3.3/offer-decisioning.md) zijn)
- Als u de **Segmentatie van Edge** wilt gebruiken, moet u de doos voor de Segmentatie van Edge controleren.
- Als u de **Doelen van Personalization** wilt gebruiken, moet u de doos voor de Doelen van Personalization controleren.

Voor nu, is geen andere configuratie nodig voor uw DataStream.

Volgende Stap: [ 1.1.3 Inleiding aan de Inzameling van Gegevens van Adobe Experience Platform ](./ex3.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
