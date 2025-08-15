---
title: Federated Audience Composition High-level Architecture & Flow
seo-title: Federated Audience Composition high-level architecture & flow | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Federated Audience Composition-architectuur op hoog niveau en -stroom
description: Overzicht van de architectuur op hoog niveau en stroom van Federated Audience Composition.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-high-level-architecture.jpg
exl-id: 4cb0b730-4206-476b-93d9-776dfbd464ff
source-git-commit: 0564f516cfba7ea09ac9da19d94f46d984e9e00a
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Federated Audience Composition-architectuur op hoog niveau en -stroom

Alvorens wij in de stappen duiken voor het steunen van het bedrijfsscenario voor SecurFinancial, zullen wij de architectuur en de stroom op hoog niveau voor deze composable CDP benadering herzien.

De Federated module van de Samenstelling van de Publiek in Adobe Experience Platform breidt toegang tot gegevenspakhuis datasets zonder de onderliggende gegevens uit daardoor gegevensbeweging en duplicatie te minimaliseren.

Dit verstrekt organisaties ook de vereiste Composable architectuur, die reeds de vereiste werkzaamheden van het gegevensbeheer op hun pakhuis hebben voltooid en een nul-exemplaar patroon willen gebruiken waar Adobe Experience Platform de betrokkenheidsmotor wordt.

Het staat ondernemingen toe om informatie snel te verwerken die in één of meerdere gegevenspakhuizen wordt opgeslagen. Het verwijdert de noodzaak om gegevens in te voeren naar Adobe Experience. Bovendien, verleent het toegang tot nieuwe datasets die in de pakhuizen van ondernemingsgegevens verblijven maar tot nu toe ontoegankelijk voor de werkschema&#39;s van de klantenervaring zijn geweest. Voorbeelden zijn bijvoorbeeld historische transacties of persoonlijke gegevens die op geaggregeerd publieksniveau nuttig zullen zijn voor de betrokkenheid van klanten.

![ fac-architectuur ](assets/fac-architecture.png)

Nu zullen wij zich op het creëren van de Verbinding van a [ Data Warehouse ](data-warehouse-connection.md) bewegen.
