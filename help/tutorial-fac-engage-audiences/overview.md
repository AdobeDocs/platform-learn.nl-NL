---
title: Neem contact op met Soorten publiek uit uw Data Warehouse met behulp van Federatieve Audience Composition
description: De Federatieve Samenstelling van het Publiek is een krachtige eigenschap die gegevensarchitecten en gegevensingenieurs toelaat om publiek van derdegegevenspakhuizen direct te bouwen en te verrijken.
breadcrumb-title: Overzicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
source-git-commit: dd5f594a54a9cab8ef78d36d2cf15a9b5f2b682a
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Neem contact op met Soorten publiek uit uw Data Warehouse met behulp van Federatieve Audience Composition

Federated Audience Composition (FAC) is een krachtige functie die beschikbaar is voor Adobe Real-Time Customer Data Platform- (Real-Time CDP) en Adobe Journey Optimizer-omgevingen. Het machtigt gegevensarchitecten en gegevensingenieurs om hoogwaardig publiek direct van [ gesteunde opslag van ondernemingsgegevens ](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} te leiden en te activeren, zonder klantengegevens te kopiëren of te bewegen in Adobe Experience Platform (AEP). Deze composable CDP benadering (een op maat gesneden oplossing voor klanten) richt zich op industrietrends, toelatend ondernemingen om hun gegevensinfrastructuur voor gepersonaliseerde digitale ervaringen te gebruiken terwijl het handhaven van gegevensbeheer.

## Bedrijfscontext

SecurFinancial is een toonaangevende onderneming op het gebied van financiële diensten. Het gebruikt zijn rijkdom aan klantengegevens over verschillende bronnen om aanbiedingen en campagnes voor een groot aantal segmenten te personaliseren. Zij zijn van plan om de eigenschap van de Samenstelling van het Publiek van Adobe te gebruiken Federated om publiek van hun gegevenspakhuis te leiden terwijl het activeren van hen aan de bestemmingen van Adobe Experience Platform, evenals Adobe Journey Optimizer om een op maat gemaakte oplossing voor het leveren van gepersonaliseerde klantenervaringen te leveren.

## Bedrijfscenario

SecurFinancial wil graag een e-mailcampagne starten om haar klanten die voorgekwalificeerd zijn voor een lening op basis van goed krediet en geen actieve lening in hun SecurFinancial-portefeuille hebben, te heroriënteren. Terwijl zij online gedragsgegevens in real time invoeren, staan zij voor uitdagingen bij het identificeren van klantenpre-kwalificatie, aangezien zij van het opnemen van kredietinformatie in AEP beperkt zijn. Om pre-gekwalificeerde klanten zonder beperkte gegevens te kwalificeren, zullen zij Federated Audience Composition gebruiken om hun AEP gedragspubliek te verrijken.

## Hulplijn

Deze gids toont aan hoe wij het SecureFinancial Bedrijfs scenario steunen. Het gaat met name om de manier waarop we het publiek blootstellen aan systemen die dit soort publiek nodig hebben, zoals een S3-opslagaccount, een reis in Journey Optimizer om een e-mailcampagne te voeren en heroriëntering ter plaatse naar klanten die vooraf voor een lening waren goedgekeurd.

De volgende stappen worden uitgevoerd:

1. Verbind Adobe Experience Platform met een bedrijfs gegevenspakhuis.
2. Maak een publiek met Federated Audience Composition.
3. Wijs een gefedereerd publiek aan externe bestemming van Amazon S3 toe.
4. Bouw een klantenreis gebruikend gefederaliseerde publieksgegevens.
5. Verrijk een publiek met gefederaliseerde gegevens.
6. Op de Edge &#39;in-the-time&#39; personalisatie aansturen.

## Vereisten

Als u vergelijkbare activiteiten wilt uitvoeren in uw omgeving, moet u ervoor zorgen dat:

- Toegang tot een Adobe Experience Platform-account die is ingericht voor Real-Time CDP of Journey Optimizer.
- De toestemmingen van de Beheerder van het systeem of de capaciteit hebben gevormd toestemmingen.
- De bekendheid met de concepten van Adobe Experience Platform, zoals schema&#39;s, datasets, en (geadviseerde) publiek: voltooi de [ Inleiding aan playlist Adobe Experience Platform ](https://experienceleague.adobe.com/nl/playlists/experience-platform-introduction?lang=en){target="_blank"} op Experience League).
- Toegang tot een gesteund [ entrepot van ondernemingsgegevens ](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}.
- Basiskennis van SQL voor het vragen van gegevenspakhuizen.
- **de Milieu&#39;s van Sandbox**: Creeer een zandbak in de instantie van uw organisatie veilig experimenteren zonder productiegegevens te beïnvloeden.
- **Verbinding van Data Warehouse**: Dit leerprogramma gebruikt een verbinding van Snowflake, maar u kunt om het even welk [ gesteund gegevenspakhuis ](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites) gebruiken.

Eerst, herzien de [ Architectuur op hoog niveau &amp; Stroom voor Federatieve Samenstelling van het Publiek ](fac-architecture-and-flow.md).
