---
title: Adobe Experience Platform Data Collection & Real-time server Side Forwarding
description: In deze module, zult u de eerder gevormde datasets, schema's en het bezit van de Server van de Gegevensverzameling van Adobe Experience Platform gebruiken om gegevens te verzamelen, en dan door:sturen die gegevens server-kant aan een eindpunt van keus.
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: c157ca52-c84f-4398-a658-2b6067e41707
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 14. Real-Time CDP-verbindingen: Gebeurtenis doorsturen

**Auteur: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/), [Clement Delalande](https://www.linkedin.com/in/clement-delalande/)**

In deze module, zult u de eerder gevormde datasets, schema&#39;s en het bezit van de Cliënt van de Gegevensverzameling van Adobe Experience Platform gebruiken om gegevens te verzamelen, en dan door:sturen die gegevens server-kant aan een eindpunt van keus.

In deze module gaat u als volgt te werk:

- Een Adobe Experience Platform-eigenschap voor een gegevensverzamelingsserver maken
- De extensie Adobe Cloud Connector installeren en gebruiken in Adobe Experience Platform Data Collection
- Een Google-eindpunt voor functie maken en er gegevens naar streamen
- Een AWS-eindpunt maken en er gegevens naar streamen

Bekijk deze video om inzicht te krijgen in de waarde, de reis van de klant en het configuratieproces:

>[!VIDEO](https://video.tv.adobe.com/v/331987?quality=12&learn=on)

## Leerdoelen

- Word vertrouwd met de eigenschappen van de Server van de Inzameling van Gegevens van Adobe Experience Platform en de nieuwe uitbreiding van de Verbinding van de Wolk van de Adobe.
- Begrijp hoe u Adobe Experience Platform Web SDK-gegevens kunt hergebruiken in oplossingen van derden zoals Google en AWS
- Begrijp de architectuur achter de Inzameling van Gegevens van Adobe Experience Platform en de Kant die van de Server door:sturen.

## Vereisten

- Toegang tot gegevensverzameling in Adobe Experience Platform en Adobe Experience Platform
- Werken met Adobe Experience Platform-gegevenssets en XDM

>[!IMPORTANT]
>
>Deze zelfstudie is gemaakt om een bepaalde indeling voor de workshop te vergemakkelijken. Het gebruikt specifieke systemen en rekeningen waartot u geen toegang zou kunnen hebben. Zelfs zonder toegang denken we dat je nog veel kunt leren door deze zeer gedetailleerde inhoud te lezen. Als u een deelnemer bent aan een van de workshops en uw toegangsgegevens nodig hebt, neemt u contact op met uw Adobe-vertegenwoordiger die u de vereiste informatie zal verstrekken.

## Overzicht van architectuur

Heb een blik bij de hieronder architectuur, die de componenten benadrukt die in deze module zullen worden besproken en worden gebruikt.

![Overzicht van architectuur](../../assets/images/architecturem21.png)

## Te gebruiken sandbox

Gebruik deze sandbox voor deze module: `--aepSandboxId--`.

>[!NOTE]
>
>Vergeet niet de Chrome-extensie te installeren, configureren en gebruiken, zoals vermeld in [0.1 - Installeer de Chrome-extensie voor de documentatie van het Experience League](../module0/ex1.md)

## Uitoefening

[14.1 Een eigenschap voor het doorsturen van gegevensverzamelingsgebeurtenissen maken](./ex1.md)

In deze oefening, zult u uw het Door:sturen bezit van de Gebeurtenis van de Gegevensverzameling van Adobe Experience Platform creëren.

[14.2 Werk uw DataStream bij om gegevens ter beschikking te stellen van uw Gebeurtenis die van de Inzameling van Gegevens door:sturen bezit](./ex2.md)

In deze oefening, zult u uw bestaande DataStream bijwerken om gegevens te maken die door uw bezit van de Cliënt van de Inzameling van Gegevens van Adobe Experience Platform van de Cliënt van Gegevens beschikbaar aan uw bezit van de Server van de Inzameling van Adobe Experience Platform wordt verzameld.

[14.3 Een aangepaste webhaak maken en configureren](./ex3.md)

In deze oefening, zult u een douane webhaak tot stand brengen en vormen en zult u beginnen gegevens door:sturen die door Web SDK aan die douanewebhaak worden verzameld.

[14.4 Een Google Cloud-functie maken en configureren](./ex4.md)

In deze oefening, zult u een Functie van de Wolk van Google creëren en vormen en zult u beginnen gegevens door:sturen die door Web SDK aan Google worden verzameld.

[14.5 Toekomstige ontwikkelingen in het ecosysteem van AWS](./ex5.md)

In deze oefening, zult u uw milieu van AWS vormen gebruikend AWS API Gateway, AWS Kinesis, AWS Firehose en AWS S3 waarna u begint door:sturen gebeurtenisgegevens die door Web SDK worden verzameld.

[Samenvatting en voordelen](./summary.md)

Overzicht van deze module en overzicht van de voordelen.

>[!NOTE]
>
>Bedankt dat je je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform. Als u vragen hebt, wilt u algemene feedback delen over suggesties voor toekomstige inhoud. Neem rechtstreeks contact op met Wouter Van Geluwe door een e-mail te sturen naar **vangeluw@adobe.com**.

[Terug naar alle modules](../../overview.md)
