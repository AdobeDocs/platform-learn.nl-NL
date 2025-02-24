---
title: Aan de slag met Firefly Services
description: Leer hoe u Postman en Adobe I/O kunt gebruiken om query's uit te voeren op Adobe Firefly Services-API's
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: c5a80b87ac8e997922cb8c69b4180c4220dd9862
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Firefly Services

Leer hoe u Postman en Adobe I/O kunt gebruiken om query&#39;s uit te voeren op Adobe Firefly Services-API&#39;s.

## 1.1.1.1 Voorwaarden

Alvorens met deze oefening verder te gaan, moet u de opstelling van [ uw project van Adobe I/O ](./../../../modules/getting-started/gettingstarted/ex6.md) hebben voltooid, en u moet ook een toepassing gevormd hebben om met APIs, zoals [ Postman ](./../../../modules/getting-started/gettingstarted/ex7.md) of [ PostBuster ](./../../../modules/getting-started/gettingstarted/ex8.md) in wisselwerking te staan.

## 1.1.1.2 firefly.adobe.com

Ga naar [ https://firefly.adobe.com ](https://firefly.adobe.com). Klik het **profiel** pictogram en zorg u aan de juiste **Rekening** het programma wordt geopend, die `--aepImsOrgName--` zou moeten zijn. Indien nodig, klik **Profiel van de Schakelaar** om aan die rekening over te schakelen.

![ Postman ](./images/ffui1.png){zoomable="yes"}

Ga de herinnering `Horses in a field` in en klik **produceert**.

![ Postman ](./images/ffui2.png){zoomable="yes"}

Dan zou je iets gelijkaardigs moeten zien.

![ Postman ](./images/ffui3.png){zoomable="yes"}

Daarna, open omhoog de **Hulpmiddelen van de Ontwikkelaar** in uw browser.

![ Postman ](./images/ffui4.png){zoomable="yes"}

Dan moet je dit zien. Ga naar het **Netwerk** lusje.

![ Postman ](./images/ffui5.png){zoomable="yes"}

Ga de onderzoekstermijn **in produceren** en klik dan **** opnieuw. U zou dan een verzoek met de naam **moeten zien produceren-async**. Selecteer het en ga dan naar **Payload** waar u de details van het verzoek zult zien.

![ Postman ](./images/ffui6.png){zoomable="yes"}

Het verzoek dat u hier ziet is het verzoek dat wordt verzonden naar de server-kant achtergrond van de Diensten van Firefly. Het bevat verschillende belangrijke parameters:

- **herinnering**: Dit is uw herinnering, die om vraagt welk soort beeld Firefly zou moeten produceren

- **zaden**: In dit verzoek, werden de zaden geproduceerd op een willekeurige manier. Wanneer Firefly een afbeelding genereert, wordt het proces standaard gestart door een willekeurig getal, een zaadgetal genaamd, te kiezen. Dit willekeurige getal draagt bij aan wat elke afbeelding uniek maakt. Dit is ideaal als u een groot aantal afbeeldingen wilt genereren. Het kan echter voorkomen dat u afbeeldingen wilt genereren die op meerdere aanvragen lijken. Als Firefly bijvoorbeeld een afbeelding genereert die u wilt wijzigen met behulp van andere Firefly-opties (zoals voorinstellingen voor stijlen, referentieafbeeldingen, enz.), kunt u in toekomstige HTTP-aanvragen de onzekerheid van toekomstige afbeeldingen beperken en inbellen op de gewenste afbeelding.

![ Postman ](./images/ffui7.png){zoomable="yes"}

Bekijk de UI opnieuw. Verander de **verhouding van de Verhouding** in **Liggend (4:3)**.

![ Postman ](./images/ffui8.png){zoomable="yes"}

De rol neer aan **Gevolgen**, gaat naar **Thema&#39;s** en selecteert een effect zoals **Stripboek**.

![ Postman ](./images/ffui9.png){zoomable="yes"}

Open opnieuw de **Hulpmiddelen van de Ontwikkelaar** in uw browser. Dan, produceert de klik **** en inspecteert het netwerkverzoek dat wordt verzonden.

![ Postman ](./images/ffui10.png){zoomable="yes"}

Wanneer u de details van het netwerkverzoek inspecteert, zult u nu het volgende zien:

- **herinnering** is niet veranderd in vergelijking met het vorige verzoek
- **zaden** zijn niet veranderd in vergelijking met het vorige verzoek
- **grootte** is veranderd, gebaseerd op de verandering in **verhouding van de Verhouding**.
- **stijlen** is toegevoegd, en heeft een verwijzing naar het **stripverhaal** effect dat u selecteerde

![ Postman ](./images/ffui11.png){zoomable="yes"}

Voor de volgende oefening, zult u één van de **zaad** aantallen moeten gebruiken. Schrijf een zaadnummer van keuze.

In de volgende oefening, zult u gelijkaardige dingen met de Diensten van Firefly doen, maar dan door API in plaats van UI te gebruiken. In dit voorbeeld, is het zaadaantal **45781**.

## 1.1.1.3 Adobe I/O - access_token

In **Adobe IO - OAuth** inzameling, selecteer het verzoek genoemd **POST - krijg het Token van de Toegang** en selecteer **verzend**. De reactie zou een nieuwe **versnelling** moeten bevatten.

![ Postman ](./images/ioauthresp.png){zoomable="yes"}

## 1.1.1.4 Firefly Services API, Text 2 Image

Nu u een geldig en vers access_token hebt, bent u klaar om uw eerste aanvraag naar Firefly Services API&#39;s te verzenden.

Selecteer het verzoek genoemd **POST - Firefly - T2I V3** van de **FF - de Ingenieurs van de Technologie van de Diensten van Firefly** inzameling.

![ Firefly ](./images/ff1.png){zoomable="yes"}

Kopieer de URL van de afbeelding uit het antwoord en open deze in uw webbrowser om de afbeelding weer te geven.

![ Firefly ](./images/ff2.png){zoomable="yes"}

Er moet een mooie afbeelding worden afgebeeld `horses in a field` .

![ Firefly ](./images/ff3.png){zoomable="yes"}

In het **Lichaam** van uw verzoek **POST - Firefly - T2I V3**, voeg het volgende onder het gebied `"promptBiasingLocaleCode": "en-US"` toe en vervang veranderlijk `XXX` door één van de zaadaantallen die willekeurig door de Diensten UI van Firefly werden gebruikt. In dit voorbeeld, is het **zaad** aantal `45781`.

```json
,
  "seeds": [
    XXX
  ]
```

Klik **verzenden**. Vervolgens ontvangt u een reactie met een nieuwe afbeelding die door Firefly Services is gegenereerd. Open de afbeelding om deze weer te geven.

![ Firefly ](./images/ff4.png){zoomable="yes"}

U zou dan een nieuw beeld met lichte verschillen moeten zien, die op **worden gebaseerd zaad** dat werd gebruikt.

![ Firefly ](./images/ff5.png){zoomable="yes"}

Daarna, in het **Lichaam** van uw verzoek **POST - Firefly - T2I V3**, kleef het hieronder **stijlen** voorwerp onder het **zaden** voorwerp. Dit zal de stijl van het geproduceerde beeld in **comic_book** veranderen.

```json
,
  "contentClass": "art",
  "styles": {
    "presets": [
      "comic_book"
    ],
    "strength": 50
  }
```

Dan moet je dit hebben. Klik **verzenden**.

![ Firefly ](./images/ff6.png){zoomable="yes"}

Klik op de URL van de afbeelding om deze te openen.

![ Firefly ](./images/ff7.png){zoomable="yes"}

Uw afbeelding is nu een beetje gewijzigd. Bij het toepassen van voorinstellingen voor stijlen wordt de zaadafbeelding niet meer op dezelfde manier toegepast als voorheen.

![ Firefly ](./images/ff8.png){zoomable="yes"}

Verwijder de code voor het **zaden** voorwerp uit het **Lichaam** van uw verzoek. Klik **verzenden** en klik dan beeld URL die u van de reactie krijgt.

```json
,
  "seeds": [
    XXX
  ]
```

![ Firefly ](./images/ff9.png){zoomable="yes"}

Uw afbeelding is nu weer een beetje gewijzigd.

![ Firefly ](./images/ff10.png){zoomable="yes"}


## 1.1.1.5 Firefly Services API, Gen Expand

Selecteer het verzoek genoemd **POST - Firefly - Gen breidt zich** uit van **FF - de Ingenieurs van de Diensten van Firefly** inzameling en gaat naar het **Lichaam** van het verzoek.

- **grootte**: Ga de gewenste resolutie in. De waarde die u hier opgeeft, moet groter zijn dan de oorspronkelijke grootte van de afbeelding en mag niet groter zijn dan 4096.
- **image.source.url**: Dit gebied vereist een verbinding aan het beeld dat moet worden uitgebreid. In dit voorbeeld wordt een variabele gebruikt om te verwijzen naar de afbeelding die tijdens de vorige oefening is gegenereerd.

- **horizontale groepering**: Geaccepteerde waarden zijn: `"center"`, `"left`, `"right"`.
- **verticale groepering**: Geaccepteerde waarden zijn: `"center"`, `"top`, `"bottom"`.

![ Firefly ](./images/ff11.png){zoomable="yes"}

Klik op de afbeeldings-URL die deel uitmaakt van het antwoord.

![ Firefly ](./images/ff12.png){zoomable="yes"}

U ziet nu dat de afbeelding die in de vorige oefening is gegenereerd, is uitgebreid naar de resolutie van 3999x3999.

![ Firefly ](./images/ff13.png){zoomable="yes"}

Wanneer u de uitlijning van de plaatsing wijzigt, zal de uitvoer ook iets anders zijn. In dit voorbeeld, wordt de plaatsing veranderd in **verlaten, bodem**. Klik **verzenden** en klik dan om het geproduceerde beeld URL te openen.

![ Firefly ](./images/ff14.png){zoomable="yes"}

Vervolgens ziet u dat de oorspronkelijke afbeelding op een andere plaats wordt gebruikt, wat van invloed is op de hele afbeelding.

![ Firefly ](./images/ff15.png){zoomable="yes"}

## Volgende stappen

Ga naar [ optimaliseer uw proces van Firefly gebruikend Microsoft Azure en presigned URLs ](./ex2.md){target="_blank"}

Ga terug naar [ Overzicht van de Diensten van Adobe Firefly ](./firefly-services.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
