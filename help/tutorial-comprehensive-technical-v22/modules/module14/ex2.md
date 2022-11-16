---
title: Adobe Experience Platform Data Collection & Real-time Server Side Forwarding - Werk uw DataStream bij om gegevens beschikbaar te maken voor uw Adobe Experience Platform Data Collection Server-eigenschap
description: Werk uw DataStream bij om gegevens ter beschikking te stellen van uw bezit van de Server van de Gegevensverzameling van Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 0c42350c-c38a-410e-bdab-41aff6024f81
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 14.2 Werk uw DataStream bij om gegevens ter beschikking te stellen van uw Adobe Experience Platform-eigenschap van de Server van de Gegevensverzameling

## 14.2.1 Uw DataStream bijwerken

In [Oefening 0.2](./../../modules/module0/ex2.md), hebt u uw eigen **[!UICONTROL DataStream]**. Vervolgens hebt u de naam gebruikt `--demoProfileLdap-- - Demo System Datastream`.

In deze oefening, moet u dat vormen **[!UICONTROL DataStream]** om met uw **[!DNL Data Collection Server property]**.

Ga om dat te doen naar [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). Dan zie je dit. Klik in het linkermenu op **[!UICONTROL DataStreams]**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox die u wilt instellen als `--aepSandboxId--`.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1b.png)

Zoeken naar uw **[!UICONTROL DataStream]**, die `--demoProfileLdap-- - Demo System Datastream`. Klik op **[!UICONTROL DataStream]** om het te openen.

![WebSDK](./images/websdk0.png)

Dan zie je dit. Klikken **[!UICONTROL + Service toevoegen]**.

![WebSDK](./images/websdk3.png)

Selecteer de service **Gebeurtenis doorsturen**. Hier ziet u nog 2 andere instellingen. Selecteer de eigenschap Event Forwarding, die u in de vorige oefening hebt gemaakt en die een naam heeft `--demoProfileLdap-- - Demo System (DD/MM/YYYY) (Edge)`. Selecteer vervolgens **Ontwikkeling** krachtens **Omgeving**. Klikken **Opslaan**.

![WebSDK](./images/websdk4.png)

Uw gegevensstroom is nu bijgewerkt en klaar voor gebruik.

![WebSDK](./images/websdk8a.png)

Uw gegevensstroom is nu klaar om met uw **[!DNL Event Forwarding property]**.

Volgende stap: [14.3 Een aangepaste webhaak maken en configureren](./ex3.md)

[Ga terug naar module 14](./aep-data-collection-ssf.md)

[Terug naar alle modules](./../../overview.md)
