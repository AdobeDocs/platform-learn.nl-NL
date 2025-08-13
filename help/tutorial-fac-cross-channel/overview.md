---
title: Vergrendel kanaalinzichten met Federated Audience Composition
description: De Federatieve Samenstelling van het Publiek is een krachtige eigenschap die gegevensarchitecten en gegevensingenieurs toelaat om publiek van derdegegevenspakhuizen direct te bouwen en te verrijken.
breadcrumb-title: Overzicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
exl-id: 9d5a2e40-6cda-4164-87db-1bfffe3438e3
source-git-commit: a3c8d8b03472d01f491bf787ed647a696d3a5524
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Overzicht

Federated Audience Composition is een krachtige functie die beschikbaar is voor Adobe Real-Time Customer Data Platform- (Real-Time CDP) en Adobe Journey Optimizer-omgevingen. Het laat gegevensarchitecten en gegevensingenieurs toe om publiek van [ gesteund ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} derdegegevenspakhuizen direct te bouwen en te verrijken zonder gegevens in Adobe Experience Platform te herhalen. Dit leerprogramma verstrekt hands-on begeleiding voor technische gebruikers om de pakhuizen van ondernemingsgegevens te verbinden, publiek tot stand te brengen en te verrijken, en hen voor gepersonaliseerde marketing ervaringen te activeren.

## Visuele hulplijn

Deze visuele gids toont u de stappen voor elk van de activiteiten die worden genomen om diverse aspecten van het bedrijfsscenario te steunen. Het doel is om u van activiteiten te voorzien die u in uw milieu kunt hefboomwerking, met inbegrip van:

- Verbind Adobe Experience Platform met een bedrijfs gegevenspakhuis.
- Creeer en beheer publiek gebruikend Federated de Samenstelling van het Publiek.
- Wijs een publiek met een federatie toe aan externe bestemmingen zoals Amazon S3.
- Verrijk bestaande doelgroepen met gefederaliseerde gegevens.
- Maak een publiek dat de personalisatie &quot;in-the-moment&quot; aanstuurt.
- Bouw klantritten gebruikend gefederaliseerde publieksgegevens.

Deze handleiding is ontworpen voor gegevensarchitecten en gegevensengineers die werken met Real-Time CDP of Journey Optimizer. Het veronderstelt vertrouwdheid met Adobe Experience Platform en basisconcepten van het gegevenspakhuis.

## Bedrijfscontext

SecurFinancial is een toonaangevende onderneming op het gebied van financiële diensten. Het gebruikt zijn rijkdom aan klantengegevens over verschillende bronnen om aanbiedingen en campagnes voor een groot aantal segmenten te personaliseren. Ze zijn van plan om de Adobe Federated Audience Composition-functie te gebruiken waarmee bedrijven hun bestaande gegevenspakhuis kunnen gebruiken terwijl ze Adobe Experience Platform-toepassingen gebruiken om persoonlijke klantervaringen te bieden. Belangrijkste voordelen zijn:

- **Toegang tot pakhuisgegevens**: Creeer high-value publiek van datasets in gesteunde gegevenspakhuizen zonder gegevensreplicatie.
- **Geminimaliseerde gegevensbeweging**: De gegevens van de vraag direct in het pakhuis, die duplicatie verminderen en gegevensbeheer handhaven.
- **verenigde ervaringswerkschema&#39;s**: Wissel en activeer publiek binnen Adobe Experience Platform voor kwesties van het dwars-kanaalgebruik.
- **Verbeterde verpersoonlijking**: Verrijkt profielen en publiek met pakhuisattributen aan macht in real time, teweeggebrachte ervaringen.

## Bedrijfscenario

SecurFinancial wil graag een e-mailcampagne starten om haar klanten die voorgekwalificeerd zijn voor een lening op basis van goed krediet en geen actieve lening in hun SecurFinancial-portefeuille hebben, te heroriënteren. Terwijl zij online gedragsgegevens in real time invoeren, staan zij voor uitdagingen bij het identificeren van klantenprekwalificatie, aangezien zij van het opnemen van kredietinformatie in AEP beperkt zijn. Om voorgekwalificeerde klanten te kwalificeren zonder beperkte gegevens te verplaatsen, zullen zij Federated Audience Composition gebruiken om hun AEP gedragspubliek te verrijken.

## Vereisten

Als u vergelijkbare activiteiten wilt uitvoeren in uw omgeving, moet u ervoor zorgen dat:

- Toegang tot een Adobe Experience Platform-account die is ingericht voor Real-Time CDP of Journey Optimizer.
- De toestemmingen van de Beheerder van het systeem of de capaciteit hebben gevormd toestemmingen.
- De bekendheid met de concepten van Adobe Experience Platform, zoals schema&#39;s, datasets, en (geadviseerde) publiek: voltooi de [ Inleiding aan playlist Adobe Experience Platform ](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"} op Experience League).
- Toegang tot een ondersteund bedrijfsgegevenspakhuis (bijvoorbeeld Amazon Redshift, Azure Synapse Analytics, Snowflake of Google BigQuery).
- Basiskennis van SQL voor het vragen van gegevenspakhuizen.
- **de Milieu&#39;s van Sandbox**: Creeer een zandbak in de instantie van Real-Time CDP van uw organisatie veilig experimenteren zonder productiegegevens te beïnvloeden.
- **Verbinding van Data Warehouse**: Dit leerprogramma gebruikt een verbinding van Snowflake, maar u kunt om het even welk [ gesteund wolkenpakhuis ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites) gebruiken.

Laten wij met de [ Verbinding van Data Warehouse ](data-warehouse-connection.md) beginnen.
