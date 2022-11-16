---
title: CDP in real time - Bouw een segment en neem actie
description: CDP in real time - Bouw een segment en neem actie
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 147d9153-5742-4857-aae1-0ec434a1e626
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 6. CDP in real time - Bouw een segment en neem actie

**Auteur: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/), [Alberto De Caro](https://www.linkedin.com/in/albertodecaro/), [Benedikt Wedenik](https://www.linkedin.com/in/benedikt-wedenik/)**

In deze module, zult u een het stromen segment vormen en zult het segment aan veelvoudige bestemmingen activeren.

## Leerdoelen

- Leer hoe u een segment kunt maken en inschakelen voor streaming.
- Leer hoe u een advertentiebestemming configureert met de gebruikersinterface van Adobe Experience Platform.
- Leer hoe te om een segment met een bestemming te verbinden en het te activeren.
- Leer hoe u Adobe Experience Platform-segmenten in Adobe Audience Manager gebruikt en hoe u Adobe Audience Manager-segmenten in Adobe Experience Platform gebruikt, dankzij bidirectioneel delen van segmenten.

## Vereisten

- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot Adobe Target
- Toegang tot AWS S3

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem11.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--module11sandbox--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[6.1 Een segment maken](./ex1.md)

Leer hoe u een segment maakt.

[6.2 Overzicht hoe te om DV360 Bestemming te vormen gebruikend Doelen](./ex2.md)

Leer hoe u een advertentiebestemming configureert met de gebruikersinterface van Real-Time CDP.

[6.3 Actie ondernemen: verzend uw segment naar DV360](./ex3.md)

Sluit het segment dat u in oefening 6.1 bouwde aan de bestemming DV360 aan.

[6.4 Actie nemen: verzend uw segment naar S3-bestemming](./ex4.md)

Gebruik het segment u in oefening 6.1 bouwde en verzend het naar een S3-bestemming, typisch gebruikt voor E-mail marketing-bestemmingen.

[6.5 Actie nemen: Uw segment verzenden naar Adobe Target](./ex5.md)

Gebruik het segment u in oefening 6.1 bouwde om een Ervaring te vormen richtend Activiteit in Adobe Target.

[6.6 Extern publiek](./ex6.md)

Importeer soorten publiek van een extern bronsysteem naar Adobe Experience Platform.

[6.7 Doelen SDK](./ex7.md)

Vorm uw eigen bestemming gebruikend Doelen SDK.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
