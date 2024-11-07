---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 1.1.6 Adobe Target implementeren

## 1.1.6.1 Werk uw DataStream bij om Adobe Target te gebruiken

Als u gegevens die door Web SDK worden verzameld naar Adobe Target wilt verzenden en Adobe Target een antwoord wilt geven met een persoonlijke ervaring voor elke klant, voert u deze stappen uit.

Ga naar [ https://experience.adobe.com/launch/ ](https://experience.adobe.com/launch/) en ga naar **Datastreams**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn. Open uw specifieke gegevensstroom, die `--aepUserLdap-- - Demo System Datastream` wordt genoemd.

![ klik het pictogram van de Configuratie van Edge in de linkernavigatie ](./images/edgeconfig1b.png)

Dan zie je dit. Om Adobe Target toe te laten, klik **+ voeg de Dienst** toe.

![ Debugger AEP ](./images/aa2.png)

Dan zie je dit. Selecteer de dienst **Adobe Target**, waarna u naar keuze extra informatie kunt verstrekken. Op dit ogenblik, is er geen behoefte om dit te bewaren, zo klik **annuleert**.

![ Debugger AEP ](./images/at1.png)

Volgende Stap: [ 1.1.7 vereisten van het Schema XDM in Adobe Experience Platform ](./ex7.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
