---
title: Segmentactivering naar Microsoft Azure Event Hub - Setup the Event Hub RTCDP destination in Adobe Experience Platform
description: Segmentactivering naar Microsoft Azure Event Hub - Setup the Event Hub RTCDP destination in Adobe Experience Platform
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# 2.4.2 Configureer uw Azure Event Hub Destination in Adobe Experience Platform

## 2.4.2.1 Vereiste parameters voor Azure Connection identificeren

Als u een bestemming van een gebeurtenishub in Adobe Experience Platform wilt definiëren, hebt u uw:

- Naamruimte van gebeurtenishubs
- Gebeurtenissenhub
- Azure SAS Key Name
- Azure SAS Key

De Hub van de gebeurtenis en EventHub namespace zijn bepaald in de vorige oefening: [ oefent 1 uit - de Hub van de Gebeurtenis van de Opstelling in Azure ](./ex1.md)

### Naamruimte van gebeurtenishubs

Om de bovengenoemde informatie in Azure Portal te zoeken, navigeer aan [ https://portal.azure.com/#home ](https://portal.azure.com/#home). Zorg ervoor dat u het correcte Azure-account gebruikt.

Selecteer **Alle Middelen** in Azure Portal:

![ 2-01-azure-all-resources.png ](./images/2-01-azure-all-resources.png)

### Gebeurtenissenhub

Zoek een middel met middeltype **Namespace van de Hubs van de Gebeurtenis**, als u de noemende overeenkomsten volgde die in de vorige oefening worden gebruikt zult u de Hubs Namespace van de Gebeurtenis `--aepUserLdap---aep-enablement` zijn. Neem er nota van, u zult het in de volgende oefening nodig hebben.

![ 2-02-selecteren-gebeurtenis-hubs-namespace.png ](./images/2-02-select-event-hubs-namespace.png)

Klik op de naam van de naamruimte Gebeurtenishubs om de details op te halen:

![ 2-03-select-event-hub.png ](./images/2-03-select-event-hub.png)

Selecteer **de Hubs van de Gebeurtenis** om een lijst van Gebeurtenishubs te krijgen die in uw Namespace van de Hubs van de Gebeurtenis wordt bepaald, als u de noemende overeenkomsten volgde die in de vorige oefening worden gebruikt zult u een genoemde Hub van de Gebeurtenis `--aepUserLdap---aep-enablement-event-hub` vinden. Neem er nota van, u zult het in de volgende oefening nodig hebben.

![ 2-04-gebeurtenis-hub-selected.png ](./images/2-04-event-hub-selected.png)

### SAS-sleutelnaam

Selecteer **Gedeeld toegangsbeleid** voor uw **Namespace van de Hubs van de Gebeurtenis**

![ 2-05-select-sas.png ](./images/2-05-select-sas.png)

U zult een lijst van Gedeeld toegangsbeleid zien. De SAS Sleutel die wij zoeken is **RootManageSharedAccessKey**. Dit is de SAS Key-naam. Schrijf het op.

![ 2-06-sas-overview.png ](./images/2-06-sas-overview.png)

### SAS-sleutelwaarde

Klik op **RootManageSharedAccessKey** om de Belangrijkste Waarde van SAS te krijgen. En druk het **Exemplaar aan klembord** pictogram om de **Primaire sleutel** te kopiëren:

![ 2-07-sas-key-value.png ](./images/2-07-sas-key-value.png)

### Overzicht van doelwaarden

Op dit punt zou u alle waarden moeten geïdentificeerd hebben nodig om de Azure bestemming van de Hub van de Gebeurtenis in Adobe Experience Platform in real time CDP te bepalen.

| Naam doelkenmerk | Waarde doelkenmerk | Voorbeeldwaarde |
|---|---|---|
| sasKeyName | SAS-sleutelnaam | RootManageSharedAccessKey |
| sasKey | SAS-sleutelwaarde | srREx9ShJG1Rv7f/... |
| namespace | Naamruimte van gebeurtenishubs | `--aepUserLdap---aep-enablement` |
| eventHubName | Gebeurtenissenhub | `--aepUserLdap---aep-enablement-event-hub` |

## 2.4.2.2 Azure Event Hub Destination in Adobe Experience Platform maken

Login aan Adobe Experience Platform door naar dit URL te gaan: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

Ga naar **Doelen**, dan gaan naar **Catalogus**.

![ Ingestie van Gegevens ](./images/sb2a.png)

Selecteer **de Opslag van de Wolk van 0} {en ga naar** Azure de Hubs van de Gebeurtenis **en klik** Opstelling **of** vormen **:**

![ 2-08-list-references.png ](./images/2-08-list-destinations.png)

Vul de bestemmingswaarden in die u in de vorige oefening hebt verzameld. Daarna, klik **verbinden met Doel**.

![ 2-09-bestemming-values.png ](./images/2-09-destination-values.png)

Als uw geloofsbrieven correct waren, zult u een bevestiging zien: **Verbonden**.

![ 2-09-bestemming-values.png ](./images/2-09-destination-valuesa.png)

U moet nu de naam en beschrijving invoeren in de notatie `--aepUserLdap---aep-enablement` . Ga **eventHubName** in (zie vorige oefening, kijkt het als dit: `--aepUserLdap---aep-enablement-event-hub`) en klik **daarna**.

![ 2-10-create-destination.png ](./images/2-10-create-destination.png)

Klik **sparen en weg**.

![ 2-11-save-exit-activation.png ](./images/2-11-save-exit-activation.png)

Je bestemming is nu gemaakt en beschikbaar in Adobe Experience Platform.

![ 2-12-bestemming-created.png ](./images/2-12-destination-created.png)

Volgende Stap: [ 2.4.3 leidt tot een segment ](./ex3.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
