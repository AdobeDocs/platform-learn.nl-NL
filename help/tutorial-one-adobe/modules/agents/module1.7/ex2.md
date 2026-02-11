---
title: Gebruik Cursor om uw project te ontwikkelen
description: Gebruik Cursor om uw project te ontwikkelen
kt: 5342
doc-type: tutorial
exl-id: c73498b6-5e08-41b5-81a9-c0a76a6e2792
source-git-commit: 25901342e8d9c46b0edce3b2092b9f1d66ba5849
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 0%

---

# 1.7.2 De Cursor van het gebruik om uw project te ontwikkelen

## 1.7.2.1 Stel uw map en gereedschappen in

Maak op uw bureaublad een nieuwe map met de naam `--aepUserLdap---commerce`

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai1.png)

Klik met de rechtermuisknop op uw map en selecteer **Nieuwe terminal bij Map** .

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai2.png)

Dan moet je dit zien.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai3.png)

U moet nu een bestaande bewaarplaats van Github klonen, die u [&#x200B; https://github.com/adobe/commerce-integration-starter-kit &#x200B;](https://github.com/adobe/commerce-integration-starter-kit) kunt bekijken.

Deze opslagplaats is Adobe-integratiestartkit die Adobe Developer App Builder gebruikt om de betrouwbaarheid van real-time verbindingen te verbeteren en de tijd-aan-markt voor integratie tussen Adobe Commerce en andere back-office systemen, zoals ERPs, CRMs, en PIMs te verminderen.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai4.png)

Er zijn verscheidene manieren om deze bewaarplaats te klonen, in dit voorbeeld wordt de Terminal gebruikt.

Ga het volgende bevel in uw Eind venster in en voer het uit.

`git clone https://github.com/adobe/commerce-integration-starter-kit`

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai5.png)

Na een paar seconden ziet u dit resultaat.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai6.png)

Navigeer vervolgens naar de map die zojuist is gemaakt. Voer de volgende opdracht in en voer deze uit.

`cd commerce-integration-starter-kit`

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai7.png)

Dan moet je dit zien.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai8.png)

Vervolgens moet u de Commerce-gereedschappen voor uitbreidbaarheid instellen voor Cursor. Voer de volgende opdracht in en voer deze uit.

`aio commerce extensibility tools-setup`

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai9.png)

Selecteer **Huidige folder**.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai10.png)

Selecteer **Cursor**.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai11.png)

Selecteer **npm**.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai12.png)

Na een paar minuten moet je dit zien.

![&#x200B; Commerce &amp; Agentic &#x200B;](./images/cursorai13.png)

Door Commerce-uitbreidingsgereedschappen voor Cursor te installeren, is er nu een MCP-server beschikbaar als onderdeel van de cursoromgeving. In de volgende oefeningen, zult u die server gebruiken MCP om u te helpen het app builder project ontwikkelen en opstellen.

## 1.7.2.2 Webhaak instellen

Voor deze oefening, zult u een webhaak nodig hebben die moet worden gevormd zodat wanneer een orde wordt gecreeerd, de ordegebeurtenis aan die webhaak kan worden gestroomd. In deze oefening, zult u een steekproefeindpunt gebruiken gebruikend [&#x200B; https://pipedream.com/requestbin &#x200B;](https://pipedream.com/requestbin).

Ga naar [&#x200B; https://pipedream.com/requestbin &#x200B;](https://pipedream.com/requestbin), creeer een rekening en creeer dan een werkruimte. Als de werkruimte eenmaal is gemaakt, ziet u iets gelijkaardigs.

Klik **exemplaar** om url te kopiëren. U zult deze url in de volgende oefening moeten specificeren. De URL in dit voorbeeld is `https://eodts05snjmjz67.m.pipedream.net` .

![&#x200B; Cursor + Commerce &#x200B;](./images/webhook1.png)

## 1.7.2.3 App maken met cursor

Open de cursor. Klik **Open project**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai14.png)

Navigeer naar de map die u hebt gemaakt en die de naam `--aepUserLdap---commerce` moet krijgen. Selecteer in die map de map met de naam `commerce-integration-starter-kit` . Klik **Open**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai15.png)

Dan moet je dit zien. Voordat u verdergaat, moet u controleren of de map op hoofdniveau die in de cursor wordt geopend, `commerce-integration-starter-kit` is.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai16.png)

Gebruik de sneltoets `Cmd + Shift + J` om de cursorinstellingen te openen. Dan moet je dit zien. Ga naar **Hulpmiddelen &amp; MCP**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai17.png)

Laat de server MCP **handel-rekbaarheid** toe. Zodra dat wordt gedaan, klik **X** om het venster te sluiten.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai18.png)

Kopieer de volgende prompt en plak deze in Cursor. Dan, klik **verzenden** knoop.

`I would like to build an app that subscribes to order created events and sends them to a configurable URL with basic authentication`

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai19.png)

De cursor begint met redeneren en uitvoeren. Cursor vraagt u een paar keer om bevestiging. Wanneer dat gebeurt, klik **Looppas**. Dit kan 5 tot 10 keer gebeuren, afhankelijk van het redeneren en uw montages.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai20.png)

Na een paar minuten zou je zoiets moeten zien.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai21.png)

De volgende stap, zoals aangegeven door de cursor, is het maken van een bestand met de naam `.env` en het verschaffen van de vereiste variabelen.

## 1.7.2.4 Het bestand your.env maken

Selecteer het dossier **env.dist**. Voer de opdracht `Cmd + C` in en voer vervolgens de opdracht `Cmd + V` in.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai22.png)

Wijzig de naam van het nieuwe bestand in `.env` .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai23.png)

Vervolgens moet u de waarden opgeven voor alle variabelen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai24.png)

Hier vind je alle vereiste informatie.

### Commerce-eindpunten

U kunt deze variabelen vinden door naar [&#x200B; https://experience.adobe.com &#x200B;](https://experience.adobe.com) te gaan. Klik **Commerce**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai25.png)

Dan moet je dit zien. Klik het **informatie** pictogram naast uw milieu ACCS, dat zou moeten worden genoemd `--aepUserLdap-- - ACCS`. Kopieer de waarden van het REST eindpunt en het GraphQL eindpunt.

In dit voorbeeld zijn dit de waarden die u wilt kopiëren. Plak ze naast de onderstaande variabelen in het bestand **.env** op regel 6 &amp; 7.


- **COMMERCE_BASE_URL** = https://na1-sandbox.api.commerce.adobe.com/Lkp3U7tvTBNAmpFvwnZJ4B/
- **COMMERCE_GRAPHQL_ENDPOINT** = https://na1-sandbox.api.commerce.adobe.com/Lkp3U7tvTBNAmpFvwnZJ4B/graphql

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai26.png)

Dit moet u vervolgens opnemen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai26a.png)

### Adobe I/O-projectvariabelen

U kunt deze variabelen vinden door naar [&#x200B; https://developer.adobe.com/console &#x200B;](https://developer.adobe.com/console) te gaan. Ga naar **Projecten** en klik om het project van Adobe I/O te openen u in de vorige oefening creeerde, die zou moeten worden genoemd `--aepUserLdap-- Commerce Events`.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai27.png)

Ga naar **Productie**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai28.png)

Ga naar **Server-aan-Server**. Dan moet je dit zien.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai29.png)

Kopieer de waarden van identiteitskaart van de Server van gebieden **&#x200B;**, **Geheime cliënt**, **identiteitskaart van de Technische Rekening**, **E-mail van de Rekening** en **identiteitskaart van de Organisatie** en kleef hen naast de hieronder variabelen in het dossier **.env** op lijnen 13-17.

- **OAUTH_CLIENT_ID**= **identiteitskaart van de Cliënt**
- **OAUTH_CLIENT_SECRET**= **Geheime cliënt**
- **OAUTH_TECHNICAL_ACCOUNT_ID**= **identiteitskaart van de Technische Rekening**
- **OAUTH_TECHNICAL_ACCOUNT_EMAIL**= **E-mail van de Technische Rekening**
- **OAUTH_ORG_ID**= **identiteitskaart van de Organisatie**

Dit moet u vervolgens opnemen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai29a.png)

### COMMERCE_ADOBE_IO_EVENTS_MERCHANT_ID

Voor het gebied **COMMERCE_ADOBE_IO_EVENTS_MERCHANT_ID=**, ga de waarde `--aepUserLdap--_commerce_events` op lijn 34 in het dossier **.env** in.

Dit moet u vervolgens opnemen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai30.png)

### Workspace-configuraties

Om deze variabelen terug te winnen, ga terug naar uw project van Adobe I/O en klik **overzicht van Workspace**.

Na het gaan naar **overzicht van Workspace**, hebben een blik bij URL, die als dit zou moeten kijken: **https://developer.adobe.com/console/projects/133309/4566206088345586770/workspaces/4566206088345619105/details**.

Het eerste aantal in dit voorbeeld, 133309, is de waarde voor het gebied **IO_CONSUMER_ID** te gebruiken.
Het tweede aantal in dit voorbeeld, 4566206088345586770, is de waarde voor het gebied **IO_PROJECT_ID** te gebruiken.
Het derde aantal in dit voorbeeld, 4566206088345619105, is de waarde voor het gebied **IO_WORKSPACE_ID** te gebruiken.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai31.png)

- **IO_CONSUMER_ID**= 13309
- **IO_PROJECT_ID**= 456620608834586770
- **IO_WORKSPACE_ID**= 4566206088345619105

Kopieer deze waarden en plak ze naast de onderstaande variabelen in het bestand **.env** op de regels 42-44.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai32.png)

### EVENT_PREFIX

Voor het gebied **EVENT_PREFIX =**, ga de waarde `--aepUserLdap--_` op lijn 47 in het dossier **.env** in.

Dit moet u vervolgens opnemen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai33.png)

### Webhaak

Voor het gebied **ORDER_WEBHOOK_URL**, zou u URL van de webhaak moeten kleven u vroeger in deze oefening creeerde, die als dit zou moeten kijken: `https://eodts05snjmjz67.m.pipedream.net`.

Dit moet u vervolgens opnemen in het bestand **.env** .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai34.png)

### App Builder-referenties

Werk de volgende variabelen in het bestand **.env** bij op de regels 54-55:

- **AIO_RUNTIME_NAMESPACE**=
- **AIO_RUNTIME_AUTH**=

U kunt de waarden voor deze variabelen terugwinnen door naar uw project van Adobe I/O terug te gaan. Ga naar **overzicht van Workspace** en klik **Download allen**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai35.png)

Een bestand als dit wordt vervolgens gedownload. Open dat bestand in een teksteditor.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai36.png)

De rol aan het recht tot u **runtime** ziet. U zou dan het gebied **naam** moeten zien, die de waarde voor **AIO_RUNTIME_NAMESPACE** bevat.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai37.png)

De rol verder aan het recht tot u **auth** ziet, die de waarde voor **AIO_RUNTIME_AUTH** bevat.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai38.png)

Plak beide waarden in het bestand **.env** op de regels 54-55 en zorg dat dit het geval is.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai39.png)

Uw **.env** dossier wordt nu volledig gevormd.

## 1.7.2.5 workspace.json

In de vorige stap hebt u een dergelijk bestand gedownload van uw Adobe I/O-project.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai36.png)

Wijzig de naam van dat bestand en gebruik de naam `workspace.json` .

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai40.png)

Kopieer het dossier in de folder **manuscripten**> **op het instappen**> **config**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai41.png)

## 1.7.2.6 Aanmelden bij Adobe I/O

Ga terug naar het eindvenster dat u eerder had gebruikt. Voer de opdracht `aio login` in.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai44.png)

Dit wordt dan weergegeven nadat u zich hebt aangemeld via uw browser.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai45.png)

## 1.7.2.7 Klaar voor implementatie

Kopieer de volgende prompt en plak deze in Cursor. Dan, klik **verzenden** knoop.

`Please deploy this code to Adobe I/O`

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai42.png)

Klik **Looppas** om de actie toe te staan, kan de Curseur u verscheidene tijden vragen om een actie te bevestigen.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai43.png)

De implementatie wordt na een paar minuten voltooid.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai46.png)

Kopieer de volgende prompt en plak deze in Cursor. Dan, klik **verzenden** knoop.

`run the onboarding to commerce`

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai50.png)

Na een paar minuten moet je dit zien.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai51.png)

Kopieer de volgende prompt en plak deze in Cursor. Dan, klik **verzenden** knoop.

`subscribe to commerce events`

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai47.png)

Na een paar minuten moet je dit zien.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai49.png)

## 1.7.2.8 Configuratie controleren in Adobe Commerce as a Cloud Service

Ga naar [&#x200B; https://experience.adobe.com &#x200B;](https://experience.adobe.com). Klik **Commerce**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai60.png)

Klik op de Adobe Commerce as a Cloud Service-omgeving om deze te openen en meld u vervolgens aan.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai61.png)

Ga naar **Systeem** en dan naar **Abonnementen van de Gebeurtenis**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai62.png)

Deze lijst met abonnementen voor gebeurtenissen wordt dan weergegeven.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai63.png)

Ga naar **Opslag** en dan naar **Configuratie**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai64.png)

Ga naar **de Diensten van Adobe** en selecteer **Adobe I/O Events**. U zou dan moeten zien dat het gebied **de Configuratie van Adobe I/O Workspace** een waarde van een paar asterixen heeft en gebied **Merchant identiteitskaart** zou ook een waarde als `--aepUserLdap--_commerce_events` moeten hebben.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai65.png)

Met deze configuratie op zijn plaats, kunt u uw configuratie nu testen.

## 1.7.2.9 Uw scenario testen

Open uw website.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai101.png)

Ga naar **horloges** en klik om het even welk product.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai102.png)

Vorm het product en klik **toevoegen aan wortel**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai103.png)

Klik het **pictogram van het Kart** en selecteer **Controle**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai104.png)

Vul uw details in en klik **orde van de Plaats**.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai105.png)

Vervolgens wordt de bestelling bevestigd.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai106.png)

Schakel over naar de webhaaktoepassing. Er wordt nu een inkomende gebeurtenis weergegeven voor de volgorde die zojuist is bevestigd.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai107.png)

## 1.7.2.10 Foutopsporing in Adobe I/O

Ga terug naar je Adobe I/O-project. Ga naar **overzicht van Workspace**. Je zou iets gelijkaardigs moeten zien. Schuif een beetje omlaag.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai108.png)

Klik om **Synchronisatie van de Orde van Commerce** te openen.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai109.png)

Ga naar **zuivert het Vinden**. U kunt daar de recentste inkomende gebeurtenissen, samen met hun lading vinden. Dit is handig als u wilt weten welke gebeurtenissen zijn verwerkt en of deze zijn verwerkt.

![&#x200B; Cursor + Commerce &#x200B;](./images/cursorai110.png)

## Volgende stappen

Ga terug naar [&#x200B; Intelligente Hulpmiddelen van de Ontwikkelaar voor Adobe Commerce &#x200B;](./aiassisteddev.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
