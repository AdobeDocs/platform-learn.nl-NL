---
title: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web - voer Adobe Target uit
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 4aee8ae2-38ca-49a3-8f1b-57713d16f5b5
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# 1.6 Adobe Target implementeren

## 1.6 Uw DataStream bijwerken voor gebruik van Adobe Target

Als u gegevens die door Web SDK worden verzameld naar Adobe Target wilt verzenden en Adobe Target een antwoord wilt geven met een persoonlijke ervaring voor elke klant, voert u deze stappen uit.

Ga naar [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) en ga naar **DataStreams**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox die u wilt instellen als `--aepSandboxId--`. Open uw specifieke gegevensstroom, die genoemd wordt `--demoProfileLdap-- - Demo System Datastream`.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1b.png)

Dan zie je dit. Als u Adobe Target wilt inschakelen, klikt u op **+Service toevoegen**.

![AEP-foutopsporing](./images/aa2.png)

Dan zie je dit. Selecteer de service **Adobe Target**, waarna u desgewenst aanvullende informatie kunt verstrekken. Op dit moment is het niet nodig dit op te slaan, dus klikt u op **Annuleren**.

![AEP-foutopsporing](./images/at1.png)

Volgende stap: [1.7 XDM-schemavereisten in Adobe Experience Platform](./ex7.md)

[Ga terug naar module 1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../overview.md)
