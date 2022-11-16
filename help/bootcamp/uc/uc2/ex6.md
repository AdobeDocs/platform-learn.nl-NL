---
title: Bootkamp - Personalisatie in het callcenter
description: Bootkamp - Personalisatie in het callcenter
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: f7697673-38f9-41f6-ac4d-2561db2ece67
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# 2.6 Personalisatie in het callcenter

Zoals die veelvoudige tijden tijdens bootkamp reeds wordt besproken, is het personaliseren van de klantenervaring iets dat op een omnichannel manier zou moeten gebeuren. Een callcenter is vaak vrij losgekoppeld van de rest van de klantenreis en dat leidt vaak tot frustrerende klantenervaringen, maar het hoeft niet te zijn. Laten wij u een voorbeeld tonen van hoe het callcenter gemakkelijk met Adobe Experience Platform, in real time kan worden verbonden.

## Klantreis

Tijdens de vorige exercitie hebt u met de mobiele toepassing een product aangeschaft door op de knop **Kopen** knop.

![DSN](./images/app20.png)

Laten we aannemen dat u een vraag hebt over de status van uw bestelling, wat zou u doen? Typisch zou u het vraagcentrum roepen.

Alvorens het vraagcentrum te roepen, moet u uw kennen **Loyalty-id**. U vindt uw Loyalty-id in de profielviewer van de website.

![DSN](./images/cc1.png)

In dit geval worden de **Loyalty-id** is **5863105**. Als deel van onze douaneimplementatie van de eigenschap van het vraagcentrum in het demomilieu, moet u een prefix aan uw toevoegen **Loyalty-id**. Het voorvoegsel is **11373** De Loyalty-id die in dit voorbeeld moet worden gebruikt, is **11373 5863105**.

Laten we dat nu doen. Gebruik uw telefoon en roep het aantal **+1 (323) 745-1670**.

![DSN](./images/cc2.png)

Je wordt gevraagd je Loyalty-id in te voeren, gevolgd door **Aantal**. Voer je Loyalty-id in.

![DSN](./images/cc3.png)

Dan hoor je **Hallo, voornaam**. Deze voornaam is afkomstig uit het Real-Time Klantprofiel in Adobe Experience Platform. Dan heb je 3 keuzes. Drukpersnummer **1**, **Status van bestelling**.

![DSN](./images/cc4.png)

Nadat u de status van uw bestelling hebt gehoord, kunt u **1** Druk op 2 om terug te gaan naar het hoofdmenu of een ander menu. Druk **2**.

![DSN](./images/cc5.png)

U zult dan worden gevraagd om uw ervaring van het vraagcentrum te schatten, door een aantal tussen 1 en 5 te selecteren, met 1 laag en 5 die hoog zijn. Maak uw keuze.

![DSN](./images/cc6.png)

Uw vraag aan het vraagcentrum zal nu beëindigen.

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

Ga in het linkermenu naar **Profielen** en **Bladeren**.

![Klantprofiel](./images/homemenu.png)

Selecteer **Naamruimte identiteit** **E-mail** en voer het e-mailadres van uw klantenprofiel in. Klikken **Weergave**. Klik om uw profiel te openen.

![DSN](./images/cc7.png)

Je ziet het profiel van je klant opnieuw. Ga naar **Gebeurtenissen**.

![DSN](./images/cc8.png)

Onder gebeurtenissen ziet u 2 gebeurtenissen met een eventType van **callCenter**. De eerste gebeurtenis is het resultaat van uw antwoord op de vraag **Beoordeel uw vraagtevredenheid**.

![DSN](./images/cc9.png)

Een beetje omlaag schuiven en u ziet de gebeurtenis die is opgenomen toen u de optie selecteert om uw **Status van bestelling**.

![DSN](./images/cc10.png)

Ga naar **Segmentlidmaatschap**. U zult nu zien dat 2 segmenten op uw profiel, in real time kwalificeren, die op de interactie wordt gebaseerd u door het vraagcentrum had. Deze segmentlidmaatschappen kunnen en zouden dan moeten worden gebruikt om te beïnvloeden welke mededeling en verpersoonlijking over een ander kanaal gebeurt.

![DSN](./images/cc11.png)

Je hebt deze oefening nu afgerond.

[Ga terug naar Gebruikersstroom 2](./uc2.md)

[Terug naar alle modules](../../overview.md)
