---
title: Segmentactivering naar Microsoft Azure Event Hub - Overzicht en voordelen
description: Segmentactivering naar Microsoft Azure Event Hub - Overzicht en voordelen
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---

# Samenvatting en voordelen

Gefeliciteerd en bedankt voor uw investering in uw tijd in het leren over de Hub van de Gebeurtenis van Microsoft Azure en Adobe Experience Platform!
In deze module, leerde u hoe te opstelling een Azure instantie van de Hub van de Gebeurtenis en hoe te om dat met Adobe Experience Platform te verbinden.

## Voordelen

Laten we de voordelen benadrukken van de integratie van Adobe Experience Platform met Microsoft Azure Event Hub:

- Met Microsoft Azure Event Hubs als Adobe Experience Platform Destination kunt u segmentkwalificatie in realtime vastleggen en deze verwerken met een Azure Event Hub-functie. Met zulk een functie van de Hub van de Gebeurtenis kunt u om het even welk soort manager van de activering van het douanesegment bouwen en als dusdanig om het even welk soort bestemming van de derde integreren.

- Hoewel de bestemmingen slechts door gespecificeerde segmenten teweeggebracht worden, zal de activeringslading alle segmenten omvatten waarvoor bepaald profiel kwalificeert.

- Een segment activeert alleen een activering wanneer de status van het segment verandert. Een profiel dat bijvoorbeeld vier keer voor een segment in een periode van drie maanden in aanmerking komt, worden alleen de eerste twee keer geactiveerd. Eerste is een statusverandering van aan **gerealiseerde**, tweede wordt teweeggebracht door een statusverandering van **gerealiseerde** aan **bestaand**.

- Wanneer u segmenten voor bekende profielen activeert, wordt een volledig identiteitsoverzicht opgenomen in de activeringslading. Uw functie Azure kan om het even welke beschikbare identiteiten gebruiken om de segmenten aan een profiel in een derdetoepassing in kaart te brengen die, terwijl het gebruiken van het klantenherkenningsteken van de toepassing wordt beheerd.

- In deze module, werd de functie van de gebeurtenishub plaatselijk opgesteld (zuivert wijze in de Code van Visual Studio), die u veel het oplossen van problemen aanbiedt en opties zuivert.

## Bekijk dit

- N.v.t.

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
