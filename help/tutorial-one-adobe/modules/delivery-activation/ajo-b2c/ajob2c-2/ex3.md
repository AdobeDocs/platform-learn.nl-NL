---
title: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
description: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
kt: 5342
doc-type: tutorial
exl-id: 92752e84-3bbe-4d11-b187-bd9fdbbee709
source-git-commit: e3d3b8e3abdea1766594eca53255df024129cb2c
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# 3.2.3 Een aangepaste handeling definiëren

In deze oefening, zult u een douaneactie creëren om een bericht naar een kanaal van Slack te verzenden.

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak** zijn.`--aepSandboxName--`

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

U gebruikt nu een bestaand Slack-kanaal en verzendt berichten naar dat Slack-kanaal. Slack heeft een gebruiksvriendelijke API en u gebruikt Adobe Journey Optimizer om de API te activeren.

![&#x200B; Demo &#x200B;](./images/slack.png)

In het linkermenu, scrol neer en klik **Configuraties**. Daarna, klik **leiden** knoop onder **Acties**.

![&#x200B; Demo &#x200B;](./images/menuactions.png)

U zult dan de **lijst van Acties** zien. Klik **tot Actie** leiden.

![&#x200B; Demo &#x200B;](./images/acthome.png)

Er verschijnt een leeg actiepopup.

![&#x200B; Demo &#x200B;](./images/emptyact.png)

Gebruik `--aepUserLdap--TextSlack` als naam voor de handeling.

Stel Beschrijving in op: `Send Message to Slack` .

Voor de **Configuratie URL**, gebruik dit:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>De bovenstaande URL verwijst naar een AWS Lambda-functie die uw verzoek doorstuurt naar het Slack-kanaal zoals hierboven vermeld. Dit wordt gedaan om de toegang tot een Slack-kanaal in eigendom van Adobe te beschermen. Als u uw eigen kanaal van Slack hebt, zou u een Slack App door [&#x200B; https://api.slack.com/ &#x200B;](https://api.slack.com/) moeten tot stand brengen, dan moet u een Inkomende Webhaak in die app van Slack tot stand brengen, en dan bovengenoemde URL door uw Inkomende URL van Webhaak vervangen.

![&#x200B; Demo &#x200B;](./images/slackname.png)

**Authentificatie** zou aan **Geen Authentificatie** moeten worden geplaatst.

![&#x200B; Demo &#x200B;](./images/slackauth.png)

Onder **Payloads**, moet u bepalen welke gebieden naar Slack zouden moeten worden verzonden. Logischerwijze wil je dat Adobe Journey Optimizer en Adobe Experience Platform het brein van personalisatie zijn, dus de tekst die naar Slack moet worden verzonden, moet door Adobe Journey Optimizer worden gedefinieerd en vervolgens naar Slack worden gestuurd voor uitvoering.

Voor het **Verzoek**, klik **uitgeven het pictogram van de Lading**.

![&#x200B; Demo &#x200B;](./images/slackmsgp.png)

Dan zie je een leeg popup-venster.

![&#x200B; Demo &#x200B;](./images/slackmsgpopup.png)

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

Dan zie je dit. Klik **sparen**.

![&#x200B; Demo &#x200B;](./images/slackmsgpopup1.png)

De rol omhoog en klikt **sparen** één meer tijd om uw actie te bewaren.

![&#x200B; Demo &#x200B;](./images/slackmsgpopup3.png)

Uw douaneactie is nu een deel van de **lijst van Acties**.

![&#x200B; Demo &#x200B;](./images/slackdone.png)

U hebt gebeurtenissen, externe gegevensbronnen en acties gedefinieerd. Vervolgens combineer je dat allemaal op één reis.

## Volgende stappen

Ga naar [&#x200B; 3.2.4 creeer uw reis en berichten &#x200B;](./ex4.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Journey Optimizer: Externe gegevensbronnen en douaneacties &#x200B;](journey-orchestration-external-weather-api-sms.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}
