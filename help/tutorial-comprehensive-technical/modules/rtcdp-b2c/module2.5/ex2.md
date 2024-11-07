---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Werk uw DataStream bij om gegevens beschikbaar te maken voor uw Adobe Experience Platform Data Collection Server-eigenschap
description: Werk uw DataStream bij om gegevens ter beschikking te stellen van uw bezit van de Server van de Gegevensverzameling van Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 2.5.2 Werk uw DataStream bij om gegevens ter beschikking te stellen van uw Adobe Experience Platform-eigenschap van de Server van de Gegevensverzameling

## 2.5.2.1 De gegevensstroom bijwerken

In [ Uitoefening 0.2 ](./../../gettingstarted/gettingstarted/ex2.md), creeerde u uw eigen **[!UICONTROL Datastream]**. Vervolgens hebt u de naam `--demoProfileLdap-- - Demo System Datastream` gebruikt.

In deze oefening, moet u dat **[!UICONTROL Datastream]** vormen om met uw **[!DNL Data Collection Server property]** te werken.

Om dat te doen, ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). Dan zie je dit. Klik in het linkermenu op **[!UICONTROL Datastreams]** .

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxId--` moet zijn.

![ klik het pictogram van de Configuratie van Edge in de linkernavigatie ](./images/edgeconfig1b.png)

Zoek naar uw **[!UICONTROL Datastream]**, die `--demoProfileLdap-- - Demo System Datastream` wordt genoemd. Klik op de **[!UICONTROL Datastream]** om deze te openen.

![ WebSDK ](./images/websdk0.png)

Dan zie je dit. Klik op **[!UICONTROL + Add Service]**.

![ WebSDK ](./images/websdk3.png)

Selecteer de dienst **Gebeurtenis door:sturen**. Hier ziet u nog 2 andere instellingen. Selecteer de eigenschap Event Forwarding, die u in de vorige exercitie hebt gemaakt en die de naam `--demoProfileLdap-- - Demo System (DD/MM/YYYY) (Edge)` heeft. Dan selecteer **Ontwikkeling** onder **Milieu**. Klik **sparen**.

![ WebSDK ](./images/websdk4.png)

Uw gegevensstroom is nu bijgewerkt en klaar voor gebruik.

![ WebSDK ](./images/websdk8a.png)

Uw gegevensstroom is nu klaar om met uw **[!DNL Event Forwarding property]** te werken.

Volgende Stap: [ 2.5.3 creeer en vorm een douane webhaak ](./ex3.md)

[Ga terug naar Module 2.5](./aep-data-collection-ssf.md)

[Terug naar alle modules](./../../../overview.md)
