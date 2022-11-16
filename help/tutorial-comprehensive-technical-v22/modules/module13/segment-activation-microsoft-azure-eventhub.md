---
title: Segmentactivering naar Microsoft Azure Event Hub
description: Segmentactivering naar Microsoft Azure Event Hub
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 73c2576d-0a69-4d56-a671-9ae1f75580b9
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# 13. Real-Time CDP: Segmentactivering naar Microsoft Azure Event Hub

**Auteurs: [Marc Meewis](https://www.linkedin.com/in/marcmeewis/), [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

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

- Toegang tot [Adobe Experience Platform](https://experience.adobe.com/platform)
- Kennis van de omgeving van de AEP Demo-website
- Begrijp hoe u Streaming Segmenten in Adobe Experience Platform definieert, gebruikt en activeert

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem18.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--module18sandbox--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[13.0 Uw omgeving configureren](./ex0.md)

In deze oefening, zult u uw milieu van Microsoft Azure opzetten.

[13.1 Configureer uw Microsoft Azure EventHub-omgeving](./ex1.md)

In deze oefening zult u uw milieu van Microsoft Azure EventHub opstellen.

[13.2 Configureer uw Azure Event Hub Destination in Adobe Experience Platform](./ex2.md)

In deze oefening zult u uw in real time CDP bestemmingsverbinding plaatsen die segmenten in real time aan EventHub zal leveren die u in de vorige oefening hebt gevormd.

[13.3 Een segment maken](./ex3.md)

In deze oefening zult u een het stromen segment in Adobe Experience Platform creëren

[13.4 Segment activeren](./ex4.md)

In deze oefening zult u uw het stromen segment aan uw bestemming in real time CDP EventHub activeren.

[13.5 Uw Microsoft Azure-project maken](./ex5.md)

In deze oefening zult u een Azure functie creëren die in real time zal teweegbrengen wanneer het platform van de Ervaring van Adobe segmentkwalificaties aan de overeenkomstige Azure bestemming van de Hub van de Gebeurtenis activeert.

[13.6 End-to-end scenario](./ex6.md)

Op dit punt is alles ingesteld. U kunt nu bladeren op uw AEP Demo-website en segmentkwalificaties ophalen die worden geleverd aan uw Microsoft Azure EventHub Trigger-functie.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
