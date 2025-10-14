---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 3fc4a1d6-4130-464e-98c0-5b9cac8051a0
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# 1.1.7 XDM-schemavereisten in Adobe Experience Platform

Om ervoor te zorgen dat de SDK van het Web gegevens in Adobe Experience Platform kan opnemen, is er een vereiste voor een specifieke mix XDM om deel uit te maken van het XDM-schema in Adobe Experience Platform.

Ga naar [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform) en login.

![&#x200B; Debugger AEP &#x200B;](./images/exp1.png)

Na het programma openen, selecteer de aangewezen zandbak door de tekst **Prod van de Productie** in de blauwe lijn bovenop uw scherm te klikken. Selecteer de sandbox `--aepSandboxName--` .

Na het selecteren van uw zandbak, zult u de het schermverandering zien en nu bent u in uw zandbak.

![&#x200B; Debugger AEP &#x200B;](./images/exp2.png)

In het linkermenu, ga naar **Schema&#39;s** en open het **Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1)** Schema.

![&#x200B; Debugger AEP &#x200B;](./images/exp3.png)

In dat schema, zult u zien dat de het gebiedsgroep van de gebiedsgroep **AEP Web SDK ExperienceEvent** is toegevoegd. Deze veldgroep voegt alle minimaal vereiste velden toe aan het schema. Elk schema van de Gebeurtenis van de Ervaring in Adobe Experience Platform dat door Web SDK zal worden gebruikt zal altijd vereisen dat de gebiedsgroep deel van het Schema uitmaakt.

![&#x200B; Debugger AEP &#x200B;](./images/exp4.png)

In [&#x200B; Module 1.2 &#x200B;](./../module1.2/data-ingestion.md) zult u leren hoe te om gebiedsgroepen aan schema&#39;s toe te voegen.

Volgende Stap: [&#x200B; Samenvatting en voordelen &#x200B;](./summary.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
