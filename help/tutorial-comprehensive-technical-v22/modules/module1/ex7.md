---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 8e17129c-633d-45bd-aa70-78cc3d3a2108
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# 1.7 XDM-schemavereisten in Adobe Experience Platform

Om ervoor te zorgen dat Web SDK en alloy.js gegevens in Adobe Experience Platform kunnen opnemen, is er een vereiste dat een specifieke XDM Mixin deel moet uitmaken van het XDM-schema in Adobe Experience Platform.

Ga naar [https://experience.adobe.com/platform](https://experience.adobe.com/platform) en aanmelden.

![AEP-foutopsporing](./images/exp1.png)

Nadat u zich hebt aangemeld, selecteert u de desbetreffende sandbox door op de tekst te klikken **Productieproduct** in de blauwe lijn boven op het scherm. De sandbox selecteren `--aepSandboxId--`.

Na het selecteren van uw zandbak, zult u de het schermverandering zien en nu bent u in uw zandbak.

![AEP-foutopsporing](./images/exp2.png)

Ga in het linkermenu naar **Schemas** en opent u de **Demosysteem - Gebeurtenisschema voor website (Global v1.1)** Schema.

![AEP-foutopsporing](./images/exp3.png)

Op dat Schema ziet u dat de veldgroep **AEP Web SDK ExperienceEvent Mixin** is toegevoegd. Deze veldgroep voegt alle minimaal vereiste velden toe aan het schema. Elk schema van de Gebeurtenis van de Ervaring in Adobe Experience Platform dat door Web SDK zal worden gebruikt zal altijd vereisen dat de gebiedsgroep deel van het Schema uitmaakt.

![AEP-foutopsporing](./images/exp4.png)

In [Module 2](./../module2/data-ingestion.md) u zult leren hoe te om gebiedsgroepen aan schema&#39;s toe te voegen.

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../overview.md)
