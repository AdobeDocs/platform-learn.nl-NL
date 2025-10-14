---
title: Bootkamp - Personalization in het callcenter
description: Bootkamp - Personalization in het callcenter
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: f7697673-38f9-41f6-ac4d-2561db2ece67
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 2.6 Personalization in het callcenter

Zoals die veelvoudige tijden tijdens bootkamp reeds wordt besproken, is het personaliseren van de klantenervaring iets dat op een omnichannel manier zou moeten gebeuren. Een callcenter is vaak vrij losgekoppeld van de rest van de klantenreis en dat leidt vaak tot frustrerende klantenervaringen, maar het hoeft niet te zijn. Laten wij u een voorbeeld tonen van hoe het callcenter gemakkelijk met Adobe Experience Platform, in real time kan worden verbonden.

## Klantreis

In de vorige oefening, gebruikend de mobiele toepassing, kocht u een product door **te klikken Koop** knoop.

![&#x200B; DSN &#x200B;](./images/app20.png)

Laten we aannemen dat u een vraag hebt over de status van uw bestelling, wat zou u doen? Typisch zou u het vraagcentrum roepen.

Alvorens het vraagcentrum te roepen, moet u uw **identiteitskaart van de Loyaliteit** kennen. U vindt uw Loyalty-id in de profielviewer van de website.

![&#x200B; DSN &#x200B;](./images/cc1.png)

In dit geval, is **identiteitskaart van de Loyalty** **5863105**. Als deel van onze douaneimplementatie van de eigenschap van het vraagcentrum in het demomilieu, moet u een prefix aan uw **identiteitskaart van de Loyaliteit** toevoegen. Het voorvoegsel is **11373**, zodat identiteitskaart van de Loyaliteit in dit voorbeeld te gebruiken is **11373 5863105**.

Laten we dat nu doen. Gebruik uw telefoon en roep het aantal **+1 (323) 745-1670**.

![&#x200B; DSN &#x200B;](./images/cc2.png)

U wordt gevraagd uw Loyalty-id in te voeren, gevolgd door **#** . Voer je Loyalty-id in.

![&#x200B; DSN &#x200B;](./images/cc3.png)

U zult dan **Hello, eerste naam** horen. Deze voornaam is afkomstig uit het Real-Time Klantprofiel in Adobe Experience Platform. Dan heb je 3 keuzen. Het aantal van de pers **1**, **Status van de Orde**.

![&#x200B; DSN &#x200B;](./images/cc4.png)

Na het horen van uw ordestatus, zult u een keus worden gegeven om **1** te drukken om naar het belangrijkste menu terug te gaan of anders, druk 2. Pers **2**.

![&#x200B; DSN &#x200B;](./images/cc5.png)

U zult dan worden gevraagd om uw ervaring van het vraagcentrum te schatten, door een aantal tussen 1 en 5 te selecteren, met 1 laag en 5 die hoog zijn. Maak uw keuze.

![&#x200B; DSN &#x200B;](./images/cc6.png)

Uw vraag aan het vraagcentrum zal nu beëindigen.

Ga naar [&#x200B; Adobe Experience Platform &#x200B;](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``Bootcamp`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![&#x200B; Ingestie van Gegevens &#x200B;](./images/sb1.png)

In het linkermenu, ga naar **Profielen** en **doorbladeren**.

![&#x200B; Profiel van de Klant &#x200B;](./images/homemenu.png)

Selecteer **Identiteit namespace** **E-mail** en ga het e-mailadres van uw klantenprofiel in. Klik **Mening**. Klik om uw profiel te openen.

![&#x200B; DSN &#x200B;](./images/cc7.png)

Je ziet het profiel van je klant opnieuw. Ga naar **Gebeurtenissen**.

![&#x200B; DSN &#x200B;](./images/cc8.png)

Onder gebeurtenissen, zult u 2 gebeurtenissen met een eventType van **callCenter** zien. De eerste gebeurtenis is een resultaat van uw antwoord op de vraag **tarief uw vraagtevredenheid**.

![&#x200B; DSN &#x200B;](./images/cc9.png)

De rol neer een beetje, en u zult de gebeurtenis zien die werd geregistreerd toen u de optie selecteerde om uw **Status van de Orde** te controleren.

![&#x200B; DSN &#x200B;](./images/cc10.png)

Ga naar **lidmaatschap van het Segment**. U zult nu zien dat 2 segmenten op uw profiel, in real time kwalificeren, die op de interactie wordt gebaseerd u door het vraagcentrum had. Deze segmentlidmaatschappen kunnen en zouden dan moeten worden gebruikt om te beïnvloeden welke mededeling en verpersoonlijking over een ander kanaal gebeurt.

![&#x200B; DSN &#x200B;](./images/cc11.png)

Je hebt deze oefening nu afgerond.

[Ga terug naar Gebruikersstroom 2](./uc2.md)

[Terug naar alle modules](../../overview.md)
