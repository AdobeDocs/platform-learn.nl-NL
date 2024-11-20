---
title: Audience Activation naar Microsoft Azure Event Hub - Overzicht en voordelen
description: Audience Activation naar Microsoft Azure Event Hub - Overzicht en voordelen
kt: 5342
doc-type: tutorial
exl-id: 3b598ffc-875e-468d-b91c-882062e8203f
source-git-commit: 216914c9d97827afaef90e21ed7d4f35eaef0cd3
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---

# Samenvatting en voordelen

Gefeliciteerd en bedankt voor uw investering in uw tijd in het leren over de Hub van de Gebeurtenis van Microsoft Azure en Adobe Experience Platform!
In deze module, leerde u hoe te opstelling een Azure instantie van de Hub van de Gebeurtenis en hoe te om dat met Adobe Experience Platform te verbinden.

## Voordelen

Laten we de voordelen benadrukken van de integratie van Adobe Experience Platform met Microsoft Azure Event Hub:

- Met Microsoft Azure Event Hubs als Adobe Experience Platform Destination kunt u publiekskwalificatie in realtime vastleggen en deze verwerken met een Azure Event Hub-functie. Met zulk een functie van de Hub van de Gebeurtenis kunt u om het even welk soort manager van de activering van het douanepubliek bouwen en als dusdanig om het even welk soort van derdebestemming integreren.

- Hoewel de bestemmingen slechts door gespecificeerde publiek teweeggebracht worden, zal de activeringslading alle publiek omvatten waarvoor bepaald profiel kwalificeert.

- Een publiek activeert alleen een activering wanneer de status verandert. Een profiel dat bijvoorbeeld vier keer voor een publiek in een periode van drie maanden in aanmerking komt, worden alleen de eerste twee keer geactiveerd. Eerste is een statusverandering van aan **gerealiseerde**, tweede wordt teweeggebracht door een statusverandering van **gerealiseerde** aan **bestaand**.

- Bij het activeren van soorten publiek voor bekende profielen wordt een volledig identiteitsoverzicht opgenomen in de activeringslading. Uw Azure-functie kan alle beschikbare identiteiten gebruiken om het publiek toe te wijzen aan een profiel dat wordt beheerd in een externe toepassing, terwijl de klant-id van de toepassing wordt gebruikt.

- In deze module, werd de functie van de gebeurtenishub plaatselijk opgesteld (zuivert wijze in de Code van Visual Studio), die u veel het oplossen van problemen aanbiedt en opties zuivert.

## Bekijk dit

- N.v.t.

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
