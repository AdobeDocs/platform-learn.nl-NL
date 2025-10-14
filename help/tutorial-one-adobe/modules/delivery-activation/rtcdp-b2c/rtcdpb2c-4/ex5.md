---
title: Audience Activation naar Microsoft Azure Event Hub - Publiek activeren
description: Audience Activation naar Microsoft Azure Event Hub - Publiek activeren
kt: 5342
doc-type: tutorial
exl-id: e6bac0ce-4a1e-4458-af3e-3d6ac40b9cb5
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 2.4.5 Activeer uw publiek

## publiek toevoegen aan Azure Event Hub Destination

In deze exercitie voegt u uw publiek `--aepUserLdap-- - Interest in Plans` toe aan uw `--aepUserLdap---aep-enablement` Azure Event Hub-bestemming.

Login aan Adobe Experience Platform door naar dit URL te gaan: [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../../modules/delivery-activation/datacollection/dc1.2/images/sb1.png)

Ga naar **Doelen**, dan klik **doorbladeren**. U zult dan alle beschikbare bestemmingen zien. Bepaal de plaats van uw bestemming en klik de 3 punten&#x200B;**..** zoals hieronder vermeld, dan klik **actief publiek**.

![&#x200B; 5-01-select-destination.png &#x200B;](./images/501selectdestination.png)

Dan zie je dit. Zoek naar uw publiek met uw LDAP en selecteer `--aepUserLdap-- - Interest in Plans` in de lijst met soorten publiek.

Klik **daarna**.

![&#x200B; 5-04-select-segment.png &#x200B;](./images/504selectsegment.png)

Klik **toevoegen nieuw gebied**, doorblader schema en selecteer het gebied `--aepTenantId--identification.core.ecid` (schrap om het even welk ander gebied dat automatisch zou worden getoond).

Klik **daarna**.

![&#x200B; 5-05-select-attributes.png &#x200B;](./images/505selectattributes.png)

Klik **Afwerking**.

![&#x200B; 5-06-bestemming-finish.png &#x200B;](./images/506destinationfinish.png)

Uw publiek wordt nu geactiveerd naar uw bestemming van de Hub van de Gebeurtenis van Microsoft.

![&#x200B; 5-07-bestemming-segment-added.png &#x200B;](./images/507destinationsegmentadded.png)

## Volgende stappen

Ga naar [&#x200B; 2.4.6 creeer uw Microsoft Azure Project &#x200B;](./ex6.md){target="_blank"}

Ga terug naar [&#x200B; Real-Time CDP: Audience Activation aan Microsoft Azure de Hub van de Gebeurtenis &#x200B;](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}
