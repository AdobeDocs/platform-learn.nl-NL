---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Datastreams en de Inzameling van Gegevens van de Server
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - Edge Network, Datastreams en de Inzameling van Gegevens van de Server
kt: 5342
doc-type: tutorial
exl-id: f805b2a6-c813-4734-8a78-f8588ecd0683
source-git-commit: 31466040336580e9e4b2308801347dc387be4da5
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# 1.1.2 Edge Network, gegevensstreams en gegevensverzameling op de server

## Context

In deze oefening zult u a **datastream** creëren. A **datastream** vertelt de servers van het Netwerk van de Rand van Adobe waar te om de gegevens te verzenden nadat het door SDK van het Web wordt verzameld. Wilt u de gegevens bijvoorbeeld naar Adobe Experience Platform verzenden? Adobe Analytics? Adobe Audience Manager? Adobe Target?

De stromen van gegevens worden altijd geleid in het gebruikersinterface van de Gegevensverzameling van Experience Platform en zijn kritiek aan de gegevensinzameling van Experience Platform met [ SDK van het Web ](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home). Zelfs wanneer u het Web SDK met een niet-Adobe oplossing van het markeringsbeheer uitvoert, moet u nog een gegevensstroom tot stand brengen.

U zult het Web SDK op browser in de volgende oefening uitvoeren. Het zal u dan duidelijker zijn hoe de gegevens die worden verzameld eruit zien. Vooralsnog vertellen we alleen maar aan de datastream waar we de gegevens moeten doorsturen.

## Een gegevensstroom maken

In [ Begonnen ](./../../../../modules/getting-started/gettingstarted/ex2.md) u creeerde reeds een datastream, maar wij bespraken niet de achtergrond en de reden waarvoor u het creeerde.

A [ datastream ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview) vertelt de servers van Edge Network waar te om de gegevens te verzenden nadat het door het Web SDK wordt verzameld. Zie de documentatie voor [ toevoegend de diensten aan een datastream ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure#add-services) voor volledige details over waar u uw gegevens door de datastream kunt verzenden.

De stromen van gegevens worden beheerd in het gebruikersinterface van de Gegevensverzameling van Experience Platform en zijn kritiek aan gegevensinzameling met Web SDK, ongeacht of u het Web SDK via de Inzameling van Gegevens van Adobe Experience Platform uitvoert.

Controleer uw **[!UICONTROL datastream]** :

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
- Alle gegevens van het Profiel zullen door gebrek in het dataset **Systeem van de Manifestatie - de Dataset van het Profiel voor Website (Globale v1.1) worden verzameld** (het opnemen van profielgegevens nefend met Web SDK wordt momenteel niet gesteund door Web SDK)
- **de Segmentatie van Edge** wordt toegelaten door gebrek, zo betekent het dat het gekwalificeerde publiek bij de rand, bij opname van inkomend verkeer zal worden geëvalueerd
- Als u [ verpersoonlijkingsbestemmingen ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview) wilt gebruiken, controleer de doos voor **Doelen van Personalization**.
- Als u **mogelijkheden van Adobe Journey Optimizer** in deze datastream wilt gebruiken, moet u de doos voor **Adobe Journey Optimizer** controleren.

Voor nu, is geen andere configuratie nodig voor uw gegevensstroom.

## Volgende stappen

Ga naar [ 1.1.3 Inleiding aan de Inzameling van Gegevens van Adobe Experience Platform ](./ex3.md){target="_blank"}

Ga terug naar [ Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de de markeringsuitbreiding van SDK van het Web ](./data-ingestion-launch-web-sdk.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
