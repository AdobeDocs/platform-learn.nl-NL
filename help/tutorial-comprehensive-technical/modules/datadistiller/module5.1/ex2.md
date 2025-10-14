---
title: Query-service - Aan de slag
description: Query-service - Aan de slag
kt: 5342
doc-type: tutorial
exl-id: 5c4615c6-41c0-465a-b9b6-f59eef388c73
source-git-commit: d9d9a38c1e160950ae755e352a54667c8a7b30f7
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 5.1.2 Aan de slag

## De gebruikersinterface van Adobe Experience Platform leren kennen

Ga naar [&#x200B; Adobe Experience Platform &#x200B;](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/sb1.png)

## Gegevens op het platform verkennen

Het leveren van gegevens van verschillende kanalen is een zware taak voor elk merk. In deze exercitie werken Citi Signal-klanten samen met Citi Signal op haar website, op haar mobiele app. De aankoopgegevens worden verzameld door het Point of Sale-systeem van Citi Signal en ze beschikken over CRM- en Loyalty-gegevens. Citi Signal gebruikt Adobe Analytics en Adobe Launch om gegevens vast te leggen op zijn website, mobiele app en POS-systeem. Deze gegevens stromen dus al naar Adobe Experience Platform. Laten we beginnen met het verkennen van alle gegevens voor Citi Signal die al in Adobe Experience Platform bestaan.

In het linkermenu, ga naar **Datasets**.

![&#x200B; emea-website-interactie-dataset.png &#x200B;](./images/emeawebsiteinteractiondataset.png)

Citi Signal streamt gegevens naar Adobe Experience Platform en deze gegevens zijn beschikbaar in de gegevensset `Demo System - Event Dataset for Website (Global v1.1)` . Zoeken naar `Demo System - Event Dataset for Website` .

![&#x200B; emea-callcenter-interaction-dataset.png &#x200B;](./images/emeawebsiteinteractiondataset1.png)

De Interactie-gegevens van Callcenter van Citi Signal worden vastgelegd in de gegevensset `Demo System - Event Dataset for Call Center (Global v1.1)` . Zoek naar `Demo System - Event Dataset for Call Center` gegevens in onderzoeksdoos. Klik op de naam van de gegevensset om deze te openen.

![&#x200B; emea-callcenter-interaction-dataset.png &#x200B;](./images/emeacallcenterinteractiondataset.png)

Na het klikken van de dataset, zult u een overzicht van de datasetactiviteit zoals ingebed en ontbroken partijen krijgen. Klik **Dataset van de Voorproef** om een steekproef van de gegevens te zien die in `Demo System - Event Dataset for Call Center (Global v1.1)` dataset worden opgeslagen.

![&#x200B; voorproef-interactie-dataset.png &#x200B;](./images/previewinteractiondataset.png)

Het linkerpaneel toont de schemastructuur voor deze dataset en op de rechterkant zult u een steekproef van de gegevens zien die werden opgenomen.

![&#x200B; onderzoek-interactie-dataset.png &#x200B;](./images/exploreinteractiondataset.png)

Klik **Sluiten** om het **venster van de Dataset van de Voorproef** te sluiten.

## Inleiding aan de Dienst van de Vraag

De Dienst van de vraag wordt betreden door **Vragen** in het linkermenu te klikken.

![&#x200B; select-questions.png &#x200B;](./images/selectqueries.png)

Door naar **Logboek** te gaan zult u de pagina van de Lijst van de Vraag zien, die u een lijst van alle vragen verstrekt die in deze organisatie, met het recentste bij de bovenkant in werking hebben gesteld.

![&#x200B; vraag-list.png &#x200B;](./images/querylist.png)

Klik op een SQL-query in de lijst en bekijk de details in de rechtertrack.

![&#x200B; klik-sql-query.png &#x200B;](./images/clicksqlquery.png)

U kunt door het venster bladeren om de volledige query weer te geven, of u kunt op het hieronder gemarkeerde pictogram klikken om de volledige query naar uw laptop te kopiëren. U hoeft de query momenteel niet te kopiëren.

![&#x200B; klik-exemplaar-query.png &#x200B;](./images/clickcopyquery.png)

U kunt niet enkel de vragen zien die zijn uitgevoerd, laat dit Gebruikersinterface u nieuwe datasets van vragen tot stand brengen. Deze gegevenssets kunnen worden gekoppeld aan het Adobe Experience Platform-klantprofiel in realtime of kunnen worden gebruikt als invoer voor Adobe Experience Platform Data Science Workspace.

## Connect PSQL Client to Query Service

De Dienst van de vraag steunt cliënten met een bestuurder voor PostSQL. In dit zullen wij PSQL, een bevel-lijn interface, en Power BI of Tableau gebruiken. Laten we verbinding maken met PSQL.

Klik **Geloofsbrieven**.

![&#x200B; vragen-selecteren-configuration.png &#x200B;](./images/queriesselectconfiguration.png)

U ziet hieronder het scherm. Het scherm verstrekt serverinformatie en geloofsbrieven voor het voor authentiek verklaren aan de Dienst van de Vraag. Momenteel, zullen wij op de rechterkant van het scherm concentreren dat een verbindingsbevel voor PSQL bevat. Klik de exemplaarknoop om het bevel aan uw klembord te kopiëren.

![&#x200B; copy-psql-connection.png &#x200B;](./images/copypsqlconnection.png)

Voor Vensters: open de bevellijn door de venstersleutel te raken en cmd te typen en dan op het Snelle resultaat van het Bevel te klikken.

![&#x200B; open-bevel-prompt.png &#x200B;](./images/opencommandprompt.png)

Voor macOS: open terminal.app via spotlight-zoekopdracht:

![&#x200B; open-terminal-osx.png &#x200B;](./images/openterminalosx.png)

Plak het verbindingsbevel dat u van de Dienst UI van de Vraag hebt gekopieerd en druk binnengaan in het venster van de bevelherinnering:

Windows:

![&#x200B; bevel-herinnering-connected.png &#x200B;](./images/commandpromptconnected.png)

MacOS:

![&#x200B; bevel-herinnering-deeg-osx.png &#x200B;](./images/commandpromptpasteosx.png)

U bent nu verbonden met de Dienst van de Vraag gebruikend PSQL.

In de volgende oefeningen zal er behoorlijk wat interactie met dit venster zijn. Wij zullen naar het als uw **PSQL bevel-lijn interface** verwijzen.

Nu bent u klaar om vragen te beginnen verzenden.

Volgende Stap: [&#x200B; 5.1.3 Gebruikend de Dienst van de Vraag &#x200B;](./ex3.md)

[Ga terug naar module 5.1](./query-service.md)

[Terug naar alle modules](../../../overview.md)
