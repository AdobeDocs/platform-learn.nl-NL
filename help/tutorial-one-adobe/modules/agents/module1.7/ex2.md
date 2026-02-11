---
title: Gebruik Cursor.ai om uw project te ontwikkelen
description: Gebruik Cursor.ai om uw project te ontwikkelen
kt: 5342
doc-type: tutorial
source-git-commit: 2bfa7f4bee54df8411c96b001224d2986e9fcaf9
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# 1.7.2 Gebruik Cursor.ai om uw project te ontwikkelen

## 1.7.2.1 Stel uw map en gereedschappen in

Maak op uw bureaublad een nieuwe map met de naam `--aepUserLdap---commerce`

![ Commerce &amp; Agentic ](./images/cursorai1.png)

Klik met de rechtermuisknop op uw map en selecteer **Nieuwe terminal bij Map** .

![ Commerce &amp; Agentic ](./images/cursorai2.png)

Dan moet je dit zien.

![ Commerce &amp; Agentic ](./images/cursorai3.png)

U moet nu een bestaande bewaarplaats van Github klonen, die u [ https://github.com/adobe/commerce-integration-starter-kit ](https://github.com/adobe/commerce-integration-starter-kit) kunt bekijken.

Deze opslagplaats is Adobe-integratiestartkit die Adobe Developer App Builder gebruikt om de betrouwbaarheid van real-time verbindingen te verbeteren en de tijd-aan-markt voor integratie tussen Adobe Commerce en andere back-office systemen, zoals ERPs, CRMs, en PIMs te verminderen.

![ Commerce &amp; Agentic ](./images/cursorai4.png)

Er zijn verscheidene manieren om deze bewaarplaats te klonen, in dit voorbeeld wordt de Terminal gebruikt.

Ga het volgende bevel in uw Eind venster in en voer het uit.

`git clone https://github.com/adobe/commerce-integration-starter-kit`

![ Commerce &amp; Agentic ](./images/cursorai5.png)

Na een paar seconden ziet u dit resultaat.

![ Commerce &amp; Agentic ](./images/cursorai6.png)

Navigeer vervolgens naar de map die zojuist is gemaakt. Voer de volgende opdracht in en voer deze uit.

`cd commerce-integration-starter-kit`

![ Commerce &amp; Agentic ](./images/cursorai7.png)

Dan moet je dit zien.

![ Commerce &amp; Agentic ](./images/cursorai8.png)

Vervolgens moet u de uitbreidbaarheidsgereedschappen van Commerce instellen voor Cursor.ai. Voer de volgende opdracht in en voer deze uit.

`aio commerce extensibility tools-setup`

![ Commerce &amp; Agentic ](./images/cursorai9.png)

Selecteer **Huidige folder**.

![ Commerce &amp; Agentic ](./images/cursorai10.png)

Selecteer **Cursor**.

![ Commerce &amp; Agentic ](./images/cursorai11.png)

Selecteer **npm**.

![ Commerce &amp; Agentic ](./images/cursorai12.png)

Na een paar minuten moet je dit zien.

![ Commerce &amp; Agentic ](./images/cursorai13.png)

Door de uitbreidingshulpmiddelen van Commerce voor Cursor.ai te installeren, is er nu een server MCP beschikbaar als deel van uw milieu Cursor.ai. In de volgende oefeningen, zult u die server gebruiken MCP om u te helpen het app builder project ontwikkelen en opstellen.

## 1.7.2.2 Webhaak instellen

Voor deze oefening, zult u een webhaak nodig hebben die moet worden gevormd zodat wanneer een orde wordt gecreeerd, de ordegebeurtenis aan die webhaak kan worden gestroomd. In deze oefening, zult u een steekproefeindpunt gebruiken gebruikend [ https://pipedream.com/requestbin ](https://pipedream.com/requestbin).

Ga naar [ https://pipedream.com/requestbin ](https://pipedream.com/requestbin), creeer een rekening en creeer dan een werkruimte. Als de werkruimte eenmaal is gemaakt, ziet u iets gelijkaardigs.

Klik **exemplaar** om url te kopiëren. U zult deze url in de volgende oefening moeten specificeren. De URL in dit voorbeeld is `https://eodts05snjmjz67.m.pipedream.net` .

![ Cursor.ai + Commerce ](./images/webhook1.png)

## 1.7.2.3 Cursor.ai

Open Cursor.ai. Klik **Open project**.

![ Cursor.ai + Commerce ](./images/cursorai14.png)

Navigeer naar de map die u hebt gemaakt en die de naam `--aepUserLdap---commerce` moet krijgen. Selecteer in die map de map met de naam `commerce-integration-starter-kit` . Klik **Open**.

![ Cursor.ai + Commerce ](./images/cursorai15.png)

Dan moet je dit zien. Voordat u verdergaat, moet u ervoor zorgen dat de map op hoofdniveau die wordt geopend in Cursor.ai, `commerce-integration-starter-kit` is.

![ Cursor.ai + Commerce ](./images/cursorai16.png)

`I would like to build an app that subscribes to order created events and sends them to a configurable URL with basic authentication`

## Volgende stappen

Ga terug naar [ Intelligente Hulpmiddelen van de Ontwikkelaar voor Adobe Commerce ](./aiassisteddev.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}