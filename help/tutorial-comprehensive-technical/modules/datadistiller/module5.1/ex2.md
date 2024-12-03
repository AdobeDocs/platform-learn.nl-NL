---
title: Query-service - Aan de slag
description: Query-service - Aan de slag
kt: 5342
doc-type: tutorial
exl-id: 5c4615c6-41c0-465a-b9b6-f59eef388c73
source-git-commit: b53ee64ae8438b8f48f842ed1f44ee7ef3e813fc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---

# 5.1.2 Aan de slag

## De gebruikersinterface van Adobe Experience Platform leren kennen

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)


## Gegevens op het platform verkennen

Het leveren van gegevens van verschillende kanalen is een zware taak voor elk merk. In deze exercitie werken Citi Signal-klanten samen met Citi Signal op haar website, op haar mobiele app. De aankoopgegevens worden verzameld door het Point of Sale-systeem van Citi Signal en ze beschikken over CRM- en Loyalty-gegevens. Citi Signal gebruikt Adobe Analytics en Adobe Launch om gegevens vast te leggen op zijn website, mobiele app en POS-systeem. Deze gegevens stromen dus al naar Adobe Experience Platform. Laten we beginnen met het verkennen van alle gegevens voor Citi Signal die al in Adobe Experience Platform bestaan.

In het linkermenu, ga naar **Datasets**.

![ emea-website-interactie-dataset.png ](./images/emea-website-interaction-dataset.png)

Citi Signal streamt gegevens naar Adobe Experience Platform en deze gegevens zijn beschikbaar in de gegevensset `Demo System - Event Dataset for Website (Global v1.1)` . Zoeken naar `Demo System - Event Dataset for Website` .

![ emea-callcenter-interaction-dataset.png ](./images/emea-website-interaction-dataset1.png)

De Interactie-gegevens van Callcenter van Citi Signal worden vastgelegd in de gegevensset `Demo System - Event Dataset for Call Center (Global v1.1)` . Zoek naar `Demo System - Event Dataset for Call Center` gegevens in onderzoeksdoos. Klik op de naam van de gegevensset om deze te openen.

![ emea-callcenter-interaction-dataset.png ](./images/emea-callcenter-interaction-dataset.png)

Na het klikken van de dataset, zult u een overzicht van de datasetactiviteit zoals ingebed en ontbroken partijen krijgen.

![ voorproef-interactie-dataset.png ](./images/preview-interaction-dataset.png)

Klik op **Dataset van de Voorproef** om een steekproef van de gegevens te zien die in `Demo System - Event Dataset for Call Center (Global v1.1)` dataset worden opgeslagen. Het linkerpaneel toont schemastructuur voor deze dataset.

![ onderzoek-interactie-dataset.png ](./images/explore-interaction-dataset.png)

Klik de **Dichte** knoop om het **venster van de Dataset van de Voorproef** te sluiten.

## Inleiding aan de Dienst van de Vraag

De Dienst van de Vraag van Adobe Experience Platform wordt betreden door op **Vragen** in het linkermenu te klikken.

![ select-questions.png ](./images/select-queries.png)

Door naar **Logboek** te gaan zult u de pagina van de Lijst van de Vraag zien, die u een lijst van alle vragen verstrekt die in deze organisatie, met het recentste bij de bovenkant in werking hebben gesteld.

![ vraag-list.png ](./images/query-list.png)

Klik op een SQL-query in de lijst en bekijk de details in de rechtertrack.

![ klik-sql-query.png ](./images/click-sql-query.png)

U kunt door het venster bladeren om de volledige query weer te geven, of u kunt op het hieronder gemarkeerde pictogram klikken om de volledige query naar uw laptop te kopiëren. U hoeft de query momenteel niet te kopiëren.

![ klik-exemplaar-query.png ](./images/click-copy-query.png)

U kunt niet enkel de vragen zien die zijn uitgevoerd, laat dit Gebruikersinterface u nieuwe datasets van vragen tot stand brengen. Deze gegevenssets kunnen worden gekoppeld aan het Adobe Experience Platform-klantprofiel in realtime of kunnen worden gebruikt als invoer voor Adobe Experience Platform Data Science Workspace.

## Connect PSQL Client to Query Service

De Dienst van de vraag steunt cliënten met een bestuurder voor PostSQL. In dit zullen wij PSQL, een bevel-lijn interface, en Power BI of Tableau gebruiken. Laten we verbinding maken met PSQL.

Klik op **Geloofsbrieven**.

![ vragen-selecteren-configuration.png ](./images/queries-select-configuration.png)

U ziet hieronder het scherm. Het scherm van de Configuratie verstrekt serverinformatie en geloofsbrieven voor het voor authentiek verklaren aan de Dienst van de Vraag. Momenteel, zullen wij op de rechterkant van het scherm concentreren dat een verbindingsbevel voor PSQL bevat. Klik op de knop Kopiëren om de opdracht naar het klembord te kopiëren.

![ copy-psql-connection.png ](./images/copy-psql-connection.png)

Voor Vensters: open de bevellijn door de venstersleutel te raken en cmd te typen en dan op het Snelle resultaat van het Bevel te klikken.

![ open-bevel-prompt.png ](./images/open-command-prompt.png)

Voor macOS: open terminal.app via spotlight-zoekopdracht:

![ open-terminal-osx.png ](./images/open-terminal-osx.png)

Plak het verbindingsbevel dat u van de Dienst UI van de Vraag hebt gekopieerd en druk binnengaan in het venster van de bevelherinnering:

Windows:

![ bevel-herinnering-connected.png ](./images/command-prompt-connected.png)

MacOS:

![ bevel-herinnering-deeg-osx.png ](./images/command-prompt-paste-osx.png)

U bent nu verbonden met de Dienst van de Vraag gebruikend PSQL.

In de volgende oefeningen zal er behoorlijk wat interactie met dit venster zijn. Wij zullen naar het als uw **PSQL bevel-lijn interface** verwijzen.

Nu bent u klaar om vragen te beginnen verzenden.

Volgende Stap: [ 5.1.3 Gebruikend de Dienst van de Vraag ](./ex3.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)
