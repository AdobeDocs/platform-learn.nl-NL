---
title: Aan de slag - Maak uw DataStream
description: Aan de slag - Maak uw DataStream
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: c967b01e-9a0b-4a74-b536-706db0cb237f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# 0.3 Maak uw gegevensstroom

Ga naar [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Na de vorige oefening, hebt u nu twee eigenschappen van de Inzameling van Gegevens: één voor het web en één voor mobiel.

![DSN](./images/launchprop.png)

Deze eigenschappen zijn bijna klaar om te worden gebruikt, maar alvorens u gegevens kunt beginnen te verzamelen gebruikend deze eigenschappen moet u opstelling een gegevensstroom. U zult meer informatie over het concept krijgen wat een gegevensstroom is en wat het in Uitoefening 1.2 betekent.

Voer voorlopig deze stappen uit.

## 0.3.1 Maak uw DataStream voor het Web

Klikken **[!UICONTROL DataStreams]** of **[!UICONTROL Gegevensstromen (bèta)]**.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1a.png)

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox die u wilt instellen als `--aepSandboxId--`.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1b.png)

Klikken **[!UICONTROL Nieuwe DataStream]**.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1.png)

Voor de **[!UICONTROL Vriendschappelijke naam]** en voor de facultatieve beschrijving `--demoProfileLdap-- - Demo System Datastream`. Selecteer bij Gebeurtenisschema de optie **Demosysteem - Gebeurtenisschema voor website (Global v1.1)**. Klikken **Opslaan**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig2.png)

Dan zie je dit. Klikken **Service toevoegen**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig3.png)

Selecteer de service **[!UICONTROL Adobe Experience Platform]**, die extra velden beschikbaar maakt. Dan zie je dit.

Selecteer bij Gebeurtenisgegevens de optie **Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1)** en voor Profielgegevensset selecteert u **Demosysteem - profielgegevensset voor website (Global v1.1)**. Klikken **Opslaan**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig4.png)

Dit zie je nu.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig5.png)

Dat is het voor nu. In [Module 1](./../module1/data-ingestion-launch-web-sdk.md) u zult meer over Web SDK leren en hoe te om elk van zijn mogelijkheden te vormen.

Klik in het linkermenu op **[!UICONTROL Tags]**.

Filter de onderzoeksresultaten om uw twee eigenschappen van de Inzameling van Gegevens te zien. De eigenschap openen voor **Web** door erop te klikken.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig10a.png)

Dan zie je dit. Klikken **Extensies**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig11.png)

Klik in de extensie Adobe Experience Platform Web SDK op **Configureren**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig12.png)

Dan zie je dit. Voor **DataStreams**, wordt er momenteel een dummywaarde van 1 weergegeven. U moet nu op de knop **Kiezen uit lijst** keuzerondje. Selecteer in de vervolgkeuzelijst de DataStream die u eerder hebt gemaakt.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig13.png)

Zorg ervoor dat u de optie **DataStream**. TIP: U kunt de resultaten in de vervolgkeuzelijst eenvoudig filteren door uw `--demoProfileLdap--`.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig14.png)

Omlaag schuiven totdat u ziet **Gegevensverzameling**. Controleer of het selectievakje voor **Klikgegevensverzameling inschakelen** is niet ingeschakeld. Klikken **Opslaan** om uw wijzigingen op te slaan.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig14a.png)

Ga naar **Publishing Flow**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig15.png)

Klik op de knop **...** for **Hoofd** en klik vervolgens op **Bewerken**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig16.png)

Klikken **Alle gewijzigde bronnen toevoegen** en klik vervolgens op **Opslaan en bouwen voor ontwikkeling**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig17.png)

Uw wijzigingen worden nu gepubliceerd en zijn over een paar minuten klaar.

## 0.3.2 Maak uw gegevensstroom voor mobiele apparaten

Ga naar [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/).

Klikken **[!UICONTROL DataStreams]** of **[!UICONTROL Gegevensstromen (bèta)]**.

![Klik op het pictogram DataStream in de linkernavigatie](./images/edgeconfig1a.png)

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox die u wilt instellen als `--aepSandboxId--`.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1b.png)

Klikken **[!UICONTROL Nieuwe DataStream]**.

![Klik op het pictogram DataStream in de linkernavigatie](./images/edgeconfig1.png)

Voor de **[!UICONTROL Vriendschappelijke naam]** en voor de facultatieve beschrijving `--demoProfileLdap-- - Demo System Datastream (Mobile)`. Selecteer bij Gebeurtenisschema de optie **Demosysteem - Gebeurtenisschema voor mobiele app (Global v1.1)**. Klikken **Opslaan**.

Klikken **[!UICONTROL Opslaan]**.

![Geef de gegevensstroom een naam en sla deze op](./images/edgeconfig2m.png)

Dan zie je dit. Klikken **Service toevoegen**.

![Geef de gegevensstroom een naam en sla deze op](./images/edgeconfig3m.png)

Selecteer de service **[!UICONTROL Adobe Experience Platform]**, die extra velden beschikbaar maakt. Dan zie je dit.

Selecteer bij Gebeurtenisgegevens de optie **Demosysteem - Dataset voor gebeurtenissen voor mobiele app (Global v1.1)** en voor Profielgegevensset selecteert u **Demosysteem - profielgegevensset voor mobiele app (Global v1.1)**. Klikken **Opslaan**.

![Noem de Configuratie DataStream en sparen](./images/edgeconfig4m.png)

Dan zie je dit.

![Noem de Configuratie DataStream en sparen](./images/edgeconfig5m.png)

Uw DataStream is nu klaar om in uw bezit van de Cliënt van de Inzameling van Gegevens van Adobe Experience Platform voor Mobiel te worden gebruikt.

Ga naar **Tags** en filtert de zoekresultaten om uw twee eigenschappen van de Gegevensverzameling te zien. De eigenschap openen voor **Mobiel** door erop te klikken.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig10am.png)

Dan zie je dit. Klikken **Extensies**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig11m.png)

Op de **Adobe Experience Platform Edge Network** extensie, klikken **Configureren**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig12m.png)

Dan zie je dit. U moet nu de juiste sandbox en datastream selecteren die u net hebt geconfigureerd. De sandbox die moet worden gebruikt, is `--aepSandboxId--` en de gegevensstroom wordt aangeroepen `--demoProfileLdap-- - Demo System Datastream (Mobile)`.

Voor de **Edge Network-domein** gebruikt u het standaarddomein dat **edge.adobedc.net**.

Klikken **Opslaan** om uw wijzigingen op te slaan.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig13m.png)

Ga naar **Publishing Flow**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig15m.png)

Klik op de knop **...** naast **Hoofd** en klik vervolgens op **Bewerken**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig16m.png)

Klikken **Alle gewijzigde bronnen toevoegen** en klik vervolgens op **Opslaan en bouwen voor ontwikkeling**.

![Geef de Edge-configuratie een naam en sla deze op](./images/edgeconfig17m.png)

Uw wijzigingen worden nu gepubliceerd en zijn over een paar minuten klaar.

Volgende stap: [0.4 De website gebruiken](./ex4.md)

[Ga terug naar module 0](./getting-started.md)

[Terug naar alle modules](./../../overview.md)