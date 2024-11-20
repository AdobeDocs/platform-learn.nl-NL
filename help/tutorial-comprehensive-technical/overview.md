---
title: Overzicht
description: Het uitgangspunt voor de Ingenieurs van Gegevens, de Analysten van Gegevens, de Architecten van Gegevens, de Wetenschappers van Gegevens, de Ingenieurs van Orchestratie en Marketers om een volledig inzicht in de bedrijfswaarde van Adobe Experience Platform en al zijn Diensten van de Toepassing te krijgen.
doc-type: multipage-overview
hide: false
exl-id: 88c19383-c185-40f0-b118-6cb82db0ce0e
source-git-commit: b46c753a8d854b5a448d10d30c7a5701900a35b8
workflow-type: tm+mt
source-wordcount: '1524'
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
- Segmenten maken
- Verschillende Adobe Experience Platform API&#39;s gebruiken
- SQL gebruiken om query&#39;s uit te voeren op uw gegevens in Adobe Experience Platform
- Realtime, op trigger gebaseerde reizen configureren en uitvoeren
- Gebruik Real-time CDP om actie te voeren door een segment aan diverse bestemmingen te activeren
- Gebruik Customer Journey Analytics om te rapporteren over omnichannel klantgegevens uit verschillende bronnen, waaronder Google BigQuery

## Vereisten

- Toegang tot Adobe Experience Platform: [ https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Toegang tot de Inzameling van Gegevens van Adobe Experience Platform: [ https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/)
- Toegang tot het Systeem van de Demo: [ https://dashboard.adobedemo.com/](https://dashboard.adobedemo.com/)

## Video&#39;s

U kunt veel interessante video&#39;s van onze gebeurtenissen van de Academie van de Technologie, van Bootcamps en meer op ons [ Communautaire kanaal van YouTube van de Makers van de Ervaring vinden Communautaire ](https://www.youtube.com/channel/UCUKG2dkZ9pYuZUPebQ21jUw).

## Inhoud

[0. Aan de slag](./modules/gettingstarted/gettingstarted/getting-started.md)

- **Publiek:** Alle deelnemers van het Uitgebreide Technische Leerprogramma voor Adobe Experience Platform
- **Vereisten:** Toegang tot het Systeem van de Demo daarna, Adobe Experience Platform en de Inzameling van Gegevens van Adobe Experience Platform.
- **Beschrijving:** in deze grondmodule, zult u opstelling alles zodat u tot het demomilieu kunt toegang hebben en gebruiken.
- **de Investering van de Tijd:** 30 minuten

### 1. Gegevensverzameling

[1.1 Foundation - Setup of Adobe Experience Platform Data Collection &amp; Web SDK](./modules/datacollection/module1.1/data-ingestion-launch-web-sdk.md)

- **Publiek:** Ingenieur van Gegevens, Architect van Gegevens
- **Vereisten:** Toegang tot de Inzameling van Gegevens van Adobe Experience Platform en van Adobe Experience Platform.
- **Beschrijving:** in deze grondmodule, zult u over de Inzameling van Gegevens van Adobe Experience Platform en de nieuwe uitbreiding van SDK van het Web leren.
- **de Investering van de Tijd:** 30 minuten

[1.2 Stichting - de Ingestie van Gegevens](./modules/datacollection/module1.2/data-ingestion.md)

- **Publiek:** Ingenieur van Gegevens, Architect van Gegevens
- **Vereisten:** Toegang tot de Inzameling van Gegevens van Adobe Experience Platform en van Adobe Experience Platform.
- **Beschrijving:** In deze stichtingsmodule, zult u gegevens van de website in Platform innemen
- **de Investering van de Tijd:** 120 minuten

[1.3 Federale Audience Composition](./modules/datacollection/module1.3/fac.md)

- **Publiek:** Analyst van Gegevens, de Ingenieur van Gegevens, Architect van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform
- **Beschrijving:** In deze module, zult u leren hoe te om uw eigen cluster van Apache Kafka te plaatsen, onderwerpen, producenten en consumenten te bepalen en gegevens in Adobe Experience Platform te stromen gebruikend de Schakelaar van de Roze van Adobe Experience Platform voor Kafka Connect.
- **de Investering van de Tijd:** 90 minuten

### 2. Real-Time CDP B2C

[2.1 Foundation - Real-time klantprofiel](./modules/rtcdp-b2c/module2.1/real-time-customer-profile.md)

- **Publiek:** de Ingenieur van Gegevens, Architect van Gegevens, Marketer
- **Vereisten:** Toegang tot Adobe Experience Platform en Postman
- **Beschrijving:** in deze grondmodule, zult u het Profiel van de Klant in real time in Adobe Experience Platform onderzoeken door gebruik van UI en API te maken.
- **de Investering van de Tijd:** 90 minuten
- **Download deze activa**:
   - [Postman-verzamelingen](./assets/postman/postman_profile.zip)

[2.2 Intelligente diensten](./modules/rtcdp-b2c/module2.2/intelligent-services.md)

- **Publiek:** de Ingenieur van Gegevens, Architect van Gegevens, de Wetenschappelijke wetenschappen van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform, de Intelligente Diensten
- **Beschrijving:** In deze module, zult u leren hoe te opstelling, vorm en gebruik de Intelligente Diensten van Adobe Experience Platform.
- **de Investering van de Tijd:** 60 minuten

[2.3 Real-Time CDP - Een segment maken en actie ondernemen](./modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md)

- **Publiek:** Architect van Gegevens, de Ingenieur van Orchestratie, Marketer
- **Vereisten:** Toegang tot Adobe Experience Platform, Real-time CDP, Adobe Audience Manager, Adobe Target, AWS S3
- **Beschrijving:** In deze module, zult u een segment vormen, het voor het Streamen Segmentatie toelaten en het segment aan verscheidene bestemmingen, met inbegrip van Google DV360, Google AdWords, Adobe Audience Manager, Adobe Target en S3 bestemmingen zoals de Marketing Cloud van Salesforce activeren.
- **de Investering van de Tijd:** 90 minuten

[2.4 Real-Time CDP: Segmentactivering naar Microsoft Azure Event Hub](./modules/rtcdp-b2c/module2.4/segment-activation-microsoft-azure-eventhub.md)

- **Publiek:** De Ingenieur van Gegevens, Architect van Gegevens, de Analyst van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform, Real-time CDP en Microsoft Azure
- **Beschrijving:** In deze module, zult u een bestemming van Microsoft Azure EventHub als bestemming in real time voor Adobe Experience Platform in real time CDP plaatsen. U zult ook opstelling en een Azure functie opstellen die in real time zal teweeggebracht worden wanneer Adobe Experience Platform een segmentlading aan uw Azure bestemming EventHub levert. De Azure Functie die u zult teweegbrengen zal het mechanisme van Adobe Experience Platform in real time CDP activeringsmogelijkheden tonen.
Als deel van deze module zult u ook een begrip van krijgen wat in real time CDP teweegbrengt om een nuttige lading aan een gespecificeerde bestemming eigenlijk te leveren. We zullen ook de status van een segmentkwalificatie bespreken en de relatie ervan met activering.
- **de Investering van de Tijd:** 90 minuten

[2.5 Real-Time CDP-verbindingen: gebeurtenissen doorsturen](./modules/rtcdp-b2c/module2.5/aep-data-collection-ssf.md)

- **Publiek:** De Ingenieur van Gegevens, Architect van Gegevens, de Analyst van Gegevens
- **Vereisten:** Toegang tot de Verbindingen van Real-Time CDP, Markeringen en Gebeurtenis die eigenschappen door:sturen
- **Beschrijving:** In deze module, zult u de eerder gevormde datasets, schema&#39;s en het bezit van de Inzameling van Gegevens van Adobe Experience Platform gebruiken om gegevens te verzamelen, en dan door:sturen die gegevens server-kant aan een eindpunt van keus.
- **de Investering van de Tijd:** 90 minuten

[2.6 Gegevens streamen van Apache Kafka naar Real-Time CDP](./modules/rtcdp-b2c/module2.6/aep-apache-kafka.md)

- **Publiek:** Analyst van Gegevens, de Ingenieur van Gegevens, Architect van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform
- **Beschrijving:** In deze module, zult u leren hoe te om uw eigen cluster van Apache Kafka te plaatsen, onderwerpen, producenten en consumenten te bepalen en gegevens in Adobe Experience Platform te stromen gebruikend de Schakelaar van de Roze van Adobe Experience Platform voor Kafka Connect.
- **de Investering van de Tijd:** 90 minuten

### 3. Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestratie](./modules/ajo-b2c/module3.1/journey-orchestration-create-account.md)

- **Publiek:** de Ingenieur van Gegevens, Architect van Gegevens, de Ingenieur van de Orchestratie
- **Vereisten:** Toegang tot Adobe Experience Platform en Adobe Journey Optimizer
- **Beschrijving:** In deze module, zult u Adobe Journey Optimizer gebruiken om een op trekker-gebaseerde reis te bouwen.
- **de Investering van de Tijd:** 60 minuten

[3.2 Adobe Journey Optimizer: Externe gegevensbronnen en aangepaste acties](./modules/ajo-b2c/module3.2/journey-orchestration-external-weather-api-sms.md)

- **Publiek:** de Ingenieur van Gegevens, Architect van Gegevens, de Ingenieur van Orchestratie, Marketer
- **Vereisten:** Toegang tot Adobe Experience Platform, Adobe Journey Optimizer, Open Weather API, Twilio
- **Beschrijving:** In deze module, zult u Adobe Journey Optimizer gebruiken om aan klantengedrag, zowel online als off-line te luisteren, en aan het op een intelligente, contextafhankelijke en manier in real time over diverse kanalen te antwoorden.
- **de Investering van de Tijd:** 90 minuten

[3.3 Adobe Journey Optimizer: Offer Decisioning](./modules/ajo-b2c/module3.3/offer-decisioning.md)

- **Publiek:** de Ingenieur van Gegevens, Architect van Gegevens, de Ingenieur van Orchestratie, Marketer
- **Vereisten:** Toegang tot Adobe Experience Platform en Offer decisioning
- **Beschrijving:** In deze module, zult u de Adobe Experience Platform - Aanbiedingen/het Beslissen toepassingsdienst op een hands-on manier gebruiken om Gepersonaliseerde Aanbiedingen en uw eigen Activiteit van het Aanbod te vormen.
- **de Investering van de Tijd:** 120 minuten

[3.4 Adobe Journey Optimizer: Reizen op basis van gebeurtenissen](./modules/ajo-b2c/module3.4/journeyoptimizer.md)

- **Publiek:** E-mailMarkering, Specialist van het Orchestration, de Ingenieur van Gegevens, Architect van Gegevens, de Analyst van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform en Journey Optimizer
- **Beschrijving:** In deze module, zult u alles leren er over Journey Optimizer te weten is, die bedrijven helpt verbonden, contextafhankelijke, en gepersonaliseerde ervaringen ontwerpen en leveren aan hun klanten.
- **de Investering van de Tijd:** 120 minuten

### 4. Adobe Customer Journey Analytics

[4.1 Customer Journey Analytics: bouw een dashboard met Analysis Workspace bovenop Adobe Experience Platform](./modules/cja-b2c/module4.1/customer-journey-analytics-build-a-dashboard.md)

- **Publiek:** De Ingenieur van Gegevens, Architect van Gegevens, de Analyst van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform en Customer Journey Analytics
- **Beschrijving:** In deze module, zult u Online aan Off-line inzichten door een dashboard te vormen die omni-kanaalgegevens zoals Interacties van de Website, Mobiele Interacties van de App, Interacties van het Centrum van de Vraag, Interacties In-Store en veel meer bevatten.
- **de Investering van de Tijd:** 120 minuten

[4.2 Customer Journey Analytics: Gegevens van Googles Analytics in Adobe Experience Platform verzamelen en analyseren met de BigQuery Source-connector](./modules/cja-b2c/module4.2/customer-journey-analytics-bigquery-gcp.md)

- **Publiek:** De Ingenieur van Gegevens, Architect van Gegevens, de Analyst van Gegevens
- **Vereisten:** Toegang tot Adobe Experience Platform, Customer Journey Analytics, het Platform van de Wolk van Google, Google BigQuery
- **Beschrijving:** In deze module, zult u opstelling uw eigen geval van het Platform van de Wolk van Google, laadt demonstratiegegevens in het Platform van de Wolk van Google en u zult dan de Schakelaar van BigQuery Source gebruiken om die gegevens van het Platform van de Wolk van Google in Adobe Experience Platform in te voeren. Tot slot zult u Customer Journey Analytics gebruiken om die gegevens te visualiseren.
- **de Investering van de Tijd:** 120 minuten
- **Download deze activa**:
   - [JSON - Voorbeeldgegevens: demo - Loyalty-gegevens](./assets/json/bqLoyalty.json)

### 5. Data Distiller

[5.1 Query-service](./modules/datadistiller/module5.1/query-service.md)

- **Publiek:** De Ingenieur van Gegevens, Architect van Gegevens, Analyst van Gegevens, Expert BI
- **Vereisten:** Toegang tot Adobe Experience Platform, de Dienst van de Vraag, Power BI of Tableau
- **Beschrijving:** In deze module, zult u leren hoe te om de Dienst van de Vraag van Adobe Experience Platform te gebruiken.
- **de Investering van de Tijd:** 90 minuten
- **Download deze activa**:
   - [JSON - Voorbeeldgegevens: demosysteem - Dataset voor gebeurtenis voor website](./assets/json/ee.json)
   - [JSON - Voorbeeldgegevens: Demosysteem - Dataset voor gebeurtenis voor callcenter](./assets/json/callcenter.json)
   - [JSON - Voorbeeldgegevens: demosysteem - profielgegevensset voor Loyalty](./assets/json/loyalty.json)





