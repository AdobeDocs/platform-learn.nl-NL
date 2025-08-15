---
title: Federated Audience Composition High-level Architecture & Flow
seo-title: Federated Audience Composition High-level Architecture & Flow | Engage with Audiences from your Data Warehouse using Federated Audience Composition
breadcrumb-title: Federated Audience Composition High-level Architecture & Flow
description: Overzicht van de architectuur op hoog niveau en stroom van Federated Audience Composition.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-high-level-architecture.jpg
source-git-commit: dd5f594a54a9cab8ef78d36d2cf15a9b5f2b682a
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Federated Audience Composition High-level Architecture &amp; Flow

Alvorens wij in de stappen duiken voor het steunen van het bedrijfsscenario voor SecurFinancial, zullen wij de architectuur en de stroom op hoog niveau voor deze composable CDP benadering herzien.

De Federated module van de Samenstelling van de Publiek in Adobe Experience Platform breidt toegang tot gegevenspakhuis datasets zonder de onderliggende gegevens uit daardoor gegevensbeweging en duplicatie te minimaliseren.

Dit verstrekt organisaties ook de vereiste Composable architectuur, die reeds de vereiste werkzaamheden van het gegevensbeheer op hun pakhuis hebben voltooid en een nul-exemplaar patroon willen gebruiken waar Adobe Experience Platform de betrokkenheidsmotor wordt.

Het staat ondernemingen toe om informatie snel te verwerken die in één of meerdere gegevenspakhuizen wordt opgeslagen. Het verwijdert de noodzaak om gegevens in te voeren naar Adobe Experience. Bovendien, verleent het toegang tot nieuwe datasets die in de pakhuizen van ondernemingsgegevens verblijven maar tot nu toe ontoegankelijk voor de werkschema&#39;s van de klantenervaring zijn geweest. Voorbeelden zijn bijvoorbeeld historische transacties of persoonlijke gegevens die op geaggregeerd publieksniveau nuttig zullen zijn voor de betrokkenheid van klanten.

![ fac-architectuur ](assets/fac-architecture.png)

Nu zullen wij zich op het creëren van de Verbinding van a [ Data Warehouse ](data-warehouse-connection.md) bewegen.

