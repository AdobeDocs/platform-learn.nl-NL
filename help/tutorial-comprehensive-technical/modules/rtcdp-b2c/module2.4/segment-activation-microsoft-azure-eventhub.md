---
title: Segmentactivering naar Microsoft Azure Event Hub
description: Segmentactivering naar Microsoft Azure Event Hub
kt: 5342
doc-type: tutorial
exl-id: 23713cb4-2055-43e8-9380-0ca8845a75e8
source-git-commit: 0dbcda0cfc9f199a44c845c1b5caf00a8d740251
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# 2.4 Real-Time CDP: Segmentactivering naar Microsoft Azure Event Hub

**Auteurs: [ Marc Meewis ](https://www.linkedin.com/in/marcmeewis/), [ Wouter Van Geluwe ](https://www.linkedin.com/in/woutervangeluwe/)**

In deze module, zult u een bestemming Microsoft Azure EventHub als bestemming in real time voor Adobe Experience Platform in real time CDP plaatsen. U zult ook opstelling en een Azure functie opstellen die in real time zal teweeggebracht worden wanneer Adobe Experience Platform een segmentlading aan uw Azure bestemming EventHub levert. De Azure Functie die u zult teweegbrengen zal het mechanisme van Adobe Experience Platform in real time CDP activeringsmogelijkheden tonen.

Als deel van deze module zult u ook een begrip van krijgen wat in real time CDP teweegbrengt om een nuttige lading aan een gespecificeerde bestemming eigenlijk te leveren. We zullen ook de status van een segmentkwalificatie bespreken en de relatie ervan met activering.

Adobe Experience Platform CDP in real time steunt gegevensactivering aan het stromen de bestemmingen van de wolkenopslag, die u toestaan om publieksgegevens en gebeurtenissen in real time naar deze bestemmingen in formaat uit te voeren JSON. U kunt bedrijfslogica bovenop deze gebeurtenissen in uw bestemmingen dan beschrijven

Microsoft Azure Event Hubs is een volledig beheerde, realtime service voor gegevensinvoer die eenvoudig, vertrouwd en schaalbaar is. Stroom miljoenen gebeurtenissen per seconde van om het even welke bron om dynamische gegevenspijpleidingen te bouwen en onmiddellijk aan bedrijfsuitdagingen te antwoorden.

## Leerdoelen

- Word vertrouwd met de Microsoft Azure Event Hubs
- Een RTCDP-bestemming instellen voor uw Microsoft Azure Event Hub
- Begrijp wanneer CDP in real time activeert en wat de activeringslading als kijkt
- De Code van Visual Studio van de opstelling om uw Azure project te ontwikkelen, te testen en op te stellen
- Maak en implementeer een Azure-functie die segmentkwalificaties gebruikt die in real-time door RTCDP worden geleverd

## Vereisten

- Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform)
- Kennis van de omgeving van de AEP Demo-website
- Begrijp hoe u Streaming Segmenten in Adobe Experience Platform definieert, gebruikt en activeert

>[!NOTE]
>
>Vergeet niet om de Uitbreiding van Chrome te installeren, te vormen en te gebruiken zoals die in [ wordt van verwijzingen voorzien installeer de uitbreiding van Chrome voor de documentatie van het Experience League ](../../gettingstarted/gettingstarted/ex1.md)

## Uitoefening

[2.4.0 Uw omgeving configureren](./ex0.md)

In deze oefening, zult u uw milieu van Microsoft Azure opzetten.

[2.4.1 De Microsoft Azure EventHub-omgeving configureren](./ex1.md)

In deze oefening zult u uw milieu van Microsoft Azure EventHub opstellen.

[2.4.2 Configureer uw Azure Event Hub Destination in Adobe Experience Platform](./ex2.md)

In deze oefening zult u uw in real time CDP bestemmingsverbinding plaatsen die segmenten in real time aan EventHub zal leveren die u in de vorige oefening hebt gevormd.

[2.4.3 Een segment maken](./ex3.md)

In deze oefening zult u een het stromen segment in Adobe Experience Platform creëren

[2.4.4 Segment activeren](./ex4.md)

In deze oefening zult u uw het stromen segment aan uw bestemming in real time CDP EventHub activeren.

[2.4.5 Uw Microsoft Azure-project maken](./ex5.md)

In deze oefening zult u een Azure functie creëren die in real time zal teweegbrengen wanneer het platform van de Ervaring van de Adobe segmentkwalificaties aan de overeenkomstige Azure bestemming van de Hub van de Gebeurtenis activeert.

[2.4.6 Eindscenario](./ex6.md)

Op dit punt is alles ingesteld. U kunt nu bladeren op uw AEP Demo-website en segmentkwalificaties ophalen die worden geleverd aan uw Microsoft Azure EventHub Trigger-functie.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](../../../overview.md)
