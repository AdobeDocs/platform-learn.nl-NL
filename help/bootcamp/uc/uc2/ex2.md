---
title: Bootamp - Journey Optimizer Uw gebeurtenis maken
description: Bootamp - Journey Optimizer Uw gebeurtenis maken
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 89db40ab-d4c5-4310-aca6-cb64828e7bc9
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# 2.2 Uw gebeurtenis maken

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `Bootcamp` genoemd. Om van één zandbak in een andere te veranderen, klik op **Prod** en selecteer de zandbak van de lijst. In dit voorbeeld, wordt de zandbak genoemd **Bootkamp**. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak `Bootcamp` zijn.**

![ ACOP ](./images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gebeurtenissen**.

![ ACOP ](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klik **creëren Gebeurtenis** beginnen uw eigen gebeurtenis te creëren.

![ ACOP ](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

![ ACOP ](./images/emptyevent1.png)

Geef uw gebeurtenis eerst een naam als deze: `yourLastNameAccountCreationEvent` en voeg een beschrijving als deze toe `Account Creation Event` .

![ ACOP ](./images/eventdescription.png)

Daarna, zorg ervoor het **Type** aan **Eenheids** wordt geplaatst, en voor de **Verzamelde het Type van identiteitskaart van de Gebeurtenis** selectie, uitgezocht **Systeem**.

![ ACOP ](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1` .

![ ACOP ](./images/eventschema.png)

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van Gebieden** worden geselecteerd. U zou nu over de **sectie van Gebieden** moeten bewegen en u zult 3 popup pictogrammen zien. Klik op **uitgeven** pictogram.

![ ACOP ](./images/eventpayload.png)

U zult het venster van a **Gebieden** popup zien, waarin u enkele gebieden moet selecteren die wij e-mail moeten personaliseren.  We kiezen later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![ ACOP ](./images/eventfields.png)

In het voorwerp `_experienceplatform.demoEnvironment`, zorg gelieve ervoor om de gebieden **brandLogo** en **brandName** te selecteren.

![ ACOP ](./images/eventpayloadbr.png)

In het voorwerp `_experienceplatform.identification.core`, gelieve ervoor te zorgen om het gebied **e-mail** te selecteren.

![ ACOP ](./images/eventpayloadbrid.png)

Klik **O.K.** om uw veranderingen te bewaren.

![ ACOP ](./images/saveok.png)

Dan moet je dit zien. Klik **sparen** opnieuw om uw veranderingen te bewaren.

![ ACOP ](./images/eventsave.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![ ACOP ](./images/eventdone.png)

Klik opnieuw uw gebeurtenis om **te openen geef het 1&rbrace; scherm van de Gebeurtenis &lbrace;opnieuw uit.** Beweeg over **Gebieden** opnieuw om de 3 pictogrammen opnieuw te zien. Klik op het **pictogram van de Payload van de Mening**.

![ ACOP ](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.
Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

![ ACOP ](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de reis te activeren die u in een van de volgende oefeningen gaat maken. Onthoud deze eventID, aangezien u deze later nodig kunt hebben.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Klik **O.K.**, die door **wordt gevolgd annuleert**.

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 2.3 creeer uw e-mailbericht ](./ex3.md)

[Ga terug naar Gebruikersstroom 2](./uc2.md)

[Terug naar alle modules](../../overview.md)
