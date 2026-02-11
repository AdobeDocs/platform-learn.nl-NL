---
title: De ontwikkelomgeving instellen
description: De ontwikkelomgeving instellen
kt: 5342
doc-type: tutorial
exl-id: c9bfb327-362f-4475-89da-8e9788940d56
source-git-commit: ce3ee3dde103383a6f7897cba36d548058879ea7
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# 1.7.1 De ontwikkelomgeving instellen

## 1.7.1.1 Uw Adobe I/O-project maken

Ga naar [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home){target="_blank"}.

Selecteer de juiste instantie in de rechterbovenhoek van het scherm. Uw instantie is `--aepImsOrgName--` .

>[!NOTE]
>
> In de onderstaande schermafbeelding ziet u een specifieke org die wordt geselecteerd. Wanneer u door dit leerprogramma gaat, is het zeer waarschijnlijk dat uw org een verschillende naam heeft. Wanneer u zich hebt aangemeld voor deze zelfstudie, hebt u de te gebruiken omgevingsdetails ontvangen. Volg deze instructies.

Daarna, uitgezochte **creeer project van malplaatje**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent1.png)

Selecteer **App Builder**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent2.png)

Voer de naam `--aepUserLdap-- vangeluw Commerce Events` in. Klik **sparen**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent4.png)

Dan moet je iets dergelijks zien.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent5.png)

Klik **+ voeg de dienst** toe en selecteer dan **API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent6.png)

Onderzoek en selecteer de API **I/O Gebeurtenissen**. Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent7.png)

Wijzig de naam van de referentie in `vangeluw Commerce Events - Production` . Klik **sparen gevormde API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent8.png)

Dan moet je dit zien. Klik **+ voeg de dienst** toe en selecteer dan **API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent9.png)

Onderzoek en selecteer API van het Beheer API van API **I/O**. Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent10.png)

Klik **sparen gevormde API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent11.png)

Dan moet je dit zien. Klik **+ voeg de dienst** toe en selecteer dan **API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent12.png)

Onderzoek en selecteer API **Adobe Commerce as a Cloud Service**. Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent13.png)

Selecteer **Server-aan-Server Authentificatie**. Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent14.png)

Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent15.png)

Selecteer **Gebrek - Cloud Manager**. Klik **sparen gevormde API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent16.png)

Dan moet je dit zien. Klik **+ voeg de dienst** toe en selecteer dan **API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent17.png)

Onderzoek en selecteer API **Adobe I/O Events voor Adobe Commerce**. Klik **daarna**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent18.png)

Klik **sparen gevormde API**.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent19.png)

Uw project is nu ingesteld en kan worden gebruikt.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent20.png)

## 1.7.1.2 De ontwikkelomgeving configureren

Als u een uitbreidbare app wilt maken, verzenden en implementeren, moet in uw lokale ontwikkelomgeving de volgende toepassingen en pakketten zijn geïnstalleerd:

- Node.js (versie 20.x of hoger)
- npm (verpakt met Node.js)
- Adobe Developer command-line interface (CLI)

Voer de volgende stappen uit als deze toepassingen of pakketten nog niet op uw computer zijn geïnstalleerd.

### Node.js &amp; npm

Ga naar [ https://nodejs.org/en/download ](https://nodejs.org/en/download). U zou dit, met een aantal eindbevelen dan moeten zien die moeten worden uitgevoerd om Node.js en npm geïnstalleerd te hebben. De hier getoonde opdrachten zijn van toepassing op MacBook.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent21.png)

Open eerst een nieuw terminalvenster. Plak en voer de opdracht op regel 2 in de schermafbeelding uit:

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash`

Voer vervolgens de opdracht op regel 5 uit in de schermafbeelding:

`\. "$HOME/.nvm/nvm.sh"`

Nadat beide opdrachten zijn uitgevoerd, voert u deze opdracht uit:

`node -v`

Er wordt een versienummer weergegeven.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent22.png)

Voer vervolgens deze opdracht uit:

`npm -v`

Als NPM nog niet is geïnstalleerd, kunt u het installeren gebruikend dit bevel: `npm install -g npm@11.9.0`.

Er wordt een versienummer weergegeven.

![ Uitbreidbaarheid GSPeM ](./images/commerceagent23.png)

Als de laatste 2 bevelen met succes een versieaantal terugkeerde, dan is uw configuratie van deze 2 mogelijkheden succesvol.

### Adobe Developer command-line interface (CLI)

Om Adobe Developer bevel-lijn interface (CLI) te installeren, stel het volgende bevel in een eindvenster in werking:

`npm install -g @adobe/aio-cli`

Het uitvoeren van deze opdracht kan een paar minuten duren. Het eindresultaat moet er ongeveer als volgt uitzien:

![ Uitbreidbaarheid GSPeM ](./images/commerceagent24.png)

De opdrachtregelinterface (CLI) van Adobe Developer is nu ook geïnstalleerd.

### Adobe Developer Command-line Interface (CLI) SDK extension for Commerce

Als u de extensie Adobe I/O SDK voor Commerce wilt installeren, voert u de volgende opdracht uit in een terminalvenster:

`npm install @adobe/aio-commerce-sdk`

![ Uitbreidbaarheid GSPeM ](./images/commerceagent25.png)

### Adobe Commerce-insteekmodules voor Adobe I/O CLI

Als u de Adobe Commerce-insteekmodules voor Adobe I/O CLI wilt installeren, voert u de volgende opdracht uit in een terminalvenster:

`aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime`

![ Uitbreidbaarheid GSPeM ](./images/commerceagent26.png)

U hebt nu de basiselementen ingesteld om een App Builder-project te kunnen uitvoeren, in combinatie met Adobe Commerce, Adobe I/O Events en Adobe I/O Runtime.

## Volgende stappen

Ga naar [ Cursor.ai van het Gebruik om uw project ](./ex2.md){target="_blank"} te ontwikkelen

Ga terug naar [ Intelligente Hulpmiddelen van de Ontwikkelaar voor Adobe Commerce ](./aiassisteddev.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
