---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Werk uw DataStream bij om gegevens beschikbaar te maken voor uw Adobe Experience Platform Data Collection Server-eigenschap
description: Werk uw DataStream bij om gegevens ter beschikking te stellen van uw bezit van de Server van de Gegevensverzameling van Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: f4bb0673-d553-4027-8bfd-53d2608efaf5
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 2.5.2 Werk uw DataStream bij om gegevens ter beschikking te stellen van uw Adobe Experience Platform-eigenschap van de Server van de Gegevensverzameling

## Uw DataStream bijwerken

In [ Aan de slag ](./../../../getting-started/gettingstarted/ex2.md), creeerde u uw eigen **[!UICONTROL Datastream]**. Vervolgens hebt u de naam `--aepUserLdap-- - Demo System Datastream` gebruikt.

In deze oefening, moet u dat **[!UICONTROL Datastream]** vormen om met uw **bezit van de Server van de Inzameling van Gegevens te werken**.

Om dat te doen, ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). Dan zie je dit. Klik in het linkermenu op **[!UICONTROL Datastreams]** .

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn.

![ klik het pictogram van de Configuratie van Edge in de linkernavigatie ](./images/edgeconfig1b.png)

Zoek naar uw **[!UICONTROL Datastream]**, die `--aepUserLdap-- - Demo System Datastream` wordt genoemd. Klik op de **[!UICONTROL Datastream]** om deze te openen.

![ WebSDK ](./images/websdk0.png)

Dan zie je dit. Klik op **[!UICONTROL + Add Service]**.

![ WebSDK ](./images/websdk3.png)

Selecteer de dienst **Gebeurtenis door:sturen**. Hier ziet u nog 2 andere instellingen. Selecteer de eigenschap Event Forwarding, die u in de vorige exercitie hebt gemaakt en die de naam `--aepUserLdap-- - Demo System (DD/MM/YYYY) (Edge)` heeft. Dan selecteer **Ontwikkeling** onder **Milieu**. Klik **sparen**.

![ WebSDK ](./images/websdk4.png)

Uw gegevensstroom is nu bijgewerkt en klaar voor gebruik.

![ WebSDK ](./images/websdk8a.png)

Uw gegevensstroom is nu klaar om met uw **[!DNL Event Forwarding property]** te werken.

## Volgende stappen

Ga naar [ 2.5.3 creeer en vorm een douane webhaak ](./ex3.md){target="_blank"}

Ga terug naar [ Verbindingen van Real-Time CDP: Gebeurtenis door:sturen ](./aep-data-collection-ssf.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
