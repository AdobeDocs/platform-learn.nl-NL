---
title: Audience Activation naar Microsoft Azure Event Hub - Definieer een Azure Function
description: Audience Activation naar Microsoft Azure Event Hub - Definieer een Azure Function
kt: 5342
doc-type: tutorial
exl-id: c39fea54-98ec-45c3-a502-bcf518e6fd06
source-git-commit: b4a7144217a68bc0b1bc70b19afcbc52e226500f
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# 2.4.6 Maak uw Microsoft Azure-project

## Het worden vertrouwd met de functies van de Hub van de Gebeurtenis

Azure Functies staan u toe om kleine stukken van code (genoemd **functies**) in werking te stellen zonder zich over toepassingsinfrastructuur ongerust te maken. Met Azure-functies biedt de cloudinfrastructuur alle up-to-date servers die u nodig hebt om uw toepassing op schaal te houden.

Een functie wordt **teweeggebracht** door een specifiek type van gebeurtenis. De gesteunde trekkers omvatten het antwoorden aan veranderingen in gegevens, die aan berichten (bijvoorbeeld de Hubs van de Gebeurtenis) antwoorden, die op een programma, of als resultaat van een HTTP- verzoek lopen.

Azure Functions is een serverloze compute service waarmee u gebeurtenisgestuurde code kunt uitvoeren zonder dat u expliciet infrastructuur hoeft aan te bieden of te beheren.

Azure Event Hubs integreert met Azure Functions voor een serverloze architectuur.

## Open de Code van Visual Studio en Logon aan Azure

De Code van Visual Studio maakt het gemakkelijk aan...

- Azure-functies definiëren en binden aan Event Hubs
- lokaal testen
- implementeren in Azure
- externe logboekfunctie uitvoeren

### Visual Studio-code openen

### Aanmelden bij Azure

Wanneer u met uw Azure rekening aanmelden die u gebruikte om in de vorige oefening te registreren, zal de Code van Visual Studio u alle middelen van de Hub van de Gebeurtenis vinden en binden.

Open de Code van Visual Studio en klik het **Azure** pictogram.

Volgende uitgezochte **Teken binnen aan Azure**:

![ 3-01-vsc-open.png ](./images/301vscopen.png)

U wordt omgeleid naar uw browser om u aan te melden. Vergeet niet de Azure-account te selecteren die u hebt gebruikt om u te registreren.

Wanneer u het volgende scherm in uw browser ziet, wordt u het programma geopend met Visual Code Studio:

![ 3-03-vsc-login-ok.png ](./images/303vscloginok.png)

Terugkeer aan Visual Code Studio (u zult de naam van uw Azure abonnement zien, bijvoorbeeld **Azure abonnement 1**):

![ 3-04-vsc-het programma geopend-in.png ](./images/304vscloggedin.png)

## Een Azure-project maken

Klik **creëren het Project van de Functie...**:

![ 3-05-vsc-create-project.png ](./images/vsc2.png)

Selecteer of creeer een lokale omslag van uw keus om het project te bewaren en **Uitgezocht** te klikken:

![ 3-06-vsc-select-folder.png ](./images/vsc3.png)

U gaat nu de wizard voor het maken van projecten openen. Klik **Javascript** als taal voor uw project:

![ 3-07-vsc-select-language.png ](./images/vsc4.png)

Dan selecteer **Model v4**.

![ 3-07-vsc-select-language.png ](./images/vsc4a.png)

Selecteer {de trekker van de Hub van de Gebeurtenis 0} Azure **als eerste de functiesjabloon van uw project:**

![ 3-08-vsc-function-template.png ](./images/vsc5.png)

Voer een naam voor de functie in, gebruik de volgende notatie `--aepUserLdap---aep-event-hub-trigger` en druk op Enter:

![ 3-09-vsc-function-name.png ](./images/vsc6.png)

Selecteer **creeer nieuwe lokale app het plaatsen**:

![ 3-10-vsc-function-local-app-setting.png ](./images/vsc7.png)

Klik om de naamruimte van de Hub van de Gebeurtenis te selecteren die u vroeger creeerde, die `--aepUserLdap---aep-enablement` wordt genoemd.

![ 3-11-vsc-function-select-namespace.png ](./images/vsc8.png)

Klik vervolgens om de gebeurtenishub te selecteren die u eerder hebt gemaakt en die de naam `--aepUserLdap---aep-enablement-event-hub` heeft.

![ 3-12-vsc-function-select-eventhub.png ](./images/vsc9.png)

Klik om **RootManageSharedAccessKey** als uw beleid van de Hub van de Gebeurtenis te selecteren:

![ 3-13-vsc-function-select-eventhub-policy.png ](./images/vsc10.png)

Selecteer **toevoegen aan werkruimte** op hoe te om uw project te openen:

![ 3-15-vsc-project-toe:voegen-aan-werkspace.png ](./images/vsc12.png)

Dan krijg je een bericht als deze. In dat geval, klik ja **, vertrouw ik de auteurs**.

![ 3-15-vsc-project-toe:voegen-aan-werkspace.png ](./images/vsc12a.png)

Nadat u een project hebt gemaakt, opent u het bestand `--aepUserLdap---aep-event-hub-trigger.js` in de editor:

![ 3-16-vsc-open-index-js.png ](./images/vsc13.png)

De lading die door Adobe Experience Platform naar uw Hub van de Gebeurtenis wordt verzonden zal als dit kijken:

```json
{
  "identityMap": {
    "ecid": [
      {
        "id": "36281682065771928820739672071812090802"
      }
    ]
  },
  "segmentMembership": {
    "ups": {
      "94db5aed-b90e-478d-9637-9b0fad5bba11": {
        "createdAt": 1732129904025,
        "lastQualificationTime": "2024-11-21T07:33:52Z",
        "mappingCreatedAt": 1732130611000,
        "mappingUpdatedAt": 1732130611000,
        "name": "vangeluw - Interest in Plans",
        "status": "realized",
        "updatedAt": 1732129904025
      }
    }
  }
}
```

Werk de code in uw Code van Visual Studio `--aepUserLdap---aep-event-hub-trigger.js` met de hieronder code bij. Deze code zal worden uitgevoerd telkens als CDP in real time publiekskwalificaties naar uw bestemming van de Hub van de Gebeurtenis verzendt. In dit voorbeeld gaat de code alleen over het weergeven van de binnenkomende lading, maar u kunt zich elke aanvullende functie voorstellen om de publiekskwalificaties in real-time te verwerken en het ecosysteem van de gegevenspijpleiding verder te gebruiken.

Regel 11 in het bestand `--aepUserLdap---aep-event-hub-trigger.js` geeft het volgende aan:

```javascript
context.log('Event hub message:', message);
```

Wijzig regel 11 in `--aepUserLdap---aep-event-hub-trigger.js` om er als volgt uit te zien:

```javascript
context.log('Event hub message:', JSON.stringify(message));
```

De totale lading zou dan als volgt moeten zijn:

```javascript
const { app } = require('@azure/functions');

app.eventHub('--aepUserLdap---aep-event-hub-trigger', {
    connection: '--aepUserLdap--aepenablement_RootManageSharedAccessKey_EVENTHUB',
    eventHubName: '--aepUserLdap---aep-enablement-event-hub',
    cardinality: 'many',
    handler: (messages, context) => {
        if (Array.isArray(messages)) {
            context.log(`Event hub function processed ${messages.length} messages`);
            for (const message of messages) {
                context.log('Event hub message:', message);
            }
        } else {
            context.log('Event hub function processed message:', messages);
        }
    }
});
```


Het resultaat moet er als volgt uitzien:

![ 3-16b-vsc-geef-index-js.png uit ](./images/vsc1.png)

## Azure Project uitvoeren

Nu is het tijd om uw project uit te voeren. In dit stadium zullen wij niet het project aan Azure opstellen. Wij zullen het plaatselijk in zuivert wijze in werking stellen. Selecteer het pictogram Uitvoeren en klik op de groene pijl.

![ 3-17-vsc-looppas-project.png ](./images/vsc14.png)

De eerste keer u in werking stelt u zuivert wijze, zult u een Azure opslagrekening moeten vastmaken, **Uitgezochte opslagrekening** klikken.

![ 3-17-vsc-looppas-project.png ](./images/vsc14a.png)

en selecteer vervolgens de opslagaccount die u eerder hebt gemaakt, met de naam `--aepUserLdap--aepstorage` .

![ 3-17-vsc-looppas-project.png ](./images/vsc14b.png)

Uw project is nu in gebruik en maakt een lijst van voor gebeurtenissen in de Hub van de Gebeurtenis. In de volgende oefening zult u gedrag op de CitiSignal demo website aantonen die u voor publiek zal kwalificeren. Dientengevolge zult u een nuttige lading van de publiekskwalificatie in de terminal van uw de trekkerfunctie van de Hub van de Gebeurtenis ontvangen.

![ 3-24-vsc-application-stop.png ](./images/vsc18.png)

## Azure-project stoppen

Om uw project tegen te houden, ga naar de KORTE **KNOPSTART** in VSC, klik op de pijl op uw lopend project en klik dan **Einde**.

![ 3-24-vsc-application-stop.png ](./images/vsc17.png)

Volgende Stap: [ 2.4.7 scenario van begin tot eind ](./ex7.md)

[Terug naar module 2.4](./segment-activation-microsoft-azure-eventhub.md)

[Terug naar alle modules](./../../../overview.md)
