---
title: Audience Activation naar Microsoft Azure Event Hub - Publiek activeren
description: Audience Activation naar Microsoft Azure Event Hub - Publiek activeren
kt: 5342
doc-type: tutorial
exl-id: 89cfda0e-6c5e-45ab-9506-f0f0f6211e7f
source-git-commit: b4a7144217a68bc0b1bc70b19afcbc52e226500f
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 2.4.5 Activeer uw publiek

## publiek toevoegen aan Azure Event Hub Destination

In deze exercitie voegt u uw publiek `--aepUserLdap-- - Interest in Plans` toe aan uw `--aepUserLdap---aep-enablement` Azure Event Hub-bestemming.

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

Ga naar **Doelen**, dan klik **doorbladeren**. U zult dan alle beschikbare bestemmingen zien. Bepaal de plaats van uw bestemming en klik de 3 punten**..** zoals hieronder vermeld, dan klik **actief publiek**.

![ 5-01-select-destination.png ](./images/501selectdestination.png)

Dan zie je dit. Zoek naar uw publiek met uw LDAP en selecteer `--aepUserLdap-- - Interest in Plans` in de lijst met soorten publiek.

Klik **daarna**.

![ 5-04-select-segment.png ](./images/504selectsegment.png)

Klik **toevoegen nieuw gebied**, doorblader schema en selecteer het gebied `--aepTenantId--identification.core.ecid` (schrap om het even welk ander gebied dat automatisch zou worden getoond).

Klik **daarna**.

![ 5-05-select-attributes.png ](./images/505selectattributes.png)

Klik **Afwerking**.

![ 5-06-bestemming-finish.png ](./images/506destinationfinish.png)

Uw publiek wordt nu geactiveerd naar uw bestemming van de Hub van de Gebeurtenis van Microsoft.

![ 5-07-bestemming-segment-added.png ](./images/507destinationsegmentadded.png)

Volgende Stap: [ 2.4.6 creeer uw Microsoft Azure Project ](./ex6.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
