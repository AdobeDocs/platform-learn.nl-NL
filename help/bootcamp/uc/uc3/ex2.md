---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw gebeurtenis
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw gebeurtenis
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 3d47c686-c2d8-4961-a05b-0990025392fa
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 3.2 Uw gebeurtenis maken

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `Bootcamp` genoemd. Om van één zandbak in een andere te veranderen, klik op **Prod** en selecteer de zandbak van de lijst. In dit voorbeeld, wordt de zandbak genoemd **Bootamp2**. U zult dan in de **1} mening van het Huis {van uw zandbak `Bootcamp` zijn.**

![ ACOP ](./images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gebeurtenissen**.

![ ACOP ](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klik **creëren Gebeurtenis** beginnen uw eigen gebeurtenis te creëren.

![ ACOP ](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

Geef uw gebeurtenis eerst een naam als deze: `yourLastNameBeaconEntryEvent` en voeg een beschrijving als deze toe `Beacon Entry Event` .

![ ACOP ](./images/eventdescription.png)

Daarna, zorg ervoor het **Type** aan **Eenheids** wordt geplaatst, en voor de **Verzamelde het Type van identiteitskaart van de Gebeurtenis** selectie, uitgezocht **Systeem**.

![ ACOP ](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1` .

![ ACOP ](./images/eventschema.png)

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van Gebieden** worden geselecteerd. U zou nu over de **sectie van Gebieden** moeten bewegen en u zult 3 popup pictogrammen zien. Klik op **uitgeven** pictogram.

![ ACOP ](./images/eventpayload.png)

U zult het venster van a **Gebieden** popup zien, waarin u enkele gebieden moet selecteren die wij de reis moeten personaliseren.  We kiezen later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![ ACOP ](./images/eventfields.png)

Schuif omlaag totdat u het object `Place context` ziet en schakel het selectievakje in. Met dit, zal alle context van de plaats van de klant aan de reis ter beschikking worden gesteld. Klik **O.K.** om uw veranderingen te bewaren.

![ ACOP ](./images/eventpayloadbr.png)

Dan moet je dit zien. Klik **sparen** opnieuw om uw veranderingen te bewaren.

![ ACOP ](./images/eventsave.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![ ACOP ](./images/eventdone.png)

Klik opnieuw uw gebeurtenis om **te openen geef het 1} scherm van de Gebeurtenis {opnieuw uit.** Beweeg over **Gebieden** opnieuw om de 3 pictogrammen te zien. Klik op het **pictogram van de Mening**.

![ ACOP ](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.
Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

![ ACOP ](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de reis te activeren die u in een van de volgende oefeningen gaat maken. Onthoud deze eventID, aangezien u deze later nodig kunt hebben.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Klik **O.K.**, die door **wordt gevolgd annuleert**.

Je hebt deze oefening nu afgerond.

Volgende Stap: [ 3.3 creeer uw reis en duw bericht ](./ex3.md)

[Ga terug naar gebruikersstroom 3](./uc3.md)

[Terug naar alle modules](../../overview.md)
