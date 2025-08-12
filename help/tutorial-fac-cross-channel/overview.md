---
title: Vergrendel kanaalinzichten met Federated Audience Composition
description: De Federatieve Samenstelling van het Publiek is een krachtige eigenschap die gegevensarchitecten en gegevensingenieurs toelaat om publiek van derdegegevenspakhuizen direct te bouwen en te verrijken.
breadcrumb-title: Overzicht
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2025-08-11T00:00:00Z
source-git-commit: a5ae2695763bc3d6dce786861dcbc15f3422c035
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---


# Overzicht

Federated Audience Composition is een krachtige functie die beschikbaar is voor Adobe Real-Time Customer Data Platform- (Real-Time CDP) en Adobe Journey Optimizer-omgevingen. Het laat gegevensarchitecten en gegevensingenieurs toe om publiek van [ gesteund ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites){target="_blank"} derdegegevenspakhuizen direct te bouwen en te verrijken zonder gegevens in Adobe Experience Platform te herhalen. Dit leerprogramma verstrekt hands-on begeleiding voor technische gebruikers om de pakhuizen van ondernemingsgegevens te verbinden, publiek tot stand te brengen en te verrijken, en hen voor gepersonaliseerde marketing ervaringen te activeren.

## Leerdoelen

Door deze zelfstudie te voltooien, zult u:

- Begrijp hoe te om Adobe Experience Platform met een opslag van ondernemingsgegevens te verbinden.
- Leer om publiek tot stand te brengen en te beheren gebruikend Federated Audience Composition.
- Onderzoek hoe te om bestaand publiek met pakhuisgegevens te verrijken.
- Wijs een publiek met een federatie toe aan externe bestemmingen zoals Amazon S3.
- Bouw klantritten gebruikend gefederaliseerde publieksgegevens.
- Gegevens en processen valideren via praktische oefeningen en demo&#39;s.

Deze zelfstudie is ontworpen voor gegevensarchitecten en -engineers die werken met Real-Time CDP of Journey Optimizer. Het veronderstelt vertrouwdheid met Adobe Experience Platform en basisconcepten van het gegevenspakhuis.

## Bedrijfscontext

SecurFinancial is een toonaangevende onderneming op het gebied van financiële diensten. Het gebruikt zijn rijkdom aan klantengegevens over verschillende bronnen om aanbiedingen en campagnes voor een groot aantal segmenten te personaliseren. Ze zijn van plan om de Adobe Federated Audience Composition-functie te gebruiken waarmee bedrijven hun bestaande gegevenspakhuis kunnen gebruiken terwijl ze Adobe Experience Platform-toepassingen gebruiken om persoonlijke klantervaringen te bieden. Belangrijkste voordelen zijn:

- **Toegang tot pakhuisgegevens**: Creeer high-value publiek van datasets in gesteunde gegevenspakhuizen zonder gegevensreplicatie.
- **Geminimaliseerde gegevensbeweging**: De gegevens van de vraag direct in het pakhuis, die duplicatie verminderen en gegevensbeheer handhaven.
- **verenigde ervaringswerkschema&#39;s**: Wissel en activeer publiek binnen Adobe Experience Platform voor kwesties van het dwars-kanaalgebruik.
- **Verbeterde verpersoonlijking**: Verrijkt profielen en publiek met pakhuisattributen aan macht in real time, teweeggebrachte ervaringen.

## Bedrijfscenario

SecurFinancial wil graag een e-mailcampagne starten om haar klanten die voorgekwalificeerd zijn voor een lening op basis van goed krediet en geen actieve lening in hun SecurFinancial-portefeuille hebben, te heroriënteren. Terwijl zij online gedragsgegevens in real time invoeren, staan zij voor uitdagingen bij het identificeren van klantenprekwalificatie, aangezien zij van het opnemen van kredietinformatie in AEP beperkt zijn. Om voorgekwalificeerde klanten te kwalificeren zonder beperkte gegevens te verplaatsen, zullen zij Federated Audience Composition gebruiken om hun AEP gedragspubliek te verrijken.



## Vereisten

Om deze zelfstudie te volgen, zorg ervoor u hebt:

- Toegang tot een Adobe Experience Platform-account die is ingericht voor Real-Time CDP of Journey Optimizer.
- De toestemmingen van de Beheerder van het systeem of de capaciteit hebben gevormd toestemmingen.
- De bekendheid met de concepten van Adobe Experience Platform, zoals schema&#39;s, datasets, en (geadviseerde) publiek: voltooi de [ Inleiding aan playlist Adobe Experience Platform ](https://experienceleague.adobe.com/en/playlists/experience-platform-introduction?lang=en){target="_blank"} op Experience League).
- Toegang tot een ondersteund bedrijfsgegevenspakhuis (bijvoorbeeld Amazon Redshift, Azure Synapse Analytics, Snowflake of Google BigQuery).
- Basiskennis van SQL voor het vragen van gegevenspakhuizen.

## Deze zelfstudie gebruiken

Deze zelfstudie is gestructureerd voor technische gebruikers. De lessen bouwen op elkaar voort, zo volledig hen in orde tenzij anders vermeld.

## Technische noten

- **de Milieu&#39;s van Sandbox**: Creeer een zandbak in de instantie van Real-Time CDP van uw organisatie veilig experimenteren zonder productiegegevens te beïnvloeden.
- **Verbinding van Data Warehouse**: Dit leerprogramma gebruikt een verbinding van Snowflake, maar u kunt om het even welk [ gesteund wolkenpakhuis ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/start/access-prerequisites) gebruiken.

Begin met de [ 1&rbrace; les van de Verbinding van Data Warehouse &lbrace;beginnen uw milieu te vormen.](data-warehouse-connection.md)
