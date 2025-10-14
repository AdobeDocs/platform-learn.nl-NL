---
title: Aan de slag - Maak uw gegevensstroom
description: Aan de slag - Maak uw gegevensstroom
kt: 5342
doc-type: tutorial
exl-id: b3e6f66d-fb7a-43ab-aedb-45141af76d3e
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# Uw gegevensstroom maken

Ga naar [&#x200B; https://experience.adobe.com/#/data-collection/ &#x200B;](https://experience.adobe.com/#/data-collection/).

![&#x200B; DSN &#x200B;](./images/launchprop.png)

Klik in het linkermenu op **[!UICONTROL Tags]** . Na de vorige exercitie hebt u nu drie eigenschappen voor gegevensverzameling: een voor het web, een voor mobiel en een voor de CX-app.

![&#x200B; DSN &#x200B;](./images/launchprop1.png)

Deze eigenschappen zijn bijna klaar om te worden gebruikt, maar alvorens u gegevens kunt beginnen te verzamelen gebruikend deze eigenschappen moet u opstelling een gegevensstroom. U zult meer informatie rond het concept krijgen wat een gegevensstroom is en wat het in een recentere oefening in de module van de Inzameling van Gegevens betekent.

Voer voorlopig deze stappen uit.

## Uw gegevensstroom maken voor webgegevensverzameling

Klik op **[!UICONTROL Datastreams]**.

![&#x200B; klik het pictogram van de Configuratie van Edge in de linkernavigatie &#x200B;](./images/edgeconfig1a.png)

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn.

![&#x200B; klik het pictogram van de Configuratie van Edge in de linkernavigatie &#x200B;](./images/edgeconfig1b.png)

Klik op **[!UICONTROL New Datastream]**.

![&#x200B; klik het pictogram van de Configuratie van Edge in de linkernavigatie &#x200B;](./images/edgeconfig1.png)

Voer `--aepUserLdap-- - Demo System Datastream` in voor de **[!UICONTROL Name]** en voor de optionele beschrijving. Voor **het Schema van de Toewijzing**, uitgezochte **Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1)**. Klik **sparen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig2.png)

Dan zie je dit. Klik **toevoegen de Dienst**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig3.png)

Selecteer de service **[!UICONTROL Adobe Experience Platform]** , waarmee extra velden worden weergegeven. Dan zie je dit.

Voor de Dataset van de Gebeurtenis, uitgezochte **Systeem van de Demo - de Dataset van de Gebeurtenis voor Website (Globale v1.1)** en voor de Dataset van de Dataset van het Profiel, uitgezochte **demosysteem - de Dataset van het Profiel voor Website (Globale v1.1)**. Klik **sparen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig4.png)

Dit zie je nu.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig5.png)

Dat is het voor nu. In [&#x200B; Module 1.1 &#x200B;](./../../../modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md) zult u meer over SDK van het Web leren en hoe te om elk van zijn mogelijkheden te vormen.

Klik in het linkermenu op **[!UICONTROL Tags]** .

Filter de zoekresultaten om de eigenschappen van de gegevensverzameling te bekijken. Open het bezit voor **Web** door het te klikken.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig10a.png)

Dan zie je dit. Klik **Uitbreidingen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig11.png)

Eerst, klik de uitbreiding van SDK van het Web van Adobe Experience Platform en klik dan **vormen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig12.png)

Dan zie je dit. Heb een blik bij het **menu van Gegevensstromen** en zorg ervoor de juiste zandbak wordt geselecteerd, die in u geval `--aepSandboxName--` zou moeten zijn.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig12a.png)

Open **Datastreams** dropdown, en selecteer de Datasstream u vroeger creeerde.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig13.png)

Zorg ervoor om uw **Datastream** in alle drie verschillende milieu&#39;s te hebben geselecteerd. Dan, klik **sparen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig14.png)

Ga naar **het Publiceren Stroom**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig15.png)

Klik **...** voor **Hoofd**, dan klik **uitgeven**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig16.png)

Klik **toevoegen Alle Gewijzigde Middelen** en klik dan **sparen &amp; bouwt voor Ontwikkeling**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig17.png)

Uw veranderingen worden nu gepubliceerd en zullen in een paar notulen klaar zijn, waarna zult u de groene punt naast **Hoofd** zien.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig17a.png)

## Uw gegevensstroom maken voor mobiele gegevensverzameling

Ga naar [&#x200B; https://experience.adobe.com/#/data-collection/ &#x200B;](https://experience.adobe.com/#/data-collection/).

Klik op **[!UICONTROL Datastreams]**.

![&#x200B; klik het pictogram DataStream in de linkernavigatie &#x200B;](./images/edgeconfig1a.png)

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn.

![&#x200B; klik het pictogram van de Configuratie van Edge in de linkernavigatie &#x200B;](./images/edgeconfig1b.png)

Klik op **[!UICONTROL New Datastream]**.

![&#x200B; klik het pictogram DataStream in de linkernavigatie &#x200B;](./images/edgeconfig1.png)

Voer `--aepUserLdap-- - Demo System Datastream (Mobile)` in voor de **[!UICONTROL Friendly Name]** en voor de optionele beschrijving. Voor **het Schema van de Toewijzing**, uitgezochte **Systeem van de Demo - het Schema van de Gebeurtenis voor Mobiele Toepassing (Globale v1.1)**. Klik **sparen**.

Klik op **[!UICONTROL Save]**.

![&#x200B; noem DataStream en bewaar &#x200B;](./images/edgeconfig2m.png)

Dan zie je dit. Klik **toevoegen de Dienst**.

![&#x200B; noem DataStream en bewaar &#x200B;](./images/edgeconfig3m.png)

Selecteer de service **[!UICONTROL Adobe Experience Platform]** , waarmee extra velden worden weergegeven. Dan zie je dit.

Voor de Dataset van de Gebeurtenis, uitgezochte **Systeem van de Demo - de Dataset van de Gebeurtenis voor Mobiele App (Globale v1.1)** en voor de Dataset van de Dataset van het Profiel, uitgezochte **Systeem van de Demo - de Dataset van het Profiel voor Mobiele App (Globale v1.1)**. Klik **sparen**.

![&#x200B; noem de Configuratie DataStream en sparen &#x200B;](./images/edgeconfig4m.png)

Dan zie je dit.

![&#x200B; noem de Configuratie DataStream en sparen &#x200B;](./images/edgeconfig5m.png)

Uw datastream kan nu worden gebruikt in uw Adobe Experience Platform Data Collection Client-eigenschap voor mobiele apparatuur.

Ga naar **Markeringen** en filter de onderzoeksresultaten om uw eigenschappen van de Inzameling van Gegevens te zien. Open het bezit voor **Mobiel** door het te klikken.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig10am.png)

Dan zie je dit. Klik **Uitbreidingen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig11m.png)

Klik de **Edge Network van Adobe Experience Platform** uitbreiding en klik dan **vormen**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig12m.png)

Dan zie je dit. U moet nu de juiste sandbox en datastream selecteren die u net hebt geconfigureerd. De sandbox die moet worden gebruikt, is `--aepSandboxName--` en de datastream wordt `--aepUserLdap-- - Demo System Datastream (Mobile)` genoemd.

Voor het **domein van de Edge Network**, gelieve het standaarddomein te gebruiken.

Klik **sparen** om uw veranderingen te bewaren.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig13m.png)

Ga naar **het Publiceren Stroom**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig15m.png)

Klik **...** naast **Hoofd**, dan klik **uitgeven**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig16m.png)

Klik **toevoegen Alle Gewijzigde Middelen**, dan klik **sparen &amp; bouwt voor Ontwikkeling**.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig17m.png)

Uw veranderingen worden nu gepubliceerd en zullen in een paar notulen klaar zijn, waarna zult u de groene punt naast **Hoofd** zien.

![&#x200B; noem de Configuratie van Edge en bewaar &#x200B;](./images/edgeconfig17ma.png)

Volgende Stap: [&#x200B; gebruik de website &#x200B;](./ex4.md)

[Terug naar Aan de slag](./getting-started.md)

[Terug naar alle modules](./../../../overview.md)
