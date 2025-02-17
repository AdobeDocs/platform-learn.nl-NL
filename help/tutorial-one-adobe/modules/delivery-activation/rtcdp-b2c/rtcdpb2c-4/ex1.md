---
title: Segmentactivering naar Microsoft Azure Event Hub - Configureer uw Microsoft Azure-omgeving
description: Segmentactivering naar Microsoft Azure Event Hub - Configureer uw Microsoft Azure-omgeving
kt: 5342
doc-type: tutorial
exl-id: 568ba33f-cdde-48d9-9991-78d4e29be7e7
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 2.4.1 Uw omgeving configureren

## Een Azure-abonnement maken

>[!NOTE]
>
>Als u al een Azure-abonnement hebt, kunt u deze stap overslaan. Ga in dat geval verder met de volgende exercitie.

Ga naar [ https://portal.azure.com ](https://portal.azure.com) en login met uw Azure rekening. Als je er geen hebt, gebruik dan je persoonlijke e-mailadres om je Azure-account te maken.

![ 02-azure-portal-email.png ](./images/02azureportalemail.png)

Na succesvolle login zult u het volgende scherm zien:

![ 03-azure-gelogd-in.png ](./images/03azureloggedin.png)

Klik op het aan linkermenu en selecteer **Alle Middelen**, zal het Azure abonnementsscherm verschijnen als u nog niet wordt ingetekend. In dat geval uitgezocht **Begin met een Azure vrije Proef**.

![ 04-azure-start-subscribe.png ](./images/04azurestartsubscribe.png)

Vul het Azure-abonnementsformulier in, geef uw mobiele telefoon en creditcard op voor activering (u hebt 30 dagen een gratis label en u wordt geen kosten in rekening gebracht, tenzij u een upgrade uitvoert).

Als het abonnementsproces is voltooid, kunt u het beste gaan:

![ 06-azure-subscription-ok.png ](./images/06azuresubscriptionok.png)

## Visual Code Studio installeren

U zult Microsoft Visual Code Studio gebruiken om uw Azure Project te beheren. U kunt het via [ deze verbinding ](https://code.visualstudio.com/download) downloaden. Volg de installatie-instructies voor uw specifieke besturingssysteem op dezelfde website.

## Visuele codeextensies installeren

Installeer de Azure Functies voor de Code van Visual Studio van [ https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions ](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions). Klik op de knop Installeren:

![ 07-azure-code-uitbreiding-install.png ](./images/07azurecodeextensioninstall.png)

Installeer Azure Account en Sign-In voor de Code van Visual Studio van [ https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account). Klik op de knop Installeren:

![ 08-azure-account-extension-install.png ](./images/08azureaccountextensioninstall.png)

## Knooppunt.js installeren

>[!NOTE]
>
>Als node.js al is geïnstalleerd, kunt u deze stap overslaan. Ga in dat geval verder met de volgende exercitie.

### macOS

Zorg ervoor om [ eerst geïnstalleerde Homebrew ](https://brew.sh/) te hebben. Volg hier de instructies [ ](https://brew.sh/).

![ Knoop ](./images/brew.png)

Nadat u Homebrew hebt geïnstalleerd, voert u deze opdracht uit:

```javascript
brew install node
```

### Windows

Download direct de [ Installateur van Vensters ](https://nodejs.org/en/#home-downloadhead) van [ nodejs.org ](https://nodejs.org/en/) website.

## Versie van node.js verifiëren

Voor deze module, moet u node.js versie 18 geïnstalleerd hebben. Elke andere versie van node.js kan problemen veroorzaken met deze oefening.

Verifieer nu uw versie van node.js voordat u verdergaat.

Voer deze opdracht uit om de versie van node.js te verifiëren:

```javascript
node -v
```

Als uw versie onder of boven de 18 ligt, moet u een upgrade uitvoeren of de kwaliteit verlagen.

### Upgrade/downgrade node.js-versie op macOS

Zorg ervoor dat u het pakket **n** geïnstalleerd hebt.

Om het pakket **n** te installeren, stel dit bevel in werking:

```javascript
sudo npm install -g n
```

Als uw versie onder of boven versie 12 ligt, voert u deze opdracht uit om een upgrade uit te voeren of de upgrade uit te voeren:

```javascript
sudo n 18
```

### Upgrade/downgrade node.js-versie in Windows

Verwijder node.js uit Windows > Configuratiescherm > Software.

Het installeren van de vereiste versie van de {](https://nodejs.org/en/) website 0} nodejs.org.[

## NPM-pakket installeren: verzoek

U moet het pakket **verzoek** als deel van uw knoop.js opstelling installeren.

Om het pakket **verzoek** te installeren, stel dit bevel in werking:

```javascript
npm install request
```

## Azure Functions Core Tools installeren:

```
brew tap azure/functions
brew install azure-functions-core-tools@4
```

## Volgende stappen

Ga naar [ 2.4.2 vorm uw milieu van Microsoft Azure EventHub ](./ex2.md){target="_blank"}

Ga terug naar [ Real-Time CDP: Audience Activation aan Microsoft Azure de Hub van de Gebeurtenis ](./segment-activation-microsoft-azure-eventhub.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
