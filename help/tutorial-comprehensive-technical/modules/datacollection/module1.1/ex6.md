---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
kt: 5342
doc-type: tutorial
exl-id: 475e9a34-c80e-41e4-9660-61c79f26922d
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# 1.1.6 Adobe Target implementeren

## Uw gegevensstroom bijwerken naar Adobe Target

Als u gegevens die door Web SDK zijn verzameld naar Adobe Target wilt verzenden en Adobe Target een antwoord wilt geven met een persoonlijke ervaring voor elke klant, volgt u deze stappen.

Ga naar [&#x200B; https://experience.adobe.com/launch/ &#x200B;](https://experience.adobe.com/launch/) en ga naar **Datastreams**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox, die `--aepSandboxName--` moet zijn. Open uw specifieke gegevensstroom, die `--aepUserLdap-- - Demo System Datastream` wordt genoemd.

![&#x200B; klik het pictogram van de Configuratie van Edge in de linkernavigatie &#x200B;](./images/edgeconfig1b.png)

Dan zie je dit. Om Adobe Target toe te laten, klik **de Dienst** toevoegen.

![&#x200B; Debugger AEP &#x200B;](./images/aa2.png)

Dan zie je dit. Selecteer de dienst **Adobe Target**, waarna u naar keuze extra informatie kunt verstrekken. Klik **sparen**.

![&#x200B; Debugger AEP &#x200B;](./images/at1.png)

Volgende Stap: [&#x200B; 1.1.7 vereisten van het Schema XDM in Adobe Experience Platform &#x200B;](./ex7.md)

[Terug naar module 1.1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../../overview.md)
