---
title: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
description: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# 2.4.1 De Microsoft Azure EventHub-omgeving configureren

Azure Event Hubs is een hoogst scalable publish-subscribe dienst die miljoenen gebeurtenissen per seconde kan opnemen en hen in veelvoudige toepassingen stroomt. Zo kunt u de enorme hoeveelheden gegevens verwerken en analyseren die door de aangesloten apparaten en toepassingen worden geproduceerd.

## 2.4.1.1 Wat is Azure Event Hubs?

Azure Event Hubs is een groot platform voor gegevensstreaming en service voor het opnemen van gebeurtenissen. Het kan miljoenen gebeurtenissen per seconde ontvangen en verwerken. Gegevens die naar een gebeurtenishub worden verzonden, kunnen worden getransformeerd en opgeslagen met behulp van een realtime analyseprovider of batchadapters.

De Hubs van de gebeurtenis vertegenwoordigt de **voordeur** voor een gebeurtenispijpleiding, vaak genoemd een gebeurtenis ingestor in oplossingsarchitectuur. Een gebeurtenislistener is een component of service die zich tussen gebeurtenisuitgevers (zoals Adobe Experience Platform RTCDP) en gebeurtenisgebruikers bevindt om de productie van een gebeurtenisstream los te koppelen van het gebruik van die gebeurtenissen. De Hubs van de gebeurtenis verstrekt een verenigd stromend platform met tijdretentiebuffer, ontkoppelt gebeurtenisproducenten van gebeurtenisconsumenten.

## 2.4.1.2 Een naamruimte Gebeurtenishubs maken

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **creeer een middel**.

![ 1-01-open-azure-portal.png ](./images/1-01-open-azure-portal.png)

In het middelscherm, ga **Gebeurtenis** in de onderzoeksbar in en selecteer **de Hubs van de Gebeurtenis** van dropdown:

![ 1-02-onderzoek-gebeurtenis-hubs.png ](./images/1-02-search-event-hubs.png)

Klik **creëren**:

![ 1-03-gebeurtenis-hub-create.png ](./images/1-03-event-hub-create.png)

Als dit de eerste keer is dat u een middel in Azure creeert, zult u een nieuwe **groep van het Middel** moeten creëren. Als u al een middelgroep hebt kunt u het selecteren (of nieuwe creëren).

Selecteer **creeer nieuw**, noem uw groep `--demoProfileLdap---aep-enablement`.

![ 1-04-creeer-middel-group.png ](./images/1-04-create-resource-group.png)

Voltooi de test van de velden zoals aangegeven:

- Naamruimte: definieer de naamruimte, deze moet uniek zijn en gebruik het volgende patroon `--demoProfileLdap---aep-enablement`
- Plaats: **West-Europa** verwijst naar Azure datacenter in Amsterdam
- Prijsende rij: **Basis**
- De Eenheden van de productie: **1**

![ 1-05-create-namespace.png ](./images/1-05-create-namespace.png)

Klik **Overzicht + creeer**.

![ 1-06-namespace-revisie-create.png ](./images/1-06-namespace-review-create.png)

Klik **creëren**.

![ 1-07-namespace-create.png ](./images/1-07-namespace-create.png)

De plaatsing van uw middelgroep kan 1-2 minuten vergen, wanneer succesvol u het volgende scherm zult zien:

![ 1-08-namespace-deploy.png ](./images/1-08-namespace-deploy.png)

## 2.4.1.3 Opstelling uw Hub van de Gebeurtenis in Azure

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **Alle middelen**.

![ 1-09-all-resources.png ](./images/1-09-all-resources.png)

Selecteer in de lijst met bronnen de naamruimte `--demoProfileLdap---aep-enablement` :

![ 1-10-list-resources.png ](./images/1-10-list-resources.png)

In `--demoProfileLdap---aep-enablement` detailscherm, uitgezochte **Hubs van de Gebeurtenis**:

![ 1-11-eventhub-namespace.png ](./images/1-11-eventhub-namespace.png)

Klik **+ de Hub van de Gebeurtenis**.

![ 1-12-toe:voegen-gebeurtenis-hub.png ](./images/1-12-add-event-hub.png)

Gebruik `--demoProfileLdap---aep-enablement-event-hub` als naam en klik **creeer**.

![ 1-13-create-event-hub.png ](./images/1-13-create-event-hub.png)

Klik **de Hubs van de Gebeurtenis** in uw naamruimte van de gebeurtenishub. U zou uw **vermelde Hub van de Gebeurtenis** nu moeten zien. Als dat het geval is, kunt u overgaan op de volgende oefening.

![ 1-14-event-hub-list.png ](./images/1-14-event-hub-list.png)

## 2.4.1.4 Stel uw Azure Storage Account in

Om uw functie van de Hub van de Gebeurtenis van de Azure in recentere oefeningen te zuiveren, zult u een Azure Rekening van de Opslag als deel van uw het projectopstelling van de Code van Visual Studio moeten verstrekken. U gaat nu die Azure Storage Account maken.

Ga naar [ https://portal.azure.com/#home ](https://portal.azure.com/#home) en selecteer **creeer een Middel**.

![ 1-15-event-hub-storage.png ](./images/1-15-event-hub-storage.png)

Ga **opslag** in het onderzoek in en selecteer **Rekening van de Opslag** van de lijst.

![ 1-16-event-hub-search-storage.png ](./images/1-16-event-hub-search-storage.png)

Selecteer **creeer**.

![ 1-17-event-hub-create-storage.png ](./images/1-17-event-hub-create-storage.png)

Specificeer uw **Groep van het Middel** (gecreeerd in het begin van deze oefening), gebruik `--demoProfileLdap--aepstorage` als uw naam van de de rekeningsrekening van de Opslag, en selecteer **lokaal-overtollige opslag (LRS)**, dan klik **Overzicht + creeer**.

![ 1-18-event-hub-create-review-storage.png ](./images/1-18-event-hub-create-review-storage.png)

Klik **creëren**.

![ 1-19-gebeurtenis-hub-submit-storage.png ](./images/1-19-event-hub-submit-storage.png)

Het maken van uw opslagaccount duurt een paar seconden:

![ 1-20-gebeurtenis-hub-opstellen-storage.png ](./images/1-20-event-hub-deploy-storage.png)

Wanneer gebeëindigd zal uw scherm **aan middel** knoop tonen.

Klik **Microsoft Azure**.

![ 1-21-gebeurtenis-hub-opstellen-klaar-storage.png ](./images/1-21-event-hub-deploy-ready-storage.png)

Uw Rekening van de Opslag is nu zichtbaar onder **Recente Middelen**.

![ 1-22-gebeurtenis-hub-opstellen-middelen-list.png ](./images/1-22-event-hub-deploy-resources-list.png)

Volgende Stap: [ 2.4.2 vormt uw Azure Doel van de Hub van de Gebeurtenis in Adobe Experience Platform ](./ex2.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
