---
title: Gegevens van Google Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector
description: Gegevens van Google Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: c9c28b5a-d158-49fa-9533-1a295876f6c4
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# 12. Gegevens van Google Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector

**Auteurs: [Victor de la Iglesia](https://www.linkedin.com/in/victordelaiglesia/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module stelt u uw eigen exemplaar van het Google Cloud-Platform in, laadt u voorbeeldgegevens in het Google Cloud-Platform en gebruikt u vervolgens de BigQuery Source Connector om die gegevens van het Google Cloud-Platform in Adobe Experience Platform in te voeren. Tot slot zult u Customer Journey Analytics gebruiken om die gegevens te visualiseren.

Bronconnectors in Adobe Experience Platform maken het proces om gegevens in Adobe Experience Platform in te voeren gemakkelijk. Google BigQuery is een van de reeds beschikbare connectors. Dankzij Adobe Experience Platform en de BigQuery Source Connector kunnen we nu Google Analytics gegevens naar Analysis Workspace brengen in Customer Journey Analytics.

Bovendien kunnen wij die gegevens van Google Analytics verrijken door het met andere gegevensbronnen zoals CRM, het Centrum van de Vraag of gegevens van de Loyalty binnen Customer Journey Analytics aan te sluiten.

## Leerdoelen

- Bekend worden met het Google Cloud-Platform en de BigQuery-gebruikersinterface
- Gegevens van Google Analytics opnemen in Adobe Experience Platform
- Gebruik Customer Journey Analytics om de gegevens van Google Analytics te analyseren
- Gegevens van Google Analytics verrijken met offlinegegevens

## Vereisten

- Enige kennis van Customer Journey Analytics verdient de voorkeur, maar is niet vereist
- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot Customer Journey Analytics
- Toegang tot Google Cloud-Platform en Google BigQuery
- **Deze middelen downloaden**:
   - [JSON - Voorbeeldgegevens: Loyaliteitsgegevens](./../../assets/json/bqLoyalty.json)

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem16.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[12.1 Een Google Cloud Platform-account maken](./ex1.md)

Maak uw Google Cloud Platform-account.

[12.2 Maak uw eerste query in BigQuery](./ex2.md)

Leer hoe u BigQuery gebruikt om de gegevens voor te bereiden voor het laden in het Platform.

[12.3 GCP en BigQuery aansluiten op Adobe Experience Platform](./ex3.md)

Leer hoe u de bronaansluiting in Adobe Experience Platform instelt.

[12.4 Gegevens laden van BigQuery naar Adobe Experience Platform](./ex4.md)

Leer hoe te om de Bron BigQuery schakelaar in Adobe Experience Platform te vormen om uw Gegevens van Google Analytics in te voeren.

[12.5 Gegevens van Google Analytics analyseren met behulp van Customer Journey Analytics](./ex5.md)

Leer hoe u Google Analytics-gegevens analyseert in Customer Journey Analytics en deze combineert met Loyalty-gegevens.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
