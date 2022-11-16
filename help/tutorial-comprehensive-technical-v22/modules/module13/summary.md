---
title: Segmentactivering naar Microsoft Azure Event Hub - Overzicht en voordelen
description: Segmentactivering naar Microsoft Azure Event Hub - Overzicht en voordelen
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 2174ac52-b5dd-4bc8-ab5f-4d84ae9ef19b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# Samenvatting en voordelen

Gefeliciteerd en bedankt voor uw investering in uw tijd in het leren over de Hub van de Gebeurtenis van Microsoft Azure en Adobe Experience Platform!
In deze module, leerde u hoe te opstelling een Azure instantie van de Hub van de Gebeurtenis en hoe te om dat met Adobe Experience Platform te verbinden.

## Voordelen

Laten we de voordelen benadrukken van de integratie van Adobe Experience Platform met Microsoft Azure Event Hub:

- Met Microsoft Azure Event Hubs als Adobe Experience Platform Destination kunt u segmentkwalificatie in realtime vastleggen en deze verwerken met een Azure Event Hub-functie. Met zulk een functie van de Hub van de Gebeurtenis kunt u om het even welk soort manager van de activering van het douanesegment bouwen en als dusdanig om het even welk soort bestemming van derden integreren.

- Hoewel de bestemmingen slechts door gespecificeerde segmenten teweeggebracht worden, zal de activeringslading alle segmenten omvatten waarvoor bepaald profiel kwalificeert.

- Een segment activeert alleen een activering wanneer de status verandert. Een profiel dat bijvoorbeeld vier keer voor een segment in een periode van drie maanden in aanmerking komt, worden alleen de eerste twee keer geactiveerd. De eerste is een statuswijziging van naar **gereed**, wordt de tweede geactiveerd door een statuswijziging van **gereed** tot **bestaand**.

- Wanneer u segmenten voor bekende profielen activeert, wordt een volledig identiteitsoverzicht opgenomen in de activeringslading. Uw functie Azure kan om het even welke beschikbare identiteiten gebruiken om de segmenten aan een profiel in een derdetoepassing in kaart te brengen die, terwijl het gebruiken van het klantenherkenningsteken van de toepassing wordt beheerd.

- In deze module, werd de functie van de gebeurtenishub plaatselijk opgesteld (zuivert wijze in de Code van Visual Studio), die u veel het oplossen van problemen aanbiedt en opties zuivert.

## Bekijk dit

- N.v.t.

[Ga terug naar module 13](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../overview.md)
