---
title: Foundation - Real-time klantprofiel
description: Foundation - Real-time klantprofiel
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 050e5d99-544d-4a86-a7f6-9f103381dca5
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# 3. Foundation - Real-time klantprofiel

**Auteur: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module gaan we diep in de mogelijkheden van Adobe Experience Platform om in real-time klantprofiel en identiteit te gebruiken. U zult leren hoe het publiek kan worden bepaald, de rol van de Dienst van de Identiteit en identiteitskaart van de Experience Cloud, en hoe te om de vragen van de segmentbouwer te bepalen om uw eigen segmenten te bepalen.

## Leerdoelen

- Leer hoe u het realtime klantprofiel van een klant visualiseert via de gebruikersinterface van Adobe Experience Platform
- Leer hoe u een segment maakt met Adobe Experience Platform Segment Builder
- Leer hoe u een segment maakt en de resultaten van het segment opslaat in een dataset met Adobe Experience Platform API&#39;s
- Leer over de gevolgen van het hebben van toegang tot een volledig klantenprofiel, met inbegrip van gedrag in real time, in off-line milieu&#39;s

## Vereisten

- Toegang tot [Adobe Experience Platform](https://experience.adobe.com/platform)
- Toegang tot [https://public.aepdemo.net](https://public.aepdemo.net)
- **Deze middelen downloaden**:
   - [Postman-verzamelingen](./../../assets/postman/postman_profile.zip)

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem3.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[3.1 Bezoek de website](./ex1.md)

In deze oefening, zult u een manuscript volgen en door de website lopen.

[3.2 Visualiseer uw eigen real-time klantenprofiel - UI](./ex2.md)

In deze oefening, zult u login aan Adobe Experience Platform en u zult uw eigen Profiel van de Klant in real time in UI bekijken.

[3.3 Visualiseer uw eigen real-time klantprofiel - API](./ex3.md)

In deze oefening, zult u Postman en Adobe I/O gebruiken om uw eigen real-time klantenprofiel te bekijken, door Adobe Experience Platform te gebruiken APIs.

[3.4 Een segment maken - UI](./ex4.md)

In deze oefening, zult u een segment tot stand brengen door gebruik van de Bouwer van het Segment van Adobe Experience Platform te maken.

[3.5 Een segment maken - API](./ex5.md)

In deze oefening, zult u Postman en Adobe I/O gebruiken om een segment tot stand te brengen en de resultaten van dat segment op te slaan als dataset, door Adobe Experience Platform APIs te gebruiken.

[3.6 Zie uw profiel van de Klant in real time in actie in het Centrum van de Vraag](./ex6.md)

In deze oefening, zult u een medewerker van het vraagcentrum nadoen die een vraag van een klant ontvangt. Om werkelijk invloed op de ervaring van deze klant te kunnen uitoefenen, hebt u toegang tot alle beschikbare informatie in real time nodig.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
