---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Een gebeurtenis definiëren
description: Adobe Journey Optimizer - External Weather API, SMS Action & more
kt: 5342
doc-type: tutorial
exl-id: bde4290a-59d1-4471-83a7-1cad69f94ff1
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# 3.2.1 Een gebeurtenis definiëren

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Gebeurtenissen**.

![ ACOP ](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klik **creëren Gebeurtenis** beginnen uw eigen gebeurtenis te creëren.

![ ACOP ](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.
Gebruik `--aepUserLdap--GeofenceEntry` als naam voor de gebeurtenis.

Stel Beschrijving in op: `Geofence Entry Event` .

Zorg ervoor het **Type** aan **Eenheids** wordt geplaatst, en voor de **Verzamelde de selectie van het Type van identiteitskaart van de Gebeurtenis**, uitgezocht **Systeem**

![ Demo ](./images/evname.png)

Vervolgens moet u een schema selecteren. Alle schema&#39;s die hier worden getoond, zijn Adobe Experience Platform Schemas.

![ Demo ](./images/evschema.png)

U zult merken dat niet alle schema&#39;s worden getoond. Er zijn veel meer schema&#39;s beschikbaar in Adobe Experience Platform.
Om in deze lijst te tonen, moet een schema een zeer specifieke gebiedsgroep hebben met het verbonden. De veldgroep die hier moet worden weergegeven, wordt `Orchestration eventID` genoemd.

Laten we eens kijken hoe deze schema&#39;s in Adobe Experience Platform zijn gedefinieerd.

In het linkermenu, ga naar **Schema&#39;s** en open dit in een nieuwe browser tabel. In **Schema&#39;s**, ga **doorbladeren** om de lijst van beschikbare Schema&#39;s te zien.
Open het schema `Demo System - Event Schema for Website (Global v1.1)` .

![ Ingestie van Gegevens ](./images/schemas.png)

Nadat u het schema hebt geopend, ziet u dat de veldgroep `Orchestration eventID` deel uitmaakt van het schema.
Deze veldgroep heeft slechts twee velden, `_experience.campaign.orchestration.eventID` en `originJourneyID` .

![ Ingestie van Gegevens ](./images/schemageo.png)

Zodra deze veldgroep en dit specifieke eventID gebied deel van een schema uitmaken, zal dat schema voor gebruik door Adobe Journey Optimizer beschikbaar zijn.

Ga terug naar uw gebeurtenisconfiguratie in Adobe Journey Optimizer.

![ Demo ](./images/evschema.png)

In dit geval wilt u luisteren naar een Geofence-gebeurtenis om te begrijpen of een klant zich op een specifieke locatie bevindt. Selecteer nu het schema `Demo System - Event Schema for Website (Global v1.1)` als het schema voor uw gebeurtenis.

![ Demo ](./images/evschema1.png)

Adobe Journey Optimizer selecteert dan automatisch een aantal vereiste velden, maar u kunt de velden bewerken die beschikbaar zijn voor Adobe Journey Optimizer.

Klik het **potlood** pictogram om de gebieden uit te geven.

![ Demo ](./images/editfields.png)

Vervolgens ziet u een pop-upvenster met een schemahiërarchie waarin u velden kunt selecteren.

![ Demo ](./images/popup.png)

Velden zoals de ECID en de Orchestration eventID zijn vereist en als zodanig vooraf geselecteerd.

Een marketeer moet echter flexibele toegang hebben tot alle datapunten die context voor een reis bieden. Laten we dus ook de volgende velden als minimum selecteren (gevonden in het contextknooppunt Plaatsen):

- Plaats

Zodra dat wordt gedaan, klik O.K. ****.

![ Demo ](./images/popupok.png)

Adobe Journey Optimizer heeft ook een id nodig om de klant te identificeren. Aangezien Adobe Journey Optimizer is gekoppeld aan Adobe Experience Platform, wordt de primaire id van een schema automatisch beschouwd als de id voor de reis.
De primaire id houdt ook automatisch rekening met de volledige identiteitsgrafiek van Adobe Experience Platform en koppelt al het gedrag in alle beschikbare identiteiten, apparaten en kanalen aan hetzelfde profiel, zodat Adobe Journey Optimizer contextueel, relevant en consistent is. Klik **sparen**.

![ Demo ](./images/eventidentifier.png)

Uw gebeurtenis maakt dan deel uit van de lijst met beschikbare gebeurtenissen.

![ Demo ](./images/eventlist.png)

Tot slot moet u de `Orchestration eventID` voor uw aangepaste gebeurtenis herstellen.

Open de gebeurtenis opnieuw door erop te klikken in de lijst met gebeurtenissen.
Voor uw Gebeurtenis, klik op het **pictogram van de Payload van de Mening** naast **Gebieden**.

![ Demo ](./images/fieldseyepayload.png)

Het klikken van het **pictogram van de Payload van de Mening** opent omhoog een steekproefXDM nuttige lading voor deze gebeurtenis. De rol neer in de **nuttige lading** tot u de lijn `eventID` ziet.

![ Demo ](./images/fieldseyepayloadev.png)

Schrijf `eventID` neer aangezien u het in het laatste zult nodig hebben om uw configuratie te testen.

In dit voorbeeld is de waarde `eventID` `4df8dc10731eba7b0c37af83a9db38d4de7aa6aebcce38196d9d47929b9c598e` .

U hebt nu de gebeurtenis gedefinieerd die de reis zal activeren die we aan het bouwen zijn. Zodra de reis in werking wordt gesteld, zullen de geofence-gebieden zoals Stad, en anderen die u (zoals Land, Breedtegraad en Lengtegraad) kunt kiezen ter beschikking worden gesteld aan de reis.

Zoals besproken in de beschrijving van het gebruikscase, moeten we dan contextuele promoties bieden die afhankelijk zijn van het weer. Om weerinformatie te krijgen, zullen wij een externe gegevensbronnen moeten bepalen die ons van de weerinformatie voor die plaats zullen voorzien. U zult de **OpenWeather API** dienst gebruiken om ons van die informatie te voorzien.

## Volgende stappen

Ga naar [ 3.2.2 bepalen een externe gegevensbron ](./ex2.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer: Externe gegevensbronnen en douaneacties ](journey-orchestration-external-weather-api-sms.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
