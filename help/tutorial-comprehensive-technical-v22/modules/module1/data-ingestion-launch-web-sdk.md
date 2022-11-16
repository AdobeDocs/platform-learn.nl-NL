---
title: 1. Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web
description: Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 86da7132-cb06-4be3-b6b8-ea3ab937e6dc
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# 1. Stichting - Opstelling van de Inzameling van Gegevens van Adobe Experience Platform en de uitbreiding van SDK van het Web

**Auteur: [Matthew Joseph Woolley](https://www.linkedin.com/in/matthewjwoolley/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

Deze grondmodule introduceert u aan Adobe gegevensinzameling visie en verklaart hoe te om gegevens van een website en mobiele toepassing in Adobe Experience Platform en andere toepassingen via de Inzameling van Gegevens van Adobe Experience Platform, de SDKs en het Netwerk van de Rand van Adobe Experience Platform te krijgen. Deze module introduceert enkele concepten en technologieën die een impact hebben buiten het bereik van een technische zelfstudie van Adobe Experience Platform. Het moet duidelijk zijn welke delen van deze oefeningen aan de rest van de uitvoerige zelfstudie, die u meer over de Rand van de Ervaring en zijn mogelijkheden, en waar te gaan voor verdere informatie en leerprogramma&#39;s stichten.

## Leerdoelen

- Leer hoe een merk Adobe Experience Platform Data Collection als hun Systeem van Tag Management (TMS) gebruikt.
- Leer de gegevensstromen die door een merk worden gebruikt om gegevens aan hun producten van de Adobe in te voeren.
- Leer hoe u gegevens naar de Adobe Experience Platform en andere producten kunt verzenden via het Adobe Experience Platform Edge Network.
- Leer hoe u gegevenselementen en regels maakt die gegevens verzamelen van internet en mobiele apparatuur.
- Leer over de het volgen gebeurtenissen van SDK van het Web en hoe te om hun inhoud te zuiveren.
- Leer wat een gegevenslaag is en wat Adobe adviseert wanneer het uitvoeren van één.
- Leer wat de stappen zijn Web SDK van kras uit te voeren.
- Leer het verschil tussen een web- en mobiele implementatie.

## Vereisten

- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot Adobe Experience Platform-gegevensverzameling: [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Toegang tot de demo-website

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem1.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[1.1 Adobe Experience Platform-gegevensverzameling](./ex1.md)

In deze oefening, onderzoek de UI van de Gegevensinzameling van Adobe Experience Platform en krijg inzicht in zijn mogelijkheden.

[1.2 Edge Network, DataStream en Server Side Data Collection](./ex2.md)

In deze oefening, zult u leren hoe te om gegevens aan de producten van Adobe in de interface van de Inzameling van Gegevens van Adobe Experience Platform door:sturen en de gegevensstromen onderzoeken die door de demowebsite worden gebruikt.

[1.3 Inleiding tot Adobe Experience Platform-gegevensverzameling](./ex3.md)

In deze oefening, zult u leren hoe te opstelling een Uitbreiding, de Elementen van Gegevens en Regels van Gegevens te bouwen en hen aan het Web te publiceren.

[1.4 Clientside Web Data Collection](./ex4.md)

In deze oefening, zuivert SDK van het Web die is geïnstalleerd om te begrijpen hoe het werkt en welke gegevens in toekomstige oefeningen zullen worden gebruikt.

[1.5 Adobe Analytics en Adobe Audience Manager implementeren](./ex5.md)

In deze oefening, zie en gebruik Webgegevens die met het Web SDK in Adobe Analytics en Adobe Audience Manager worden verzameld.

[1.6 Adobe Target implementeren](./ex6.md)

In deze oefening, opstelling een activiteit in Adobe Target, die via het Web SDK wordt uitgevoerd.

[1.7 XDM-schemavereisten in Adobe Experience Platform](./ex7.md)

Om ervoor te zorgen dat Web SDK en alloy.js gegevens in Adobe Experience Platform kunnen opnemen, is er een vereiste dat een specifieke XDM Mixin deel moet uitmaken van het XDM-schema in Adobe Experience Platform.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
