---
title: Journey Optimizer Create your event
description: Journey Optimizer Create your event
kt: 5342
doc-type: tutorial
exl-id: b132ad78-aaa3-458d-9895-0935f8ba88bb
source-git-commit: f843c50af04d744a7d769f320b5b55a5e6d25ffd
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# 3.1.1 Een gebeurtenis maken

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis &lbrace;in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd.

![&#x200B; ACOP &#x200B;](./images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gebeurtenissen**.

![&#x200B; ACOP &#x200B;](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klik **creëren Gebeurtenis** beginnen uw eigen gebeurtenis te creëren.

![&#x200B; ACOP &#x200B;](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

![&#x200B; ACOP &#x200B;](./images/emptyevent1.png)

Geef uw gebeurtenis eerst een naam zoals deze: `--aepUserLdap--AccountCreationEvent` .
Plaats de beschrijving aan `Account Creation Event`, zorg ervoor het **Type** aan **Eenheids** wordt geplaatst en voor de **Identiteitskaart van de Gebeurtenis** selectie, uitgezocht **Gegenereerd Systeem**.

![&#x200B; ACOP &#x200B;](./images/eventdescription.png)

Nu de selectie van het schema. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1` .

![&#x200B; ACOP &#x200B;](./images/eventschema.png)

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. U zou nu over de **sectie van de Payload** moeten bewegen en u zult 3 pictogrammen popup zien. Klik op **uitgeven** pictogram.

![&#x200B; ACOP &#x200B;](./images/eventpayload.png)

U zult het venster van a **Gebieden** popup zien, waarin u enkele gebieden moet selecteren die wij e-mail moeten personaliseren.  We kiezen later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![&#x200B; ACOP &#x200B;](./images/eventfields.png)

In het voorwerp `--aepTenantId--.demoEnvironment`, zorg gelieve ervoor om de gebieden **brandLogo** en **brandName** te selecteren.

![&#x200B; ACOP &#x200B;](./images/eventpayloadbr.png)

In het voorwerp `--aepTenantId--.identification.core`, gelieve ervoor te zorgen om het gebied **e-mail** te selecteren. Klik **O.K.** om uw veranderingen te bewaren.

![&#x200B; ACOP &#x200B;](./images/eventpayloadbrid.png)

Dan moet je dit zien. Plaats **Namespace** aan **ECID (ECID)**. Klik **sparen**.

![&#x200B; ACOP &#x200B;](./images/eventsave.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![&#x200B; ACOP &#x200B;](./images/eventdone.png)

Klik opnieuw uw gebeurtenis om **te openen geef het 1&rbrace; scherm van de Gebeurtenis &lbrace;opnieuw uit.** Beweeg over het **gebied van de Lading** opnieuw om de 3 pictogrammen opnieuw te zien. Klik op het **pictogram van de Payload van de Mening**.

![&#x200B; ACOP &#x200B;](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.

![&#x200B; ACOP &#x200B;](./images/fullpayload.png)

Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de volgende reis te activeren. Herinner deze eventID, aangezien u het in één van de volgende oefeningen zult nodig hebben.
`"eventID": "5ae9b8d3f68eb555502b0c07d03ef71780600c4bd0373a4065c692ae0bfbd34d"`

Klik **OK**.

![&#x200B; ACOP &#x200B;](./images/payloadeventID.png)

Klik **annuleren**.

![&#x200B; ACOP &#x200B;](./images/payloadeventID1.png)

Je hebt deze oefening nu afgerond.

Volgende Stap: [&#x200B; 3.1.2 creeer fragmenten die in uw bericht &#x200B;](./ex2.md) moeten worden gebruikt

[Terug naar module 3.1](./journey-orchestration-create-account.md)

[Terug naar alle modules](../../../overview.md)
