---
title: Foundation - gegevensinname
description: Foundation - gegevensinname
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: dbbc0539-ae1b-488d-b312-76a74d4d361f
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# 2. Foundation - gegevensinname

**Auteur: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module, is het doel alles over gegevensopname te leren. U leert meer over gegevensinvoer in Streaming en Batch. U implementeert Streaming Data Ingestie met behulp van Launch, zodat het gedrag van de klant op de website Hands-On Lab in real-time naar Adobe Experience Platform wordt gestreamd. U zult over de Opname van Gegevens van de Partij leren door een Werkschema van Adobe Experience Platform te gebruiken om een CSV-dossier te nemen, het tegen een XDM-schema in kaart te brengen en dan het in Adobe Experience Platform in te nemen.

## Leerdoelen

- Leer hoe u een XDM-schema maakt in Adobe Experience Platform
- Meer informatie over het maken van gegevenssets in Adobe Experience Platform
- Leer hoe u een streamingeindpunt maakt en de Adobe Experience Platform-extensie in Launch configureert
- Leer hoe u regels maakt in Launch om gegevens te streamen naar Adobe Experience Platform
- Leer hoe u Adobe Experience Platform Launch op een webpagina kunt integreren
- Leer hoe u een Adobe Experience Platform-workflow kunt gebruiken om een CSV-bestand in Adobe Experience Platform in te voeren

## Vereisten

- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot Adobe Experience Platform Launch: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Toegang tot [https://public.aepdemo.net](https://public.aepdemo.net)
- Toegang tot Postman

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem2.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--module2sandbox--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[2.1 De website verkennen](./ex1.md)

In deze oefening, zult u de website onderzoeken die u als deel van dit toelaat zult gebruiken.

[2.2 Schema&#39;s configureren en id&#39;s instellen](./ex2.md)

In deze oefening, zult u de vereiste XDM schema&#39;s vormen om profielinformatie en klantengedrag te vangen. In elk schema XDM, zult u ook een primaire herkenningsteken moeten vormen om alle informatie te verbinden met.

[2.3 Gegevensbestanden configureren](./ex3.md)

In deze oefening, zult u de vereiste datasets terugwinnen om profielinformatie en klantengedrag te vangen en op te slaan.

[2.4 Gegevensinname uit offlinebronnen](./ex4.md)

In deze exercitie gaat u naar de website en de mobiele app en gedraagt u zich als een klant, die gegevens naar het Platform stroomt.

[2.5 Gegevenslandingszone](./ex5.md)

Zet uw gegevenslandingszone Source-connector in met Azure Blob-opslag.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
