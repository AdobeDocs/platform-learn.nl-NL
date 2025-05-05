---
title: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
description: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
kt: 5342
doc-type: tutorial
exl-id: 5c77d09f-18c8-4e29-9392-3f6f8004fa7c
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# 2.4.2 Uw Microsoft Azure EventHub-omgeving configureren

Azure Event Hubs is een hoogst scalable publish-subscribe dienst die miljoenen gebeurtenissen per seconde kan opnemen en hen in veelvoudige toepassingen stroomt. Zo kunt u de enorme hoeveelheden gegevens verwerken en analyseren die door de aangesloten apparaten en toepassingen worden geproduceerd.

## Wat is Azure Event Hubs?

Azure Event Hubs is een groot platform voor gegevensstreaming en service voor het opnemen van gebeurtenissen. Het kan miljoenen gebeurtenissen per seconde ontvangen en verwerken. Gegevens die naar een gebeurtenishub worden verzonden, kunnen worden getransformeerd en opgeslagen met behulp van een realtime analyseprovider of batchadapters.

De Hubs van de gebeurtenis vertegenwoordigt de **voordeur** voor een gebeurtenispijpleiding, vaak genoemd een gebeurtenis ingestor in oplossingsarchitectuur. Een gebeurtenislistener is een component of service die zich tussen gebeurtenisuitgevers (zoals Adobe Experience Platform RTCDP) en gebeurtenisgebruikers bevindt om de productie van een gebeurtenisstream los te koppelen van het gebruik van die gebeurtenissen. De Hubs van de gebeurtenis verstrekt een verenigd stromend platform met tijdretentiebuffer, ontkoppelt gebeurtenisproducenten van gebeurtenisconsumenten.

## Een naamruimte voor gebeurtenishubs maken

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **creeer een middel**.

![ 1-01-open-azure-portal.png ](./images/101openazureportal.png)

In het middelscherm, ga **Gebeurtenis** in de onderzoeksbar in. Vind de **kaart van de Hubs van de Gebeurtenis 0&rbrace; &lbrace;, klik** creeer **en klik dan** de Hubs van de Gebeurtenis **.**

![ 1-02-onderzoek-gebeurtenis-hubs.png ](./images/102searcheventhubs.png)

Als dit de eerste keer is dat u een middel in Azure creeert, zult u een nieuwe **groep van het Middel** moeten creëren. Als u al een middelgroep hebt kunt u het selecteren (of nieuwe creëren).

Klik **creeer nieuw** en noem uw groep `--aepUserLdap---aep-enablement`, klik **O.K.**.

![ 1-04-creeer-middel-group.png ](./images/104createresourcegroup.png)

Vul de overige opgegeven velden in:

- Naamruimte: definieer de naamruimte, deze moet uniek zijn en gebruik het volgende patroon `--aepUserLdap---aep-enablement`
- Locatie: kies een locatie
- Prijsende rij: **Basis**
- De Eenheden van de productie: **1**

Klik **Overzicht + creeer**.

![ 1-05-create-namespace.png ](./images/105createnamespace.png)

Klik **creëren**.

![ 1-07-namespace-create.png ](./images/107namespacecreate.png)

De plaatsing van uw middelgroep kan 1-2 minuten vergen, wanneer succesvol u het volgende scherm zult zien:

![ 1-08-namespace-deploy.png ](./images/108namespacedeploy.png)

## Uw gebeurtenishub in Azure instellen

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **Alle middelen**.

![ 1-09-all-resources.png ](./images/109allresources.png)

Klik in de lijst met bronnen op de naamruimte `--aepUserLdap---aep-enablement` Gebeurtenishubs:

![ 1-10-list-resources.png ](./images/110listresources.png)

In `--aepUserLdap---aep-enablement` detailscherm, ga **Entiteiten** en klik **de Hubs van de Gebeurtenis**:

![ 1-11-eventhub-namespace.png ](./images/111eventhubnamespace.png)

Klik **+ de Hub van de Gebeurtenis**.

![ 1-12-toe:voegen-gebeurtenis-hub.png ](./images/112addeventhub.png)

Gebruik `--aepUserLdap---aep-enablement-event-hub` als naam en klik **Overzicht + creeer**.

![ 1-13-create-event-hub.png ](./images/113createeventhub.png)

Klik **creëren**.

![ 1-13-create-event-hub.png ](./images/113createeventhub1.png)

In **de Hubs van de Gebeurtenis** onder uw gebeurtenishub namespace, zult u uw **vermelde Hub van de Gebeurtenis** nu zien.

![ 1-14-event-hub-list.png ](./images/114eventhublist.png)

## Uw Azure Storage Account instellen

Om uw functie van de Hub van de Gebeurtenis van de Azure in recentere oefeningen te zuiveren, zult u een Azure Rekening van de Opslag als deel van uw het projectopstelling van de Code van Visual Studio moeten verstrekken. U gaat nu die Azure Storage Account maken.

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **creeer een Middel**.

![ 1-15-event-hub-storage.png ](./images/115eventhubstorage.png)

Ga **opslagrekening** in het onderzoek in, vind de kaart voor **Rekening van de Opslag** en klik **rekening van de Opslag**.

![ 1-16-event-hub-search-storage.png ](./images/116eventhubsearchstorage.png)

Specificeer uw **Groep van het Middel** (gecreeerd in het begin van deze oefening), gebruik `--aepUserLdap--aepstorage` als uw naam van de de rekeningsrekening van de Opslag en selecteer **lokaal-overtollige opslag (LRS)**, dan klik **Overzicht + creeer**.

![ 1-18-event-hub-create-review-storage.png ](./images/118eventhubcreatereviewstorage.png)

Klik **creëren**.

![ 1-19-gebeurtenis-hub-submit-storage.png ](./images/119eventhubsubmitstorage.png)

Het maken van onze opslagaccount duurt een paar seconden:

![ 1-20-gebeurtenis-hub-opstellen-storage.png ](./images/120eventhubdeploystorage.png)

Wanneer gebeëindigd zal uw scherm **aan middel** knoop tonen.

Klik **Huis**.

![ 1-21-gebeurtenis-hub-opstellen-klaar-storage.png ](./images/121eventhubdeployreadystorage.png)

Uw Rekening van de Opslag is nu zichtbaar onder **Recente Middelen**.

![ 1-22-gebeurtenis-hub-opstellen-middelen-list.png ](./images/122eventhubdeployresourceslist.png)

## Volgende stappen

Ga naar [ 2.4.3 vorm uw Azure Doel van de Hub van de Gebeurtenis in Adobe Experience Platform ](./ex3.md){target="_blank"}

Ga terug naar [ Real-Time CDP: Audience Activation aan Microsoft Azure de Hub van de Gebeurtenis ](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
