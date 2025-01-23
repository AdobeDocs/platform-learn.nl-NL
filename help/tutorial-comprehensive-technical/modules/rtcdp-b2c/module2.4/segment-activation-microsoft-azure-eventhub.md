---
title: Audience Activation naar Microsoft Azure Event Hub
description: Audience Activation naar Microsoft Azure Event Hub
kt: 5342
doc-type: tutorial
exl-id: 23713cb4-2055-43e8-9380-0ca8845a75e8
source-git-commit: bd46be455f88007174f7e6be9a1ce5f508edc09b
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 2.4 Real-Time CDP: Audience Activation naar Microsoft Azure Event Hub

In deze module, zult u een bestemming Microsoft Azure EventHub als bestemming in real time voor Adobe Experience Platform in real time CDP plaatsen. U zult ook opstelling en een Azure functie opstellen die in real time zal teweegbrengen wanneer Adobe Experience Platform een publiekslading aan uw Azure bestemming EventHub levert. De Azure Functie die u zult teweegbrengen zal het mechanisme van Adobe Experience Platform in real time CDP activeringsmogelijkheden tonen.

Als deel van deze module zult u ook een begrip van krijgen wat in real time CDP teweegbrengt om een nuttige lading aan een gespecificeerde bestemming eigenlijk te leveren. We zullen ook de status van een publiekskwalificatie bespreken en de relatie ervan met activering.

Adobe Experience Platform CDP in real time steunt gegevensactivering aan het stromen de bestemmingen van de wolkenopslag, die u toestaan om publieksgegevens en gebeurtenissen in real time naar deze bestemmingen in formaat uit te voeren JSON. U kunt bedrijfslogica bovenop deze gebeurtenissen in uw bestemmingen dan beschrijven

Microsoft Azure Event Hubs is een volledig beheerde, realtime service voor gegevensinvoer die eenvoudig, vertrouwd en schaalbaar is. Stroom miljoenen gebeurtenissen per seconde van om het even welke bron om dynamische gegevenspijpleidingen te bouwen en onmiddellijk aan bedrijfsuitdagingen te antwoorden.

## Leerdoelen

- Word vertrouwd met de Microsoft Azure Event Hubs
- Een RTCDP-bestemming instellen voor uw Microsoft Azure Event Hub
- Begrijp wanneer CDP in real time activeert en wat de activeringslading als kijkt
- De Code van Visual Studio van de opstelling om uw Azure project te ontwikkelen, te testen en op te stellen
- Maak en implementeer een Azure-functie die publiekskwalificaties gebruikt die in real-time door RTCDP worden geleverd

## Vereisten

- Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform)
- Begrijp hoe u publiek in Adobe Experience Platform definieert, gebruikt en activeert

>[!NOTE]
>
>Vergeet niet om de Uitbreiding van Chrome te installeren, te vormen en te gebruiken zoals die in [ wordt van verwijzingen voorzien installeer de uitbreiding van Chrome voor de documentatie van het Experience League ](../../gettingstarted/gettingstarted/ex1.md)

## Uitoefening

[2.4.1 Uw omgeving configureren](./ex1.md)

In deze oefening, zult u uw milieu van Microsoft Azure opzetten.

[2.4.2 Uw Microsoft Azure EventHub-omgeving configureren](./ex2.md)

In deze oefening zult u uw milieu van Microsoft Azure EventHub opstellen.

[2.4.3 Configureer uw Azure Event Hub Destination in Adobe Experience Platform](./ex3.md)

In deze oefening zult u uw Real-time CDP bestemmingsverbinding opstelling die publiek in real time aan de instantie van de Hub van de Gebeurtenis zal leveren die u in de vorige oefening hebt gevormd.

[2.4.4 Een publiek maken](./ex4.md)

In deze oefening zult u een publiek in Adobe Experience Platform creëren

[2.4.5 Activeer uw publiek](./ex5.md)

In deze oefening zult u uw publiek aan uw bestemming activeren EventHub.

[2.4.6 Maak uw Microsoft Azure-project](./ex6.md)

In deze oefening zult u een Azure functie creëren die in real time zal teweegbrengen wanneer het platform van de Ervaring van de Adobe publiekskwalificaties aan de overeenkomstige Azure bestemming van de Hub van de Gebeurtenis levert.

[2.4.7 End-to-end scenario](./ex7.md)

Op dit punt is alles ingesteld. U kunt nu bladeren op uw demowebsite en publiekskwalificaties krijgen die worden geleverd aan uw Microsoft Azure Event Hub Trigger-functie.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

![ Indexen van de Tech ](./../../../assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](../../../overview.md)
