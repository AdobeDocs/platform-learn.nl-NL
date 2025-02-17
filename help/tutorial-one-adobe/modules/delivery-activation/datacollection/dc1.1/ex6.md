---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
kt: 5342
doc-type: tutorial
exl-id: 31cdde2f-011d-442d-8e47-15a318a6c89d
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# 1.1.6 Adobe Target implementeren

## Uw gegevensstroom bijwerken naar Adobe Target

Als u gegevens die door Web SDK zijn verzameld naar Adobe Target wilt verzenden en Adobe Target een antwoord wilt geven met een persoonlijke ervaring voor elke klant, volgt u deze stappen.

Ga naar [ https://experience.adobe.com/launch/ ](https://experience.adobe.com/launch/) en ga naar **Datastreams**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn. Open uw specifieke gegevensstroom, die `--aepUserLdap-- - Demo System Datastream` wordt genoemd.

![ klik het pictogram van de Configuratie van Edge in de linkernavigatie ](./images/edgeconfig1b.png)

Dan zie je dit. Om Adobe Target toe te laten, klik **de Dienst** toevoegen.

![ Debugger AEP ](./images/aa2.png)

Dan zie je dit. Selecteer de dienst **Adobe Target**, waarna u naar keuze extra informatie kunt verstrekken. Klik **sparen**.

![ Debugger AEP ](./images/at1.png)

## Volgende stappen

Ga naar [ 1.1.7 vereisten van het Schema XDM in Adobe Experience Platform ](./ex7.md){target="_blank"}

Ga terug naar [ Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de de markeringsuitbreiding van SDK van het Web ](./data-ingestion-launch-web-sdk.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
