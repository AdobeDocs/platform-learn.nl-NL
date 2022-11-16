---
title: Segmentactivering naar Microsoft Azure Event Hub - Segment activeren
description: Segmentactivering naar Microsoft Azure Event Hub - Segment activeren
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 250f8536-b6bd-4c64-a552-80d5c6fb6358
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# 13.4 Segment activeren

## 13.4.1 Segment toevoegen aan Azure Event Hub Destination

In deze oefening zult u uw segment toevoegen `--demoProfileLdap-- - Interest in Equipment` aan uw `--demoProfileLdap---aep-enablement` Azure Event Hub destination.

Meld u aan bij Adobe Experience Platform door naar deze URL te gaan: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![Gegevensinname](../module2/images/sb1.png)

Ga naar **Doelen** en klik vervolgens op **Bladeren**. U zult dan alle beschikbare bestemmingen zien. Zoek uw doel en klik op de knop **+** zoals hieronder aangegeven.

![5-01-select-destination.png](./images/5-01-select-destination.png)

Dan zie je dit. Zoek uw segment gebruikend uw ldap en selecteer `--demoProfileLdap-- - Interest in Equipment` in de lijst met segmenten.

Klik op **Next**.

![5-04-select-segment.png](./images/5-04-select-segment.png)

Adobe Experience Platform Real-time CDP kan een lading aan twee soorten bestemmingen, segmentbestemmingen en profielbestemmingen leveren.

De bestemmingen van het segment zullen een vooraf bepaalde lading van de segmentkwalificatie ontvangen die later zal worden besproken. Een dergelijke lading bevat **alles** de segmentkwalificaties voor een specifiek profiel. Zelfs voor segmenten die niet in de activeringslijst van de bestemming zijn. Een voorbeeld van een dergelijke segmentbestemming zijn **Azure Event Hubs** en **AWS Kinesis**.

Op profiel gebaseerde bestemmingen laten u om het even welk attribuut (firstName, lastName, ...) van het Schema van de Unie van het Profiel selecteren XDM en het omvatten in de activeringslading. Een voorbeeld van een dergelijke bestemming is de **E-mailmarketing**.

omdat uw Azure Event Hub-bestemming een **segment** doel, selecteer bijvoorbeeld het veld `--aepTenantId--.identification.core.ecid`.

Klikken **Nieuw veld toevoegen**, klikt u op schema bladeren en selecteert u het veld `--aepTenantId--identification.core.ecid` (Verwijder alle andere velden die automatisch worden weergegeven.)

Klik op **Next**.

![5-05-select-attributes.png](./images/5-05-select-attributes.png)

Klikken **Voltooien**.

![5-06-destination-finish.png](./images/5-06-destination-finish.png)

Uw segment wordt nu geactiveerd naar uw bestemming van de Hub van de Gebeurtenis van Microsoft.

![5-07-bestemming-segment-added.png](./images/5-07-destination-segment-added.png)

Volgende stap: [13.5 Uw Microsoft Azure-project maken](./ex5.md)

[Ga terug naar module 13](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../overview.md)
