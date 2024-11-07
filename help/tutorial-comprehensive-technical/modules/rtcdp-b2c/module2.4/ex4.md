---
title: Segmentactivering naar Microsoft Azure Event Hub - Segment activeren
description: Segmentactivering naar Microsoft Azure Event Hub - Segment activeren
kt: 5342
doc-type: tutorial
source-git-commit: cd603fdcbac6cc77b00d50be888805329f014443
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 2.4.4 Segment activeren

## 2.4.4.1 Segment toevoegen aan Azure Event Hub Destination

In deze exercitie voegt u uw segment `--demoProfileLdap-- - Interest in Equipment` toe aan uw `--demoProfileLdap---aep-enablement` Azure Event Hub-bestemming.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxId--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

Ga naar **Doelen**, dan klik **doorbladeren**. U zult dan alle beschikbare bestemmingen zien. Zoek de bestemming en klik op het pictogram **+** zoals hieronder aangegeven.

![ 5-01-select-destination.png ](./images/5-01-select-destination.png)

Dan zie je dit. Zoek het segment met uw ldap en selecteer `--demoProfileLdap-- - Interest in Equipment` in de lijst met segmenten.

Klik **daarna**.

![ 5-04-select-segment.png ](./images/5-04-select-segment.png)

Adobe Experience Platform Real-time CDP kan een lading aan twee soorten bestemmingen, segmentbestemmingen en profielbestemmingen leveren.

De bestemmingen van het segment zullen een vooraf bepaalde lading van de segmentkwalificatie ontvangen die later zal worden besproken. Zulk een nuttige lading bevat **alle** de segmentkwalificaties voor een specifiek profiel. Zelfs voor segmenten die niet in de activeringslijst van de bestemming zijn. Een voorbeeld van zulk een segmentbestemming is **Azure de Hubs van de Gebeurtenis** en **AWS Kinesis**.

Op profiel gebaseerde bestemmingen laten u om het even welk attribuut (firstName, lastName, ...) van het Schema van de Unie van het Profiel selecteren XDM en het omvatten in de activeringslading. Een voorbeeld van dergelijke bestemming is de **E-mail marketing**.

Omdat uw Azure bestemming van de Hub van de Gebeurtenis a **segment** bestemming, uitgezocht bijvoorbeeld het gebied `--aepTenantId--.identification.core.ecid` is.

Klik **toevoegen nieuw gebied**, doorblader schema en selecteer het gebied `--aepTenantId--identification.core.ecid` (schrap om het even welk ander gebied dat automatisch zou worden getoond).

Klik **daarna**.

![ 5-05-select-attributes.png ](./images/5-05-select-attributes.png)

Klik **Afwerking**.

![ 5-06-bestemming-finish.png ](./images/5-06-destination-finish.png)

Uw segment wordt nu geactiveerd naar uw bestemming van de Hub van de Gebeurtenis van Microsoft.

![ 5-07-bestemming-segment-added.png ](./images/5-07-destination-segment-added.png)

Volgende Stap: [ 2.4.5 leidt tot uw Microsoft Azure Project ](./ex5.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
