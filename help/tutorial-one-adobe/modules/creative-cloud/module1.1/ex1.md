---
title: Aan de slag met Firefly Services
description: Leer hoe u Postman en Adobe I/O kunt gebruiken om query's uit te voeren op Adobe Firefly Services-API's
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 5ee9c3b7cde5444ecceca4b01cc275d6263d8a59
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Firefly Services

Leer hoe u Postman en Adobe I/O kunt gebruiken om query&#39;s uit te voeren op Adobe Firefly Services-API&#39;s.

## 1.1.1.1 Vereisten

Alvorens met deze oefening verder te gaan, moet u de opstelling van [ uw project van Adobe I/O ](./../../../modules/getting-started/gettingstarted/ex6.md) hebben voltooid, en u moet ook een toepassing gevormd hebben om met APIs, zoals [ Postman ](./../../../modules/getting-started/gettingstarted/ex7.md) of [ PostBuster ](./../../../modules/getting-started/gettingstarted/ex8.md) in wisselwerking te staan.

## 1.1.1.2 Adobe I/O - access_token

In **Adobe IO - OAuth** inzameling, selecteer het verzoek genoemd **POST - krijg het Token van de Toegang** en selecteer **verzend**. De reactie zou een nieuwe **versnelling** moeten bevatten.

![ Postman ](./images/ioauthresp.png){zoomable="yes"}

## 1.1.1.3 Firefly Services API, Text 2 Image

Nu u een geldig en vers access_token hebt, bent u klaar om uw eerste aanvraag naar Firefly Services API&#39;s te verzenden.

Selecteer het verzoek genoemd **POST - Firefly - T2I V3** van de **FF - de Ingenieurs van de Technologie van de Diensten van Firefly** inzameling.

![ Firefly ](./images/ff1.png){zoomable="yes"}

Kopieer de URL van de afbeelding uit het antwoord en open deze in uw webbrowser om de afbeelding weer te geven.

![ Firefly ](./images/ff2.png){zoomable="yes"}

Er moet een mooie afbeelding worden afgebeeld `horses in a field` .

![ Firefly ](./images/ff3.png){zoomable="yes"}

U kunt vrij spelen met de API-aanvraag voordat u verdergaat met de volgende oefening.

## Volgende stappen

Ga naar [ optimaliseer uw proces van Firefly gebruikend Microsoft Azure en presigned URLs ](./ex2.md){target="_blank"}

Ga terug naar [ Overzicht van de Diensten van Adobe Firefly ](./firefly-services.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
