---
title: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
description: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
kt: 5342
doc-type: tutorial
exl-id: d9bdc4c6-7539-4646-9b75-f397b792479f
source-git-commit: c531412a2c0a5c216f49560e01fb26b9b7e71869
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# 3.2.3 Een aangepaste handeling definiëren

In deze oefening, zult u een douaneactie creëren om een bericht naar een kanaal van de Slack te verzenden.

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.1/images/acoptriglp.png)

U zult nu een bestaand kanaal van de Slack gebruiken en berichten verzenden naar dat kanaal van de Slack. Slack heeft een eenvoudig te gebruiken API en u gebruikt Adobe Journey Optimizer om de API ervan te activeren.

![ Demo ](./images/slack.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Acties**.

![ Demo ](./images/menuactions.png)

U zult dan de **lijst van Acties** zien. Klik **tot Actie** leiden.

![ Demo ](./images/acthome.png)

Er verschijnt een leeg actiepopup.

![ Demo ](./images/emptyact.png)

Gebruik `--aepUserLdap--TextSlack` als naam voor de handeling.

Stel Beschrijving in op: `Send Message to Slack` .

Voor de **Configuratie URL**, gebruik dit:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>De bovenstaande URL verwijst naar een AWS Lambda-functie die uw verzoek doorstuurt naar het Slack kanaal zoals hierboven vermeld. Dit wordt gedaan om toegang tot een Adobe-Bezit kanaal van de Slack te beschermen. Als u uw eigen kanaal van de Slack hebt, zou u een SlackApp door [ https://api.slack.com/ ](https://api.slack.com/) moeten tot stand brengen, dan moet u een Inkomende Webhaak in die SlackApp tot stand brengen, en dan bovengenoemde URL door uw Inkomende URL van Webhaak vervangen.

![ Demo ](./images/slackname.png)

U hoeft de koptekstvelden niet te wijzigen.

![ Demo ](./images/slackurl.png)

**Authentificatie** zou aan **Geen Authentificatie** moeten worden geplaatst.

![ Demo ](./images/slackauth.png)

Onder **Payloads**, moet u bepalen welke gebieden naar Slack zouden moeten worden verzonden. Logischerwijze wil je dat Adobe Journey Optimizer en Adobe Experience Platform het brein van personalisatie zijn, dus de tekst die naar Slack moet worden gestuurd, moet door Adobe Journey Optimizer worden gedefinieerd en vervolgens naar de Slack worden gestuurd voor uitvoering.

Voor het **Verzoek**, klik **uitgeven het pictogram van de Lading**.

![ Demo ](./images/slackmsgp.png)

Dan zie je een leeg popup-venster.

![ Demo ](./images/slackmsgpopup.png)

Kopieer de onderste tekst en plak deze in het lege pop-upvenster.

```json
{
 "text": {
  "toBeMapped": true,
  "dataType": "string",
  "label": "textToSlack"
 }
}
```

U zult dan dit zien:

![ Demo ](./images/slackmsgpopup1.png)

De rol omhoog en klikt **sparen** één meer tijd om uw actie te bewaren.

![ Demo ](./images/slackmsgpopup3.png)

Uw douaneactie is nu een deel van de **lijst van Acties**.

![ Demo ](./images/slackdone.png)

U hebt gebeurtenissen, externe gegevensbronnen en acties gedefinieerd. Laten we dat allemaal op één reis consolideren.

Volgende Stap: [ 3.2.4 leidt tot uw reis en berichten ](./ex4.md)

[Terug naar module 3.2](journey-orchestration-external-weather-api-sms.md)

[Terug naar alle modules](../../../overview.md)
