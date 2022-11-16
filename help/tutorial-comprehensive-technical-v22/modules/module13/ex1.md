---
title: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
description: Segmentactivering naar Microsoft Azure Event Hub - Setup Event Hub in Azure
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 9434ac83-5554-48bf-838c-7346d571efbf
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 13.1 Configureer uw Microsoft Azure EventHub-omgeving

Azure Event Hubs is een hoogst scalable publish-subscribe dienst die miljoenen gebeurtenissen per seconde kan opnemen en hen in veelvoudige toepassingen stroomt. Zo kunt u de enorme hoeveelheden gegevens verwerken en analyseren die door de aangesloten apparaten en toepassingen worden geproduceerd.

## 13.1.1 Wat is Azure Event Hubs?

Azure Event Hubs is een groot platform voor gegevensstreaming en service voor het opnemen van gebeurtenissen. Het kan miljoenen gebeurtenissen per seconde ontvangen en verwerken. Gegevens die naar een gebeurtenishub worden verzonden, kunnen worden getransformeerd en opgeslagen met behulp van een realtime analyseprovider of batchadapters.

Gebeurtenishubs vertegenwoordigen de **voorkant** voor een gebeurtenispijpleiding, vaak genoemd een gebeurtenis ingestor in oplossingsarchitectuur. Een gebeurtenislistener is een component of service die zich tussen gebeurtenisuitgevers (zoals Adobe Experience Platform RTCDP) en gebeurtenisgebruikers bevindt om de productie van een gebeurtenisstream los te koppelen van het gebruik van die gebeurtenissen. De Hubs van de gebeurtenis verstrekt een verenigd stromend platform met tijdretentiebuffer, ontkoppelt gebeurtenisproducenten van gebeurtenisconsumenten.

## 13.1.2 Een naamruimte Gebeurtenishubs maken

Ga naar [https://portal.azure.com/#home](https://portal.azure.com/#home) en selecteert u **Een bron maken**.

![1-01-open-azure-portal.png](./images/1-01-open-azure-portal.png)

In het middelscherm, ga binnen **Gebeurtenis** in de zoekbalk en selecteer **Gebeurtenishubs** uit het vervolgkeuzemenu:

![1-02-onderzoek-gebeurtenis-hubs.png](./images/1-02-search-event-hubs.png)

Klikken **Maken**:

![1-03-event-hub-create.png](./images/1-03-event-hub-create.png)

Als dit de eerste keer is dat u een middel in Azure creeert, zult u een nieuw moeten creëren **Brongroep**. Als u al een middelgroep hebt kunt u het selecteren (of nieuwe creëren).

Selecteren **Nieuw maken**, geef uw groep een naam `--demoProfileLdap---aep-enablement`.

![1-04-create-resource-group.png](./images/1-04-create-resource-group.png)

Voltooi de test van de velden zoals aangegeven:

- Namespace: Definieer de naamruimte, deze moet uniek zijn en gebruik het volgende patroon `--demoProfileLdap---aep-enablement`
- Locatie: **West-Europa** verwijst naar het Azure datacenter in Amsterdam
- Prijsniveau: **Basis**
- Doorvoereenheden: **1**

![1-05-create-namespace.png](./images/1-05-create-namespace.png)

Klikken **Revisie + maken**.

![1-06-namespace-review-create.png](./images/1-06-namespace-review-create.png)

Klikken **Maken**.

![1-07-namespace-create.png](./images/1-07-namespace-create.png)

De plaatsing van uw middelgroep kan 1-2 minuten vergen, wanneer succesvol u het volgende scherm zult zien:

![1-08-namespace-deploy.png](./images/1-08-namespace-deploy.png)

## 13.1.3 Opstelling uw Hub van de Gebeurtenis in Azure

Ga naar [https://portal.azure.com/#home](https://portal.azure.com/#home) en selecteert u **Alle bronnen**.

![1-09-all-resources.png](./images/1-09-all-resources.png)

Selecteer in de lijst met bronnen de optie `--demoProfileLdap---aep-enablement` naamruimte:

![1-10-list-resources.png](./images/1-10-list-resources.png)

In `--demoProfileLdap---aep-enablement` detailscherm selecteren **Gebeurtenishubs**:

![1-11-eventhub-namespace.png](./images/1-11-eventhub-namespace.png)

Klikken **+ Gebeurtenissenhub**.

![1-12-add-event-hub.png](./images/1-12-add-event-hub.png)

Gebruiken `--demoProfileLdap---aep-enablement-event-hub` als de naam en klik op **Maken**.

![1-13-create-event-hub.png](./images/1-13-create-event-hub.png)

Klikken **Gebeurtenishubs** in de naamruimte van de gebeurtenishub. U moet nu uw **Gebeurtenishub** vermeld. Als dat het geval is, kunt u overgaan op de volgende oefening.

![1-14-event-hub-list.png](./images/1-14-event-hub-list.png)

## 13.1.4 Stel uw Azure Storage Account in

Om uw functie van de Hub van de Gebeurtenis van de Azure in recentere oefeningen te zuiveren, zult u een Azure Rekening van de Opslag als deel van uw het projectopstelling van de Code van Visual Studio moeten verstrekken. U gaat nu die Azure Storage Account maken.

Ga naar [https://portal.azure.com/#home](https://portal.azure.com/#home) en selecteert u **Een bron maken**.

![1-15-event-hub-storage.png](./images/1-15-event-hub-storage.png)

Enter **opslag** in de zoekopdracht en selecteer **Opslagaccount** in de lijst.

![1-16-event-hub-search-storage.png](./images/1-16-event-hub-search-storage.png)

Selecteer **Maken**.

![1-17-event-hub-create-storage.png](./images/1-17-event-hub-create-storage.png)

Geef uw **Brongroep** (gemaakt aan het begin van deze oefening), gebruik `--demoProfileLdap--aepstorage` als uw naam voor de opslagaccount en selecteer **Lokaal redundante opslag (LRS)** en klik vervolgens op **Revisie + maken**.

![1-18-event-hub-create-review-storage.png](./images/1-18-event-hub-create-review-storage.png)

Klikken **Maken**.

![1-19 gebeurtenis-hub-submit-storage.png](./images/1-19-event-hub-submit-storage.png)

Het maken van uw opslagaccount duurt een paar seconden:

![1-20 gebeurtenis-hub-opstellen-storage.png](./images/1-20-event-hub-deploy-storage.png)

Als u klaar bent, wordt het scherm weergegeven **Ga naar bron** knop.

Klikken **Microsoft Azure**.

![1-21-gebeurtenis-hub-opstellen-klaar-opslag.png](./images/1-21-event-hub-deploy-ready-storage.png)

Uw opslagaccount is nu zichtbaar onder **Recente bronnen**.

![1-22 gebeurtenis-hub-opstellen-middelen-list.png](./images/1-22-event-hub-deploy-resources-list.png)

Volgende stap: [13.2 Configureer uw Azure Event Hub Destination in Adobe Experience Platform](./ex2.md)

[Ga terug naar module 13](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../overview.md)
