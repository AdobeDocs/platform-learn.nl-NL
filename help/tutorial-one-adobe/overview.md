---
title: Overzicht - Uitgebreide technische zelfstudie - Eén Adobe
description: Uitgebreide technische zelfstudie - Eén Adobe
doc-type: multipage-overview
exl-id: 5bc0d621-0662-4d94-80a0-b6c173c0ac9e
source-git-commit: 603e48e0453911177823fe7ceb340f8ca801c5e1
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---

# Uitgebreide technische zelfstudie - Eén Adobe

![Technische insiders](./assets/images/techinsiders.png){width="50px" align="left"}

## Overzicht

Deze tutorial is zeer divers en biedt duidelijke inzichten in de volgende toepassingen:

- Adobe Firefly-services, Adobe Photoshop, Adobe Frame I/O, Adobe Substance 3D-fasering
- Adobe Workfront en Adobe Workfront Fusion
- Adobe Experience Manager-services voor cloudservice, sites, assets en edge-levering
- Adobe Experience Platform
- Adobe Real-Time CDP
- Adobe Journey Optimizer

Deze zelfstudie richt zich niet alleen op Adobe-toepassingen, maar houdt rekening met het bredere ecosysteem waarin merken werken. Om dat te doen, is er in sommige lessen nadruk op hoe niet-Adobe toepassingen met Adobe toepassingen integreren. Als zodanig krijgt u meer inzicht in de manier waarop de volgende toepassingen samenwerken met Adobe Experience Platform:

- Amazon AWS
- Google Cloud Platform
- Microsoft Azure
- Postbode
- Snowflake
- ...

## Vereisten

Als u deze zelfstudie wilt gebruiken met uw eigen Adobe Experience Cloud-exemplaar, moeten de volgende toepassingen in uw exemplaar worden ingericht en moet u toegang hebben tot:

- Adobe Firefly
- Adobe Photoshop, Adobe Frame I/O, Adobe Substance 3D Staging
- Adobe Workfront
- Adobe Workfront Fusion
- Adobe Experience Platform, Adobe Experience Platform Gegevensverzameling
- Toegang tot demosysteem Volgende: [https://dsn.adobe.com/](https://dsn.adobe.com/){target="_blank"}

## Oplevering en certificering

Deze zelfstudie maakt deel uit van een Adobe-certificeringscursus. Je kunt je naast deze tutorial aanmelden voor de cursus door naar [https://certification.adobe.com](https://certification.adobe.com) te gaan.

Voor elke module die u voltooit met behulp van de onderstaande tutorial, moet u een bewijs van voltooiing indienen zoals hier[&#128279;](./completion.md) aangegeven.

## Status van de inhoud

Om het statuut van de hieronder inhoud te controleren, gelieve naar de [ statuspagina ](./status.md){target="_blank"} te gaan.

### Aan de slag

[Aan de slag](./modules/getting-started/gettingstarted/getting-started.md){target="_blank"}

In deze grondmodule, zult u alles voorbereiden zodat u tot het demomilieu toegang hebt en kunt gebruiken.

### 1. Workflow en planning

### 2. Creatie en productie

[1.1 Adobe Firefly-services](./modules/creation-production/module1.1/firefly-services.md){target="_blank"}

In deze module gebruikt u Adobe Firefly Services-API&#39;s, Photoshop-API&#39;s en Microsoft Azure Storage Services om afbeeldingen te genereren en deze programmatisch op te slaan.

[1.2 Creatieve workflowautomatisering met Workfront Fusion](./modules/creation-production/module1.2/automation.md){target="_blank"}

In deze basismodule gebruikt u Adobe Workfront Fusion om uw workflows voor het maken van inhoud te automatiseren en te schalen.

[ 1.3 Adobe Express en Adobe Experience Cloud ](./modules/creation-production/module1.3/express.md){target="_blank"}

In deze basismodule gebruikt u Adobe Express om afbeeldingen en video&#39;s te maken en deelt u deze elementen met het bredere Adobe Experience Cloud-ecosysteem.

### 3. Beheer van bedrijfsmiddelen

[ 1.1 Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}

In deze basismodule stelt u uw Adobe Experience Manager Cloud Service Program, Site and Assets-repository in.

[1.2 Workflowbeheer met Adobe Workfront](./modules/asset-mgmt/module2.2/workfront.md){target="_blank"}

In deze basismodule configureert en gebruikt u Adobe Workfront om goedkeuringsstromen te beheren en gebruikt u integraties met Adobe Experience Manager Assets, Universal Editor, Photoshop en meer.

### 4. Levering en activering

#### Dataverzameling

[1.1 Foundation - Setup of Adobe Experience Platform Data Collection &amp; Web SDK](./modules/delivery-activation/datacollection/dc1.1/data-ingestion-launch-web-sdk.md)

In deze basismodule leert u meer over Adobe Experience Platform Data Collection en de nieuwe Web SDK-extensie.

[1.2 Stichting - de Ingestie van Gegevens](./modules/delivery-activation/datacollection/dc1.2/data-ingestion.md)

In deze basismodule neemt u gegevens uit verschillende bronnen op in Adobe Experience Platform

[1.3 Samenstelling van het federatieve publiek](./modules/delivery-activation/datacollection/dc1.3/fac.md)

In deze module leert u hoe u een Federated Audiences-model instelt en doelgroepen genereert met behulp van federatieve gegevens.

#### Real-Time CDP B2C

[2.1 Fundering - Real-time klantprofiel](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-1/real-time-customer-profile.md)

In deze basismodule gaat u het Real-time klantprofiel in Adobe Experience Platform verkennen met behulp van de gebruikersinterface en de API.

[2.2 Intelligente diensten](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-2/intelligent-services.md)

In deze module leert u hoe u Adobe Experience Platform Intelligent Services kunt instellen, configureren en gebruiken.

[2.3 Real-Time CDP - Bouw een publiek en onderneem actie](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-3/real-time-cdp-build-a-segment-take-action.md)

In deze module configureer je een doelgroep en activeer je de doelgroep naar verschillende bestemmingen, waaronder Google DV360, Adobe Target en AWS S3.

[2.4 Real-time CDP: Publieksactivering naar Microsoft Azure Event Hub](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-4/segment-activation-microsoft-azure-eventhub.md)

In deze module stelt u een Microsoft Azure EventHub-bestemming in als een realtime-bestemming voor Adobe Experience Platform Real-time CDP.

[2.5 Real-time CDP-verbindingen: gebeurtenissen doorsturen](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-5/aep-data-collection-ssf.md)

In deze module stuur je data server-side door naar verschillende endpoints, zoals Google Cloud Platform Pub/Sub en AWS Kinesis.

[2.6 Gegevens van Apache Kafka naar Real-Time CDP streamen](./modules/delivery-activation/rtcdp-b2c/rtcdpb2c-6/aep-apache-kafka.md)

In deze module leert u hoe u uw eigen Apache Kafka-cluster instelt en gegevens streamt naar Adobe Experience Platform.

#### Adobe Journey Optimizer B2C

[3.1 Adobe Journey Optimizer: Orchestratie](./modules/delivery-activation/ajo-b2c/ajob2c-1/journey-orchestration-create-account.md)

In deze module zult u Adobe Journey Optimizer gebruiken om een op trigger-gebaseerde reis uit te bouwen.

[3.2 Adobe Journey Optimizer: Externe gegevensbronnen en aangepaste acties](./modules/delivery-activation/ajo-b2c/ajob2c-2/journey-orchestration-external-weather-api-sms.md)

In deze module, zult u Adobe Journey Optimizer gebruiken om aan klantengedrag, zowel online als off-line te luisteren, en aan het op een intelligente, contextafhankelijke en manier in real time over diverse kanalen te antwoorden.

[3.3 Adobe Journey Optimizer: Besluitvorming over aanbiedingen](./modules/delivery-activation/ajo-b2c/ajob2c-3/offer-decisioning.md)

In deze module gebruikt u Adobe Journey Optimizer om gepersonaliseerde aanbiedingen en uw eigen aanbiedingsbeslissing te configureren.

[3.4 Adobe Journey Optimizer: op gebeurtenissen gebaseerde reizen](./modules/delivery-activation/ajo-b2c/ajob2c-4/journeyoptimizer.md)

In deze module leer je alles wat je moet weten over Journey Optimizer, dat bedrijven helpt bij het ontwerpen en leveren van verbonden, contextuele en gepersonaliseerde ervaringen aan hun klanten.

[3.5 Adobe Journey Optimizer: vertaaldiensten](./modules/delivery-activation/ajo-b2c/ajob2c-5/ajotranslationsvcs.md)

In deze module leert u hoe u de vertaalservices in Adobe Journey Optimizer kunt instellen en gebruiken om uw berichten te lokaliseren voor uw klanten.

### 5. Rapportage en inzichten

#### Adobe Customer Journey Analytics

[1.1 Customer Journey Analytics: maak een dashboard met Analysis Workspace bovenop Adobe Experience Platform](./modules/reporting-insights/cja-b2c/cjab2c-1/customer-journey-analytics-build-a-dashboard.md)

In deze module, zult u Online aan Off-line inzichten door een dashboard te vormen die omni-channel gegevens bevat.

[1.2 Customer Journey Analytics: Google Analytics-gegevens opnemen en analyseren in Adobe Experience Platform met de BigQuery Source Connector](./modules/reporting-insights/cja-b2c/cjab2c-2/customer-journey-analytics-bigquery-gcp.md)

In deze module stelt u uw eigen exemplaar van Google Cloud Platform in, laadt u demogegevens in Google Cloud Platform en gebruikt u vervolgens de BigQuery Source Connector om die gegevens van Google Cloud Platform op te nemen in Adobe Experience Platform.

#### Data distilleerder

[2.1 De Dienst van de vraag](./modules/reporting-insights/datadistiller/dd-1/query-service.md)

In deze module leert u hoe u Adobe Experience Platform Query Service gebruikt.

![Technische insiders](./assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Als je vragen hebt, algemene feedback wilt delen of suggesties hebt over toekomstige inhoud, neem dan rechtstreeks contact op met Tech Insiders door een e-mail te sturen naar **techinsiders@adobe.com**.
