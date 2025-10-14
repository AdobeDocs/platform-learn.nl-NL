---
title: Met publiek in dienst nemen met Federatieve Audience Composition
description: Leer over Federated Audience Composition (FAC) en hoe het gegevensarchitecten en gegevensingenieurs toelaat om hoogwaardig publiek van gesteunde gegevenspakhuizen direct te leiden en te activeren.
breadcrumb-title: Overzicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
source-git-commit: e7484bcb8fa643a5c86b7d97da8c45d333e2e0ae
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Betrokkenheid met publiek van gegevenspakhuis die de Samenstelling van het Federale publiek gebruikt

Federated Audience Composition (FAC) is een module voor Adobe Real-Time Customer Data Platform (Real-Time CDP) en Adobe Journey Optimizer. Het is ook beschikbaar bij het Adobe Real-Time CDP Composable publiek (een op maat gemaakte oplossing voor klanten als Composable CDP). Het machtigt gegevensarchitecten en gegevensingenieurs om hoogwaardig publiek direct van [&#x200B; gesteunde opslag van ondernemingsgegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} te leiden en te activeren, zonder klantengegevens te kopiëren of te bewegen in Adobe Experience Platform (AEP). Deze composable CDP benadering (een op maat gesneden oplossing voor klanten) richt zich op industrietrends, toelatend ondernemingen om hun gegevensinfrastructuur voor gepersonaliseerde digitale ervaringen te gebruiken terwijl het handhaven van gegevensbeheer.

## Bedrijfs context

SecurFinancial is een toonaangevende onderneming op het gebied van financiële diensten. Het gebruikt zijn rijkdom aan klantengegevens over verschillende bronnen om aanbiedingen en campagnes voor een groot aantal segmenten te personaliseren. Zij zijn van plan om de module van de Samenstelling van het Publiek van Adobe Real-Time CDP Federated te gebruiken, die ondernemingen toestaat om hun gegevenspakhuis voor gegevensbeheer te gebruiken terwijl het gebruiken van Experience Platform voor het leveren van gepersonaliseerde klantenervaringen. Belangrijkste voordelen zijn:

- **Toegang tot pakhuisgegevens**: Creeer high-value publiek van datasets in gesteunde gegevenspakhuizen zonder gegevensreplicatie.
- **Geminimaliseerde gegevensbeweging**: De gegevens van de vraag direct in het pakhuis, zonder duplicatie en het handhaven van gegevensbeheer.
- **verenigde ervaringswerkschema&#39;s**: Wissel en activeer publiek binnen Adobe Experience Platform voor kwesties van het dwars-kanaalgebruik.
- **Verbeterde verpersoonlijking**: Verrijkt profielen en publiek met pakhuisattributen aan macht in real time, teweeggebrachte ervaringen.

## Bedrijfsscenario

SecurFinancial wil graag een e-mailcampagne starten om haar klanten die voorgekwalificeerd zijn voor een lening op basis van goed krediet en geen actieve lening in hun SecurFinancial-portefeuille hebben, te heroriënteren. Terwijl zij online gedragsgegevens in real time invoeren, staan zij voor uitdagingen bij het identificeren van klantenpre-kwalificatie, aangezien zij van het opnemen van kredietinformatie in AEP beperkt zijn. Om pre-gekwalificeerde klanten zonder beperkte gegevens te kwalificeren, zullen zij Federated Audience Composition gebruiken om hun AEP gedragspubliek te verrijken.

## Hulplijn

Deze gids toont aan hoe wij het scenario SecureFinancial Bedrijfs steunen. Het gaat met name om de manier waarop we het publiek blootstellen aan systemen die dit soort publiek nodig hebben, zoals een S3-opslagaccount, een reis in Journey Optimizer om een e-mailcampagne te voeren en heroriëntering ter plaatse naar klanten die vooraf voor een lening waren goedgekeurd.

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
- De bekendheid met de concepten van Adobe Experience Platform, zoals schema&#39;s, datasets, en (geadviseerde) publiek: voltooi de [&#x200B; Inleiding aan playlist Adobe Experience Platform &#x200B;](https://experienceleague.adobe.com/nl/playlists/experience-platform-introduction?lang=en){target="_blank"} op Experience League).
- Toegang tot een gesteund [&#x200B; entrepot van ondernemingsgegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"}.
- Basiskennis van SQL voor het vragen van gegevenspakhuizen.
- **de Milieu&#39;s van Sandbox**: Creeer een zandbak in de instantie van uw organisatie veilig experimenteren zonder productiegegevens te beïnvloeden.
- **Verbinding van Data Warehouse**: Dit leerprogramma gebruikt een verbinding van Snowflake, maar u kunt om het even welk [&#x200B; gesteund gegevenspakhuis &#x200B;](https://experienceleague.adobe.com/nl/docs/federated-audience-composition/using/start/access-prerequisites) gebruiken.

Eerst, herzien de [&#x200B; Architectuur op hoog niveau &amp; Stroom voor Federatieve Samenstelling van het Publiek &#x200B;](fac-architecture-and-flow.md).
