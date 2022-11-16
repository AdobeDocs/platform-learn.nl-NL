---
title: Intelligente services
description: Intelligente services
kt: 5342
audience: Data Engineer, Data Architect, Data Scientist
doc-type: tutorial
activity: develop
exl-id: 99b56722-95bf-4c51-b4d6-8b5a8e5fd936
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# 5. Intelligente services

**Auteurs: [Diptiman Badajena](https://www.linkedin.com/in/diptiman-badajena-1b178019/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module leert u hoe u Adobe Experience Platform Intelligent Services kunt instellen, configureren en gebruiken.

## Leerdoelen

- Bekend worden met Adobe Experience Platform
- Vorm Schema/Dataset voor gebruik met de Intelligente Diensten
- Nieuwe Customer AI-instantie maken
- Scoredashboard en segmentatie

## Vereisten

- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem5.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--module10sandbox--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[5.1 AI van klant - Gegevensvoorbereiding (Ingest)](./ex1.md)

De gegevens van de klant worden opgenomen en getransformeerd met het Model van de Gegevens van de Ervaring (XDM) op Adobe Experience Platform. Specifiek, moeten alle datasets die in de Intelligente Diensten worden gebruikt met het schema van XDM van Consumer ExperienceEvent (CEE) in overeenstemming zijn.

[5.2 AI van de Klant - creeer een Nieuwe Instantie (vorm)](./ex2.md)

De marketinganalist configureert de gewenste voorspellingen door bedrijfsregels op te geven en relevante gegevens te identificeren. Na het vormen van het model, planningsuitvoering en overzichtsscores.

[5.3 AI van de Klant - Score en Segmentatie (Voorspelling en actie ondernemen)](./ex3.md)

Nadat de modellen klaar zijn met training en scoren, worden de scores weer in het Platform geschreven. U kunt bepalen welke acties u wilt uitvoeren met de voorspelling, zoals het definiëren van segmenten, het maken van aangepaste dashboards enzovoort.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
