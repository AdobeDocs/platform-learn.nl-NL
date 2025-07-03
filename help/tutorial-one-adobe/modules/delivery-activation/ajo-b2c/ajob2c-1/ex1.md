---
title: Journey Optimizer Create your event
description: Journey Optimizer Create your event
kt: 5342
doc-type: tutorial
exl-id: 2c03cc8d-0106-4fa5-80c6-e25712ca2eab
source-git-commit: d19bd2e39c7ff5eb5c99fc7c747671fb80e125ee
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 3.1.1 Een gebeurtenis maken

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![ ACOP ](./images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gebeurtenissen**.

![ ACOP ](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klik **creëren Gebeurtenis** beginnen uw eigen gebeurtenis te creëren.

![ ACOP ](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

![ ACOP ](./images/emptyevent1.png)

Geef uw gebeurtenis eerst een naam zoals deze: `--aepUserLdap--AccountCreationEvent` .
Plaats de beschrijving aan `Account Creation Event`, zorg ervoor het **Type** aan **Eenheids** wordt geplaatst en voor de **Identiteitskaart van de Gebeurtenis** selectie, uitgezocht **Gegenereerd Systeem**.

![ ACOP ](./images/eventdescription.png)

Nu de selectie van het schema. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1` .

![ ACOP ](./images/eventschema.png)

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. U zou nu over de **sectie van de Payload** moeten bewegen en u zult 3 pictogrammen popup zien. Klik op **uitgeven** pictogram.

![ ACOP ](./images/eventpayload.png)

U zult het venster van a **Gebieden** popup zien, waarin u enkele gebieden moet selecteren die wij e-mail moeten personaliseren.  U kiest later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![ ACOP ](./images/eventfields.png)

In het voorwerp `--aepTenantId--.demoEnvironment`, zorg gelieve ervoor om de gebieden **brandLogo** en **brandName** te selecteren.

![ ACOP ](./images/eventpayloadbr.png)

In het voorwerp `--aepTenantId--.identification.core`, gelieve ervoor te zorgen om het gebied **e-mail** te selecteren. Klik **O.K.** om uw veranderingen te bewaren.

![ ACOP ](./images/eventpayloadbrid.png)

Dan moet je dit zien. Zorg ervoor dat **Namespace** aan **ECID (ECID)** wordt geplaatst. Klik **sparen**.

![ ACOP ](./images/eventsave.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![ ACOP ](./images/eventdone.png)

Klik opnieuw uw gebeurtenis om **te openen geef het 1} scherm van de Gebeurtenis {opnieuw uit.** Beweeg over het **gebied van de Lading** opnieuw om de 3 pictogrammen opnieuw te zien. Klik op het **pictogram van de Payload van de Mening**.

![ ACOP ](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.

![ ACOP ](./images/fullpayload.png)

Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de volgende reis te activeren. Herinner deze eventID, aangezien u het in één van de volgende oefeningen zult nodig hebben.
`"eventID": "d40815dbcd6ffd813035b4b590b181be21f5305328e16c5b75e4f32fd9e98557"`

Klik **OK**.

![ ACOP ](./images/payloadeventID.png)

Klik **annuleren** om dit venster te sluiten.

![ ACOP ](./images/payloadeventID1.png)

## Volgende stappen

Ga naar [ 3.1.2 creeer fragmenten in uw bericht moeten worden gebruikt ](./ex2.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer: Orchestratie ](./journey-orchestration-create-account.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
