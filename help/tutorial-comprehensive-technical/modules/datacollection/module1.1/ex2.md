---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Gegevensstromen en de Inzameling van Gegevens van de Server
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Gegevensstromen en de Inzameling van Gegevens van de Server
kt: 5342
doc-type: tutorial
exl-id: e97d40b5-616d-439c-9d6b-eaa4ebf5acb0
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# 1.1.2 Edge Network, gegevensstreams en gegevensverzameling op de server

## Context

In deze oefening zult u a **Datastream** creëren. A **datastream** vertelt de servers van Adobe Edge waar te om de gegevens te verzenden nadat het door Web SDK wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

De gegevensstromen worden altijd geleid in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan de gegevensinzameling van Adobe Experience Platform met Web SDK. Zelfs wanneer u Web SDK met een niet-Adobe oplossing van het markeringsbeheer uitvoert, zult u nog uw DataStream in het gebruikersinterface van de Inzameling van Gegevens van Adobe Experience Platform moeten creëren.

U zult SDK van het Web op browser in de volgende oefening uitvoeren. Het zal u dan duidelijker zijn hoe de gegevens die worden verzameld eruit zien. Vooralsnog vertellen we alleen maar aan de DataStream waar we de gegevens moeten doorsturen.

## Een DataStream maken

In [ Aan de slag ](./../../../modules/gettingstarted/gettingstarted/ex2.md) creeerde u reeds een datastream, maar wij bespraken niet de achtergrond en de reden om van de Datstream te zijn.

Een satastream vertelt de Adobe Edge-servers waar ze de gegevens moeten verzenden nadat ze door de SDK van het web zijn verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target? De stromen van gegevens worden beheerd in het gebruikersinterface van de Gegevensverzameling van Adobe Experience Platform en zijn kritiek aan gegevensinzameling met Web SDK, ongeacht of u Web SDK via de Inzameling van Gegevens van Adobe Experience Platform uitvoert of niet.

Controleer uw **[!UICONTROL Datastream]** :

Ga naar [ https://experience.adobe.com/launch/ ](https://experience.adobe.com/launch/).

Klik op **[!UICONTROL Datastreams]** in het linkermenu.

![ klik het pictogram DataStream in de linkernavigatie ](./images/edgeconfig1.png)

Open de gegevensstroom met de naam `--aepUserLdap-- - Demo System Datastream` .

![ noem DataStream en bewaar ](./images/edgeconfig2.png)

U zult dan de details van uw gegevensstroom zien.

![ noem DataStream en bewaar ](./images/edgecfg1.png)

Klik **...** naast **Adobe Experience Platform** en klik **uitgeven**.

![ noem DataStream en bewaar ](./images/edgecfg1a.png)

Dan zie je dit. Op dit moment heb je alleen Adobe Experience Platform ingeschakeld. Uw configuratie zal gelijkaardig aan de hieronder configuratie kijken. (Afhankelijk van uw omgeving en Adobe Experience Platform-instantie kan de naam van de sandbox anders zijn.)

![ noem DataStream en bewaar ](./images/edgecfg2.png)

U moet de onderstaande velden als volgt interpreteren:

Voor deze gegevensstroom...

- Alle verzamelde gegevens worden opgeslagen in de `--aepSandboxName--` -sandbox in Adobe Experience Platform
- Alle gegevens van de Gebeurtenis van de Ervaring worden verzameld door gebrek in het dataset **Systeem van de Demo - de Dataset van de Gebeurtenis voor Website (Globale v1.1)**
- Alle gegevens van het Profiel zullen door gebrek in het dataset **Systeem van de Demo - de Dataset van het Profiel voor Website (Globale v1.1)** worden verzameld (het opnemen van profielgegevens nationaal met Web SDK wordt momenteel niet gesteund door Web SDK)
- Als u de **de toepassingsdienst van de Offer decisioning** voor deze gegevensstroom wilt gebruiken, moet u de doos voor Offer decisioning controleren. (Dit zal deel van [ Module 3.3 ](./../../../modules/ajo-b2c/module3.3/offer-decisioning.md) zijn)
- **de Segmentatie van Edge** wordt toegelaten door gebrek, zo betekent het dat het gekwalificeerde publiek bij de rand, bij opname van inkomend verkeer zal worden geëvalueerd
- Als u de **Doelen van Personalization** wilt gebruiken, moet u de doos voor de Doelen van Personalization controleren.
- 
   - Als u **Adobe Journey Optimizer** mogelijkheden in deze gegevensstroom wilt gebruiken, moet u de doos voor Adobe Journey Optimizer controleren.


Voor nu, is geen andere configuratie nodig voor uw gegevensstroom.

Volgende Stap: [ 1.1.3 Inleiding aan de Inzameling van Gegevens van Adobe Experience Platform ](./ex3.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
