---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - vereisten van het Schema XDM in Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# 1.1.7 XDM-schemavereisten in Adobe Experience Platform

Om ervoor te zorgen dat Web SDK en alloy.js gegevens in Adobe Experience Platform kunnen opnemen, is er een vereiste dat een specifieke XDM Mixin deel moet uitmaken van het XDM-schema in Adobe Experience Platform.

Ga naar [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform) en login.

![ Debugger AEP ](./images/exp1.png)

Na het programma openen, selecteer de aangewezen zandbak door de tekst **Prod van de Productie** in de blauwe lijn bovenop uw scherm te klikken. Selecteer de sandbox `--aepSandboxId--` .

Na het selecteren van uw zandbak, zult u de het schermverandering zien en nu bent u in uw zandbak.

![ Debugger AEP ](./images/exp2.png)

In het linkermenu, ga naar **Schema&#39;s** en open het **Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1)** Schema.

![ Debugger AEP ](./images/exp3.png)

Op dat Schema, zult u zien dat de de ErvaringEvent Mixin van SDK van het Web van het Web van AEP **is toegevoegd.** Deze veldgroep voegt alle minimaal vereiste velden toe aan het schema. Elk schema van de Gebeurtenis van de Ervaring in Adobe Experience Platform dat door Web SDK zal worden gebruikt zal altijd vereisen dat de gebiedsgroep deel van het Schema uitmaakt.

![ Debugger AEP ](./images/exp4.png)

In [ Module 1.2 ](./../module1.2/data-ingestion.md) zult u leren hoe te om gebiedsgroepen aan schema&#39;s toe te voegen.

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
