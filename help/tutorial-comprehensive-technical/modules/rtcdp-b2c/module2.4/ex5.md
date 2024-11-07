---
title: Segmentactivering naar Microsoft Azure Event Hub - Een Azure Function definiëren
description: Segmentactivering naar Microsoft Azure Event Hub - Een Azure Function definiëren
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 2.4.5 Uw Microsoft Azure-project maken

## 2.4.5.1 Het worden vertrouwd met de functies van de Hub van de Gebeurtenis

Azure Functies staat u toe om kleine stukken van code (genoemd **functies**) in werking te stellen zonder zich over toepassingsinfrastructuur ongerust te maken. Met Azure-functies biedt de cloudinfrastructuur alle up-to-date servers die u nodig hebt om uw toepassing op schaal te houden.

Een functie wordt **teweeggebracht** door een specifiek type van gebeurtenis. De gesteunde trekkers omvatten het antwoorden aan veranderingen in gegevens, die aan berichten (bijvoorbeeld de Hubs van de Gebeurtenis) antwoorden, die op een programma, of als resultaat van een HTTP- verzoek lopen.

Azure Functions is een serverloze compute service waarmee u gebeurtenisgestuurde code kunt uitvoeren zonder dat u expliciet infrastructuur hoeft aan te bieden of te beheren.

Azure Event Hubs integreert met Azure Functions voor een serverloze architectuur.

## 2.4.5.2 Open Visual Studio Code en Logon aan Azure

De Code van Visual Studio maakt het gemakkelijk aan...

- Azure-functies definiëren en binden aan Event Hubs
- lokaal testen
- implementeren in Azure
- externe logboekfunctie uitvoeren

### Visual Studio-code openen

Om de Code van Visual Studio te openen ga **visueel** in het onderzoek van uw werkend systeem (Spotlight onderzoek op OSX, Onderzoek in Taakbalk van Venster) in. Als u het niet vindt, moet u de stappen herhalen die in [ worden geschetst Uitoefening 0 - Voorwaarden ](./ex0.md).

![ visueel-studio-code-icon.png ](./images/visual-studio-code-icon.png)

### Aanmelden bij Azure

Wanneer u met uw Azure rekening aanmeldt die u gebruikte om in [ uit te oefenen 0 - prerequisites ](./ex0.md), zal de Code van Visual Studio u alle middelen van de Hub van de Gebeurtenis vinden en binden.

Klik het **Azure** pictogram in de Code van Visual Studio. Als u die optie niet hebt, kan er iets misgegaan zijn met de installatie van de vereiste extensies.

Volgende uitgezochte **Teken binnen aan Azure**:

![ 3-01-vsc-open.png ](./images/3-01-vsc-open.png)

U wordt omgeleid naar uw browser om u aan te melden. Vergeet niet de Azure-account te selecteren die u hebt gebruikt om u te registreren.

![ 3-02-vsc-oogst-account.png ](./images/3-02-vsc-pick-account.png)

Wanneer u het volgende scherm in uw browser ziet, wordt u het programma geopend met Visual Code Studio:

![ 3-03-vsc-login-ok.png ](./images/3-03-vsc-login-ok.png)

Terugkeer aan Visual Code Studio (u zult de naam van uw Azure abonnement zien, bijvoorbeeld **Azure abonnement 1**):

![ 3-04-vsc-het programma geopend-in.png ](./images/3-04-vsc-logged-in.png)

## 2.4.5.3 Een Azure-project maken

Wanneer u over **Azure abonnement 1** beweegt, zal een menu boven de sectie verschijnen, uitgezocht **Nieuw Project creëren..**:

![ 3-05-vsc-create-project.png ](./images/vsc2.png)

Selecteer een lokale omslag van uw keus om het project te bewaren en **Uitgezocht** te klikken:

![ 3-06-vsc-select-folder.png ](./images/vsc3.png)

U gaat nu de wizard voor het maken van projecten openen. Selecteer **Javascript** als taal voor uw project:

![ 3-07-vsc-select-language.png ](./images/vsc4.png)

Selecteer {de trekker van de Hub van de Gebeurtenis 0} Azure **als eerste de functiesjabloon van uw project:**

![ 3-08-vsc-function-template.png ](./images/vsc5.png)

Voer een naam voor de functie in, gebruik de volgende notatie `--demoProfileLdap---aep-event-hub-trigger` en druk op Enter:

![ 3-09-vsc-function-name.png ](./images/vsc6.png)

Selecteer **creeer nieuwe lokale app het plaatsen**:

![ 3-10-vsc-function-local-app-setting.png ](./images/vsc7.png)

Selecteer een gebeurtenishub namespace, zou u de Hub van de Gebeurtenis moeten zien die u in **Uitoefening 2** bepaalde. In dit voorbeeld is de Hub van de Gebeurtenis namespace **vangeluw-aep-enablement**:

![ 3-11-vsc-function-select-namespace.png ](./images/vsc8.png)

Selecteer uw Hub van de Gebeurtenis, zou u de Hub van de Gebeurtenis moeten zien die u in **Uitoefening 2** bepaalde. In mijn geval dat **vangeluw-aep-enablement-event-hub** is:

![ 3-12-vsc-function-select-eventhub.png ](./images/vsc9.png)

Selecteer **RootManageSharedAccessKey** als uw beleid van de Hub van de Gebeurtenis:

![ 3-13-vsc-function-select-eventhub-policy.png ](./images/vsc10.png)

Ga binnen om **$Default** te gebruiken:

![ 3-14-vsc-eventhub-consumer-group.png ](./images/vsc11.png)

Selecteer **toevoegen aan werkruimte** op hoe te om uw project te openen:

![ 3-15-vsc-project-toe:voegen-aan-werkspace.png ](./images/vsc12.png)

Nadat u project wordt gecreeerd, klik op **index.js** om het dossier te hebben open in de redacteur:

![ 3-16-vsc-open-index-js.png ](./images/vsc13.png)

De nuttige lading die door Adobe Experience Platform naar uw Hub van de Gebeurtenis wordt verzonden zal segment id&#39;s omvatten:

```json
[{
"segmentMembership": {
"ups": {
"ca114007-4122-4ef6-a730-4d98e56dce45": {
"lastQualificationTime": "2020-08-31T10:59:43Z",
"status": "realized"
},
"be2df7e3-a6e3-4eb4-ab12-943a4be90837": {
"lastQualificationTime": "2020-08-31T10:59:56Z",
"status": "realized"
},
"39f0feef-a8f2-48c6-8ebe-3293bc49aaef": {
"lastQualificationTime": "2020-08-31T10:59:56Z",
"status": "realized"
}
}
},
"identityMap": {
"ecid": [{
"id": "08130494355355215032117568021714632048"
}]
}
}]
```

Vervang de code in index.js van uw Code van Visual Studio met de hieronder code. Deze code zal worden uitgevoerd telkens als CDP in real time segmentkwalificaties naar uw bestemming van de Hub van de Gebeurtenis verzendt. In ons voorbeeld gaat de code alleen over het weergeven en verbeteren van de ontvangen lading. Maar je kunt je een of andere functie voorstellen om segmentkwalificaties in real-time te verwerken.

```javascript
// Marc Meewis - Solution Consultant Adobe - 2020
// Adobe Experience Platform Enablement - Module 13

// Main function
// -------------
// This azure function is fired for each segment activated to the Adobe Exeperience Platform Real-time CDP Azure 
// Eventhub destination
// This function enriched the received segment payload with the name fo the segment. 
// You can replace this function with any logic that is require to process and deliver
// Adobe Experience Platform segments in real-time to any application or platform that 
// would need to act upon an AEP segment qualiification.
// 

module.exports = async function (context, eventHubMessages) {

    return new Promise (function (resolve, reject) {

        context.log('Message : ' + JSON.stringify(eventHubMessages, null, 2));

        resolve();

    });    

};
```

Het resultaat moet er als volgt uitzien:

![ 3-16b-vsc-geef-index-js.png uit ](./images/vsc1.png)

## 2.4.5.4 Run Azure Project

Nu is het tijd om uw project uit te voeren. In dit stadium zullen wij niet het project aan Azure opstellen. Wij zullen het plaatselijk in zuivert wijze in werking stellen. Selecteer het pictogram Uitvoeren en klik op de groene pijl.

![ 3-17-vsc-looppas-project.png ](./images/vsc14.png)

De eerste keer u in werking stelt u zuivert wijze, zult u een Azure opslagrekening moeten vastmaken, **Uitgezochte opslagrekening** klikken.

![ 3-17-vsc-looppas-project.png ](./images/vsc15.png)

Van de lijst van opslagrekeningen, selecteer die u als deel van [ 13.1.4 Opstelling uw Azure Rekening van de Opslag ](./ex1.md) hebt gecreeerd. Uw opslagrekening wordt genoemd `--demoProfileLdap--aepstorage`, bijvoorbeeld: **mmewisaepstorage**.

![ 3-22-vsc-select-storage-account.png ](./images/vsc16.png)

Uw project is nu in gebruik en maakt een lijst van voor gebeurtenissen in de Hub van de Gebeurtenis. In de volgende oefening zult u gedrag op de website van de demo van de Luma aantonen die u voor die segmenten zal kwalificeren. Dientengevolge zult u een lading van de segmentkwalificatie in de terminal van uw de trekkerfunctie van de Hub van de Gebeurtenis ontvangen:

![ 3-23-vsc-application-started.png ](./images/vsc17.png)

## 2.4.5.5 Stop Azure Project

Om uw project tegen te houden, selecteer het **Eind** lusje, klik in het eindvenster en druk **CMD-C** op OSX of **CTRL-C** op Vensters:

![ 3-24-vsc-application-stop.png ](./images/vsc18.png)

Volgende Stap: [ 2.4.6 scenario van begin tot eind ](./ex6.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
