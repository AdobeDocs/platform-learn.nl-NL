---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more
description: Adobe Journey Optimizer - External Weather API, SMS Action & more
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7f3d6dcb-845d-4ff1-97c3-8e93b8d2c624
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 8. Adobe Journey Optimizer: Externe gegevensbronnen en aangepaste acties

**Auteur: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module, zult u Adobe Journey Optimizer gebruiken om aan klantengedrag, zowel online als off-line te luisteren, en aan het op een intelligente, contextafhankelijke en in real time manier te antwoorden. U hebt reeds een eerste hands-on ervaring met Adobe Journey Optimizer in Module 6 gehad. In deze oefening, zult u een beetje dieper gaan en een geavanceerder gebruiksgeval onderzoeken waarbij de externe gegevensbronnen als deel van een reis worden gebruikt.

## Leerdoelen

- Leer hoe u gebeurtenissen, externe gegevensbronnen en reizen in Adobe Journey Optimizer kunt maken
- Leer hoe u weerinformatie kunt gebruiken via de Open Weather-API
- Leer hoe u aangepaste actiedoelen gebruikt, zoals Twilio en Slack uit Adobe Journey Optimizer

## Vereisten

- Toegang tot Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot Adobe Journey Optimizer
- Toegang tot de API voor Open Weather

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem12.png)

## Bedrijfscontext

Als merk heb je veel geïnvesteerd in het personaliseren van online ervaringen. Nu wilt u contextueel en relevant zijn voor offline ervaringen.
In deze module, zult u de aanwezigheid van een klant in een off-line opslag gebruiken om dan een gepersonaliseerde ervaring binnen de opslag te leveren door relevante inhoud aan die klant op onze in-store schermen te tonen en tezelfdertijd, willen wij een gepersonaliseerd Push of SMS Bericht aan die zelfde klant, allen in real time leveren.
Als merk begrijpt u ook dat de context een grote invloed heeft op de belangen van de klant, zodat u de huidige weerinformatie van de locatie van die klant wilt opnemen om te bepalen welke inhoud of promotie moet worden weergegeven.

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[8.1 Een gebeurtenis definiëren](./ex1.md)

Leer hoe u een aangepaste gebeurtenis definieert met Adobe Journey Optimizer.

[8.2 Een externe gegevensbron definiëren](./ex2.md)

Leer hoe u een externe gegevensbron configureert met Adobe Journey Optimizer.

[8.3 Een aangepaste handeling definiëren](./ex3.md)

Leer hoe u een externe actie definieert met Adobe Journey Optimizer.

[8.4 Maak uw reis en uw berichten](./ex4.md)

Combineer gebeurtenissen, gegevensbronnen en acties tot een intelligente en contextuele reis.

[8.5 Trigger je reis](./ex5.md)

Trigger uw specifieke reis.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
