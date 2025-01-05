---
title: Overzicht
description: Het uitgangspunt voor de Ingenieurs van Gegevens, de Analysten van Gegevens, de Architecten van Gegevens, de Wetenschappers van Gegevens, de Ingenieurs van Orchestratie en Marketers om een volledig inzicht in de bedrijfswaarde van Adobe Experience Platform en al zijn Diensten van de Toepassing te krijgen.
doc-type: multipage-overview
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
source-git-commit: 21718a7c3a4df2793ae257a9b7cbe4466f1193f5
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 0%

---

# Uitgebreide technische zelfstudie voor Adobe Experience Platform

## Overzicht

Deze zelfstudie is het perfecte startpunt voor gegevensengineers, Data Analysts, Data Architects, Data Scientists, Orchestration Engineers en Marketers om een volledig inzicht te krijgen in de bedrijfswaarde van Adobe Experience Platform en alle toepassingsservices. Elke les concentreert zich op een echte uitdaging ondernemingen in het complexe ecosysteem van verpersoonlijking van vandaag zien en onderbreekt hoe het Experience Platform die uitdaging in diverse hands-on oefeningen oplost.

Deze zelfstudie is zeer divers en biedt duidelijke inzichten in de volgende toepassingen:

- Adobe Experience Platform
- Adobe Experience Platform-gegevensverzameling
- Real-time CDP
- Adobe Journey Optimizer
- Customer Journey Analytics

Deze zelfstudie richt zich niet alleen op Adobe toepassingen, maar houdt rekening met het bredere ecosysteem waarin merken werken. Om dat te doen, in sommige lessen is er een nadruk op hoe _niet-Adobe_ toepassingen met Adobe Experience Platform integreren. Als zodanig krijgt u meer inzicht in de manier waarop de volgende toepassingen samenwerken met Adobe Experience Platform:

- Amazon: AWS Lambda, AWS S3, AWS Kinesis
- Google: Google Cloud Platform, Google BigQuery, Google Display&amp;Video 360, Google AdWords
- Microsoft: Power BI, Azure EventHub, Azure Blob Storage
- Salesforce: Tableau
- Apache Kafka
- Postman
- ...

Nadat u de oefeningen in deze zelfstudie hebt voltooid, kunt u het volgende doen:

- Schema&#39;s, veldgroepen, gegevenssets en identiteiten configureren
- Vorm een bezit van de Inzameling van Gegevens van Adobe Experience Platform en opstelling de nieuwe uitbreiding van SDK van het Web in de Inzameling van de Gegevens van Adobe Experience Platform
- Gegevens in real-time naar Adobe Experience Platform streamen met Adobe Experience Platform Data Collection
- Gegevens in Adobe Experience Platform opnemen met behulp van een workflow of met behulp van een ETL-toepassing (extract, transform, load)
- Het Real-time klantprofiel in Adobe Experience Platform visualiseren en gebruiken
- Soorten publiek maken
- Verschillende Adobe Experience Platform API&#39;s gebruiken
- SQL gebruiken om query&#39;s uit te voeren op uw gegevens in Adobe Experience Platform
- Realtime, op trigger gebaseerde reizen configureren en uitvoeren
- Gebruik Real-time CDP om actie te ondernemen door een publiek aan diverse bestemmingen te activeren
- Gebruik Customer Journey Analytics om te rapporteren over omnichannel klantgegevens uit verschillende bronnen, waaronder Google BigQuery

## Vereisten

Als u dit leerprogramma wilt nemen gebruikend uw eigen instantie van Adobe Experience Platform, die de instructies [ hier ](./setup.md) volgt om uw org voor het leerprogramma voor te bereiden.

- Toegang tot Adobe Experience Platform: [ https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot de Inzameling van Gegevens van Adobe Experience Platform: [ https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Toegang tot het Systeem van de Demo: [ https://dsn.adobe.com/](https://dsn.adobe.com/)

## Video&#39;s

U kunt veel interessante video&#39;s van onze webinars van de Academie van de Technologie, van bootcamps en meer op ons [ Communautaire kanaal van YouTube van de Makers van de Ervaring vinden Communautaire ](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Voltooiing en certificering

Deze zelfstudie maakt deel uit van een Adobe Certification-cursus. U kunt omhoog voor de cursus naast dit leerprogramma ondertekenen door [ https://certification.adobe.com ](https://certification.adobe.com) te gaan.

Voor elke module die u het gebruiken van het hieronder leerprogramma voltooit, moet u een bewijs van voltooiing voorleggen zoals vermeld [ hier ](./completion.md).

## Inhoud

Om het statuut van de hieronder inhoud te controleren, gelieve naar de [ statuspagina ](./status.md) te gaan.

[0. Aan de slag](./modules/gettingstarted/gettingstarted/getting-started.md)

In deze grondmodule, zult u alles plaatsen zodat u tot het demomilieu kunt toegang hebben en gebruiken.

**de Investering van de Tijd:** 30 minuten

### 1. Gegevensverzameling

[1.1 Foundation - Setup of Adobe Experience Platform Data Collection &amp; Web SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

In deze basismodule leert u meer over Adobe Experience Platform Data Collection en de nieuwe Web SDK-extensie.

**de Investering van de Tijd:** 30 minuten

[1.2 Stichting - de Ingestie van Gegevens](./modules/datacollection/module1.2/data-ingestion.md)

In deze basismodule gaat u gegevens uit verschillende bronnen in Adobe Experience Platform invoeren

**de Investering van de Tijd:** 120 minuten

[1.3 Federale Audience Composition](./modules/datacollection/module1.3/fac.md)

In deze module, zult u leren hoe te om een Federated model van het Soorten publiek te plaatsen en publiek te produceren gebruikend gefedereerde gegevens.

**de Investering van de Tijd:** 90 minuten

### 2. Real-Time CDP B2C

[2.1 Foundation - Real-time klantprofiel](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

In deze basismodule gaat u het Real-time klantprofiel in Adobe Experience Platform verkennen met behulp van de gebruikersinterface en de API.

**de Investering van de Tijd:** 90 minuten

[2.2 Intelligente diensten](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

In deze module leert u hoe u Adobe Experience Platform Intelligent Services kunt instellen, configureren en gebruiken.

**de Investering van de Tijd:** 60 minuten

[2.3 Real-Time CDP - Bouw een publiek en onderneem actie](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

In deze module, zult u een publiek vormen en zult het publiek aan verscheidene bestemmingen, met inbegrip van Google DV360, Adobe Target en AWS S3 activeren.

**de Investering van de Tijd:** 90 minuten

[2.4 Real-Time CDP: Audience Activation naar Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

In deze module, zult u een bestemming Microsoft Azure EventHub als bestemming in real time voor Adobe Experience Platform in real time CDP plaatsen. U zult ook opstelling en een Azure functie opstellen die in real time zal teweegbrengen wanneer Adobe Experience Platform een publiekslading aan uw Azure bestemming EventHub levert. De Azure Functie die u zult teweegbrengen zal het mechanisme van Adobe Experience Platform in real time CDP activeringsmogelijkheden tonen.
Als deel van deze module zult u ook een begrip van krijgen wat in real time CDP teweegbrengt om een nuttige lading aan een gespecificeerde bestemming eigenlijk te leveren. We zullen ook de status van een publiekskwalificatie bespreken en de relatie ervan met activering.

**de Investering van de Tijd:** 90 minuten

[2.5 Real-Time CDP-verbindingen: gebeurtenissen doorsturen](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

In deze module, zult u de eerder gevormde datasets, schema&#39;s en het bezit van de Inzameling van Gegevens van Adobe Experience Platform gebruiken om gegevens te verzamelen, en dan door:sturen die gegevensserver-kant aan verscheidene eindpunten, zoals het Platform Pub/Sub van Google Cloud en AWS Kinesis.

**de Investering van de Tijd:** 90 minuten

[2.6 Gegevens streamen van Apache Kafka naar Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

In deze module leert u hoe u uw eigen Apache Kafka-cluster instelt, onderwerpen, producenten en consumenten definieert en gegevens stroomt naar Adobe Experience Platform met behulp van de Adobe Experience Platform Sink Connector voor Kafka Connect.

**de Investering van de Tijd:** 90 minuten

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestratie](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

In deze module zult u Adobe Journey Optimizer gebruiken om een op trigger-gebaseerde reis uit te bouwen.

**de Investering van de Tijd:** 60 minuten

[3.2 Adobe Journey Optimizer: Externe gegevensbronnen en aangepaste acties](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

In deze module, zult u Adobe Journey Optimizer gebruiken om aan klantengedrag, zowel online als off-line te luisteren, en aan het op een intelligente, contextafhankelijke en manier in real time over diverse kanalen te antwoorden.

**de Investering van de Tijd:** 90 minuten

[3.3 Adobe Journey Optimizer: Offer Decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

In deze module, zult u Adobe Experience Platform - Aanbiedingen/de Toepassingsdienst van Beslissing op een praktische manier gebruiken om Persoonlijke Aanbiedingen en uw eigen Activiteit van de Aanbieding te vormen.

**de Investering van de Tijd:** 120 minuten

[3.4 Adobe Journey Optimizer: Reizen op basis van gebeurtenissen](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

In deze module leert u alles wat er over Journey Optimizer te weten is, wat bedrijven helpt om verbonden, contextafhankelijke en persoonlijke ervaringen te ontwerpen en te leveren aan hun klanten.

**de Investering van de Tijd:** 120 minuten

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: bouw een dashboard met Analysis Workspace bovenop Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

In deze module, zult u Online aan Off-line inzichten door een dashboard te vormen die omni-kanaalgegevens zoals de Interacties van de Website, Mobiele Interacties van de App, Interacties van het Centrum van de Vraag, Interacties In-Store en veel meer bevatten.

**de Investering van de Tijd:** 120 minuten

[4.2 Customer Journey Analytics: Gegevens van Googles Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

In deze module stelt u uw eigen exemplaar van Google Cloud Platform in, laadt u demogegevens in het Google Cloud Platform en gebruikt u vervolgens de BigQuery Source Connector om deze gegevens van het Google Cloud Platform in Adobe Experience Platform in te voeren. Tot slot zult u Customer Journey Analytics gebruiken om die gegevens te visualiseren.

**de Investering van de Tijd:** 120 minuten

### 5. Data Distiller

[5.1 Query-service](./modules/datadistiller/module5.1/query-service.md)

In deze module leert u hoe u de Adobe Experience Platform Query Service kunt gebruiken.

**de Investering van de Tijd:** 90 minuten
