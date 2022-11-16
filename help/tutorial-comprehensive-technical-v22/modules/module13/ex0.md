---
title: Segmentactivering naar Microsoft Azure Event Hub - Configureer uw Microsoft Azure-omgeving
description: Segmentactivering naar Microsoft Azure Event Hub - Configureer uw Microsoft Azure-omgeving
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 79711c1a-674c-4233-9c6c-af3bad6d0e0c
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 13.0 Uw omgeving configureren

## 13.0.1 Een Azure-abonnement maken

>[!NOTE]
>
>Als u al een Azure-abonnement hebt, kunt u deze stap overslaan. Gelieve in dat geval de oefening 13.0.2 voort te zetten.

Ga naar [https://portal.azure.com](https://portal.azure.com) en meld u aan met uw Azure-account. Als je er geen hebt, gebruik dan je persoonlijke e-mailadres om je Azure-account te maken.

![02-azure-portal-email.png](./images/02-azure-portal-email.png)

Na succesvolle login zult u het volgende scherm zien:

![03-azure-Login.png](./images/03-azure-logged-in.png)

Klik op het menu aan de linkerkant en selecteer **Alle bronnen**, wordt het Azure-abonnementsscherm weergegeven als u nog niet bent geabonneerd. Selecteer in dat geval **Begin met een Azure gratis proefversie**.

![04-azure-start-subscribe.png](./images/04-azure-start-subscribe.png)

Vul het Azure-abonnementsformulier in, geef uw mobiele telefoon en creditcard op voor activering (u hebt 30 dagen een gratis label en u wordt geen kosten in rekening gebracht, tenzij u een upgrade uitvoert):

![05-azure-subscription-form.png](./images/05-azure-subscription-form.png)

Als het abonnementsproces is voltooid, kunt u het beste gaan:

![06-azure-subscription-ok.png](./images/06-azure-subscription-ok.png)


## 13.0.2 Installeer Visual Code Studio

U zult Microsoft Visual Code Studio gebruiken om uw Azure Project te beheren. U kunt het downloaden via [deze koppeling](https://code.visualstudio.com/download). Volg de installatie-instructies voor uw specifieke besturingssysteem op dezelfde website.

## 13.0.3 Visual Code-extensies installeren

Installeer de Azure Functies voor de Code van Visual Studio van [https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions). Klik op de knop Installeren:

![07-azure-code-extension-install.png](./images/07-azure-code-extension-install.png)

Installeer Azure Account en Sign In for Visual Studio Code van [https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account](https://marketplace.visualstudio.com/items?itemName=ms-vscode.azure-account). Klik op de knop Installeren:

![08-azure-account-extension-install.png](./images/08-azure-account-extension-install.png)

## 13.0.4 Install node.js

>[!NOTE]
>
>Als node.js al is geïnstalleerd, kunt u deze stap overslaan. Gelieve in dat geval de oefening 13.0.5 voort te zetten.

### macOS

Zorg ervoor dat u [Homebrew](https://brew.sh/) eerst geïnstalleerd. Volg de instructies [hier](https://brew.sh/).

![Knooppunt](./images/brew.png)

Nadat u Homebrew hebt geïnstalleerd, voert u deze opdracht uit:

```javascript
brew install node
```

### Windows

Download de [Windows Installer](https://nodejs.org/en/#home-downloadhead) rechtstreeks van de [nodejs.org](https://nodejs.org/en/) website.

## 13.0.5 Verify node.js version

Voor deze module, moet u node.js versie 12 geïnstalleerd hebben. Elke andere versie van node.js kan problemen veroorzaken met oefening 13.5.

Verifieer nu uw versie van node.js voordat u verdergaat.

Voer deze opdracht uit om de versie van node.js te verifiëren:

```javascript
node -v
```

Als uw versie onder of boven de 12 ligt, moet u een upgrade uitvoeren of de kwaliteit verlagen.

### Upgrade/downgrade node.js-versie op macOS

Zorg ervoor dat u over het pakket beschikt **n** geïnstalleerd.

Het pakket installeren **n** Deze opdracht uitvoeren:

```javascript
sudo npm install -g n
```

Als uw versie onder of boven versie 12 ligt, voert u deze opdracht uit om een upgrade uit te voeren of de upgrade uit te voeren:

```javascript
sudo n 12.6.0
```

### Upgrade/downgrade node.js-versie in Windows

Verwijder node.js uit Windows > Configuratiescherm > Software.

De vereiste versie installeren vanuit de [nodejs.org](https://nodejs.org/en/) website.

## 13.0.6 NPM-pakket installeren: verzoek

U moet het pakket installeren **verzoek** als deel van uw node.js opstelling.

Het pakket installeren **verzoek** Deze opdracht uitvoeren:

```javascript
npm install request
```


Volgende stap: [13.1 Configureer uw Microsoft Azure EventHub-omgeving](./ex1.md)

[Ga terug naar module 13](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../overview.md)
